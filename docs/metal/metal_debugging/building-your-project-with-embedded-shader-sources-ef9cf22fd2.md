Source: [https://developer.apple.com/documentation/xcode/building-your-project-with-embedded-shader-sources](<https://developer.apple.com/documentation/xcode/building-your-project-with-embedded-shader-sources>)

<a id="building-your-project-with-embedded-shader-sources"></a>

# Building your project with embedded shader sources

Prepare to debug your project’s shaders by including source code in the build.

<a id="overview"></a>

## Overview

To debug your shaders in Xcode, configure your build to include shader source code by changing your project’s build settings.
Select your project in the Project navigator, click the Build Settings tab, and search for the Produce Debugging Information setting in the Metal Compiler Build Options section.
Then, change the setting’s Debug entry to “Yes, include source code.”

![An Xcode screenshot showing the Build Settings for a project target, highlighting the Produce Debugging Information setting with the Debug entry set to Yes, include source code.](<building-your-project-with-embedded-shader-sources/745377687470c7968c1922c4.png>)

Alternatively, you can debug the shaders that you compile for release by generating a separate symbol file for each Metal library in your project.
For more information on using this approach, see <doc://com.apple.documentation/documentation/Metal/generating-and-loading-a-metal-library-symbol-file>.

> Important: To ensure you don’t include debugging information in apps you ship to customers, be sure to reset the Produce Debugging Information for Release option to No when you finish debugging.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
