|[Getting Started](Getting-Started.md) for DX11|[Getting Started](https://github.com/microsoft/DirectXTK12/wiki/Getting-Started) for DX12|
|---|---|

This lesson covers adding the _DirectX Tool Kit for Audio_ library and headers to your project.

# Setup
First create a new project using the instructions from the earlier lessons: [Using DeviceResources](Using-DeviceResources.md) and
[Adding the DirectX Tool Kit](Adding-the-DirectX-Tool-Kit.md) which we will use for this lesson.

> If using *DirectX Tool Kit for DX12*, use [Using DeviceResources](https://github.com/microsoft/DirectXTK12/wiki/Using-DeviceResources) and [Adding the DirectX Tool Kit](https://github.com/microsoft/DirectXTK12/wiki/Adding-the-DirectX-Tool-Kit). In this case, the only thing to do in this lesson is adding ``#include <Audio.h>`` and ``#define _USE_MATH_DEFINES`` to **pch.h**.

# NuGet package manager
If you used [NuGet](https://docs.microsoft.com/nuget/what-is-nuget) when [Adding the DirectX Tool Kit](Adding-the-DirectX-Tool-Kit.md), then you already have support for _DirectX Tool Kit for Audio._.

<table>
 <tr>
  <td>directxtk_desktop_2019</td>
  <td>This package is configured for Windows 8.1, and makes use of XAudio 2.8 for <I>DirectX Tool Kit for Audio</I>.</td>
 </tr>
 <tr>
  <td>directxtk_desktop_win10<br />directxtk_uwp<br />directxtk12_uwp<br />directxtk12_desktop_2019<br />directxtk12_desktop_win10</td>
  <td>These packages are configured for Windows 10 and Windows 11, and makes use of <b>XAudio 2.9</b> for <I>DirectX Tool Kit for Audio</I>.</td>
 </tr>
</table>

Complete the steps in **Adding the headers** below including the additional configuration for *XAudio2 Redistributable* or *XAudio 2.9*.

# vc Package Manager (VCPKG)

VCPKG supports both MSBuild and CMake integration. VCPKG is included in [Visual Studio 2022](https://devblogs.microsoft.com/cppblog/vcpkg-is-now-included-with-visual-studio/) v17.6 or later. For an example of MSBuild integration using 'manifest mode', see [d3d11game_vcpkg](https://github.com/walbourn/directx-vs-templates/tree/main/d3d11game_vcpkg) and [d3d11game_vcpkg](https://github.com/walbourn/directx-vs-templates/tree/main/d3d12game_vcpkg).

Edit the `vcpkg.json` file to have an entry for the *directxtk* port with the audio feature enabled:

```
{
  "$schema": "https://raw.githubusercontent.com/microsoft/vcpkg-tool/main/docs/vcpkg.schema.json",
  "dependencies": [
    "directxmath",
    {
      "name": "directxtk",
      "default-features": false,
      "features": [
        "xaudio2redist"
      ]
    },
  ]
}
```

or for DirectX 12, use the *directxtk12* port:

```
{
  "$schema": "https://raw.githubusercontent.com/microsoft/vcpkg-tool/main/docs/vcpkg.schema.json",
  "dependencies": [
    "directxmath",
    {
      "name": "directxtk12",
      "default-features": false,
      "features": [
        "xaudio2-9"
      ]
    },
  ]
}
```

# CMake projects

The *DirectX Tool Kit* CMake projects have a build option for different XAudio2 versions. The [vcpkg](https://vcpkg.io/) port for **directxtk** includes three different features: ``[xaudio2redist]``, ``[xaudio2-9]``, and ``[xaudio2-8]``. See [this page](Audio.md#using-the-vcpkg-c-library-manager) for details.

<details><summary><i>Click here for troubleshooting advice</i></summary>
<p>If using the MinGW toolset, you will likely get unresolved link errors for <code>KSCATEGORY_AUDIO</code>. You should explicitly link to <code>ksguid.lib</code> to fix this.</p></details>

# Adding the headers
Now that we have the _DirectX Tool Kit for Audio_ usable in your project, the next step is to include the library header into your project. You should also make sure ``_USE_MATH_DEFINES`` is set before any header includes ``math.h`` or ``cmath`` since XAudio2 headers require values like ``_M_PI`` to be defined.

```cpp
//
// pch.h
// Header for standard system include files.
//

#pragma once

// Make sure math.h defines M_PI
#define _USE_MATH_DEFINES

...

#include "Audio.h"

...
```

## XAudio 2.9
For a desktop application that requires Windows 10 or Windows 11, in your *pch.h* modify the following section:

```cpp
#include <winsdkver.h>
#define _WIN32_WINNT 0x0A00
#include <sdkddkver.h>
```

> For Windows 10 / Windows 11 platforms other than Windows desktop, you do not need to explicitly set ``_WIN32_WINNT`` as it's already set appropriately.

## XAudio 2.8
If you are using XAudio 2.8, then your application should be built to require Windows 8.1 or later. In *pch.h* modify the following section:

```cpp
#include <winsdkver.h>
#define _WIN32_WINNT 0x0603
#include <sdkddkver.h>
```

<details><summary><i>Click here for troubleshooting advice</i></summary>
<p>If you get a compilation error related to DirectX SDK headers, then you likely don't have the <b>Microsoft.XAudio2.Redist</b> NuGet package set up for the project that is using <code>Audio.h</code></p>
<p>If you get runtime errors related to not being able to find <code>XAUDIO2_9REDIST.DLL</code>, then you likely don't have the <b>Microsoft.XAudio2.Redist</b> NuGet package set up for the project that generates the EXE, or you need to include that DLL from the NuGet package in your installer/deployment.</p></details>

## vc Package Manager

If using VCPKG, you should prefix all the header names with `directxtk` or `directxtk12`:

```cpp
#include <directxtk/Audio.h>
```
```cpp
#include <directxtk12/Audio.h>
```

# Deployment
If you are using XAudio 2.8, then your application has a dependency on Windows 8 or later. If using XAudio 2.9, your application will only run on Windows 10 or Windows 11 devices.

If you are using the XAudio2 Redistributable, then you will need to include the ``XAUDIO2_9REDIST.DLL`` from the NuGet package as part of your application.

**Next lesson:** [Adding audio to your project](Adding-audio-to-your-project.md)

# Further reading
DirectX Tool Kit docs [Audio](Audio.md)

[DirectX Tool Kit for Audio](https://walbourn.github.io/directx-tool-kit-for-audio/)

[XAudio2 and Windows 8](https://walbourn.github.io/xaudio2-and-windows-8/)

[Twilight for Windows 7](https://walbourn.github.io/twilight-for-windows-7/)
