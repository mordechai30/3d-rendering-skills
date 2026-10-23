# Next Steps

## Graphics

To explore more about DirectX Graphics functionality, continue with the tutorials at [Getting Started](Getting-Started.md) starting at [Rendering a model](Rendering-a-model.md).

## Input

To implement game input using GamePad, see [Game controller input](Game-controller-input.md) which for this tutorial's project will use the GameInput APIs.

To implement game input using Mouse and Keyboard, see [Mouse and keyboard input](Mouse-and-keyboard-input.md).

## Math

For more on the SimpleMath library, which is a C++ wrapper for the DirectXMath SIMD library, see [Using the SimpleMath library](Using-the-SimpleMath-library.md).

Alternatively, advanced users can use the **directxmath-usage** skill from [DirectXMath](https://github.com/microsoft/DirectXMath).

## DirectX Tool Kit for Audio

The audio functionality is built on XAudio2 which is a game audio API for Windows which provides real-time mixing and audio processing capabilities.

To add *DirectX Tool Kit for Audio* to your project, update the `vcpkg.json` file:

```json
{
  "name": "directxtk",
  "default-features": false,
  "features": [
    "gameinput",
    "xaudio2-9"
  ]
}
```

For example, the full `vcpkg.json` should look something like:

```json
{
  "$schema": "https://raw.githubusercontent.com/microsoft/vcpkg-tool/main/docs/vcpkg.schema.json",
  "dependencies": [
    "directxmath",
    {
      "name": "directxtk",
      "default-features": false,
      "features": [
        "gameinput",
        "xaudio2-9"
      ]
    }
  ]
}
```

Then add to the pch.h:

```cpp
#include <directxtk/Audio.h>
```

From there, pick up at [Adding audio to your project](Adding-audio-to-your-project.md).
