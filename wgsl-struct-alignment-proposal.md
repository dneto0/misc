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
| mat3x2      | 8                 | 24                                      |
| mat4x2      | 8                 | 32                                      |
| mat2x3      | 16                | 32                                      |
| mat3x3      | 16                | 48                                      |
| mat4x3      | 16                | 64                                      |
| mat2x4      | 16                | 32                                      |
| mat3x4      | 16                | 48                                      |
| mat4x4      | 16                | 64                                      |
| struct      | 16                | last element offset + last element size |
| array<T, N> | element alignment | N * element size rounded to element alignment |


> Note: Recall that mat2x3 has 2 column vectors, each of which is vec3.

> Note: Unlike vectors, matrix size have been rounded to alignment, preventing packing. This was to simplify the size rules. Debatable decision.

A matrix is laid out so that a program can form a reference to each of its column
vectors, and that reference (pointer) is like a reference to a regular column vector.
In particular, the column vector must be aligned.

### Structure Layouts

The rules for aligning a struct field:
* Structures themselves are always 16 byte aligned.
* The first field is always at offset 0 of the structure.
* Subsequent fields have an offset that is the next alignment on or after the previous field offset + previous field size. 
* Structures nested inside other structures will be aligned to a 16 bytes, but fields can otherwise be treated as inlined 
  (there's no special rules for padding at the end of a nested structure).  

Example:

```rust
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

Struct members may be annotated with `[[align(n)]]` and / or `[[size(n)]]` attributes.
For MVP, these attributes can be used to verify that the type's layout rules are as expected by the developer ("show your working out").
In the future these attributes could be used to allow custom control of the alignment and size of each member.

> Note: We may wish to also annotate user defined types (`struct`, `type` aliases) with the same attributes. These would affect all uses of the type, but are still overridable with per-member attributes.

### Array Layouts

Arrays take the alignment of their element type.

Element stride (byte offsets between array elements) is equal to the size of the element rounded to a multiple of the element alignment.

The total size of an array is equal to the number of elements multipled by the element stride.

## WGSL translations

This proposal is similar to, but is not the same as `std140` and `std430` - there are differences around sizes of `vec3`s and arrays.

If the backend does not support this layout ruleset natively, there are some simple transformations that can be done on the AST to make it compatible:

### 1. Packing to `vec4`

Given the natural layout rules described above, all field members can be transformed into a sequence of contiguous `vec4`s, without requiring any unaligned vector loads or stores.

Fields that have been packed are accessed by using swizzles.

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

#### Interaction with atomics

Atomics are coming. See https://github.com/gpuweb/gpuweb/issues/1360

The widen-to-vec4 technique doesn't work directly if one of the fields being absorbed is atomic:
```rust
[[block]] struct Uniforms {
    a : vec2<u32>;
    b : atomic<u32>;
    c : u32;
};
```

Suppose we translate it like this:
```rust
[[block]] struct Uniforms {
    a : vec4<u32>;
};
```

Consider the Vulkan translation. 
We should only touch the `b` component via atomic operations.
We might introduce data races if we do non-atomic loads and stores on the whole vector or on what would be the `b` component. 

The right solution is likely to scalarize the 4 elements of the vector:

```rust
[[block]] struct Uniforms {
    a0 : u32;
    a1 : u32;
    b : u32; // only atomic operations here.
    c : u32;
};
```
When we wanted to operate on the vec2 `a` component, keep the pointer to the whole struct, and then scalarize the memory accesses.
This adds an extra pointer-calculation and an extra memory access.

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

#### Notes on replacing the inner type by an outer type

The technique of inlining an inner struct into outer struct type has non-local effects.
For example the inner struct type might be used in other contexts:

* As a value type when constructing a value or declaring a `const`.
* Used as the store type for a pointer value, and then used later in the function.
* As a value type used as a function parameter
* Used as the store type for a pointer value, used as a function parameter

##### Replacing value of the inner type within a function

In this case the inner type is used as a value type when constructing a value or declaring a `const`.

We can type-construct the inner-type value on demand, and decompose it on demand.

#### Replacing a pointer to the inner type in the same function

In this case the inner type is referenced as the store type for a pointer value, and then used later in the function 
to load from or store through.

It is safe to replace uses of the inner pointer to uses of the outer pointer,
but only paying attention to the fields from the inner type.

However there is no way to refer to exactly the set of inner fields, so you have to
decompose the load/store to load/store of each of the inner fields.  That is, if the
inner type has _N_ fields, then loading or storing to it turns into loading or storing
to each of the _N_ fields as subfields of the outer struct.
However, if the inner type has _N_ fields, then loads or stores of the inner fields

Example, before:

```rust
struct Inner {
    ia : i32;
    ib: i32;
};
struct Outer {
    oa:i32;
    ob: Inner;
};

fn foo() -> void {
    var v : Outer;
    const value : Inner = Inner(1,2);
    const p : ptr<function,Inner> = v.ob;
    p = value;
}
```

Replace it like this:
```rust
struct Inner {
    ia : i32;
    ib: i32;
};
struct Outer {
    oa:i32;
    ob_ia : i32; // inline the fields
    ob_ib : i32;
};

fn foo() -> void {
    var v : Outer;
    const value : Inner = Inner(1,2);
    const pmodified : ptr<function,Outer> = v; // keep the reference to the outer type
    // Store through each of the fields in the outer type, to cover all the fields that
    // were inlined from the inner type.
    p.ob_ia = value.ia;
    p.ob_ib = value.ib;
}
```

#### Replacing a function parameter of the inner type

In this case we can replace the function with one that acts on the outer type.

For example, there may be a function such as `fn foo( a : Inner ) -> T`.

However, there may be other calls to the function that still pass in the inner type.

Therefore, like all call-site specialization, this causes us to emit multiple versions
of a function to accommodate the different variants of the original type.

For example, we end up with both `fn foo( a : Inner ) -> T` and also the specialized
function `fn foo_Outer( a: Outer ) -> T`.

#### Replacing a function parameter that is a pointer to the inner type

In this case a function has a formal parameter of type pointer-to-the-inner-type.
This must be rewritten to be a function taking a pointer-to-the-outer-type.

In base WGSL, pointers to uniform or storage storage classes are not permitted as function parameters.
However, we expect this to be supported by an extension corresponding to the VariablePointers SPIR-V feature.
So we expect we have to address this.

This can be handled with call site specialiazation, but it causes us to emit
multiple versions of the function.


## Future features

We may also wish to allow `[[contiguous]]` attributes on structs to switch all fields to use scalar (`[[align(4)]]`) packing.
