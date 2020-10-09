# Shader Texture Function Comparison

This document was created from the information found in:

* [Metal Shading Language Specification](https://developer.apple.com/metal/Metal-Shading-Language-Specification.pdf) (MSL) \
  All functions added after Metal 1.0 have been omitted.
* [Direct3D HLSL Shader Model 4 Texture Object](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-to-type) \
  All functions added after HLSL Shader Model 5.1 have been omitted.

## Sampling functions

### Sample - 1D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture1D.Sample(sampler, float coord[, int offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture1d-sample)
| MSL     | `Tv sample(sampler, float coord)`
| SPIR-V  |

### Sample - 1D Texture Array

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture1DArray.Sample(sampler, float2 coord[, int offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture1darray-sample)
| MSL     | `Tv sample(sampler, float coord, uint array)`
| SPIR-V  |

### Sample - 2D Texture

#### Sample - 2D Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2D.Sample(sampler, float2 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture-sample-overload)
| MSL     | `Tv sample(sampler s, float2 coord[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2D.SampleBias(sampler, float2 coord, float bias[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplebias)
| MSL     | `Tv sample(sampler s, float2 coord, bias(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2D.SampleLevel(sampler, float2 coord, float LOD[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplelevel)
| MSL     | `Tv sample(sampler s, float2 coord, level(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2D.SampleGrad(sampler, float2 coord, float2 ddx, float2 ddy[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplegrad)
| MSL     | `Tv sample(sampler s, float2 coord, gradient2d(float2 dx, float2 dy)[, int2 offset])`
| SPIR-V  |

### Sample - 2D Texture Array

#### Sample - 2D Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2DArray.Sample(sampler, float2 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-sample)
| MSL     | `Tv sample(sampler s, float2 coord, uint array[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2DArray.SampleBias(sampler, float3 coord, float bias[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplebias)
| MSL     | `Tv sample(sampler s, float2 coord, uint array, bias(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Texture Array - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2DArray.SampleLevel(sampler, float3 coord, float LOD[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplelevel)
| MSL     | `Tv sample(sampler s, float2 coord, uint array, level(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2DArray.SampleGrad(sampler, float3 coord, float2 ddx, float2 ddy[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplegrad)
| MSL     | `Tv sample(sampler s, float2 coord, uint array, gradient2d(float2 dx, float2 dy)[, int2 offset])`
| SPIR-V  |

### Sample - 3D Texture

#### Sample - 3D Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture3D.Sample(sampler, float3 coord[, int3 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture3d-sample)
| MSL     | `Tv sample(sampler s, float3 coord[, int3 offset])`
| SPIR-V  |

#### Sample - 3D Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture3D.SampleBias(sampler, float3 coord, float bias[, int3 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture3d-samplebias)
| MSL     | `Tv sample(sampler s, float3 coord, bias(float)[, int3 offset])`
| SPIR-V  |

#### Sample - 3D Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture3D.SampleLevel(sampler, float3 coord, float LOD[, int3 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture3d-samplelevel)
| MSL     | `Tv sample(sampler s, float3 coord, level(float)[, int3 offset])`
| SPIR-V  |

#### Sample - 3D Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture3D.SampleGrad(sampler, float3 coord, float3 ddx, float3 ddy[, int3 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture3d-samplegrad)
| MSL     | `Tv sample(sampler s, float3 coord, gradient3d(float3 dx, float3 dy)[, int3 offset])`
| SPIR-V  |

### Sample - Cube Texture

#### Sample - Cube Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCube.Sample(sampler, float3 coord)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-sample)
| MSL     | `Tv sample(sampler s, float3 coord)`
| SPIR-V  |

#### Sample - Cube Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCube.SampleBias(sampler, float3 coord, float bias)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplebias)
| MSL     | `Tv sample(sampler s, float3 coord, bias(float))`
| SPIR-V  |

#### Sample - Cube Texture - Level

| Target  | Function                                           | Comments
|---------|----------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCube.SampleLevel(sampler, float3 coord, float LOD)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplelevel)
| MSL     | `Tv sample(sampler s, float3 coord, level(float))` | Not entirely sure if this exists - spec is vague.
| SPIR-V  |

#### Sample - Cube Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCube.SampleGrad(sampler, float3 coord, float3 ddx, float3 ddy)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplegrad)
| MSL     | `Tv sample(sampler s, float3 coord, gradientcube(float3 dx, float3 dy))`
| SPIR-V  |

### Sample - Cube Texture Array

#### Sample - Cube Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCubeArray.Sample(sampler, float4 coord)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-sample)
| MSL     | `Tv sample(sampler s, float3 coord, uint array)`
| SPIR-V  |

#### Sample - Cube Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCubeArray.SampleBias(sampler, float4 coord, float bias)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplebias)
| MSL     | `Tv sample(sampler s, float3 coord, uint array, bias(float))`
| SPIR-V  |

#### Sample - Cube Texture Array - Level

| Target  | Function                                                       | Comments
|---------|----------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCubeArray.SampleLevel(sampler, float4 coord, float LOD)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplelevel)
| MSL     | `Tv sample(sampler s, float3 coord, uint array, level(float))` | Not entirely sure if this exists - spec is vague.
| SPIR-V  |

#### Sample - Cube Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv TextureCubeArray.SampleGrad(sampler, float4 coord, float3 ddx, float3 ddy)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplegrad)
| MSL     | `Tv sample(sampler s, float3 coord, uint array, gradientcube(float3 dx, float3 dy))`
| SPIR-V  |

### Sample - 2D Depth Texture

#### Sample - 2D Depth Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2D.Sample(sampler, float2 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture-sample-overload)
| MSL     | `T sample(sampler s, float2 coord[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Depth Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2D.SampleBias(sampler, float2 coord, float bias[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplebias)
| MSL     | `T sample(sampler s, float2 coord, bias(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Depth Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2D.SampleLevel(sampler, float2 coord, float LOD[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplelevel)
| MSL     | `T sample(sampler s, float2 coord, level(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Depth Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2D.SampleGrad(sampler, float2 coord, float2 ddx, float2 ddy[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplegrad)
| MSL     | `T sample(sampler s, float2 coord, gradient2d(float2 dx, float2 dy)[, int2 offset])`
| SPIR-V  |

### Sample - 2D Depth Texture Array

#### Sample - 2D Depth Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DArray.Sample(sampler, float2 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-sample)
| MSL     | `T sample(sampler s, float2 coord, uint array[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Depth Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DArray.SampleBias(sampler, float3 coord, float bias[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplebias)
| MSL     | `T sample(sampler s, float2 coord, uint array, bias(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Depth Texture Array - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DArray.SampleLevel(sampler, float3 coord, float LOD[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplelevel)
| MSL     | `T sample(sampler s, float2 coord, uint array, level(float)[, int2 offset])`
| SPIR-V  |

#### Sample - 2D Depth Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DArray.SampleGrad(sampler, float3 coord, float2 ddx, float2 ddy[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplegrad)
| MSL     | `T sample(sampler s, float2 coord, uint array, gradient2d(float2 dx, float2 dy)[, int2 offset])`
| SPIR-V  |

### Sample - Cube Depth Texture

#### Sample - Cube Depth Texture - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCube.Sample(sampler, float3 coord)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-sample)
| MSL     | `T sample(sampler s, float3 coord)`
| SPIR-V  |

#### Sample - Cube Depth Texture - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCube.SampleBias(sampler, float3 coord, float bias)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplebias)
| MSL     | `T sample(sampler s, float3 coord, bias(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCube.SampleLevel(sampler, float3 coord, float LOD)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplelevel)
| MSL     | `T sample(sampler s, float3 coord, level(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCube.SampleGrad(sampler, float3 coord, float3 ddx, float3 ddy)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplegrad)
| MSL     | `T sample(sampler s, float3 coord, gradientcube(float3 dx, float3 dy))`
| SPIR-V  |

### Sample - Cube Depth Texture Array

#### Sample - Cube Depth Texture Array - Basic

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCubeArray.Sample(sampler, float4 coord)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-sample)
| MSL     | `T sample(sampler s, float3 coord, uint array)`
| SPIR-V  |

#### Sample - Cube Depth Texture Array - Bias

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCubeArray.SampleBias(sampler, float4 coord, float bias)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplebias)
| MSL     | `T sample(sampler s, float3 coord, uint array, bias(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture Array - Level

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCubeArray.SampleLevel(sampler, float4 coord, float LOD)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplelevel)
| MSL     | `T sample(sampler s, float3 coord, uint array, level(float))`
| SPIR-V  |

#### Sample - Cube Depth Texture Array - Gradient

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCubeArray.SampleGrad(sampler, float4 coord, float3 ddx, float3 ddy)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplegrad)
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
| HLSL    | [`T Texture2D.SampleCmp(SamplerComparisonState, float2 coord, float compare_value[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplecmp)
| MSL     | `T sample_compare(sampler s, float2 coord, float compare_value[, int2 offset])`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - 2D Depth Texture - Level

| Target  | Function                                                                                                                                                                                          | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2D.SampleCmp(SamplerComparisonState, float2 coord, float compare_value[, int2 offset], float clamp)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplecmp) | `clamp` is used as a `max()` on the mip level selected.<br>See also: [`SampleCmpLevelZero()`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-samplecmplevelzero)
| MSL     | `T sample_compare(sampler s, float2 coord, float compare_value, level(float lod)[, int2 offset])` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

### Sample & Compare - 2D Depth Texture Array

#### Sample & Compare - 2D Depth Texture Array - Basic

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DArray.SampleCmp(SamplerComparisonState, float3 coord, float compare_value[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplecmp)
| MSL     | `T sample_compare(sampler s, float2 coord, uint array, float compare_value[, int2 offset])`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - 2D Depth Texture Array - Level

| Target  | Function                                                                                                                                                                                                    | Comments
|---------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DArray.SampleCmp(SamplerComparisonState, float3 coord, float compare_value[, int2 offset], float clamp)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplecmp) | `clamp` is used as a `max()` on the mip level selected.<br>See also: [`SampleCmpLevelZero()`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-samplecmplevelzero)
| MSL     | `T sample_compare(sampler s, float2 coord, uint array, float compare_value, level(float lod)[, int2 offset])` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

### Sample & Compare - Cube Depth Texture

#### Sample & Compare - Cube Depth Texture - Basic

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCube.SampleCmp(SamplerComparisonState, float3 coord, float compare_value)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplecmp)
| MSL     | `T sample_compare(sampler s, float3 coord, float compare_value)`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - Cube Depth Texture - Level

| Target  | Function                                                                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCube.SampleCmp(SamplerComparisonState, float3 coord, float compare_value, float clamp)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplecmp) | `clamp` is used as a `max()` on the mip level selected.<br>See also: [`SampleCmpLevelZero()`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplecmplevelzero)
| MSL     | `T sample_compare(sampler s, float3 coord, float compare_value, level(float lod))` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

### Sample & Compare - Cube Depth Texture Array

#### Sample & Compare - Cube Depth Texture Array - Basic

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCubeArray.SampleCmp(SamplerComparisonState, float4 coord, float compare_value)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplecmp)
| MSL     | `T sample_compare(sampler s, float3 coord, uint array, float compare_value)`  | `T` must be a float type
| SPIR-V  |

#### Sample & Compare - Cube Depth Texture Array - Level

| Target  | Function                                                                                                                                                                                         | Comments
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T TextureCubeArray.SampleCmp(SamplerComparisonState, float4 coord, float compare_value, float clamp)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-samplecmp) | `clamp` is used as a `max()` on the mip level selected.<br>See also: [`SampleCmpLevelZero()`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-samplecmplevelzero)
| MSL     | `T sample_compare(sampler s, float3 coord, uint array, float compare_value, level(float lod))` | `T` must be a float type<br>`lod` **must** be a zero constant on macOS
| SPIR-V  |

## Read

### Read - 1D Texture

| Target  | Function                                                                                                                    | Comments
|---------|-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture1D.Load(int2 coord[, int offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture1d-load) |
| MSL     | `Tv read(uint coord, uint lod = 0)`                                                                                         | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Read - 1D Texture Array

| Target  | Function                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture1DArray.Load(int3 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture1darray-load) |
| MSL     | `Tv read(uint coord, uint array, uint lod = 0)`                                                                                        | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Read - 2D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2D.Load(int3 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-load) |
| MSL     | `Tv read(uint2 coord, uint lod = 0)`
| SPIR-V  |

### Read - 2D Texture Array

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2DArray.Load(int4 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-load) |
| MSL     | `Tv read(uint2 coord, ushort array, uint lod = 0)`
| SPIR-V  |

### Read - 3D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture3D.Load(int4 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture3d-load) |
| MSL     | `Tv read(uint3 coord, uint lod = 0)`
| SPIR-V  |

### Read - Cube Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | \<not-supported\>
| MSL     | `Tv read(uint2 coord, uint face, uint lod = 0)`   | `face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

### Read - Cube Texture Array

| Target  | Function                                                    | Comments
|---------|-------------------------------------------------------------|----------------------------------------|
| HLSL    | \<not-supported\>
| MSL     | `Tv read(uint2 coord, uint face, uint array, uint lod = 0)` | `face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

### Read - 2D Multisampled Texture

| Target  | Function                                                                                                                                   | Comments
|---------|--------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Tv Texture2DMS.Load(int3 coord, int sample[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-load) |
| MSL     | `Tv read(uint2 coord, uint sample)`                                                                                                        | `MTLRenderPassDescriptor.setSamplePositions` can specify sample positions
| SPIR-V  |

### Read - 2D Depth Texture

| Target  | Function                                      | Comments
|---------|-----------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2D.Load(int3 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-load) |
| MSL     | `T read(uint2 coord, uint lod = 0)`           |
| SPIR-V  |

### Read - 2D Depth Texture Array

| Target  | Function                                        | Comments
|---------|-------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DArray.Load(int4 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-load) |
| MSL     | `T read(uint2 coord, uint array, uint lod = 0)` |
| SPIR-V  |

### Read - 2D Multisampled Depth Texture

| Target  | Function                                                                                                                                  | Comments
|---------|-------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`T Texture2DMS.Load(int3 coord, int sample[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-load) |
| MSL     | `T read(uint2 coord, uint sample)` |
| SPIR-V  |

### Read - Cube Depth Texture

| Target  | Function                                       | Comments
|---------|------------------------------------------------|----------------------------------------|
| HLSL    | \<not-supported\>
| MSL     | `T read(uint2 coord, uint face, uint lod = 0)` |
| SPIR-V  |

### Read - Cube Depth Texture Array

| Target  | Function                                                   | Comments
|---------|------------------------------------------------------------|----------------------------------------|
| HLSL    | \<not-supported\>
| MSL     | `T read(uint2 coord, uint face, uint array, uint lod = 0)` |
| SPIR-V  |

## Write

HLSL texture writes require using `RWTexture`s - [note they do not support the same methods as regular `Texture`s](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-rwtexture1d):
> A `RWTexture1D` object cannot use methods from a `Texture1D` object, such as Sample.
However, because you can create multiple view types to the same resource, you
can declare multiple texture types as a single texture in multiple shaders.
For example, you can declare and use a RWTexture1D object as tex in a compute
shader and then declare and use a Texture1D object as tex in a pixel shader.

`RWTexture`s do not support mip maps.

### Write - 1D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`RWTexture1D.operator[int] = color`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-rwtexture1d-operatorindex) |
| MSL     | `void write(Tv color, uint coord, uint lod = 0)`  | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Write - 1D Texture Array

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`RWTexture1DArray.operator[int2] = color`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-rwtexture1darray-operatorindex) |
| MSL     | `void write(Tv color, uint coord, uint lod = 0)`  | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

### Write - 2D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`RWTexture2D.operator[int2] = color`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-rwtexture2d) |
| MSL     | `void write(Tv color, uint2 coord, uint lod = 0)` | `lod` **must** be `0` on macOS.
| SPIR-V  |

### Write - 2D Texture Array

| Target  | Function                                                      | Comments
|---------|---------------------------------------------------------------|----------------------------------------|
| HLSL    | [`RWTexture2DArray.operator[int3] = color`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-rwtexture2darray) |
| MSL     | `void write(Tv color, uint2 coord, uint array, uint lod = 0)` | `lod` **must** be `0` on macOS.
| SPIR-V  |

### Write - 3D Texture

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`RWTexture3D.operator[int3] = color`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-rwtexture3d-operatorindex) |
| MSL     | `void write(Tv color, uint3 coord, uint lod = 0)` | `lod` **must** be `0` on macOS.
| SPIR-V  |

### Write - Cube Texture

| Target  | Function                                                     | Comments
|---------|--------------------------------------------------------------|----------------------------------------|
| HLSL    | \<not-supported\>
| MSL     | `void write(Tv color, uint2 coord, uint face, uint lod = 0)` | `lod` **must** be `0` on macOS.<br>`face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

### Write - Cube Texture Array

| Target  | Function                                                                 | Comments
|---------|--------------------------------------------------------------------------|----------------------------------------|
| HLSL    | \<not-supported\>
| MSL     | `void write(Tv color, uint2 coord, uint face, uint array, uint lod = 0)` | `lod` **must** be `0` on macOS.<br>`face: [0: +X, 1: -X, 2: +Y, 3: -Y, 4: +Z, 5: -Z]`
| SPIR-V  |

## Gather

A gather returns 4 samples of a specified channel (r,g,b,a) for bilinear interpolation.

### Gather - 2D Texture

| Target  | Function                                                                                | Comments
|---------|-----------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.Gather[Red,Green,Blue,Alpha](sampler s, float2 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-gatherred) |
| MSL     | `Tv gather(sampler s, float2 coord[, int2 offset], component c = component::x)` |
| SPIR-V  |

### Gather - 2D Texture Array

| Target  | Function                                                                                | Comments
|---------|-----------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.Gather[Red,Green,Blue,Alpha](sampler s, float3 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-gatherred) |
| MSL     | `Tv gather(sampler s, float2 coord, uint array[, int2 offset], component c = component::x)` |
| SPIR-V  |

### Gather - Cube Texture

| Target  | Function                                                         | Comments
|---------|------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`TextureCube.Gather[Red,Green,Blue,Alpha](sampler s, float3 coord)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-gatherred) |
| MSL     | `Tv gather(sampler s, float3 coord, component c = component::x)` |
| SPIR-V  |

### Gather - Cube Texture Array

| Target  | Function                                                                     | Comments
|---------|------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`TextureCubeArray.Gather[Red,Green,Blue,Alpha](sampler s, float4 coord)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecubearray-gatherred) |
| MSL     | `Tv gather(sampler s, float3 coord, uint array, component c = component::x)` |
| SPIR-V  |

### Gather - 2D Depth Texture

| Target  | Function                                                    | Comments
|---------|-------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.Gather(sampler s, float2 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-gather) |
| MSL     | `Tv gather(sampler s, float2 coord[, int2 offset])` |
| SPIR-V  |

### Gather - 2D Depth Texture Array

| Target  | Function                                                                | Comments
|---------|-------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.Gather(sampler s, float3 coord[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-gather) |
| MSL     | `Tv gather(sampler s, float2 coord, uint array[, int2 offset])` |
| SPIR-V  |

### Gather - Cube Depth Texture

| Target  | Function                             | Comments
|---------|--------------------------------------|----------------------------------------|
| HLSL    | [`TextureCube.Gather(sampler s, float3 coord)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-gather) |
| MSL     | `Tv gather(sampler s, float3 coord)` |
| SPIR-V  |

## Gather Compare

### Gather Compare - 2D Depth Texture

| Target  | Function                                                                                 | Comments
|---------|------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.GatherCmp(sampler s, float2 coord, float compare_value[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2d-gathercmp) |
| MSL     | `Tv gather_compare(sampler s, float2 coord, float compare_value[, int2 offset])` |
| SPIR-V  |

### Gather Compare - 2D Depth Texture Array

| Target  | Function                                                                                             | Comments
|---------|------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GatherCmp(sampler s, float3 coord, float compare_value[, int2 offset])`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texture2darray-gathercmp) |
| MSL     | `Tv gather_compare(sampler s, float2 coord, uint array, float compare_value[, int2 offset])` |
| SPIR-V  |

### Gather Compare - Cube Depth Texture

| Target  | Function                                                          | Comments
|---------|-------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`TextureCube.GatherCmp(sampler s, float3 coord, float compare_value)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-gathercmp) |
| MSL     | `Tv gather_compare(sampler s, float3 coord, float compare_value)` |
| SPIR-V  |

### Gather Compare - Cube Depth Texture Array

| Target  | Function                                                                                                                                                        | Comments
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`TextureCubeArray.GatherCmp(sampler s, float4 coord, float compare_value)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/texturecube-gathercmp) |
| MSL     | `Tv gather_compare(sampler s, float3 coord, uint array, float compare_value)`                                                                                   |
| SPIR-V  |

## Query

### Query - 1D Texture

#### Query - 1D Texture - Width

| Target  | Function                                                                                                                                                                    | Comments
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture1D.GetDimensions(in uint mip, out uint width, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture1d-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                              | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

#### Query - 1D Texture - Number of mips

| Target  | Function                                                                                                                                                                    | Comments
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture1D.GetDimensions(in uint mip, out uint width, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture1d-getdimensions) |
| MSL     | `uint get_num_mip_levels()`                                                                                                                                                 | Mipmaps are not supported for 1D textures<br>Always returns `0`.
| SPIR-V  |

### Query - 1D Texture Array

#### Query - 1D Texture Array - Width

| Target  | Function                                                                                                                                                                                                 | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture1DArray.GetDimensions(in uint mip, out uint width, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture1darray-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                                                           | Mipmaps are not supported for 1D textures.<br>`lod` **must** be `0`.
| SPIR-V  |

#### Query - 1D Texture Array - Number of array elements

| Target  | Function                                                                                                                                                                                                 | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture1DArray.GetDimensions(in uint mip, out uint width, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture1darray-getdimensions) |
| MSL     | `uint get_array_size()`
| SPIR-V  |

#### Query - 1D Texture Array - Number of mips

| Target  | Function                                                                                                                                                                                                 | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture1DArray.GetDimensions(in uint mip, out uint width, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture1darray-getdimensions) |
| MSL     | `uint get_num_mip_levels()`                                                                                                                                                                              | Mipmaps are not supported for 1D textures<br>Always returns `0`.
| SPIR-V  |

### Query - 2D Texture

#### Query - 2D Texture - Width

| Target  | Function                                                                                                                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2d-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                                               |
| SPIR-V  |

#### Query - 2D Texture - Height

| Target  | Function                                                                                                                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2d-getdimensions) |
| MSL     | `uint get_height(uint lod = 0)`                                                                                                                                                              |
| SPIR-V  |

#### Query - 2D Texture - Number of mips

| Target  | Function                                                                                                                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2d-getdimensions) |
| MSL     | `uint get_num_mip_levels()`                                                                                                                                                                  |
| SPIR-V  |

### Query - 2D Texture Array

#### Query - 2D Texture Array - Width

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                                                                            |
| SPIR-V  |

#### Query - 2D Texture Array - Height

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_height(uint lod = 0)`                                                                                                                                                                                           |
| SPIR-V  |

#### Query - 2D Texture Array - Number of array elements

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_array_size()`
| SPIR-V  |

#### Query - 2D Texture Array - Number of mips

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_num_mip_levels()`                                                                                                                                                                                               |
| SPIR-V  |

### Query - 3D Texture

#### Query - 3D Texture - Width

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture3D.GetDimensions(in uint mip, out uint width, out uint height, out uint depth, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture3d-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                    |
| SPIR-V  |

#### Query - 3D Texture - Height

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture3D.GetDimensions(in uint mip, out uint width, out uint height, out uint depth, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture3d-getdimensions) |
| MSL     | `uint get_height(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 3D Texture - Depth

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture3D.GetDimensions(in uint mip, out uint width, out uint height, out uint depth, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture3d-getdimensions) |
| MSL     | `uint get_depth(uint lod = 0)`                   |
| SPIR-V  |

#### Query - 3D Texture - Number of mips

| Target  | Function                                          | Comments
|---------|---------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture3D.GetDimensions(in uint mip, out uint width, out uint height, out uint depth, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture3d-getdimensions) |
| MSL     | `uint get_num_mip_levels()`                       |
| SPIR-V  |

### Query - Cube Texture

#### Query - Cube Texture - Width

| Target  | Function                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCube.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_width(uint lod = 0)`                                                               |
| SPIR-V  |

#### Query - Cube Texture - Height

| Target  | Function                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCube.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_height(uint lod = 0)`                                                              |
| SPIR-V  |

#### Query - Cube Texture - Number of mips

| Target  | Function                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCube.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_num_mip_levels()`                                                                  |
| SPIR-V  |

### Query - Cube Texture Array

#### Query - Cube Texture Array - Width

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_width(uint lod = 0)`                                                                                       |
| SPIR-V  |

#### Query - Cube Texture Array - Height

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_height(uint lod = 0)`                                                                                      |
| SPIR-V  |

#### Query - Cube Texture Array - Number of array elements

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_array_size()`                                                                                              |
| SPIR-V  |

#### Query - Cube Texture Array - Number of mips

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_num_mip_levels()`                                                                                          |
| SPIR-V  |

### Query - 2D Multisampled Texture

#### Query - 2D Multisampled Texture - Width

| Target  | Function                                                                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DMS.GetDimensions(out uint width, out uint height, out uint num_samples)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2dms-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                                         |
| SPIR-V  |

#### Query - 2D Multisampled Texture - Height

| Target  | Function                                                                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DMS.GetDimensions(out uint width, out uint height, out uint num_samples)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2dms-getdimensions) |
| MSL     | `uint get_height(uint lod = 0)`                                                                                                                                                        |
| SPIR-V  |

#### Query - 2D Multisampled Texture - Number of samples

| Target  | Function                                                                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DMS.GetDimensions(out uint width, out uint height, out uint num_samples)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2dms-getdimensions) |
| MSL     | `uint get_num_samples()`                                                                                                                                                               |
| SPIR-V  |

### Query - 2D Depth Texture

#### Query - 2D Depth Texture - Width

| Target  | Function                                                                                                                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2d-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                                               |
| SPIR-V  |

#### Query - 2D Depth Texture - Height

| Target  | Function                                                                                                                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2d-getdimensions) |
| MSL     | `uint get_height(uint lod = 0)`                                                                                                                                                              |
| SPIR-V  |

#### Query - 2D Depth Texture - Number of mips

| Target  | Function                                                                                                                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2D.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2d-getdimensions) |
| MSL     | `uint get_num_mip_levels()`                                                                                                                                                                  |
| SPIR-V  |

### Query - 2D Depth Texture Array

#### Query - 2D Depth Texture Array - Width

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                                                                            |
| SPIR-V  |

#### Query - 2D Depth Texture Array - Height

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_height(uint lod = 0)`                                                                                                                                                                                           |
| SPIR-V  |

#### Query - 2D Depth Texture Array - Number of array elements

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_array_size()`
| SPIR-V  |

#### Query - 2D Depth Texture Array - Number of mips

| Target  | Function                                                                                                                                                                                                                  | Comments
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2darray-getdimensions) |
| MSL     | `uint get_num_mip_levels()`                                                                                                                                                                                               |
| SPIR-V  |

### Query - 2D Multisampled Depth Texture

#### Query - 2D Multisampled Depth Texture - Width

| Target  | Function                                                                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DMS.GetDimensions(out uint width, out uint height, out uint num_samples)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2dms-getdimensions) |
| MSL     | `uint get_width(uint lod = 0)`                                                                                                                                                         |
| SPIR-V  |

#### Query - 2D Multisampled Depth Texture - Height

| Target  | Function                                                                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DMS.GetDimensions(out uint width, out uint height, out uint num_samples)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2dms-getdimensions) |
| MSL     | `uint get_height(uint lod = 0)`                                                                                                                                                        |
| SPIR-V  |

#### Query - 2D Multisampled Depth Texture - Number of samples

| Target  | Function                                                                                                                                                                               | Comments
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | [`Texture2DMS.GetDimensions(out uint width, out uint height, out uint num_samples)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/sm5-object-texture2dms-getdimensions) |
| MSL     | `uint get_num_samples()`                                                                                                                                                               |
| SPIR-V  |

### Query - Cube Depth Texture

#### Query - Cube Depth Texture - Width

| Target  | Function                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCube.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_width(uint lod = 0)`                                                               |
| SPIR-V  |

#### Query - Cube Depth Texture - Height

| Target  | Function                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCube.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_height(uint lod = 0)`                                                              |
| SPIR-V  |

#### Query - Cube Depth Texture - Number of mips

| Target  | Function                                                                                     | Comments
|---------|----------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCube.GetDimensions(in uint mip, out uint width, out uint height, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_num_mip_levels()`                                                                  |
| SPIR-V  |

### Query - Cube Depth Texture Array

#### Query - Cube Depth Texture Array - Width

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_width(uint lod = 0)`                                                                                       |
| SPIR-V  |

#### Query - Cube Depth Texture Array - Height

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_height(uint lod = 0)`                                                                                      |
| SPIR-V  |

#### Query - Cube Depth Texture Array - Number of array elements

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_array_size()`                                                                                              |
| SPIR-V  |

#### Query - Cube Depth Texture Array - Number of mips

| Target  | Function                                                                                                             | Comments
|---------|----------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| HLSL    | `TextureCubeArray.GetDimensions(in uint mip, out uint width, out uint height, out uint elements, out uint num_mips)` | Missing from documentation, but DXC accepts it.
| MSL     | `uint get_num_mip_levels()`                                                                                          |
| SPIR-V  |
