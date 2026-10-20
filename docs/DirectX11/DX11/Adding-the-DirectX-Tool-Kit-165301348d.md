Source: [https://github.com/microsoft/DirectXTK/wiki/Adding-the-DirectX-Tool-Kit](<https://github.com/microsoft/DirectXTK/wiki/Adding-the-DirectX-Tool-Kit>)

|[[Getting Started]]|
|---|

After creating a new project in [[Using DeviceResources]], the next step is to add the _DirectX Tool Kit_ library and headers to the project so we can make use of it in our code.

# NuGet package manager
The easiest way to achieve this is to use the [NuGet package manager](https://docs.microsoft.com/nuget/what-is-nuget) built into Visual Studio.

* From the drop-down menu, select **Project** / **Manage NuGet Packages...**
* Select "Browse" on the top tab, and make sure the _Package source_ is set to "nuget.org"
* In the text search field type "DirectXTK" and hit enter to search for the packages
* Select the package with the id  **[directxtk_desktop_win10](https://www.nuget.org/packages/directxtk_desktop_win10/)** or **[directxtk_uwp](https://www.nuget.org/packages/directxtk_uwp/)** for <abbr title="Universal Windows Platform">UWP</abbr>
* Select "Install"
* When finished, close the NuGet Manager

![Manage NuGet Packages](<Adding-the-DirectX-Tool-Kit/cb3f9c9044c5689fa492d0d8.png>)

You can check for updates to the NuGet package by selecting "Updates/All" in the left-hand tree view. If there are updates, select the "DirectX Tool Kit" package, and click on "Update".

> **directxtk12_desktop_win10** supports both VS 2022 and VS 2026 since they are [binary compatible](https://learn.microsoft.com/en-us/cpp/porting/binary-compat-2015-2017?view=msvc-170).

# vc Package Manager (VCPKG)

VCPKG supports both MSBuild and CMake integration. VCPKG is included in [Visual Studio 2022](https://devblogs.microsoft.com/cppblog/vcpkg-is-now-included-with-visual-studio/) v17.6 or later. For an example of MSBuild integration using 'manifest mode', see [d3d11game_vcpkg](https://github.com/walbourn/directx-vs-templates/tree/main/d3d11game_vcpkg).

Edit the `vcpkg.json` file to have an entry for the *directxtk* port:

```
{
  "$schema": "https://raw.githubusercontent.com/microsoft/vcpkg-tool/main/docs/vcpkg.schema.json",
  "dependencies": [
    "directxmath",
    "directxtk"
  ]
}
```

# Project-to-project references
Another option is to use Visual Studio's [project-to-project references](https://devblogs.microsoft.com/cppblog/flexible-project-to-project-references/). This approach is a little more setup, but it does ensure that you are building the full DirectX Tool Kit library as part of your solution, and allows you to make changes directly to the tool kit if desired as well.

* Extract the [release .zip file](https://github.com/Microsoft/DirectXTK/releases) into a directory relative to the new project you created. For this tutorial, we will assume the ``DirectXTK`` folder is in the same folder as your new project's Visual Studio Solution (``.sln``) file.
* Right-click on your solution in the Solution Explorer, and select **Add** / **Existing Project...**
* Browse into the "DirectXTK" folder and select ``DirectXTK_Desktop_201x.vcxproj`` for Win32 -or- ``DirectXTK_Windows10_201x.vcxproj`` for UWP, click "Open"
* If Visual Studio presents a "Security Warning", select "OK". Optional: Uncheck "Ask me for every project in this solution" first.
* Right-click on your project in the Solution Explorer, and select **Add** / **Reference...**
* Check ``DirectXTK`` and select "OK"
* Click on "Configuration Properties" in the left-hand tree view, then **C/C++** / **General**
* Select "All Configurations" and "All Platforms"
* Edit _Additional Include Directories_ to the relative path to the ``DirectXTK\Inc`` folder. With our original assumption, you can use ``$(SolutionDir)\DirectXTK\Inc``.
* Select "OK"

![Add Reference](<Adding-the-DirectX-Tool-Kit/ab6eda38aca083690b9ff8bb.png>)

![Additional Includes](<Adding-the-DirectX-Tool-Kit/e5c5f7654b634f5c99bbf607.png>)

For more information see [[Integration]] under _Adding to a VS solution_.

> For Xbox One XDK apps, you have to use project-to-project references instead of NuGet to ensure the built library matches the XDK edition specific headers and shader generation.

# CMake projects

## Using directly as a sub-project

For a CMake project, you can copy/clone the DirectXTK library into your CMake project repository, and add:

```
add_subdirectory(${CMAKE_SOURCE_DIR}/DirectXTK ${CMAKE_BINARY_DIR}/bin/CMake/DirectXTK)
target_link_libraries(${PROJECT_NAME} PRIVATE DirectXTK)
```

> If using MinGW/GNUC, you should make use of the vcpkg solution instead. MinGW does not provide a working version of DirectXMath headers, and vcpkg will provide them via the **directxmath** port. Alternatively, you can manually build/install a DirectXMath instance directly from [GitHub](https://github.com/microsoft/DirectXMath).

## vcpkg C++ Package Manager
For a CMake project, the *DirectX Tool Kit* is available as a CMake package, which you reference from your ``CMakeLists.txt`` as:

```
find_package(directxtk CONFIG REQUIRED)

target_link_libraries(${PROJECT_NAME} PRIVATE
    d3d11.lib dxgi.lib dxguid.lib uuid.lib
    kernel32.lib user32.lib
    comdlg32.lib advapi32.lib shell32.lib
    ole32.lib oleaut32.lib
    Microsoft::DirectXTK
)
```

You can build and install the cmake package version using [vcpkg](https://github.com/Microsoft/vcpkg) for the various 'flavors' you require:

```
vcpkg install directxtk
vcpkg install directxtk:x64-windows
vcpkg install directxtk:arm64-uwp
```

If using ``CMakePresets.json`` set the environment variable ``VCPKG_ROOT`` and add:

```
"cacheVariables": {
  CMAKE_TOOLCHAIN_FILE": {
    value": "$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake",
    "type": "FILEPATH"
  }
},
```

If not using **vcpkg**, you have to provide a per-configuration path to the individual installed package in the ``directxtk_DIR`` variable:

![Setting cmake installed package path](<Adding-the-DirectX-Tool-Kit/46225739c2c7d673dcf655df.png>)

> The `CMakeList.txt` from *directx-vs-templates* for Win32 desktop and UWP C++/WinRT have commented out code to supporting VCPKG integration of *directxtk*.

# Adding the headers
Now that we have the _DirectX Tool Kit_ usable in your project, the next step is to include the library headers into your project.

General advice for C++ projects is that you should only add the headers you actually use to your project, but to simplify the tutorial we will go ahead and add them all to your new project's **pch.h** header:

```cpp
//
// pch.h
// Header for standard system include files.
//

#pragma once

...

#include "BufferHelpers.h"
#include "CommonStates.h"
#include "DDSTextureLoader.h"
#include "DirectXHelpers.h"
#include "Effects.h"
#include "GamePad.h"
#include "GeometricPrimitive.h"
#include "GraphicsMemory.h"
#include "Keyboard.h"
#include "Model.h"
#include "Mouse.h"
#include "PostProcess.h"
#include "PrimitiveBatch.h"
#include "ScreenGrab.h"
#include "SimpleMath.h"
#include "SpriteBatch.h"
#include "SpriteFont.h"
#include "VertexTypes.h"
#include "WICTextureLoader.h"
```

> This does not include the _DirectX Tool Kit for Audio_ header ``Audio.h`` which is covered by another [[tutorial|Adding the DirectX Tool Kit for Audio]].

If using VCPKG, you should prefix all the header names with `directxtk`:

```cpp
#include <directxtk/BufferHelpers.h>
#include <directxtk/CommonStates.h>
#include <directxtk/DDSTextureLoader.h>
#include <directxtk/DirectXHelpers.h>
#include <directxtk/Effects.h>
#include <directxtk/GamePad.h>
#include <directxtk/GeometricPrimitive.h>
#include <directxtk/GraphicsMemory.h>
#include <directxtk/Keyboard.h>
#include <directxtk/Model.h>
#include <directxtk/Mouse.h>
#include <directxtk/PostProcess.h>
#include <directxtk/PrimitiveBatch.h>
#include <directxtk/ScreenGrab.h>
#include <directxtk/SimpleMath.h>
#include <directxtk/SpriteBatch.h>
#include <directxtk/SpriteFont.h>
#include <directxtk/VertexTypes.h>
#include <directxtk/WICTextureLoader.h>
```

> If using the DLL version of *DirectX Tool Kit*, you may need to add before the include statements ``#define DIRECTX_TOOLKIT_IMPORT`` to resolve link errors. This is normally only needed with MSBuild+VCPKG integration as CMake targets automatically add this define if needed.

Then finish off the setup by adding a C++ namespace using statement to your **Game.cpp** file to make it a bit easier to use the SimpleMath types:

```cpp
//
// Game.cpp -
//

#include "pch.h"
#include "Game.h"

using namespace DirectX;
using namespace DirectX::SimpleMath;

using Microsoft::WRL::ComPtr;

...
```

# Graphics memory

**This is only required for Xbox One XDK when using DirectX 11.X (or when using [DirectX 12](https://github.com/microsoft/DirectXTK12/wiki)). It's a no-op otherwise.**

To finish off setup if using Xbox One XDK, in the **Game.h** file, add the following variable to the bottom of the Game class's private declarations:

```cpp
std::unique_ptr<DirectX::GraphicsMemory> m_graphicsMemory;
```

In **Game.cpp**, add to the TODO of **CreateDeviceDependentResources**:

```cpp
auto device = m_deviceResources->GetD3DDevice();
m_graphicsMemory = std::make_unique<GraphicsMemory>(device);
```

In **Game.cpp**, in **Render** add a call to [[GraphicsMemory]] ``Commit`` right after the present:

```cpp
void Game::Render()
{
    // Don't try to render anything before the first Update.
    if (m_timer.GetFrameCount() == 0)
    {
        return;
    }

    Clear();

    auto context = m_deviceResources->GetD3DDeviceContext();
    // TODO: Add your rendering code here.

    // Show the new frame.
    m_deviceResources->Present();
    m_graphicsMemory->Commit();
}
```

In **Game.cpp**, add to the TODO of **OnDeviceLost**:

```cpp
m_graphicsMemory.reset();
```

# Platform notes

If you are using the DirectX Tool Kit with the Xbox One XDK, then you may need to build the Xbox One shaders that match your XDK release. Generally this is handled automatically, but if you run into problems you can build them directly from the Xbox One Developer Command prompt using ``CompileShaders.cmd xbox``

**Next lessons:** [[Sprites and textures]], [[Game controller input]], [[Using the SimpleMath library]], [[Adding the DirectX Tool Kit for Audio]]
