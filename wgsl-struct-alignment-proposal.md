# [WGSL] Struct Alignment Proposal

## Goals

* Declare a default set of struct member layout rules which are simple enough to understand so that we do not require explicit `[[offset(N)]]` annotations.
* Layouts work with acceptable performance for all backends.
* Layouts do not require explicit padding in order to compile.
* Struct layouts allow for scalar-into-vector packing.
* More advanced packing rules can be added in the future (post MVP)

## Proposal

The WGSL specification will declare that all types have a natural alignment and size:

| type        | align             | size                                    |
|-------------|-------------------|-----------------------------------------|
| f32         | 4                 | 4                                       |
| i32         | 4                 | 4                                       |
| u32         | 4                 | 4                                       |
| vec2        | 8                 | 8                                       |
| vec3        | 16                | 12                                      |
| vec4        | 16                | 16                                      |
| mat2x2      | 8                 | 16                                      |
| mat2x3      | 8                 | 32                                      |
| mat2x4      | 8                 | 32                                      |
| mat3x2      | 16                | 32                                      |
| mat3x3      | 16                | 48                                      |
| mat3x4      | 16                | 64                                      |
| mat4x2      | 16                | 32                                      |
| mat4x3      | 16                | 48                                      |
| mat4x4      | 16                | 64                                      |
| struct      | 16                | last element offset + last element size |
| array<T, N> | element alignment | N * element size rounded to element alignment |


> Note: Unlike vectors, matrix size have been rounded to alignment, preventing packing. This was to simplify the size rules. Debatable decision.

The rules for aligning a struct field:
* Structures themselves are always 16 byte aligned.
* The first field is always at offset 0 of the structure.
* Subsequent fields have an offset that is the next alignment after the previous field offset + previous field size. 
* Structures nested inside other structures will be aligned to a 16 bytes, but fields can otherwise be treated as inlined 
  (there's no special rules for padding at the end of a nested structure).  

Example:

```c++
/*            align(16) size(8)  */ struct A {       
/* offset(0)  align(4)  size(4)  */     u: f32;
/* offset(4)  align(4)  size(4)  */     v: f32;
                                    }

/*            align(16) size(88) */ struct B {
/* offset(0)  align(8)  size(8)  */     a: vec2<f32>;
/* offset(8)  align(1)  size(8)         -- alignment padding -- */ 
/* offset(16) align(16) size(12) */     b: vec3<f32>;
/* offset(28) align(4)  size(4)  */     c: f32;
/* offset(32) align(4)  size(4)  */     d: f32;
/* offset(36) align(1)  size(12)        -- alignment padding -- */ 
/* offset(48) align(16) size(8)  */     e: A;
/* offset(56) align(1)  size(8)         -- alignment padding -- */ 
/* offset(64) align(16) size(8)  */     f: A;
/* offset(72) align(8)  size(8)  */     g: vec2<f32>;
/* offset(80) align(8)  size(8)  */     h: vec2<f32>;
                                    }
```

Observe that `c`, packs into end of the `vec3` of `b`.
Note: With the fixed type alignment and sizes of this initial proposal, scalars can be packed into the *end* of a vector, not the front.

Offsets between array elements are always equal to the size of the element rounded up to element alignment. 

## WGSL translations

This proposal is similar to, but is not the same as `std140` and `std430` - there are differences around sizes of `vec3`s and arrays.

If the backend does not support this layout ruleset natively, there are some simple transformations that can be done on the AST to make it compatible:

### 1. Packing to `vec4`

Given that all vectors have an alignment of 16 bytes, all field members can be transformed into `vec4`s, and swizzling can be performed where scalars are packed.

For example:

```rust
[[block]] struct Uniforms {
    a : vec2<f32>;
    b : f32;
    c : f32;
};

[[binding(0), group(0)]] var<uniform> uniforms : [[access(read)]] Uniforms;

fn foo() -> vec2<f32> {
    return uniforms.a + vec2<f32>(uniforms.b, uniforms.c);
}
```

Can be translated to:

```rust
[[block]] struct Uniforms {
    abc : vec4<f32>;
};

[[binding(0), group(0)]] var<uniform> uniforms : [[access(read)]] Uniforms;

fn foo() -> vec2<f32> {
    return uniforms.abc.xy + vec2<f32>(uniforms.abc.z, uniforms.abc.w); // or just uniforms.abc.xy + uniforms.abc.zw
}
```

### 2. Removing end-of-struct padding

Certain backends require structures to be padded to a multiple of 16 bytes. This proposal does not have this requirement.

- [Vulkan](https://www.khronos.org/registry/vulkan/specs/1.2/html/chap16.html#interfaces-resources-layout): "The Offset decoration of a member must not place it between the end of a structure or an array and the next multiple of the alignment of that structure or array."
- TODO: Others?

To support these backends, structures can be inlined at the WGSL AST level before emission:

```rust
[[block]] struct Inner {
    v3 : vec3<f32>;
};

[[block]] struct Outer {
    inner : Inner;
    // No 16-byte padding!
    outer : f32;
};

[[binding(0), group(0)]] var<uniform> uniforms : [[access(read)]] Outer;

fn foo() -> vec3<f32> {
    return uniforms.inner.v3;
}
```

Can be transformed to:

```rust
[[block]] struct Outer {
    inner_v3 : vec3<f32>;
    // Still no 16-byte padding!
    outer : f32;
};

[[binding(0), group(0)]] var<uniform> uniforms : [[access(read)]] Outer;

fn foo() -> vec3<f32> {
    return uniforms.inner_v3;
}
```

## Futureproofing

This proposal adds natural alignment and sizes for all types, but to support future cases, we may wish to override these defaults.

This may be accomplished with `[[align(N)]]`, `[[size(M)]]` annotations on struct members and/or type declarations (structs, aliases).

We may also wish to add `[[packed]]` annotations on structs to switch all fields to use `[[align(4)]]` packing.
