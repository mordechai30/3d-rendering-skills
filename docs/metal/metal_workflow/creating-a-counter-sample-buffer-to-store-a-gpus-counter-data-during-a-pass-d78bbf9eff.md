Source: [https://developer.apple.com/documentation/metal/creating-a-counter-sample-buffer-to-store-a-gpus-counter-data-during-a-pass?language=objc](<https://developer.apple.com/documentation/metal/creating-a-counter-sample-buffer-to-store-a-gpus-counter-data-during-a-pass?language=objc>)

<a id="creating-a-counter-sample-buffer-to-store-a-gpus-counter-data-during-a-pass"></a>

# Creating a counter sample buffer to store a GPU’s counter data during a pass

Make a buffer that provides a place for a GPU to save its runtime performance metrics as it runs a pass.

<a id="discussion"></a>

## Discussion

You can create and use an [`MTLCounterSampleBuffer`](https://developer.apple.com/documentation/Metal/MTLCounterSampleBuffer) instance to store information from a GPU counter. To check whether a GPU produces data for a specific counter, see [Confirming which counters and counter sets a GPU supports](./confirming-which-counters-and-counter-sets-a-gpu-supports-08847234a1.md). Each *counter sample buffer* represents memory that a GPU uses to save data from the counter as it runs a pass. Counter sample buffers provide the GPU a place to temporarily store sample data, which avoids the need to synchronize data with the CPU. However, your app has the option to *resolve* the sample data with the CPU after the pass completes. See [Converting a GPU’s counter data into a readable format](https://developer.apple.com/documentation/Metal/converting-a-gpus-counter-data-into-a-readable-format) for more information about resolving sample data.

Create a counter sample buffer for a GPU by:

1. Confirming a GPU device supports the counter set you want to sample
2. Retrieving the GPU’s instance of that counter set
3. Creating an [`MTLCounterSampleBufferDescriptor`](https://developer.apple.com/documentation/Metal/MTLCounterSampleBufferDescriptor) instance and configuring its properties for the counter set
4. Passing the descriptor to the GPU device’s [`makeCounterSampleBuffer(descriptor:)`](https://developer.apple.com/documentation/Metal/MTLDevice/makeCounterSampleBuffer(descriptor:)) factory method

```objective-c
+ (id<MTLCounterSampleBuffer>)createTimestampBufferForDevice:(id<MTLDevice>)device
{
    // Confirm the device's counter set contains the timestamp counter.
    id<MTLCounterSet> timestampCounterSet = [self.class getCounterSet:MTLCommonCounterSetTimestamp
                                                           fromDevice:device];

    if (timestampCounterSet == nil) { return nil; }

    // Confirm the device's counter set contains the timestamp counter.
    if (![self.class counterSet:timestampCounterSet
                       contains:MTLCommonCounterTimestamp]) { return nil; }

    // Create and configure a descriptor for the counter sample buffer.
    MTLCounterSampleBufferDescriptor *descriptor;
    descriptor = [[MTLCounterSampleBufferDescriptor alloc] init];

    // This counter set instance belongs to the `device` instance.
    descriptor.counterSet = timestampCounterSet;

    // Set the buffer to use shared memory so the CPU and GPU can directly access its contents.
    descriptor.storageMode = MTLStorageModeShared;

    // Set the sample count to 4, to make room for the:
    // – Vertex stage's start time
    // – Vertex stage's completion time
    // – Fragment stage's start time
    // – Fragment stage's completion time
    descriptor.sampleCount = sampleCount;

    // Create the sample buffer by passing the descriptor to the device's factory method.
    id<MTLCounterSampleBuffer> buffer;
    NSError *error = nil;
    buffer = [device newCounterSampleBufferWithDescriptor:descriptor error:&error];

    if (error != nil) {
        NSLog(@"Device failed to create a counter sample buffer.");
        return nil;
    }

    return buffer;
}
```

The code example above gives the CPU access to the counter sample buffer by configuring the descriptor’s [`storageMode`](https://developer.apple.com/documentation/Metal/MTLCounterSampleBufferDescriptor/storageMode) property to [`MTLStorageMode.shared`](https://developer.apple.com/documentation/Metal/MTLStorageMode/shared). Alternatively, you can set this property to [`MTLStorageMode.private`](https://developer.apple.com/documentation/Metal/MTLStorageMode/private) if your app only uses the GPU to access its data. The example also sets the descriptor’s [`sampleCount`](https://developer.apple.com/documentation/Metal/MTLCounterSampleBufferDescriptor/sampleCount) property to `4` to store the starting and completion timestamps for both the vertex and the fragment stages. The value for the descriptor’s sample count in this example is directly related to the following four properties of the [`MTLRenderPassSampleBufferAttachmentDescriptor`](https://developer.apple.com/documentation/Metal/MTLRenderPassSampleBufferAttachmentDescriptor) type:

- [`startOfVertexSampleIndex`](https://developer.apple.com/documentation/Metal/MTLRenderPassSampleBufferAttachmentDescriptor/startOfVertexSampleIndex)
- [`endOfVertexSampleIndex`](https://developer.apple.com/documentation/Metal/MTLRenderPassSampleBufferAttachmentDescriptor/endOfVertexSampleIndex)
- [`startOfFragmentSampleIndex`](https://developer.apple.com/documentation/Metal/MTLRenderPassSampleBufferAttachmentDescriptor/startOfFragmentSampleIndex)
- [`endOfFragmentSampleIndex`](https://developer.apple.com/documentation/Metal/MTLRenderPassSampleBufferAttachmentDescriptor/endOfFragmentSampleIndex)

> Note:
> The value you set for `doc://com.apple.metal/documentation/Metal/MTLCounterSampleBufferDescriptor/sampleCount` depends on the type of data you sample and the number of passes you sample that data from.

When your app has a counter sample buffer, it can then instruct the GPU to save its counter sample data to it during a pass. See [Sampling GPU data into counter sample buffers](https://developer.apple.com/documentation/Metal/sampling-gpu-data-into-counter-sample-buffers) for more information.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
