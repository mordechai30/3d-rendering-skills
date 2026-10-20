Source: [https://github.com/microsoft/DirectXTK/wiki/Integration](<https://github.com/microsoft/DirectXTK/wiki/Integration>)

# Adding to a VS solution
## Using project-to-project references
In your application's solution, right-click on the Solution and use **Add \ Existing Project...** to add the appropriate ``.vcxproj`` file to your solution.

<table>
 <tr>
  <td>DirectXTK_Desktop_2026</td>
  <td>Windows desktop applications for Windows 10 or later building with VS 2026 Community, Professional or higher with the latest installed Windows SDK.</td>
 </tr>
</table>

<table>
 <tr>
  <td>DirectXTK_Desktop_2022</td>
  <td>Windows desktop applications for Windows 8.1 or later building with VS 2022 Community, Professional or higher with the latest installed Windows SDK.</td>
 </tr>
 <tr>
  <td>DirectXTK_Desktop_2022_Win10</td>
  <td>Windows desktop applications for Windows 10/Windows 11 building with VS 2022 Community, Professional or higher with the latest installed Windows SDK. <I>Uses XAudio 2.9 and <code>Windows.Gaming.Input</code></I></td>
 </tr>
 <tr>
  <td>DirectXTK_Windows10_2022</td>
  <td>Universal Windows Platform (UWP) apps building with VS 2022 with the latest installed Windows SDK.</td>
 </tr>
 <tr>
  <td>DirectXTK_GDK_2022</td>
  <td>Windows 10 and Windows 11 games building with VS 2022 using the <a href="https://aka.ms/gamedevdocs">Microsoft GDK</a> for x64.</td>
 </tr>
 <tr>
  <td>DirectXTK_GDKW_2022</td>
  <td>Windows 10 and Windows 11 games building with VS 2022 using the <a href="https://aka.ms/gamedevdocs">Microsoft GDK</a> for x64 or ARM64.</td>
 </tr>
</table>

> For VS 2022, use of the [17.12](https://walbourn.github.io/vs-2022-update-12/) is required as all previous versions are no longer supported.

In your application's project, right-click on the **Project** and use "References...", then "Add New Reference...", and then check the DirectXTK project name and click OK. For a Universal Windows Platform (UWP) app or Xbox One solution, you may need to set _Reference Assembly Output_ to false since DirectXTK is a static C++ library and not a WinRT component.

![Settings dialog](<Integration/66354dac4c24a3e69cd048ce.png>)

In your application's project settings, on the "C++ / General" page set Configuration to "All Configurations", set Platform to "All Platforms", and then add the relative path to `DirectXTK\inc;`--assuming you have the DirectXTK folder in the same directory as your ``sln`` file, it should be `$(SolutionDir)\DirectXTK\inc;`--to the _Additional Include Directories_ properties. Click Apply.

![Settings dialog](<Integration/576a2928ad9d12bf2bf71b44.png>)

See [[Audio]] for additional information when setting up Windows desktop projects to use _DirectXTK for Audio_.

See also the [Visual C+ Team Blog](https://devblogs.microsoft.com/cppblog/flexible-project-to-project-references/)

## Using NuGet package manager
Alternatively you can use [NuGet](https://docs.microsoft.com/nuget/what-is-nuget) to install one of the DirectX Tool Kit packages. Use *Project / Manage NuGet Packages...* then select "Online" and search for "DirectXTK".

<table>
 <tr>
  <td><a href="https://www.nuget.org/packages/directxtk_desktop_win10/">directxtk_desktop_win10</a></td>
  <td>This NuGet is configured for Windows desktop C++ applications building for Windows 10 / Windows 11 with VS 2022 or VS 2026 Community/Professional or higher. <I>DirectXTK for Audio</I> in this package uses XAudio 2.9 in the Windows SDK. <i>This packages includes ARM64 binaries.</i></td>
 </tr>
 <tr>
  <td><a href="https://www.nuget.org/packages/directxtk_uwp/">directxtk_uwp</a></td>
  <td>This NuGet is configured for Universal Windows Platform apps for Windows 10 / Windows 11 building with VS 2022 Community/Professional or higher. <I>DirectXTK for Audio</I> in this package uses XAudio 2.9 in the Windows SDK. <i>This packages includes ARM64 binaries.</i></td>
 </tr>
</table>

You should use the NuGet interface to check for updates if you have an older version installed.

### Archived
These NuGet packages are no longer supported.

* [Windows desktop app using VS 2019](https://www.nuget.org/packages/directxtk_desktop_2019)
* [Windows desktop app using VS 2017](https://www.nuget.org/packages/directxtk_desktop_2017)
* [Windows desktop app using VS 2015](https://www.nuget.org/packages/directxtk_desktop_2015)
* [Windows desktop app using VS 2013](https://www.nuget.org/packages/directxtk_desktop_2013)
* [Windows 8.1 Store](https://www.nuget.org/packages/directxtk_windowsstore_8_1)
* [Windows phone 8.1](https://www.nuget.org/packages/directxtk_windowsphone_8_1)
* [Windows phone 8](https://www.nuget.org/packages/directxtk_windowsphone_8)

## Using the vcpkg C++ library manager
The _DirectX Tool Kit_ is also available through the [vcpkg](https://vcpkg.io/) C++ Library Manager.

Using 'manifest-mode' is the recommended way to integrate VCPKG into your project.

For 'system-wide' access, use:

```
vcpkg install directxtk
```

For the 64-bit version of the library, use:

```
vcpkg install directxtk:x64-windows
```

For the Universal Windows Platform (UWP) versions, use:

```
vcpkg install directxtk:x64-uwp
```

> ``arm``, ``arm64``, ``arm64ec``, ``x86``, ``x64``, ``windows``, ``windows-static``, ``windows-static-md``, and ``uwp`` triplets are supported.

> Windows Subsystem for Linux (i.e. ``arm64-linux`` and ``x64-linux``) is not supported.

The **vcpkg** port supports five optional features. The default is to build without *DirectX Tool Kit for Audio* support except UWP which always includes it.

* ``tools``: Installs MakeSpriteFont and xwbtool command-line tools
* ``spectre``: Builds the library with Spectre-mitigation enabled
* ``xaudio2-8`` Use XAudio 2.8 for Windows 8.1 or later support
* ``xaudio2-9`` Use XAudio 2.9 for Windows 10/Windows 11
* ``gameinput``: Makes use of GameInput for GamePad, Keyboard, and Mouse.
* ``xaudio2redist`` Use the XAudio2Redist for Windows 8.1 or later support

> If using vcpkg+MSBuild integration and the DLL versions of the libraries (i.e. not the *-static* triplets), you will need to manually define the preprocessor symbol `DIRECTX_TOOLKIT_IMPORT` or you will get link errors. This is automatically set for CMake integration when using CMake targets.

# CMake

You can reference the *DirectX Tool Kit* CMake package using:

```
find_package(directxtk CONFIG REQUIRED)

target_link_libraries(foo Microsoft::DirectXTK)
```

If using *vcpkg C++ Package Manager*, then you add the ``CMAKE_TOOLCHAIN_FILE`` path to ``vcpkg\scripts\buildsystems\vcpkg.cmake``. If not using *vcpkg*, you need to provide a per-configuration path to the installed location in the ``directxtk_DIR`` variable. Otherwise the ``find_package`` will fail.

![vcpkg toolchain setting](<Integration/1fc1dcc636458a18e9713aa6.png>)

With Visual Studio 2022 Update 6 or later, VCPKG is available via **Microsoft.VisualStudio.Component.Vcpkg**. Use of 'manifest-mode' is recommended.

> There are ``CMakePresets.json`` files available for the CMake projects on [directx-vs-templates](https://github.com/walbourn/directx-vs-templates) that use the ``VCPKG_ROOT`` environment variable to locate the VCPKG install directory. See the commented out code in ``CMakeLists.txt`` as well.

