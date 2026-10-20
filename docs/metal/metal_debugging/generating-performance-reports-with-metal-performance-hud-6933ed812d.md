Source: [https://developer.apple.com/documentation/xcode/generating-performance-reports-with-metal-performance-hud](<https://developer.apple.com/documentation/xcode/generating-performance-reports-with-metal-performance-hud>)

<a id="generating-performance-reports-with-the-metal-performance-hud"></a>

# Generating performance reports with the Metal Performance HUD

Record your app’s performance using the heads-up display.

<a id="overview"></a>

## Overview

With the Metal Performance HUD, you can generate performance reports for a specified duration to analyze your app’s performance over that interval. When report generation begins, the system resets all existing metrics, and the HUD automatically enables the performance insights feature. You can also enable other optional HUD features, such as Encoder GPU Time Tracking (see [Understand encoder GPU time tracking](./monitoring-your-metal-apps-graphics-performance-89128c4b39.md#Understand-encoder-GPU-time-tracking)), to add more metrics to the report.

<a id="generate-performance-reports"></a>

### Generate performance reports

You can trigger performance report generation from the global menu, where you select the desired duration. Report durations can range from 5 seconds to 30 minutes.

![A screenshot showing the Generate Performance Report menu.](<generating-performance-reports-with-metal-performance-hud/eb873e219645f38ac528db29.png>)

There’s a 3-second delay before the Metal Performance HUD resets all metrics, enables performance insights, and starts data collection.

![A screenshot showing the Metal Performance HUD waiting for 3 seconds before performance report generation starts.](<generating-performance-reports-with-metal-performance-hud/7fde5e27e8b8eda67352507d.png>)

After the duration elapses, the HUD saves the report to your app’s temporary folder. The system also lists reports in the menu and the insights configuration panel, with options to reveal the report in the Finder or open it directly.

![A screenshot showing the Metal Performance HUD generate performance report menu.](<generating-performance-reports-with-metal-performance-hud/24a049a16277f6ec2e8878f5.png>)

You can also specify a path to save the performance report to by using the `MTL_HUD_REPORT_URL` environment variable.

```
export MTL_HUD_REPORT_URL=<path>
```

![A screenshot showing the performance report.](<generating-performance-reports-with-metal-performance-hud/bb1a98479019b98ae9d5a8f3.png>)

<a id="analyze-and-interpret-the-performance-reports"></a>

### Analyze and interpret the performance reports

Each performance report contains a list of collapsable sections. The complete list is below:

- Report info:
  Details basic metadata about the report, such as the duration of data collection, the start and end frames, the total number of frames collected, and memory usage at the beginning and end of the collection period.
- Frame interval distribution:
  Contains a frame interval distribution table and frame rate statistics, such as 99% high and 1% low.
- Performance insights:
  Details performance insights if the HUD detects them during data collection. Certain insights also add additional tables, such as a frame encoding table if the HUD detects frequent render target changes.
- Top labeled command buffers and encoders:
  Contains a table of most GPU-intensive command buffers and encoders with a label.
- Metrics:
  Contains a table of performance metrics reported by the HUD, including the average, minimum, and maximum values.
- Frame timing:
  Contains a table of the CPU and GPU times of all command buffers and encoders for the last frame of the report.
- Frame encoding:
  Contains a table of the CPU encoding sequence for the last frame of the report. Color attachments are color-coded to help you find patterns and opportunities to merge render passes.
- Shader compilation:
  Contains a table of the shaders compiled and backend compilation time for the duration of the report, as well as an additional table containing all shaders compiled since the app launch.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
