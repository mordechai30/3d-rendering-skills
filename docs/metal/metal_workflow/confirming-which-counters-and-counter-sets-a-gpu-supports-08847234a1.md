Source: [https://developer.apple.com/documentation/metal/confirming-which-counters-and-counter-sets-a-gpu-supports?language=objc](<https://developer.apple.com/documentation/metal/confirming-which-counters-and-counter-sets-a-gpu-supports?language=objc>)

<a id="confirming-which-counters-and-counter-sets-a-gpu-supports"></a>

# Confirming which counters and counter sets a GPU supports

Check whether a GPU produces the runtime performance data you want to sample.

<a id="discussion"></a>

## Discussion

You can check to see which counters a GPU device supports before attempting to programmatically sample data from them. A GPU *counter* is typically a hardware feature that tracks a specific performance metric, such as timestamps before and after an important rendering stage. Checking which counters a GPU supports at runtime avoids assumptions that may trigger an error or a crash on a person’s device.

A *counter set* is a collection of related counters. The [`MTLCommonCounterSet`](https://developer.apple.com/documentation/Metal/MTLCommonCounterSet) type defines the name of each set, and the [`MTLCommonCounter`](https://developer.apple.com/documentation/Metal/MTLCommonCounter) type defines the name of each individual counter. Check which counter sets an [`MTLDevice`](https://developer.apple.com/documentation/Metal/MTLDevice) instance supports before you request one by checking its [`counterSets`](https://developer.apple.com/documentation/Metal/MTLDevice/counterSets) property.

```objective-c
+ (nullable id<MTLCounterSet>) getCounterSet:(MTLCommonCounterSet)counterSetName
                                  fromDevice:(id<MTLDevice>)device
{
    for (id<MTLCounterSet> counterSet in device.counterSets ){
        if ([counterSetName isEqualToString:counterSetName])
        {
            printf("GPU device \"%s\" supports the \"%s\" counter set.\n",
                   device.name.UTF8String,
                   counterSetName.UTF8String);

            return counterSet;
        }
    }

    printf("GPU device \"%s\" doesn't support the \"%s\" counter set.\n",
           device.name.UTF8String,
           counterSetName.UTF8String);

    return nil;
}
```

The method iterates through each counter set the device supports, and compares its name to the [`MTLCommonCounterSet`](https://developer.apple.com/documentation/Metal/MTLCommonCounterSet) parameter.

Even though a GPU device supports a counter set, it may only support some of the counters in that set. You can check which individual counters a device supports by checking the elements of a counter set’s [`counters`](https://developer.apple.com/documentation/Metal/MTLCounterSet/counters) property.

```objective-c
+ (bool)counterSet:(id<MTLCounterSet>)counterSet
          contains:(MTLCommonCounter)counterName
{
    for (id<MTLCounter> counter in counterSet.counters )
    {
        if ([counter.name isEqualToString:counterName])
        {
            printf("Counter set \"%s\" supports the \"%s\" counter set.\n",
                   counterSet.name.UTF8String,
                   counterName.UTF8String);
            return YES;
        }
    }

    printf("Counter set \"%s\" doesn't support the \"%s\" counter set.\n",
           counterSet.name.UTF8String,
           counterName.UTF8String);

    return NO;
}
```

The method iterates through each counter in the device’s counter set, and compares its name to the [`MTLCommonCounter`](https://developer.apple.com/documentation/Metal/MTLCommonCounter) property.

When you know a GPU supports a counter, your app can create and safely use an [`MTLCounterSampleBuffer`](https://developer.apple.com/documentation/Metal/MTLCounterSampleBuffer) instance to store that counter’s data. See [Creating a counter sample buffer to store a GPU’s counter data during a pass](./creating-a-counter-sample-buffer-to-store-a-gpus-counter-data-during-a-pass-d78bbf9eff.md) for more information and next steps.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
