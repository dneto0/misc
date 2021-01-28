# [WGSL] Struct Alignment Proposal

## Design principles

* Provides a single default layout for any datatype (primitive, struct, array).
  * It is always valid for storage buffers.
  * The rules are practical - not too wasteful.
  * The rules are forward-looking - std140/“extended” is considered legacy.
* Struct layout is defined in terms of “size” and “layout” with no additional rules. \
  The offset of a member is always exactly: \
	<code>roundUp(alignment <sub>member</sub>, offset <sub>previous member</sub> + size <sub>previous member</sub>)</code>.
* Datatypes may diverge from the default layout, by using annotations to override the default alignment, size, and array stride values. The offset formula stays the same, but uses the new values. \
  `[[align(), size()]]` on struct members. \
  `[[stride()]]` on array types.
  * In most cases, this is required to make a datatype conform to the restrictions of uniform buffers.
  * It can also be used to specify layouts denser than the default, e.g. to use with future optional capabilities (e.g. “scalar” layout).
* _Rules_ for valid uniform/storage buffer layouts are defined separately from the _algorithm_ that defines the default layout.


## Proposal

## Default sizes and alignments

These are the default values if `[[size()]]` or `[[align()]]` aren’t specified. \
They’re the same as the `Align(S, storage)` and `Extent(V, storage)` in the current WGSL draft spec.

| Type                              | Alignment (bytes)        | Size (bytes)                                                       |
|-----------------------------------|--------------------------|--------------------------------------------------------------------|
| `f32`                             | 4                        | 4                                                                  |
| `i32`                             | 4                        | 4                                                                  |
| `u32`                             | 4                        | 4                                                                  |
| `vec2`                            | 8                        | 8                                                                  |
| `vec3`                            | 16                       | 12                                                                 |
| `vec4`                            | 16                       | 16                                                                 |
| `[[stride(S)]]`<br> `array<T, N>` | `alignof(T)`             | `N * S`                                                            |
| `[[stride(S)]]`<br> `array<T>`    | `alignof(T)`             | undefined                                                          |
| `matXxY` (col-major)              | `alignof(vecY)`          | `sizeof(array<vecY, X>)`                                           |
| `mat2x2`                          | 8                        | 16                                                                 |
| `mat3x2`                          | 8                        | 24                                                                 |
| `mat4x2`                          | 8                        | 32                                                                 |
| `mat2x3`                          | 16                       | 32                                                                 |
| `mat3x3`                          | 16                       | 48                                                                 |
| `mat4x3`                          | 16                       | 64                                                                 |
| `mat2x4`                          | 16                       | 32                                                                 |
| `mat3x4`                          | 16                       | 48                                                                 |
| `mat4x4`                          | 16                       | 64                                                                 |
| `struct S`                        | max of member alignments | `roundUp(alignof(S), offsetof(last member) + sizeof(last member))` |


## Default array stride
| Type          | Stride (bytes)                   |
|---------------|----------------------------------|
| `array<T, N>` | `roundUp(alignof(T), sizeof(T))` |


A matrix is laid out so that a program can form a reference to each of its column vectors, and that reference (pointer) is like a reference to a regular column vector.
In particular, the column vector must be aligned.

### Structure Layouts

The rules for aligning a struct field:
* The first field is always at offset 0 of the structure.
* Subsequent fields have an offset that is with the byte offset <code>roundUp(alignment <sub>member</sub>, offset <sub>previous member</sub> + size <sub>previous member</sub>)</code>. 
* Structures nested inside other structures will be aligned to the maximum alignment of the inner struct's fields. 

Example:

```rust
/*             align(8)  size(24)  */ struct A {       
/* offset(0)   align(4)  size(4)   */     u: f32;
/* offset(4)   align(4)  size(4)   */     v: f32;
/* offset(8)   align(8)  size(8)   */     w: vec2<f32>;
/* offset(16)  align(4)  size(4)   */     x: f32;
/* offset(20)  align(1)  size(4)          -- struct size padding -- */ 
                                     }

/*             align(16) size(112) */ struct B {
/* offset(0)   align(8)  size(8)   */     a: vec2<f32>;
/* offset(8)   align(1)  size(8)          -- field alignment padding -- */ 
/* offset(16)  align(16) size(12)  */     b: vec3<f32>;
/* offset(28)  align(4)  size(4)   */     c: f32;
/* offset(32)  align(4)  size(4)   */     d: f32;
/* offset(36)  align(1)  size(12)         -- field alignment padding -- */ 
/* offset(40)  align(8)  size(24)  */     e: A;
/* offset(64)  align(16) size(12)  */     f: vec3<f32>;
/* offset(76)  align(1)  size(4)          -- field alignment padding -- */ 
/* offset(80)  align(8)  size(24)  */     g: A;
/* offset(104) align(1)  size(112)        -- struct size padding -- */ 
                                     }
```

Observe that `c`, packs into end of the `vec3` of `b`. With the fixed type alignment and sizes of this initial proposal, scalars can be packed into the *end* of a vector, not the front.

Struct members may be annotated with `[[align(n)]]` and / or `[[size(n)]]` attributes to override the defaults for each member.

> Note: We may wish to also annotate user defined types (`struct`, `type` aliases) with the same attributes. These would affect all uses of the type, but are still overridable with per-member attributes.

