Source: [https://github.com/microsoft/DirectXTK/wiki](<https://github.com/microsoft/DirectXTK/wiki>)

https://go.microsoft.com/fwlink/?LinkId=248929

[![OpenSSF Best Practices](<DirectXTK-wiki/4d26a51ecd7a6289979656f5.svg>)](https://www.bestpractices.dev/projects/8939)

[![GitHub All Releases](<DirectXTK-wiki/1dc022c171a0c8f3c02d8780.svg>) ![GitHub Release Date](<DirectXTK-wiki/56a4a40ff3197ca6dcf5209d.svg>)](https://github.com/microsoft/DirectXTK/releases/latest)

[![Nuget UWP](<DirectXTK-wiki/092ab8369e4ba9ec64a5ba43.svg>)](https://www.nuget.org/packages/directxtk_uwp/) [![Nuget Win10](<DirectXTK-wiki/5cb96afa3369cc7558903b8c.svg>)](https://www.nuget.org/packages/directxtk_desktop_win10/)
![Vcpkg Version](<DirectXTK-wiki/b0a0b8246e6703ea40ca7edd.svg>)
![WinGet Package Version](<DirectXTK-wiki/d4f67f0afca97daec0b3dabb.makespritefont>)

![GitHub last commit](<DirectXTK-wiki/7a4a3d24eaecb8c843d7109f.svg>)
![Code size](<DirectXTK-wiki/1eeac7b47fa6ec479ef10bf9.svg>)

![GitHub Actions test suite VS 2022/VS2026](<DirectXTK-wiki/6ea421da3fd98a0a333692c1.svg>))
![GitHub Actions native arm64 build](<DirectXTK-wiki/8f1a5fabf4c7bd5381b6bce1.yml>))

![GitHub Actions Workflow Build Verification Test x64](<DirectXTK-wiki/4ca85f75c66632dd7753d7cb.yml>))
![GitHub Actions Workflow Build Verification Test arm64](<DirectXTK-wiki/84f2a7d76713796057b8e28e.yml>))
![GitHub Actions Workflow using VCPKG](<DirectXTK-wiki/471cb1599051fd741cef1203.yml>)
![GitHub Actions Workflow Super-Linter](<DirectXTK-wiki/9fd032d731ee012d75174d76.yml>)

![DirectX Logo](<DirectXTK-wiki/b0a12877be69e18384c7e294.jpg>)The **DirectX Tool Kit** (aka **DirectXTK**) is a collection of helper classes for writing **DirectX 11.x** code in C++.

For an overview of the project, see these blog posts: [March 2012](https://walbourn.github.io/directxtk/), [January 2013](https://walbourn.github.io/directxtk-update/), [September 2014](https://walbourn.github.io/directx-tool-kit-now-with-gamepads/), [August 2015](https://walbourn.github.io/directx-tool-kit-keyboard-and-mouse-support/), [July 2016](https://walbourn.github.io/directx-tool-kit-for-directx-12/), [September 2021](https://walbourn.github.io/latest-news-on-directx-tool-kit/), and [October 2021](https://walbourn.github.io/directx-tool-kit-vertex-skinning-update/).

For an overview of *DirectX Tool Kit for Audio*, see these blog posts: [December 2013](https://walbourn.github.io/directx-tool-kit-for-audio/) and [May 2020](https://walbourn.github.io/directx-tool-kit-for-audio-updates-and-a-direct3d-9-footnote/).

For some recent changes to this project, see [this blog post](https://walbourn.github.io/github-project-updates-2025/).

[[Getting Started]]

[[Integration]]

[[DirectXTK]] for DirectX 11 library

[[MakeSpriteFont]] utility

[[XWBTool]] utility

[[Samples]]

[[Game Gallery]]

[[Resources]]

[[Utilities]]

# DirectX 11
DirectX 11 is supported on Windows 7, Windows 8.1, Windows 10, and Windows 11. Use of DirectX 11 for beginners is highly recommended.

> This project last supported Windows 7 in the October 2024 release.

# DirectX 12
A version of _DirectX Tool Kit for DirectX 12_ is available on [GitHub](https://github.com/Microsoft/DirectXTK12). DirectX 12 is an expert API for Windows 10 / Windows 11 which builds on knowing the ins & outs of DirectX 11. Both DirectX 11 and DirectX 12 provide access to the same graphics hardware features, but drive the hardware in different ways which can allow a well-optimized DirectX 12 engine to achieve much lower CPU overhead than in DirectX 11.

> Note that advanced hardware features like Shader Model 6, DirectX Raytracing, Amplification & Mesh Shaders, and other "DirectX Ultimate" features do in fact require DirectX 12 as they are not exposed in DirectX 11. The statement above is still 100% true for the core graphics functionality used by *DirectX Tool Kit*.

# NuGet

DirectX Tool Kit is also available from the NuGet Gallery:
- [Windows desktop app using VS 2022 or VS 2026 for Windows 10](https://www.nuget.org/packages/directxtk_desktop_win10/) *includes ARM64*
- [Universal Windows Platform apps using VS 2022](https://www.nuget.org/packages/directxtk_uwp/)

# vcpkg C++ Package Manager

DirectX Tool Kit has a vcpkg installation [port](https://github.com/microsoft/vcpkg/tree/master/ports/directxtk) as well.

# Porting from D3DX
See [this post](https://aka.ms/Kfsdiu) for a complete listing of D3DX equivalents.

# Support

For questions, consider using [Stack Overflow](https://stackoverflow.com/questions/tagged/directxtk) with the *directxtk* tag, or the [DirectX Discord Server](https://discord.gg/directx) in the *dx9-dx11-developers* or *input-and-audio* channels.

For bug reports and feature requests, please use GitHub [issues](https://github.com/microsoft/DirectXTK/issues) for this project.

# Security

The DirectX Tool Kit library functions are invoked by client code. While effort is made to validate parameters and arguments in code, the client code is responsible for validating any relevant user-input. The primary security focus for DirectXTK is the image loading code and audio wave file loaders which process potentially untrusted content from disk/memory. When using Windows Imaging Component (WIC), that component has a strong security guarantee and validation story for security vulnerabilities. For the custom DDS, WAV, and XWB codecs, significant hardening and validation has been applied and the code is subject to file-fuzzing.

This project is subject to Microsoft's Open Source [Security Policy](https://github.com/microsoft/DirectXTK/blob/main/SECURITY.md).

For a list of known vulnerabilities, see [GitHub](https://github.com/microsoft/DirectXTK/security/advisories).

A [minisign](https://jedisct1.github.io/minisign/) signature file is attached to the GitHub release. To verify the signature, download the `.minisig` file and `.zip` and run:

```
winget install --id jedisct1.minisign -e
minisign -Vm DirectXTK-???.zip -P RWTzwEYN1MsFqkM7jZSD40qno+B4scRpbEYkiAvP6fpEE1D+r/IA9Dqc
```

The pre-built binaries attached to the release are Authenticode signed with the *Microsoft 3rd Party Application Component* certificate.

# Contributing

This project welcomes contributions and suggestions. Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

Tests for new features should also be submitted as a PR to the [Test Suite](https://github.com/walbourn/directxtktest/wiki) repository.

Information on coding-style can be found [[here|Implementation]].

# Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

# Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party's policies.

# Governance

This project currently runs on a 'single-maintainer' governance model run by Chuck Walbourn. Contributions and participation from others is encouraged, but over the years it's mostly been a solo project.

# Credits

The _DirectX Tool Kit_ is the work of Shawn Hargreaves and Chuck Walbourn, with contributions from Aaron Rodriguez Hernandez and Dani Roman.

Thanks to Shanon Drone for the SDKMESH file format.

Thanks to Adrian Tsai for the geodesic sphere implementation.

Thanks to Garrett Serack for his help in creating the NuGet packages for DirectX Tool Kit.

Thanks to Roberto Sonnino for his help with the ``CMO``, DGSL rendering, and the VS Starter Kit animation.

Thanks to Pete Lewis and Justin Saunders for the normal-mapped and PBR shaders implementation.

Thanks to Imre Eilertsen for creating winget ports for the command-line tools.

Thanks to Andrew Farrier, Jon Martin, and Scott Matloff for their help with code reviews.

Thanks to Shawn Hargreaves and Nada Ouf for their continued support for this library.


