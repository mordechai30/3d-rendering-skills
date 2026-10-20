Source: [https://developer.apple.com/documentation/xcode/replaying-a-gpu-trace-file](<https://developer.apple.com/documentation/xcode/replaying-a-gpu-trace-file>)

<a id="replaying-a-gpu-trace-file"></a>

# Replaying a GPU trace file

Debug and profile your app’s performance using a GPU trace file in the Metal debugger.

<a id="overview"></a>

## Overview

Replaying a GPU trace file allows you to debug and profile previously captured GPU commands using the Metal debugger. For more information, see [Capturing a Metal workload in Xcode](./capturing-a-metal-workload-in-xcode-2364f9433b.md) or [Capturing a Metal workload programmatically](./capturing-a-metal-workload-programmatically-0fa5faba68.md).

To replay a GPU trace file, open it in Xcode. Before clicking Replay, you can configure which device to use (if there’s more than one available), as well as configure whether to run with profiling.

![An Xcode screenshot of the Replay GPU Trace dialog with options to begin replaying a GPU trace file.](<replaying-a-gpu-trace-file/ea9b231ae914952c07f1960f.png>)

<a id="configure-replay"></a>

### Configure replay

If you have multiple devices, you need to select a device before you can replay the GPU trace file.
Xcode automatically selects the most compatible device, but you can select a different device using the Device popover.

> Warning: GPU trace files are only compatible with devices of the same type, the same GPU, and the same operating system. Otherwise, performance may vary. For example, if you capture a Metal workload on a Mac with an AMD GPU, replaying the exported GPU trace file on a Mac with the Apple M1 chip may not work or behave the same.

You can optionally enable the Profile GPU Trace option to have Xcode automatically profile after replaying.
Profiling has an initial performance impact on the Metal debugger, so only enable this option when debugging your app’s performance.
You can always profile later as needed.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
