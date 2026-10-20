Source: [https://developer.apple.com/documentation/RealityKit/applying-realistic-material-and-lighting-effects-to-entities](<https://developer.apple.com/documentation/RealityKit/applying-realistic-material-and-lighting-effects-to-entities>)

<a id="applying-realistic-material-and-lighting-effects-to-entities"></a>

# Applying realistic material and lighting effects to entities

Enhance the appearance of objects in a RealityKit scene with Physically Based Rendering
(PBR).

<a id="overview"></a>

## Overview

A [`Material`](https://developer.apple.com/documentation/RealityKit/Material) instance describes the surface properties of an entity
and controls how RealityKit renders that entity. A [`PhysicallyBasedMaterial`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial)
is a type of material that closely approximates the way light bounces off objects
in the real world. It creates very realistic rendered objects that look natural when
placed into an AR scene.

When you import models from USDZ files, RealityKit automatically creates one or more
[`PhysicallyBasedMaterial`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial) instances from the PBR material settings in
the file. You can also create PBR materials manually, either to change the appearance
of an entity loaded from a USDZ file at runtime, or to use PBR rendering with procedurally
created entities.

<a id="create-a-material-and-specify-core-properties"></a>

### Create a material and specify core properties

PBR materials use three core properties to define an object’s fundamental appearance:
[`baseColor`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/baseColor-swift.property), [`roughness`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/roughness-swift.property),
and [`metallic`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/metallic-swift.property). The [`baseColor`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/baseColor-swift.property)
property defines the underlying color of the entity as it would look under soft,
bright, neutral lighting with no shadows or highlights. The `roughness` property
is a measure of how the surface of the entity scatters the light that it reflects.
A material with a low `roughness` looks shiny, while one with a high `roughness`
has a matte appearance. The `metallic` property defines how the material reflects
the environment around the entity. The figure below illustrates the visual effects
of changing the [`metallic`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/metallic-swift.property) and
[`roughness`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/roughness-swift.property) values of a [`PhysicallyBasedMaterial`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial)
while keeping its [`baseColor`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/baseColor-swift.property)
unchanged.

![An illustration showing a matrix of spheres rendered with a physically based material. Each sphere has a different roughness and metallic value to demonstrate the impact of changing these attributes.](<applying-realistic-material-and-lighting-effects-to-entities/2334f45ca2ee92270b78049d.png>)

This example demonstrates how to create a PBR material that uses a color and a single
`roughness` and `metallic` value for the entire material:

```swift
var material = PhysicallyBasedMaterial()
material.baseColor.tint = .orange
material.roughness = PhysicallyBasedMaterial.Roughness(
    floatLiteral: 0.0
)
material.metallic = PhysicallyBasedMaterial.Metallic(
    floatLiteral: 1.0
)
```

And the following example shows how to create a PBR material using UV-mapped image
textures for all three properties:

```swift
var material = PhysicallyBasedMaterial()

if let baseResource = try? TextureResource.load(named: "entity_basecolor") {
    let baseTexture = MaterialParameters.Texture(baseResource)
    material.baseColor = PhysicallyBasedMaterial.BaseColor(
        texture: baseTexture
    )
}

if let metalResource = try? TextureResource.load(named: "entity_metallic") {
    let metalTexture = MaterialParameters.Texture(metalResource)
    material.metallic = PhysicallyBasedMaterial.Metallic(
        texture: metalTexture
    )
}

if let roughnessResource = try? TextureResource.load(named: "entity_roughness") {
    let roughnessTexture = MaterialParameters.Texture(roughnessResource)
    material.roughness = PhysicallyBasedMaterial.Roughness(
        texture: roughnessTexture
    )
}
```

For [`metallic`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/metallic-swift.property) and [`roughness`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/roughness-swift.property)
maps, use a grayscale image. If you use a color image, RealityKit only uses the red
channel.

<a id="add-a-normal-map"></a>

### Add a normal map

*Normal mapping* is a real-time rendering technique that captures fine surface details
for a model using a texture instead of increasing the number of polygons in the model.
It works by storing *surface normals*, which are vectors perpendicular to the surface
of the model, from a much higher resolution version of the same 3D object. A normal
map stores vectors by storing its `X`, `Y`, and `Z` value as the `R`, `G`, and `B`
components of the corresponding pixel in a UV-mapped image. RealityKit uses those
normals to do lighting calculations, which results in much more realistic highlights,
shadows, and reflections without incurring the computational cost of using a much
higher resolution 3D model.

RealityKit’s `PhysicallyBasedMaterial` supports normal maps using the [`normal`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/normal-swift.property)
property.

> Note: RealityKit uses *tangent space normal maps,* which many 3D software packages
> can create. You can recognize tangent space normal maps by their predominately purple
> color.

To add a `normal` map to your entity, load it as a texture resource, and use the
resource to create a `PhysicallyBasedMaterial.Normal` instance, as in this example:

```swift
if let normalResource = try? TextureResource.load(named: "entity_normals") {
    let normalTexture = MaterialParameters.Texture(normalResource)
    material.normal = PhysicallyBasedMaterial.Normal(
        texture: normalTexture
    )
}
```

<a id="specify-blending-and-opacity"></a>

### Specify blending and opacity

By default, RealityKit materials are opaque, but RealityKit can render entities with
transparency to simulate real-world objects. To render a material with transparency,
change the [`blending`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/blending-swift.property) value from
`.opaque` to `.transparent`. The `.transparent` enumeration case takes an associated
value that controls the amount of transparency.

To specify opacity, create a `PhysicallyBasedMaterial.Opacity` object. You can specify
opacity for the entire entity using a single value between `0.0` and `1.0`, where
`1.0` is fully opaque and `0.0` is fully transparent.

```swift
material.blending = .transparent(
    opacity: PhysicallyBasedMaterial.Opacity(floatLiteral: 0.5)
)
```

You can also specify opacity using an image texture (sometimes called an *alpha map*
or *transparency map*). In an alpha map, black pixels represent fully transparent
parts of the entity, white pixels represent fully opaque parts of the entity, and
gray pixels represent parts of the entity that are partially transparent.

```swift
if let opacityResource = try? TextureResource.load(named: "entity_opacity") {
    let opacityMap = MaterialParameters.Texture(opacityResource)
    let opacityValue = PhysicallyBasedMaterial.Opacity(texture: opacityMap)
    material.blending = .transparent(opacity: opacityValue)
}
```

You can change the behavior of an alpha map to function as a *mask* rather than a
transparency map. When using an alpha mask, RealityKit draws every pixel of the entity
either fully transparent or fully opaque with no partially transparency. Use the
[`opacityThreshold`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/opacityThreshold) property to enable alpha
masking. If you specify a value greater than `0.0`, RealityKit uses the image texture
as a mask, and renders any pixel with a value of less than or equal to [`opacityThreshold`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/opacityThreshold)
as fully transparent. RealityKit draws any pixel value greater than [`opacityThreshold`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/opacityThreshold)
as fully opaque.

<a id="add-specular-highlights"></a>

### Add specular highlights

RealityKit automatically draws *specular highlights* for physically based materials
using the values of various properties, primarily [`roughness`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/roughness-swift.property)
and [`metallic`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/metallic-swift.property). Specular highlights
are bright spots of reflected light that appear on shiny objects.

![An illustration showing a sphere and a cube with rounded corners. Both have a shiny surface and a small white spot labeled “specular highlights” where they reflect the scene’s light source.](<applying-realistic-material-and-lighting-effects-to-entities/7758a16f8ca42d02934bf0df.png>)

While many real-world objects can be accurately and realistically simulated with
just the core PBR properties, you can create additional realistic effects by augmenting
the specular highlights.

Use the [`specular`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/specular-swift.property) property to
simulate the bright highlights found on certain *dielectric* (nonmetallic) materials
like cut gemstones and faceted glass, which have specular highlights much brighter
than the ones RealityKit creates from just the core properties.

Here’s how to specify specular using a single value for the entire material:

```swift
material.specular = PhysicallyBasedMaterial.Specular(
    floatLiteral: 0.8
)
```

The following example demonstrates how to specify specular using a UV-mapped image
texture:

```swift
if let specularResource = try? TextureResource.load(named: "entity_specular") {
    let specularTexture = MaterialParameters.Texture(specularResource)
    material.specular = PhysicallyBasedMaterial.Specular(
        texture: specularTexture
    )
}
```

You can also use specular highlights to simulate subtle reflections like the ones
that occur on some types of fabric. Create these types of effects with the [`sheen`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/sheen)
property, as illustrated in the following figure.

![An illustration of two spheres. The one on the right has very subtle, soft specular highlight and is labeled “With Sheen”. The one on the right has no specular highlights and is labeled “Without Sheen”.](<applying-realistic-material-and-lighting-effects-to-entities/8c1a59eeafd0e19b1c78838c.png>)

This example shows how to specify [`sheen`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/sheen) using
a single value for the entire material:

```swift
let sheenTint = PhysicallyBasedMaterial.Color(
    red: 0.8, green: 0.8, blue: 0.8, alpha: 1.0
)
material.sheen = PhysicallyBasedMaterial.SheenColor(
    tint: sheenTint
)
```

And this example demonstrates how to specify [`sheen`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/sheen)
using a UV-mapped image texture:

```swift
if let sheenResource = try? TextureResource.load(named: "entity_sheen") {
    let sheenMap = MaterialParameters.Texture(sheenResource)
    material.sheen = PhysicallyBasedMaterial.SheenColor(
        texture: sheenMap
    )
}
```

<a id="use-anisotropy-for-directional-highlights"></a>

### Use anisotropy for directional highlights

By default, PBR materials are *isotropic*; in other words, an entity that uses a
[`PhysicallyBasedMaterial`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial) reflects light uniformly in all directions,
mimicking the behavior of most real-world objects. Some objects, including those
with many small parallel striations such as vinyl records, CDs, or straight hair,
reflect light more in some directions than others, resulting in stretched or oblong
specular highlights called *anisotropic* highlights.

![An illustration showing 11 metallic spheres in a horizontal row. The left-most sphere is isotropic. The spheres represent increasing anisotropy from left to right, with the sphere furthest to the right displaying a long, stretched highlight.](<applying-realistic-material-and-lighting-effects-to-entities/329db743347876831edf9d2e.png>)

In RealityKit, you adjust anisotropy using two parameters: [`anisotropyLevel`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/anisotropyLevel-swift.property)
and [`anisotropyAngle`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/anisotropyAngle-swift.property). To control
the amount of anisotropy, use [`anisotropyLevel`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/anisotropyLevel-swift.property).
Specifying a value of `0.0` results in an entirely isotropic appearance, while nonzero
values up to `1.0` simulate the appearance of increasingly anisotropic objects. Change
the angle of anisotropy to affect the direction in which the specular highlights
stretch with [`anisotropyAngle`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/anisotropyAngle-swift.property),
which also takes a value between `0.0` and `1.0.` `A` value of `0.0` means a rotation
of 0° and a value of `1.0` indicates a rotation of 360°. To determine the [`anisotropyAngle`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/anisotropyAngle-swift.property)
value to use, divide the desired angle in degrees by `360.0` or the desired angle
in radians by pi times 2.

```swift
let angleDegrees: Float = 125
let anisotropyAngleFromDegrees = angleDegrees / 360

let angleRadians: Float = 2.181662
let anisotropyAngleFromRadians = angleRadians / (2 * .pi)
```

The following example demonstrates how to specify anisotropy using single values
for the entire material:

```swift
material.anisotropyLevel = PhysicallyBasedMaterial.AnisotropyLevel(
    floatLiteral: 0.5
)
material.anisotropyAngle = PhysicallyBasedMaterial.AnisotropyAngle(
    floatLiteral: 0.5
)
```

And this example shows how to specify anisotropy using a UV-mapped image texture
for [`anisotropyLevel`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/anisotropyLevel-swift.property) and a separate
image for [`anisotropyAngle`](https://developer.apple.com/documentation/RealityKit/PhysicallyBasedMaterial/anisotropyAngle-swift.property):

```swift
if let anisoLevelResource = try? TextureResource.load(named: "entity_aniso_level") {
    let anisoLevelMap = MaterialParameters.Texture(anisoLevelResource)
    material.anisotropyLevel = PhysicallyBasedMaterial.AnisotropyLevel(
        texture: anisoLevelMap
    )
}

if let anisoAngleResource = try? TextureResource.load(named: "entity_aniso_angle") {
    let anisoAngleMap = MaterialParameters.Texture(anisoAngleResource)
    material.anisotropyAngle = PhysicallyBasedMaterial.AnisotropyAngle(
        texture: anisoAngleMap
    )
}
```

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
