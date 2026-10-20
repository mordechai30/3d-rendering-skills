Source: [https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html](<https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html>)

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html)[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Functions and Libraries")
This chapter describes how to create a `MTLFunction` object as a reference to a Metal shader or compute function and how to organize and access functions with a `MTLLibrary` object.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "MTLFunction Represents a Shader or Compute Function")
## MTLFunction Represents a Shader or Compute Function

A `MTLFunction` object represents a single function that is written in the Metal shading language and executed on the GPU as part of a graphics or compute pipeline. For details on the Metal shading language, see the _Metal Shading Language Guide_.

To pass data or state between the Metal runtime and a graphics or compute function written in the Metal shading language, you assign an argument index for textures, buffers, and samplers. The argument index identifies which texture, buffer, or sampler is being referenced by both the Metal runtime and Metal shading code.

For a rendering pass, you specify a `MTLFunction` object for use as a vertex or fragment shader in a `MTLRenderPipelineDescriptor` object, as detailed in [Creating a Render Pipeline State](./Render-Ctx-html-760b5413cd.md#//apple_ref/doc/uid/TP40014221-CH7-SW37). For a compute pass, you specify a `MTLFunction` object when creating a `MTLComputePipelineState` object for a target device, as described in [Specify a Compute State and Resources for a Compute Command Encoder](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Compute-Ctx/Compute-Ctx.html#//apple_ref/doc/uid/TP40014221-CH6-SW30).

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "A Library Is a Repository of Functions")
## A Library Is a Repository of Functions

A `MTLLibrary` object represents a repository of one or more `MTLFunction` objects. A single `MTLFunction` object represents one Metal function that has been written with the shading language. In the Metal shading language source code, any function that uses a Metal function qualifier (`vertex`, `fragment`, or `kernel`) can be represented by a `MTLFunction` object in a library. A Metal function without one of these function qualifiers cannot be directly represented by a `MTLFunction` object, although it can called by another function within the shader.

The `MTLFunction` objects in a library can be created from either of these sources:

*   Metal shading language code that was compiled into a binary _library_ format during the app build process.

*   A text string containing Metal shading language source code that is compiled by the app at runtime.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Creating a Library from Compiled Code")
### Creating a Library from Compiled Code

For the best performance, compile your Metal shading language source code into a library file during your app's build process in Xcode, which avoids the costs of compiling function source during the runtime of your app. To create a `MTLLibrary` object from a library binary, call one of the following methods of `MTLDevice`:

*   `newDefaultLibrary` retrieves a library built for the main bundle that contains all shader and compute functions in an app’s Xcode project.

*   `newLibraryWithFile:error:` takes the path to a library file and returns a `MTLLibrary` object that contains all the functions stored in that library file.

*   `newLibraryWithData:error:` takes a binary blob containing code for the functions in a library and returns a `MTLLibrary` object.

For more information about compiling Metal shading language source code during the build process, see [Creating Libraries During the App Build Process](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Dev-Technique/Dev-Technique.html#//apple_ref/doc/uid/TP40014221-CH8-SW8).

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Creating a Library from Source Code")
### Creating a Library from Source Code

To create a `MTLLibrary` from a string of Metal shading language source code that may contain several functions, call one of the following methods of `MTLDevice`. These methods compile the source code when the library is created. To specify the compiler options to use, set the properties in a `MTLCompileOptions` object.

*   `newLibraryWithSource:options:error:` synchronously compiles source code from the input string to create `MTLFunction` objects and then returns a `MTLLibrary` object that contains them.

*   `newLibraryWithSource:options:completionHandler:` asynchronously compiles source code from the input string to create `MTLFunction` objects and then returns a `MTLLibrary` object that contains them. `completionHandler` is a block of code that is invoked when object creation is completed.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Getting a Function from a Library")
### Getting a Function from a Library

The `newFunctionWithName:` method of `MTLLibrary` returns a `MTLFunction` object with the requested name. If the name of a function that uses a Metal shading language function qualifier is not found in the library, then `newFunctionWithName:` returns `nil`.

Listing 4-1 uses the `newLibraryWithFile:error:` method of `MTLDevice` to locate a library file by its full path name and uses its contents to create a `MTLLibrary` object with one or more `MTLFunction` objects. Any errors from loading the file are returned in `error`. Then the `newFunctionWithName:` method of `MTLLibrary` creates a `MTLFunction` object that represents the function called `my_func` in the source code. The returned function object `myFunc` can now be used in an app.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Listing 4-1Accessing a Function from a Library")
**Listing 4-1**Accessing a Function from a Library

NSError *errors;
id <MTLLibrary> library = [device newLibraryWithFile:@"myarchive.metallib"
error:&errors];
id <MTLFunction> myFunc = [library newFunctionWithName:@"my_func"];

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Determining Function Details at Runtime")
## Determining Function Details at Runtime

Because the actual contents of a `MTLFunction` object are defined by a graphics shader or compute function that may be compiled before the `MTLFunction` object was created, its source code might not be directly available to the app. You can query the following `MTLFunction` properties at run time:

*   `name`, a string with the name of the function.

*   `functionType`, which indicates whether the function is declared as a vertex, fragment, or compute function.

*   `vertexAttributes`, an array of `MTLVertexAttribute` objects that describe how vertex attribute data is organized in memory and how it is mapped to vertex function arguments. For more details, see [Vertex Descriptor for Data Organization](./Render-Ctx-html-760b5413cd.md#//apple_ref/doc/uid/TP40014221-CH7-SW44).

`MTLFunction` does not provide access to function arguments. A reflection object (either `MTLRenderPipelineReflection` or `MTLComputePipelineReflection`, depending upon the type of command encoder) that reveals details of shader or compute function arguments can be obtained during the creation of a pipeline state. For details on creating pipeline state and reflection objects, see [Creating a Render Pipeline State](./Render-Ctx-html-760b5413cd.md#//apple_ref/doc/uid/TP40014221-CH7-SW37) or [Creating a Compute Pipeline State](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Compute-Ctx/Compute-Ctx.html#//apple_ref/doc/uid/TP40014221-CH6-SW3). Avoid obtaining reflection data if it will not be used.

A reflection object contains an array of `MTLArgument` objects for each type of function supported by the command encoder. For `MTLComputeCommandEncoder`, `MTLComputePipelineReflection` has one array of `MTLArgument` objects in the `arguments` property that correspond to the arguments of its compute function. For `MTLRenderCommandEncoder`, `MTLRenderPipelineReflection` has two properties, `vertexArguments` and `fragmentArguments`, that are arrays that correspond to the vertex function arguments and fragment function arguments, respectively.

Not all arguments of a function are present in a reflection object. A reflection object only contains arguments that have an associated resource, but not arguments declared with the `[[ stage_in ]]` qualifier or built-in `[[ vertex_id ]]` or `[[ attribute_id ]]` qualifier.

Listing 4-2 shows how you can obtain a reflection object (in this example, `MTLComputePipelineReflection`) and then iterate through the `MTLArgument` objects in its `arguments` property.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Listing 4-2Iteration Through Function Arguments")
**Listing 4-2**Iteration Through Function Arguments

MTLComputePipelineReflection* reflection;
id <MTLComputePipelineState> computePS = [device
newComputePipelineStateWithFunction:func
options:MTLPipelineOptionArgumentInfo
reflection:&reflection error:&error];
for (MTLArgument *arg in reflection.arguments) {
//  process each MTLArgument
}

The `MTLArgument` properties reveal the details of an argument to a shading language function.

*   The `name` property is simply the name of the argument.

*   `active` is a Boolean that indicates whether the argument can be ignored.

*   `index` is a zero-based position in its corresponding argument table. For example, for `[[ buffer(2) ]]`, `index` is 2.

*   `access` describes any access restrictions, for example, the read or write access qualifier.

*   `type` is indicated by the shading language qualifier, for example, `[[ buffer(n) ]]`, `[[ texture(n) ]]`, `[[ sampler(n) ]]`, or `[[ threadgroup(n) ]]`.

`type` determines which other `MTLArgument` properties are relevant.

*   If `type` is `MTLArgumentTypeTexture`, then the `textureType` property indicates the overall texture type (such as `texture1d_array`, `texture2d_ms`, and `texturecube` types in the shading language), and the `textureDataType` property indicates the component data type (such as `half`, `float`, `int`, or `uint`).

*   If `type` is `MTLArgumentTypeThreadgroupMemory`, the `threadgroupMemoryAlignment` and `threadgroupMemoryDataSize` properties are relevant.

*   If `type` is `MTLArgumentTypeBuffer`, the `bufferAlignment`, `bufferDataSize`, `bufferDataType`, and `bufferStructType` properties are relevant.

If the buffer argument is a struct (that is, `bufferDataType` is `MTLDataTypeStruct`), the `bufferStructType` property contains a `MTLStructType` that represents the struct, and `bufferDataSize` contains the size of the struct, in bytes. If the buffer argument is an array (or pointer to an array), then `bufferDataType` indicates the data type of an element, and `bufferDataSize` contains the size of one array element, in bytes.

Listing 4-3 drills down in a `MTLStructType` object to examine the details of struct members, each represented by a `MTLStructMember` object. A struct member may be a simple type, an array, or a nested struct. If the member is a nested struct, then call the `structType` method of `MTLStructMember` to obtain a `MTLStructType` object that represents the struct and then recursively drill down to analyze it. If the member is an array, use the `arrayType` method of `MTLStructMember` to obtain a `MTLArrayType` that represents it. Then examine its `elementType` property of `MTLArrayType`. If `elementType` is `MTLDataTypeStruct`, call the `elementStructType` method to obtain the struct and continue to drill down into its members. If `elementType` is `MTLDataTypeArray`, call the `elementArrayType` method to obtain the subarray and analyze it further.

[](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Prog-Func/Prog-Func.html "Listing 4-3Processing a Struct Argument")
**Listing 4-3**Processing a Struct Argument

MTLStructType *structObj = [arg.bufferStructType];
for (MTLStructMember *member in structObj.members) {
//  process each MTLStructMember
if (member.dataType == MTLDataTypeStruct) {
MTLStructType *nestedStruct = member.structType;
// recursively drill down into the nested struct
}
else if (member.dataType == MTLDataTypeArray) {
MTLStructType *memberArray = member.arrayType;
// examine the elementType and drill down, if necessary
}
else {
// member is neither struct nor array
// analyze it; no need to drill down further
}
}