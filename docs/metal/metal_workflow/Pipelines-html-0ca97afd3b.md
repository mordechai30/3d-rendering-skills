Source: [https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/Pipelines.html](<https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/Pipelines.html>)

<a id="//apple_ref/doc/uid/TP40016642-CH25"></a>

<a id="//apple_ref/doc/uid/TP40016642-CH25-SW2"></a>



<a id="pipelines"></a>

## Pipelines

**Best Practice:** Build your render and compute pipelines asynchronously.

Having multiple render or compute pipelines allows your app to use different state configurations for specific tasks. Building these pipelines asynchronously maximizes performance and parallelism. Build all known pipelines up front and avoid lazy loading. Listing 14-1 shows how to build multiple render pipelines asynchronously.

<a id="//apple_ref/doc/uid/TP40016642-CH25-SW1"></a>

**Listing 14-1**Building multiple render pipelines asynchronously

1. `const uint32_t pipelineCount;`
2. `dispatch_queue_t dispatch_queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);`
4. `// Dispatch the render pipeline build`
5. `__block NSMutableArray<id<MTLRenderPipelineState>> *pipelineStates = [[NSMutableArray alloc] initWithCapacity:pipelineCount];`
7. `dispatch_group_t pipelineGroup = dispatch_group_create();`
8. `for(uint32_t pipelineIndex = 0; pipelineIndex < pipelineCount; pipelineIndex++)`
9. `{`
10. `id <MTLFunction> vertexFunction = [_defaultLibrary newFunctionWithName:vertexFunctionNames[pipelineIndex]];`
11. `id <MTLFunction> fragmentFunction = [_defaultLibrary newFunctionWithName:fragmentFunctionNames[pipelineIndex]];`
13. `MTLRenderPipelineDescriptor* pipelineDescriptor = [MTLRenderPipelineDescriptor new];`
14. `pipelineDescriptor.vertexFunction = vertexFunction;`
15. `pipelineDescriptor.fragmentFunction = fragmentFunction;`
16. `/* Configure additional descriptor properties */`
18. `dispatch_group_enter(pipelineGroup);`
19. `[_device newRenderPipelineStateWithDescriptor:pipelineDescriptor completionHandler: ^(id <MTLRenderPipelineState> newRenderPipeline, NSError *error )`
20. `{`
21. `// Add error handling if newRenderPipeline is nil`
22. `pipelineStates[pipelineIndex] = newRenderPipeline;`
23. `dispatch_group_leave(pipelineGroup);`
24. `}];`
25. `}`
27. `/* Do more work */`
29. `// Wait for build to complete`
30. `dispatch_group_wait(pipelineGroup, DISPATCH_TIME_FOREVER);`
32. `/* Use the render pipelines */`

<a id="next_previous"></a>

[Functions and Libraries](./FunctionsandLibraries-html-0c595d844f.md#//apple_ref/doc/uid/TP40016642-CH24-SW1)

Copyright © 2018 Apple Inc. All rights reserved.
[Terms of Use](http://www.apple.com/legal/terms/site.html) |
[Privacy Policy](http://www.apple.com/privacy/) |
[Updated: 2017-03-27](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/MTLBestPracticesGuide/RevisionHistory.html#//apple_ref/doc/uid/TP40016642-CH99-DontLinkElementID_50)
