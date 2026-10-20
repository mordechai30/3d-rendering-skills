Source: [https://developer.apple.com/documentation/xcode/analyzing-the-memory-usage-of-your-metal-app](<https://developer.apple.com/documentation/xcode/analyzing-the-memory-usage-of-your-metal-app>)

<a id="analyzing-the-memory-usage-of-your-metal-app"></a>

# Analyzing the memory usage of your Metal app

Keep your app alive in the background by managing its memory footprint.

<a id="overview"></a>

## Overview

Instruments provides the Game Memory template to help you understand the memory growth in your Metal app.
Keeping a small memory footprint allows the system to keep the app alive in the background longer, especially on devices with more constrained memory capacity.
For more information, see [Profile and optimize your game’s memory](https://developer.apple.com/videos/play/wwdc2022/10106/).

<a id="open-the-game-memory-template"></a>

### Open the Game Memory template

Start the memory analysis from your Xcode project by choosing Product > Profile, or by pressing Command-I.
Alternatively, you can launch Instruments and then select the process from the drop-down list.

In the Template Selection window, select Game Memory.

![A screenshot of the Template Selection window with the Game Memory template selected.](<analyzing-the-memory-usage-of-your-metal-app/c22a18445860f4e322ba5362.png>)

<a id="get-to-know-the-instruments"></a>

### Get to know the instruments

- Allocations: Analyzes the memory life cycle of a process’s allocated blocks, and can record reference-counting events.
- Metal Resource Events: Records Metal GPU resource allocations, such as textures and buffers.
- VM Tracker: Tracks the virtual memory space of a process over time, identifying regions by tag and reporting usage statistics.
- Virtual Memory Trace: Tracks virtual memory activity per thread.
- Metal Application: Records Metal app events.
- GPU: Records GPU events.

<a id="record-an-instruments-capture"></a>

### Record an Instruments capture

Begin collecting the data by clicking the Record button.

![A screenshot of the Instruments window highlighting the Record button.](<analyzing-the-memory-usage-of-your-metal-app/4b0b73428a33e85e4d95b96c.png>)

Within your app, perform the actions that reproduce the memory problem, and then click the Record button to stop recording.

<a id="analyze-your-apps-memory-allocations"></a>

### Analyze your app’s memory allocations

The Game Memory template shows both memory allocations and memory footprint.

Memory allocations occupy space in the virtual memory address space.
When your app allocates memory, these new allocations may not immediately take up space on physical memory.
It’s not until your app uses these allocations that they consume physical memory.

The Allocations track provides a detailed view of memory allocations, their sizes, and object reference counts.

> Note: The Allocations track doesn’t include Metal resources with private storage mode — only managed and shared storage modes.

![A screenshot of Instruments with the Allocations track selected. The bottom details pane displays the statistics from the Allocations track.](<analyzing-the-memory-usage-of-your-metal-app/d8cc520186a819211da6da22.png>)

The Statistics view in the bottom detail area displays the categories of memory allocations.
At the top of the Category column, there are three umbrella categories that summarize all allocations:

- All Heap & Anonymous VM: Includes everything.
- All Heap Allocations: Includes dynamically allocated buffers that may contain resources.
- All Anonymous VM: Includes interesting VM regions that may be dirty.
  You can also find some Metal-related memory here.

Below them, you can find more detailed categories.
Metal resource allocations are in the `VM: IOAccelerator` category, and drawables are in `VM: IOSurface`.

To inspect the individual allocations in a category, click the arrow button next to the category name in the table.

![A screenshot of the details pane displaying the statistics from the Allocations track.](<analyzing-the-memory-usage-of-your-metal-app/db12777c8508682195878d08.png>)

After selecting a category, you can sort the table by the Size column to find the largest memory allocation during the selected time range.

![A screenshot of the details pane displaying the All Heap Allocations statistics from the Allocations track.](<analyzing-the-memory-usage-of-your-metal-app/a9bfb0f8bd741c15793157a3.png>)

You can also select an allocation in the list to view its description and stack trace in the inspector on the right.

<a id="analyze-metal-resource-allocations"></a>

### Analyze Metal resource allocations

The Metal Resource Events track displays a history of all Metal-specific resource allocations and
deallocations, along with their labels (see [Naming resources and commands](./naming-resources-and-commands-8d146531da.md)).

![A screenshot of Instruments with the Metal Resource Events track selected. The bottom details pane displays the list of resource events.](<analyzing-the-memory-usage-of-your-metal-app/09fb424cecad6c0d669c7ff3.png>)

The Resource Events view in the bottom detail area lists the resource allocation and deallocation events.
It includes events from created or destroyed resources in the selected time range.
Not all resources in the list persisted until the end of the time range.

<a id="analyze-your-apps-total-virtual-memory-footprint"></a>

### Analyze your app’s total virtual memory footprint

The Allocations track and the Metal Resource Events track both highlight memory allocations.
However, allocations don’t always translate to memory footprint.
The VM Tracker track shows the noncompressed and compressed/swapped dirty memory
that together make up your app’s memory footprint.

Memory operates on the granularity of pages, and those pages can be either clean or dirty.

- Clean memory: Includes memory-mapped files and read-only frameworks.
- Dirty memory: Includes heap-allocated memory and written symbols in frameworks.

To conserve the amount of physical memory that your app uses, the system may compress or swap
out some dirty pages that your app hasn’t accessed recently.

> Important: The system charges your app for any compressed/swapped memory based on its orginal size before compression.

![A screenshot of Instruments with the VM Tracker track selected. The bottom details pane displays a summary of the VM regions.](<analyzing-the-memory-usage-of-your-metal-app/87b3d0f53a70b96d852c4ac3.png>)

The center timeline area graphs the following metrics:

- Dirty Size: The amount of noncompressed dirty memory.
- Swapped Size: The amount of compressed/swapped dirty memory in its original size before compression.
- Resident Size: The amount of resident memory.

The corresponding columns are also available in the Summary view of the bottom detail area.
There, you can expand the VM region types.
In the mapped file type in the screenshot below, you can see the memory-mapped file of the bistro scene that the Modern Renderer app loaded:

![A screenshot of the details pane displaying a summary of the VM regions highlighting the largest memory-mapped file.](<analyzing-the-memory-usage-of-your-metal-app/9d55173ba71a2c66a37d87dd.png>)

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
