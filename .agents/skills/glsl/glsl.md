---
name: glsl
description: Use to inspect, develop, review GLSL code and C++ which uploads data to shaders.
---

# glsl skill

1. Use common header files which consumed by both C/C++ as includes and in GLSL as an extra string added to shader code before compilation (actually: GLSL shader code as string appended to the common header string).  
examples:
```
#ifdef __cplusplus

  #pragma once
  #include <glm/glm.hpp>

  #define layout(x) struct alignas(16)
  #define uniform

  using vec2 = glm::vec2;
  using vec3 = glm::vec3;
  using vec4 = glm::vec4;

  using float2 = glm::vec2;
  using float3 = glm::vec3;
  using float4 = glm::vec4;

  using mat2 = glm::mat2;
  using mat3 = glm::mat3;
  using mat4 = glm::mat4;

  using half = _Float16;// or std::float16_t if C++23 available
  using half2 = half [[clang::ext_vector_type(2)]];
  using half3 = half [[clang::ext_vector_type(3)]];
  using half4 = half [[clang::ext_vector_type(4)]];
  /// or
  /*
  using half2 = half __attribute__((ext_vector_type(2)));
  using half3 = half __attribute__((ext_vector_type(3)));
  using half4 = half __attribute__((ext_vector_type(4)));
  */
#else
  #define half mediump float
  #define half2 mediump vec2
  #define half3 mediump vec3
  #define half4 mediump vec4

  #define float2 highp vec2
  #define float3 highp vec3
  #define float4 highp vec4

#endif

#define kExtraVectors 8
#define kArbitraryReservedVectorCount 12
#define kInstances 128

struct View {
  mat4 view;
  mat4 Proj;
  mat4 viewProj;
  float4 camPosition;
  float4 invViewPort;
  float4 xtraData[kExtraVectors];
};

struct perInstanceData {
  float4 posScale;
  float4 color;
  float4 uvCorners;
  float4 texIndex_rotation_padding;
};

layout (std140) uniform ArbitraryData {
  vec4 pbrTool[2];
  vec4 depthAlphaParams;
  vec4 colorVessel;
  vec4 edgeFactorPower;
  vec4 data[kArbitraryReservedVectorCount];
};

layout (std140) uniform instances {
  perInstanceData data[kInstances];
};

layout (std140) uniform ViewData {
  View data;
};
```

2. in common files: to avoid multiple func definition in C++ make it inline:
```
#ifdef __cplusplus
inline // make it inline
#endif
vec3 linearToSRGB(vec3 x) {
const vec2 pp = vec2(1.055, 0.055);
  return pp.x * sqrt(x) - pp.y;
}
```

3. in common files: make specific instances available to GLSL only:
```
#ifndef __cplusplus

ViewData viewData;

ArbitraryData arbitData;

instances instData;

#endif
```
4. In shaders: 
- Always try to use minimal precision which gives acceptable results: `lowp` if not enough `mediump`, `highp` usually has no reason to be used at all.  
- Usually good starting point is: for all integer types `lowp`, float: `mediump`. If specific optimizations required use even lower precision for specific variables.

examples:  

- globally (per shader):
```
precision mediump float;
precision lowp int;
precision lowp uint;  
```

- for specific variables:
```
lowp float scale;
mediump vec2 val;
```

- to set globally (per shader) specific precision for all types:  
```
precision mediump;
```
5. Use instancing whenever it makes sense.