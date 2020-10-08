# Shader Texture Function Comparison

This document was created from the information found in:

* [Metal Shading Language Specification](https://developer.apple.com/metal/Metal-Shading-Language-Specification.pdf) (MSL)

All functions added after Metal 1.0 have been omitted.

## Sampling functions

### Sample - 1D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler, float coord)`
| SPIR-V  |

### Sample - 1D Texture Array

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler, float coord, uint array)`
| SPIR-V  |

### Sample - 2D Texture

#### Sample - 2D Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, bias(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, level(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, gradient2d(float2 dx, float2 dy), int2 offset = int2(0))`
| SPIR-V  |

### Sample - 2D Texture Array

#### Sample - 2D Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, uint array, int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, uint array, bias(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Texture Array - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, uint array, level(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float2 coord, uint array, gradient2d(float2 dx, float2 dy), int2 offset = int2(0))`
| SPIR-V  |

### Sample - 3D Texture

#### Sample - 3D Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, int3 offset = int3(0))`
| SPIR-V  |

#### Sample - 3D Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, bias(float), int3 offset = int3(0))`
| SPIR-V  |

#### Sample - 3D Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, level(float), int3 offset = int3(0))`
| SPIR-V  |

#### Sample - 3D Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, gradient3d(float3 dx, float3 dy), int3 offset = int3(0))`
| SPIR-V  |

### Sample - Cube Texture

#### Sample - Cube Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord)`
| SPIR-V  |

#### Sample - Cube Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, bias(float))`
| SPIR-V  |

#### Sample - Cube Texture - Level

| Target  | Function                                           | Comments
|---------|----------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, level(float))` | Not entirely sure if this exists - spec is vague.
| SPIR-V  |

#### Sample - Cube Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, gradientcube(float3 dx, float3 dy))`
| SPIR-V  |

### Sample - Cube Texture Array

#### Sample - Cube Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, uint array)`
| SPIR-V  |

#### Sample - Cube Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, uint array, bias(float))`
| SPIR-V  |

#### Sample - Cube Texture Array - Level

| Target  | Function                                                       | Comments
|---------|----------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                |
| MSL     | `Tv sample(sampler s, float3 coord, uint array, level(float))` | Not entirely sure if this exists - spec is vague.
| SPIR-V  |

#### Sample - Cube Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `Tv sample(sampler s, float3 coord, uint array, gradientcube(float3 dx, float3 dy))`
| SPIR-V  |

### Sample - 2D Depth Texture

#### Sample - 2D Depth Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Depth Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, bias(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Depth Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, level(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Depth Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, gradient2d(float2 dx, float2 dy), int2 offset = int2(0))`
| SPIR-V  |

### Sample - 2D Depth Texture Array

#### Sample - 2D Depth Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, uint array, int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Depth Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, uint array, bias(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Depth Texture Array - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, uint array, level(float), int2 offset = int2(0))`
| SPIR-V  |

#### Sample - 2D Depth Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float2 coord, uint array, gradient2d(float2 dx, float2 dy), int2 offset = int2(0))`
| SPIR-V  |

### Sample - Cube Depth Texture

#### Sample - Cube Depth Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord)`
| SPIR-V  |

#### Sample - Cube Depth Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord, bias(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord, level(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord, gradientcube(float3 dx, float3 dy))`
| SPIR-V  |

### Sample - Cube Depth Texture Array

#### Sample - Cube Depth Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord, uint array)`
| SPIR-V  |

#### Sample - Cube Depth Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord, uint array, bias(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture Array - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord, uint array, level(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample(sampler s, float3 coord, uint array, gradientcube(float3 dx, float3 dy))`
| SPIR-V  |

## Sampling & Compare functions

> Metal Shading Language: `sample_compare` performs a comparison of the
`compare_value` value against the pixel value (`1.0` if the comparison passes
and `0.0` if it fails). These comparison result values per-pixel are then
blended together as in normal texture filtering and the resulting value between
`0.0` and `1.0` is returned.

### Sample & Compare - 2D Depth Texture

#### Sample & Compare - 2D Depth Texture - Basic

| Target  | Function                                                                                 | Comments
|---------|------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float2 coord, float compare_value, int2 offset = int2(0))`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - 2D Depth Texture - Level

| Target  | Function                                                                                                  | Comments
|---------|-----------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float2 coord, float compare_value, level(float lod), int2 offset = int2(0))` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

### Sample & Compare - 2D Depth Texture Array

#### Sample & Compare - 2D Depth Texture Array - Basic

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float2 coord, uint array, float compare_value, int2 offset = int2(0))`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - 2D Depth Texture Array - Level

| Target  | Function                                                                                                              | Comments
|---------|-----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float2 coord, uint array, float compare_value, level(float lod), int2 offset = int2(0))` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

### Sample & Compare - Cube Depth Texture

#### Sample & Compare - Cube Depth Texture - Basic

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float3 coord, float compare_value)`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - Cube Depth Texture - Level

| Target  | Function                                                                           | Comments
|---------|------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float3 coord, float compare_value, level(float lod))` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

### Sample & Compare - Cube Depth Texture Array

#### Sample & Compare - Cube Depth Texture Array - Basic

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float3 coord, uint array, float compare_value)`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - Cube Depth Texture Array - Level

| Target  | Function                                                                           | Comments
|---------|------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `T sample_compare(sampler s, float3 coord, uint array, float compare_value, level(float lod))` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

## Read

### Read - 1D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `Tv read(uint coord, uint lod = 0)`               | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Read - 1D Texture Array

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `Tv read(uint coord, uint array, uint lod = 0)`   | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Read - 2D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `Tv read(uint2 coord, uint lod = 0)`
| SPIR-V  |

### Read - 2D Texture Array

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `Tv read(uint2 coord, ushort array, uint lod = 0)`
| SPIR-V  |

### Read - 3D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `Tv read(uint3 coord, uint lod = 0)`
| SPIR-V  |

### Read - Cube Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `Tv read(uint2 coord, uint face, uint lod = 0)`   | `face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

### Read - Cube Texture Array

| Target  | Function                                                    | Comments
|---------|-------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                             |
| MSL     | `Tv read(uint2 coord, uint face, uint array, uint lod = 0)` | `face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

### Read - 2D Multisampled Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `Tv read(uint2 coord, uint sample)`               | `MTLRenderPassDescriptor.setSamplePositions` can specify sample positions
| SPIR-V  |

### Read - 2D Depth Texture

| Target  | Function                                      | Comments
|---------|-----------------------------------------------|----------------------------------------|
| HLSL    |                                               |
| MSL     | `T read(uint2 coord, uint lod = 0)`           |
| SPIR-V  |

### Read - 2D Depth Texture Array

| Target  | Function                                        | Comments
|---------|-------------------------------------------------|----------------------------------------|
| HLSL    |                                                 |
| MSL     | `T read(uint2 coord, uint array, uint lod = 0)` |
| SPIR-V  |

### Read - 2D Multisampled Depth Texture

| Target  | Function                           | Comments
|---------|------------------------------------|----------------------------------------|
| HLSL    |                                    |
| MSL     | `T read(uint2 coord, uint sample)` |
| SPIR-V  |

### Read - Cube Depth Texture

| Target  | Function                                       | Comments
|---------|------------------------------------------------|----------------------------------------|
| HLSL    |                                                |
| MSL     | `T read(uint2 coord, uint face, uint lod = 0)` |
| SPIR-V  |

### Read - Cube Depth Texture Array

| Target  | Function                                                   | Comments
|---------|------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                            |
| MSL     | `T read(uint2 coord, uint face, uint array, uint lod = 0)` |
| SPIR-V  |

## Write

### Write - 1D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `void write(Tv color, uint coord, uint lod = 0)`  | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Write - 1D Texture Array

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `void write(Tv color, uint coord, uint lod = 0)`  | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Write - 2D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `void write(Tv color, uint2 coord, uint lod = 0)` | `lod` **must** be `0` on macOS.
| SPIR-V  |

### Write - 2D Texture Array

| Target  | Function                                                      | Comments
|---------|---------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                               |
| MSL     | `void write(Tv color, uint2 coord, uint array, uint lod = 0)` | `lod` **must** be `0` on macOS.
| SPIR-V  |

### Write - 3D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `void write(Tv color, uint3 coord, uint lod = 0)` | `lod` **must** be `0` on macOS.
| SPIR-V  |

### Write - Cube Texture

| Target  | Function                                                     | Comments
|---------|--------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                              |
| MSL     | `void write(Tv color, uint2 coord, uint face, uint lod = 0)` | `lod` **must** be `0` on macOS.<br>`face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

### Write - Cube Texture Array

| Target  | Function                                                                 | Comments
|---------|--------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                          |
| MSL     | `void write(Tv color, uint2 coord, uint face, uint array, uint lod = 0)` | `lod` **must** be `0` on macOS.<br>`face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

## Gather

A gather returns 4 samples of a specified channel (r,g,b,a) for bilinear interpolation.

### Gather - 2D Texture

| Target  | Function                                                                                | Comments
|---------|-----------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                                         |
| MSL     | `Tv gather(sampler s, float2 coord, int2 offset = int2(0), component c = component::x)` |
| SPIR-V  |

### Gather - 2D Texture Array

| Target  | Function                                                                                | Comments
|---------|-----------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                                         |
| MSL     | `Tv gather(sampler s, float2 coord, uint array, int2 offset = int2(0), component c = component::x)` |
| SPIR-V  |

### Gather - Cube Texture

| Target  | Function                                                         | Comments
|---------|------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                  |
| MSL     | `Tv gather(sampler s, float3 coord, component c = component::x)` |
| SPIR-V  |

### Gather - Cube Texture Array

| Target  | Function                                                                     | Comments
|---------|------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                              |
| MSL     | `Tv gather(sampler s, float3 coord, uint array, component c = component::x)` |
| SPIR-V  |

### Gather - 2D Depth Texture

| Target  | Function                                                    | Comments
|---------|-------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                             |
| MSL     | `Tv gather(sampler s, float2 coord, int2 offset = int2(0))` |
| SPIR-V  |

### Gather - 2D Depth Texture Array

| Target  | Function                                                                | Comments
|---------|-------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                         |
| MSL     | `Tv gather(sampler s, float2 coord, uint array, int2 offset = int2(0))` |
| SPIR-V  |

### Gather - Cube Depth Texture

| Target  | Function                             | Comments
|---------|--------------------------------------|----------------------------------------|
| HLSL    |                                      |
| MSL     | `Tv gather(sampler s, float3 coord)` |
| SPIR-V  |

## Gather Compare

### Gather Compare - 2D Depth Texture

| Target  | Function                                                                                 | Comments
|---------|------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                                          |
| MSL     | `Tv gather_compare(sampler s, float2 coord, float compare_value, int2 offset = int2(0))` |
| SPIR-V  |

### Gather Compare - 2D Depth Texture Array

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                                                      |
| MSL     | `Tv gather_compare(sampler s, float2 coord, uint array, float compare_value, int2 offset = int2(0))` |
| SPIR-V  |

### Gather Compare - Cube Depth Texture

| Target  | Function                                                          | Comments
|---------|-------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                   |
| MSL     | `Tv gather_compare(sampler s, float3 coord, float compare_value)` |
| SPIR-V  |

### Gather Compare - Cube Depth Texture Array

| Target  | Function                                                                      | Comments
|---------|-------------------------------------------------------------------------------|----------------------------------------|
| HLSL    |                                                                               |
| MSL     | `Tv gather_compare(sampler s, float3 coord, uint array, float compare_value)` |
| SPIR-V  |

## Query

### Query - 1D Texture

#### Query - 1D Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

#### Query - 1D Texture - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       | Mipmaps are not supported for 1D textures<br>Always returns `0`.
| SPIR-V  |

### Query - 1D Texture Array

#### Query - 1D Texture Array - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

#### Query - 1D Texture Array - Number of array elements

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `uint get_array_size()`
| SPIR-V  |

#### Query - 1D Texture Array - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       | Mipmaps are not supported for 1D textures<br>Always returns `0`.
| SPIR-V  |

### Query - 2D Texture

#### Query - 2D Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 2D Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 2D Texture - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - 2D Texture Array

#### Query - 2D Texture Array - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 2D Texture Array - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 2D Texture Array - Number of array elements

| Target  | Function
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `uint get_array_size()`
| SPIR-V  |

#### Query - 2D Texture Array - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - 3D Texture

#### Query - 3D Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 3D Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 3D Texture - Depth

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_depth(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 3D Texture - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - Cube Texture

#### Query - Cube Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - Cube Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - Cube Texture - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - Cube Texture Array

#### Query - Cube Texture Array - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - Cube Texture Array - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - Cube Texture Array - Number of array elements

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |
| MSL     | `uint get_array_size()`
| SPIR-V  |

#### Query - Cube Texture Array - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - 2D Multisampled Texture

#### Query - 2D Multisampled Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 2D Multisampled Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 2D Multisampled Texture - Number of samples

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_samples()`                          |
| SPIR-V  |

### Query - 2D Depth Texture

#### Query - 2D Depth Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 2D Depth Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 2D Depth Texture - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - 2D Depth Texture Array

#### Query - 2D Depth Texture Array - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 2D Depth Texture Array - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 2D Depth Texture Array - Number of array elements

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_array_size()`                           |
| SPIR-V  |

#### Query - 2D Depth Texture Array - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - 2D Multisampled Depth Texture

#### Query - 2D Multisampled Depth Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 2D Multisampled Depth Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 2D Multisampled Depth Texture - Number of samples

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_samples()`                           |
| SPIR-V  |

### Query - Cube Depth Texture

#### Query - Cube Depth Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - Cube Depth Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - Cube Depth Texture - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - Cube Depth Texture Array

#### Query - Cube Depth Texture Array - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - Cube Depth Texture Array - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - Cube Depth Texture Array - Number of array elements

| Target  | Function                                      | Comments
|---------|-----------------------------------------------|----------------------------------------|
| HLSL    |                                               |
| MSL     | `uint get_array_size()`                       |
| SPIR-V  |

#### Query - Cube Depth Texture Array - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    |                                                   |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |
