Source: [https://www.w3.org/TR/WGSL/](<https://www.w3.org/TR/WGSL/>)

# WebGPU Shading Language

## 1. Introduction[](#intro)

WebGPU Shading Language (WGSL) is the shader language for [[WebGPU]](https://www.w3.org/TR/WGSL/#biblio-webgpu "WebGPU"). That is, an application using the WebGPU API uses WGSL to express the programs, known as shaders, that run on the GPU.

// A fragment shader which lights textured geometry with point lights.

// Lights from a storage buffer binding.
struct PointLight {
  position : vec3f,
  color : vec3f,
}

struct LightStorage {
  pointCount : u32,
  point : array<PointLight>,
}
@group(0) @binding(0) var<storage> lights : LightStorage;

// Texture and sampler.
@group(1) @binding(0) var baseColorSampler : sampler;
@group(1) @binding(1) var baseColorTexture : texture_2d<f32>;

// Function arguments are values from the vertex shader.
@fragment
fn fragmentMain(@location(0) worldPos : vec3f,
                @location(1) normal : vec3f,
                @location(2) uv : vec2f) -> @location(0) vec4f {
  // Sample the base color of the surface from a texture.
  let baseColor = textureSample(baseColorTexture, baseColorSampler, uv);

  let N = normalize(normal);
  var surfaceColor = vec3f(0);

  // Loop over the scene point lights.
  for (var i = 0u; i < lights.pointCount; i++) {
    let worldToLight = lights.point[i].position - worldPos;
    let dist = length(worldToLight);
    let dir = normalize(worldToLight);

    // Determine the contribution of this light to the surface color.
    let radiance = lights.point[i].color * (1 / pow(dist, 2));
    let nDotL = max(dot(N, dir), 0);

    // Accumulate light contribution to the surface color.
    surfaceColor += baseColor.rgb * radiance * nDotL;
  }

  // Return the accumulated surface color.
  return vec4(surfaceColor, baseColor.a);
}

### 1.1. Overview[](#overview)

WebGPU issues a unit of work to the GPU in the form of a [GPU command](../WGPU/gpuweb-spec/gpuweb-spec.md#gpu-command). WGSL is concerned with two kinds of GPU commands:

*   a draw command executes a [render pipeline](#gpurenderpipeline) in the context of [inputs](#shader-stage-input), [outputs](#shader-stage-output), and attached [resources](#resource).

*   a dispatch command executes a [compute pipeline](#gpucomputepipeline) in the context of [inputs](#shader-stage-input) and attached [resources](#resource).

Both kinds of pipelines use shaders written in WGSL.

A shader is the portion of a WGSL program that executes a [shader stage](#shader-stages) in a pipeline. A shader comprises:

*   An [entry point](#entry-point)[function](#function-function).

*   The transitive closure of all called functions, starting with the entry point. This set includes both [user-defined](#user-defined-function) and [built-in](#built-in-functions) functions. (For a more rigorous definition, see "[functions in a shader stage](#functions-in-a-shader-stage)".)

*   The set of variables and constants [statically accessed](#statically-accessed) by all those functions.

*   The set of types used to define or analyze all those functions, variables, and constants.

Note: A WGSL program does not require an [entry point](#entry-point); however, such a program cannot be executed by the API because an entry point is required to create a `GPUProgrammableStage`.

When executing a shader stage, the implementation:

*   Computes the values of constants declared at [module-scope](#module-scope).

*   Binds [resources](#resource) to variables in the shader’s [resource interface](#resource-interface-of-a-shader), making the contents of those resources available to the shader during execution.

*   Allocates memory for other [module-scope](#module-scope) variables, and populates that memory with the specified initial values.

*   Populates the formal parameters of the entry point, if they exist, with the shader stage’s inputs.

*   Connects the entry point [return value](#return-value), if one exists, to the shader stage’s outputs.

*   Then it invokes the entry point.

A WGSL program is organized into:

*   [Directives](#directives), which specify module-level behavior controls.

*   [Functions](#functions), which specify execution behavior.

*   [Statements](#statements), which are declarations or units of executable behavior.

*   [Literals](#literals), which are text representations for pure mathematical values.

*   [Constants](#value-decls), each providing a name for a value computed at a specific time.

*   [Variables](#var-decls), each providing a name for memory holding a value.

*   [Expressions](#expressions), each of which combines a set of values to produce a result value.

*   [Types](#types), each of which describes:

    *   A set of values.

    *   Constraints on supported expressions.

    *   The semantics of those expressions.

*   [Attributes](#attributes), which modify an object to specify extra information such as:

    *   Specifying the [interfaces](#shader-interface) to [entry points](#entry-points).

    *   Specifying [diagnostic filters](#diagnostic-filtering).

Note: A WGSL program is currently composed of a single [WGSL module](#wgsl-module).

WGSL is an imperative language: behavior is specified as a sequence of statements to execute. Statements can:

*   Declare [constants](#value-decls) or [variables](#var-decls).

*   Modify the contents of variables.

*   Modify execution order using structured programming constructs:

    *   Selective execution: [if](#if-statement) (with optional `else if` and `else` clauses), [switch](#switch-statement).

    *   Repetition: [loop](#loop-statement), [while](#while-statement), [for](#for-statement).

    *   Escaping a nested execution construct: [continue](#continue-statement), [break](#break-statement), [break if](#break-if-statement).

    *   Refactoring: [function call](#function-calls) and [return](#return-statement).

*   Evaluate expressions to compute values as part of the above behaviors.

*   Check [assumptions](#assertions) at [shader creation](#shader-module-creation) time on [constant expressions](#const-expressions).

WGSL is statically typed: each value computed by a particular expression is in a specific type, determined only by examining the program source.

WGSL has types describing [booleans](#bool-type) and numbers ([integers](#integer-types) and [floating point](#floating-point-types)). These types can be aggregated into [composites](#composite-types) ([vectors](#vector-types), [matrices](#matrix-types), [arrays](#array-types), and [structures](#struct-types)). WGSL has special types (e.g. [atomics](#atomic-types)) that provide unique operations. WGSL describes the types that can be stored in [memory](#memory) as [memory views](#memory-views). WGSL provides commonly used rendering types in the form of [textures and samplers](#texture-sampler-types). These types have associated [built-in functions](#texture-builtin-functions) to expose commonly provided GPU hardware for graphics rendering.

WGSL has very limited implicit conversions and promotions. It only provides implicit conversions and promotions from [abstract](#type-abstract) types and [buffer](#buffer) pointers passed as arguments to [function calls](#function-call). Converting a value from one [concrete](#type-concrete) numeric or boolean type to another requires an explicit [conversion](#value-constructor-builtin-function), [value constructor](#value-constructor), or [reinterpretation of bits](#bitcast-builtin); however, WGSL does provide some limited facility to promote [scalar](#scalar) types to [vector](#vector) types. This also applies to [composite](#composite) types.

The work of a shader stage is partitioned into one or more invocations, each of which executes the entry point, but under slightly different conditions. Invocations in a shader stage share access to certain variables:

*   All invocations in the stage share the resources in the shader interface.

*   In a [compute shader](#compute-shader-stage), invocations in the same [workgroup](#compute-shader-stage-workgroup) share variables in the [workgroup](#address-spaces-workgroup)[address space](#address-spaces). Invocations in different workgroups do not share those variables.

However, the invocations act on different sets of shader stage inputs, including built-in inputs that provide an identifying value to distinguish an invocation from its peers. Each invocation has its own independent memory space in the form of variables in the [private](#address-spaces-private) and [function](#address-spaces-function) address spaces.

Invocations within a shader stage execute concurrently, and may often execute in parallel. The shader author is responsible for ensuring the dynamic behavior of the invocations in a shader stage:

*   Meet the [uniformity](#uniformity) requirements of certain primitive operations, including texture sampling and control barriers.

*   Coordinate potentially conflicting accesses to shared variables, to avoid data races.

WGSL sometimes permits several possible behaviors for a given feature. This is a portability hazard, as different implementations may exhibit the different behaviors. The design of WGSL aims to minimize such cases, but is constrained by feasibility, and goals for achieving high performance across a broad range of devices.

Behavioral requirements are actions the implementation will perform when processing or executing a WGSL program. They describe the implementation’s obligations in the contract with the programmer. The specification explicitly states these obligations when they might not be otherwise obvious.

### 1.2. Syntax Notation[](#syntax-notation)

Following syntax notation describes the conventions of the syntactic grammar of WGSL:

*   Italic text on both sides of a rule indicates a syntax rule.

*   Bold monospace text starting and ending with single quotes (**'**) on the right-hand side of a rule indicates keywords and tokens.

*   A colon (**:**) in regular text registers a syntax rule.

*   A vertical bar (**|**) in regular text indicates alternatives.

*   An question mark (**?**) in regular text indicates that previous keyword, token, rule, or group occurs zero or one times (is optional).

*   An asterisk (*****) in regular text indicates that previous keyword, token, rule, or group occurs zero or more times.

*   A plus (**+**) in regular text indicates that previous keyword, token, rule, or group occurs one or more times.

*   A matching pair of opening parenthesis (**(**) and closing parenthesis (**)**) in regular text indicates a group of elements.

### 1.3. Mathematical Terms and Notation[](#terms-and-notation)

Angles:

*   By convention, angles are measured in radians.

*   The reference ray for measuring angles is the ray from the origin (0,0) toward (+∞,0).

*   Let θ be the angle subtended by a comparison ray and the reference ray. Then θ increases as the comparison ray moves counterclockwise.

*   There are 2 π radians in a complete circle.

*   Examples:

    *   The angle 0 points from the origin to the right, toward (1,0)

    *   The angle 2π points from the origin to the right, toward (1,0)

    *   The angle π/4 points from the origin to the point (1,1)

    *   The angle π/2 points from the origin to the point (0,1)

    *   The angle π points from the origin to the point (-1,0)

    *   The angle (3/2)π points from the origin to the point (0,-1)

A hyperbolic angle is a unitless area, not an angle in the traditional sense. Specifically:

*   Consider the hyperbola x 2 - y 2 = 1 for x> 0.

*   Let R be a ray from the origin to some point (x, y) on the hyperbola.

*   Let a be twice the area enclosed by R, the x axis, and the curve of the hyperbola itself.

*   Consider a to be positive when R is above the x axis, and negative when below.

Then the area a is a hyperbolic angle such that x is the hyperbolic cosine of a, and y is the hyperbolic sine of a.

Positive infinity, denoted by +∞, is a unique value strictly greater than all real numbers.

Negative infinity, denoted by −∞, is a unique value strictly lower than all real numbers.

The extended real numbers (also known as the affinely extended real numbers) is the set of real numbers together with +∞ and −∞. Computers use [floating point types](#floating-point-types) to approximately represent the extended reals, including values for both infinities. See [§ 15.7 Floating Point Evaluation](#floating-point-evaluation).

An interval is a contiguous set of numbers with a lower and upper bound. Depending on context, they are sets of integers, floating point numbers, real numbers, or [extended real](#extended-real) numbers.

*   The closed interval [_a_,_b_] is the set of numbers _x_ such that _a_ ≤ _x_ ≤ _b_.

*   The half-open interval [_a_,_b_) is the set of numbers _x_ such that _a_ ≤ _x_<_b_.

*   The half-open interval (_a_,_b_] is the set of numbers _x_ such that _a_<_x_ ≤ _b_.

The floor expression is defined for [extended real](#extended-real) numbers x:

*   ⌊ +∞ ⌋ = +∞

*   ⌊ −∞ ⌋ = −∞

*   for real number x, ⌊x⌋ = k, where k is the unique integer such that k ≤ x<k+1

The ceiling expression is defined for [extended real](#extended-real) numbers x:

*   ⌈ +∞ ⌉ = +∞

*   ⌈ −∞ ⌉ = −∞

*   for real number x, ⌈x⌉ = k, where k is the unique integer such that k-1 <x ≤ k

The truncate function is defined for [extended real](#extended-real) numbers x:

*   truncate(+∞) = +∞

*   truncate(−∞) = −∞

*   for real number x, computes the nearest whole number whose absolute value is less than or equal to the absolute value of x:

    *   truncate(x) = ⌊x⌋ if x ≥ 0, and ⌈x⌉ if x< 0.

The roundUp function is defined for positive integers k and n as:

*   roundUp(k, n) = ⌈n ÷ k⌉ × k

The roundDown function is defined for positive integers k and n as:

*   roundDown(k, n) = ⌊n ÷ k⌋ × k

The transpose of an c-column r-row matrix A is the r-column c-row matrix A T formed by copying the rows of A as the columns of A T:

*   transpose(A) = A T

*   transpose(A)i,j = A j,i

The transpose of a column vector is defined by interpreting the column vector as a 1-row matrix. Similarly, the transpose of a row vector is defined by interpreting the row vector as a 1-column matrix.

## 2. WGSL Module[](#wgsl-module)

A WGSL program is composed of a single WGSL module.

A module is a sequence of optional [directives](#directive) followed by [module scope](#module-scope)[declarations](#declaration) and [assertions](#assertion). A module is organized into:

*   [Directives](#directives), which specify module-level behavior controls.

*   [Functions](#functions), which specify execution behavior.

*   [Statements](#statements), which are declarations or units of executable behavior.

*   [Literals](#literals), which are text representations for pure mathematical values.

*   [Variables](#var-decls), each providing a name for memory holding a value.

*   [Constants](#value-decls), each providing a name for a value computed at a specific time.

*   [Expressions](#expressions), each of which combines a set of values to produce a result value.

*   [Types](#types), each of which describes:

    *   A set of values.

    *   Constraints on supported expressions.

    *   The semantics of those expressions.

*   [Attributes](#attributes), which modify an object to specify extra information such as:

    *   Specifying the [interfaces](#shader-interface) to [entry points](#entry-points).

    *   Specifying [diagnostic filters](#diagnostic-filtering).

translation_unit :

[global_directive](#syntax-global_directive) * ( [global_decl](#syntax-global_decl) | [global_assert](#syntax-global_assert) | [`';'`](#syntax_sym-semicolon) ) *

### 2.1. Shader Lifecycle[](#shader-lifecycle)

There are four key events in the lifecycle of a WGSL program and the shaders it may contain. The first two correspond to the WebGPU API methods used to prepare a WGSL program for execution. The last two are the start and end of execution of a shader.

The events are:

1.   Shader module creation

    *   This occurs when the WebGPU `createShaderModule()` method is called. The source text for a WGSL program is provided at this time.

2.   Pipeline creation

    *   This occurs when the WebGPU `createComputePipeline()` method or the WebGPU `createRenderPipeline()` method is invoked. These methods use one or more previously created shader modules, together with other configuration information.

    *   Only the code forming the [shader](#shader) of the specified [entry point](#entry-point) of the `GPUProgrammableStage` is considered during pipeline creation. That is, code unrelated to the entry point is effectively stripped before compilation.

    *   Note: Each [shader stage](#shader-stages) is considered to be compiled separately and, thus, might include different portions of the module.

3.   Shader execution start

    *   This occurs when a [draw](#draw-command) or [dispatch command](#dispatch-command) is issued to the GPU, begins executing the pipeline, and invokes the [shader stage](#shader-stages)[entry point](#entry-point) function.

4.   Shader execution end

    *   This occurs when all work in the shader completes:

        *   all its [invocations](#invocations) terminate, and

        *   all accesses to [resources](#resource) complete, and

        *   outputs, if any, are passed to downstream pipeline stages.

The events are ordered due to:

*   data dependencies: shader execution requires a pipeline, and a pipeline requires a shader module.

*   causality: the shader must start executing before it can finish executing.

### 2.2. Errors[](#errors)

A WebGPU implementation may fail to process a shader for two reasons:

*   A program error occurs if the shader does not satisfy the requirements of the WGSL or WebGPU specifications.

*   An uncategorized error may occur even when all WGSL and WebGPU requirements have been satisfied. Possible causes include:

    *   The shaders are too complex, exceeding the capabilities of the implementation, but in a way not easily captured by prescribed [limits](#limits). Simplifying the shaders may work around the issue.

    *   A defect in the WebGPU implementation.

A processing error may occur during three phases in the shader lifecycle:

*   A shader-creation error is an error feasibly detectable at [shader module creation](#shader-module-creation) time. Detection relies only on the WGSL module source text and other information available to the `createShaderModule` API method. Statements in this specification that describe something the program _must_ do generally produce a shader-creation error if those assertions are violated.

*   A pipeline-creation error is an error detectable at [pipeline creation](#pipeline-creation) time. Detection relies on the WGSL module source text and other information available to the particular pipeline creation API method. These errors are only triggered for code present in the [shader](#shader) of the [entry point](#entry-point) being compiled for the `GPUProgrammableStage`.

*   A dynamic error is an error occurring during shader execution. These errors may or may not be detectable.

Note: For example, a data race may not be detectable.

Each requirement [will](#behavioral-requirements) be checked at the earliest opportunity. That is:

*   A shader-creation error results when failing to meet a requirement detectable at shader-creation time.

*   A pipeline-creation error results when failing to meet a requirement detectable at pipeline-creation time, but not detectable earlier.

When unclear from context, this specification indicates whether failure to meet a particular requirement results in a shader-creation, pipeline-creation, or dynamic error.

The consequences of an error are as follows:

*   A WGSL module with a [shader-creation error](#shader-creation-error) or [pipeline-creation error](#pipeline-creation-error) error will not be incorporated into a [pipeline](#pipeline) and hence will not be executed.

*   Detectable errors [will](#behavioral-requirements)[trigger](#triggered) a [diagnostic](#diagnostic).

*   If a [dynamic error](#dynamic-error) occurs:

    *   [Memory accesses](#memory-access)[will](#behavioral-requirements) be restricted to:

        *   [shader stage inputs](#shader-stage-input),

        *   [shader stage outputs](#shader-stage-output),

        *   any part of a [resource](#resource) bound to a variable in the WGSL module, and

        *   other variables declared in the WGSL module.

    *   Otherwise, the program may not behave as described in the rest of this specification. Note: These effects may be non-local.

### 2.3. Diagnostics[](#diagnostics)

An implementation can generate [diagnostics](#diagnostic) during [shader module creation](#shader-module-creation) or [pipeline creation](#pipeline-creation). A diagnostic is a message produced by the implementation for the benefit of the application author.

A diagnostic is created, or triggered, when a particular condition is met, known as the triggering rule. The place in the source text where the condition is met, expressed as a point or range in the source text, is known as the triggering location.

A [diagnostic](#diagnostic) has the following properties:

*   A [severity](#diagnostic-severity).

*   A [triggering rule](#diagnostic-triggering-rule).

*   A [triggering location](#diagnostic-triggering-location).

The severity of a diagnostic is one of the following, ordered from greatest to least:

error
The diagnostic is an error. This corresponds to a [shader-creation error](#shader-creation-error) or to a [pipeline-creation error](#pipeline-creation-error).

warning
The diagnostic describes an anomaly that merits the attention of the application developer, but is not an error.

info
The diagnostic describes a notable condition that merits attention of the application developer, but is not an error or warning.

off
The diagnostic is disabled. It will not be conveyed to the application.

The name of a [triggering rule](#diagnostic-triggering-rule) is either:

*   a [diagnostic_name_token](#syntax-diagnostic_name_token), or

*   two [diagnostic_name_token](#syntax-diagnostic_name_token) tokens, separated by a period `'.'` (U+002E).

#### 2.3.1. Diagnostic Processing[](#diagnostic-processing)

Triggered diagnostics [will](#behavioral-requirements) be processed as follows:

1.   For each diagnostic _D_, find the [diagnostic filter](#diagnostic-filter) with the smallest [affected range](#affected-range) that contains D’s [triggering location](#diagnostic-triggering-location), and which has the same [triggering rule](#diagnostic-triggering-rule).

    *   If such a filter exists, apply it to _D_, updating _D_'s [severity](#diagnostic-severity).

    *   Otherwise _D_ remains unchanged.

2.   Discard diagnostics that have severity [off](#severity-off).

3.   If at least one remaining diagnostic _DI_ has severity [info](#severity-info), then:

    *   Other [info](#severity-info) diagnostics with same triggering rule _may_ be discarded, leaving only the original diagnostic _DI_.

4.   If at least one remaining diagnostic _DW_ has severity [warning](#severity-warning), then:

    *   Other [info](#severity-info) or [warning](#severity-warning) diagnostics with same triggering rule _may_ be discarded, leaving only the original diagnostic _DW_.

5.   If at least one remaining diagnostic has [error](#severity-error) severity, then:

    *   Other diagnostics _may_ be discarded, including other diagnostics with [error](#severity-error) severity.

    *   A [program error](#program-error) is generated.

        *   The error is a [shader-creation error](#shader-creation-error) if the diagnostic was triggered at [shader module creation](#shader-module-creation) time.

        *   The error is a [pipeline-creation error](#pipeline-creation-error) if the diagnostic was triggered at [pipeline creation](#pipeline-creation) time.

6.   If processing during [shader module creation](#shader-module-creation) time, the remaining diagnostics populate the `messages` member of the WebGPU `GPUCompilationInfo` object.

7.   If processing during [pipeline creation](#pipeline-creation), [error](#severity-error) diagnostics result in WebGPU validation failure when validating `GPUProgrammableStage`.

Note: The rules allow an implementation to stop processing a WGSL module as soon as an error is detected. Additionally, an analysis for a particular kind of warning can stop on the first warning, and an analysis for a particular kind of info diagnostic can stop on the first occurrence. WGSL does not specify the order to perform different kinds of analyses, or an ordering within a single analysis. Therefore, for the same WGSL module, different implementations may report different instances of diagnostics with the same severity.

#### 2.3.2. Filterable Triggering Rules[](#filterable-triggering-rules)

Most [diagnostics](#diagnostic) are unconditionally reported to the WebGPU application. Some kinds of diagnostics can be [filtered](#diagnostic-filtering), in part by naming their [triggering rule](#diagnostic-triggering-rule). The following table lists the standard set of triggering rules that can be filtered.

Filterable diagnostic triggering rules
| Filterable Triggering Rule | Default Severity | Triggering Location | Description | derivative_uniformity | [error](#severity-error) | The location of the [call site](#call-site) for any [builtin function that computes a derivative](#builtin-functions-that-compute-a-derivative). That is, the location of a call to any of: * the [derivative builtin functions](#derivative-builtin-functions) * [textureSample](#texturesample) * [textureSampleBias](#texturesamplebias) * [textureSampleCompare](#texturesamplecompare) | A call to a builtin function computes derivatives, but [uniformity analysis](#uniformity-analysis) cannot prove that the call occurs in [uniform control flow](#uniform-control-flow). See [§ 15.2 Uniformity](#uniformity). | | subgroup_uniformity | [error](#severity-error) | The location of the [call site](#call-site) for any [subgroup](#subgroup-builtin-functions) or [quad](#quad-builtin-functions) built-in function. | A call to a subgroup or quad builtin function, but [uniformity analysis](#uniformity-analysis) cannot prove that the call occurs in [uniform control flow](#uniform-control-flow). Additionally, when uniformity analysis cannot prove that the following parameter values are [uniform](#uniform-value): * `delta` in [subgroupShuffleUp](#subgroupshuffleup-builtin) and [subgroupShuffleDown](#subgroupshuffledown-builtin) * `mask` in [subgroupShuffleXor](#subgroupshufflexor-builtin) See [§ 15.2 Uniformity](#uniformity). | |
| --- | --- | --- | --- |

Using an unrecognized triggering rule consisting of a single [diagnostic name-token](#diagnostic-name-token) should trigger a warning from the user agent.

An implementation may support triggering rules not specified here, provided they are spelled using the multiple-token form of [diagnostic_rule_name](#syntax-diagnostic_rule_name). Using an unrecognized triggering rule spelled in the multiple-token form _may_ itself trigger a diagnostic.

Future versions of this specification may remove a particular rule or weaken its default severity (i.e. replace its current default with a less severe default) and still be deemed as satisfying backward compatibility. For example, a future version of WGSL may change the default severity for [derivative_uniformity](#trigger-derivative_uniformity) from `error` to either `warning` or `info`. After such a change to the specification, previously valid programs would remain valid.

#### 2.3.3. Diagnostic Filtering[](#diagnostic-filtering)

Once a [diagnostic](#diagnostic) with a filterable [triggering rule](#diagnostic-triggering-rule) is [triggered](#triggered), WGSL provides mechanisms to discard the diagnostic, or to modify its severity.

A diagnostic filter _DF_ has three parameters:

*   _AR_: a range of source text known as the affected range

*   _NS_: a new [severity](#diagnostic-severity)

*   _TR_: a [triggering rule](#diagnostic-triggering-rule)

Applying a diagnostic filter _DF_(_AR_,_NS_,_TR_) to a diagnostic _D_ has the following effect:

*   If _D_'s [triggering location](#diagnostic-triggering-location) is in _AR_ and _D_'s [triggering rule](#diagnostic-triggering-rule) is _TR_, then set _D_'s [severity](#diagnostic-severity) property to _NS_.

*   Otherwise, _D_ is unchanged.

A range diagnostic filter is a [diagnostic filter](#diagnostic-filter) whose [affected range](#affected-range) is a specified range of source text. A range diagnostic filter is specified as a `@diagnostic`[attribute](#attribute) at the start of the affected source range, as specified in the following table. A `@diagnostic` attribute [must not](#shader-creation-error) appear anywhere else.

Placement of a range diagnostic filter
| Placement | Affected Range | [Beginning](#syntax-compound_statement) of a [compound statement](#compound-statement). | The compound statement. | | [Beginning](#syntax-function_decl) of a [function declaration](#function-declaration). | The function declaration. | | [Beginning](#syntax-if_statement) of an [if](#statement-if) statement. | The if statement: the [if_clause](#syntax-if_clause) and all associated [else_if_clause](#syntax-else_if_clause) and [else_clause](#syntax-else_clause) clauses, including all controlling condition expressions. | | [Beginning](#syntax-switch_statement) of a [switch](#statement-switch) statement. | The switch statement: the selector expression and the [switch_body](#syntax-switch_body). | | [Beginning](#syntax-switch_body) of a [switch_body](#syntax-switch_body). | The [switch_body](#syntax-switch_body). | | [Beginning](#syntax-loop_statement) of a [loop](#statement-loop) statement. | The loop statement. | | [Beginning](#syntax-while_statement) of a [while](#statement-while) statement. | The while statement: both the condition expression and the loop body. | | [Beginning](#syntax-for_statement) of a [for](#statement-for) statement. | The for statement: the [for_header](#syntax-for_header) and the loop body. | | Immediately before the opening brace (`'{'`) of the [loop body](#loop-body) of a [loop](#statement-loop), [while](#statement-while), or [for](#statement-for) loop. | The [loop body](#loop-body). | | [Beginning](#syntax-continuing_compound_statement) of a [continuing_compound_statement](#syntax-continuing_compound_statement). | The [continuing_compound_statement](#syntax-continuing_compound_statement). | |
| --- | --- |

Note: The following are also [compound statements](#compound-statement): a [function body](#function-body), a [case clause](#case-clause), a [default-alone clause](#default-alone-clause), the bodies of [while](#statement-while) and [for](#statement-for) loops, and the bodies of [if_clause](#syntax-if_clause), [else_if_clause](#syntax-else_if_clause), and [else_clause](#syntax-else_clause).

EXAMPLE: Range diagnostic filter on texture sampling

var<private> d: f32;
fn helper() -> vec4<f32> {
  // Disable the derivative_uniformity diagnostic in the
  // body of the "if".
  if (d < 0.5) @diagnostic(off,derivative_uniformity) {
    return textureSample(t,s,vec2(0,0));
  }
  return vec4(0.0);
}

A [global diagnostic filter](#global-diagnostic-filter) can be used to apply a diagnostic filter to the entire WGSL module.

EXAMPLE: Global diagnostic filter for derivative uniformity

diagnostic(off,derivative_uniformity);
var<private> d: f32;
fn helper() -> vec4<f32> {
  if (d < 0.5) {
    // The derivative_uniformity diagnostic is disabled here
    // by the global diagnostic filter.
    return textureSample(t,s,vec2(0,0));
  } else {
    // The derivative_uniformity diagnostic is set to 'warning' severity.
    @diagnostic(warning,derivative_uniformity) {
      return textureSample(t,s,vec2(0,0));
    }
  }
  return vec4(0.0);
}

Two [diagnostic filters](#diagnostic-filter)_DF_(_AR1_,_NS1_,_TR1_) and _DF_(_AR2_,_NS2_,_TR2_) conflict when:

*   (_AR1_ = _AR2_), and

*   (_TR1_ = _TR2_), and

*   (_NS1_ ≠ _NS2_).

[Diagnostic filters](#diagnostic-filter)[must](#shader-creation-error) not [conflict](#diagnostic-conflict).

Note: Multiple [global diagnostic filters](#global-diagnostic-filter) are permitted when they do not [conflict](#diagnostic-conflict).

WGSL’s diagnostic filters are designed so their affected ranges nest perfectly. If the affected range of DF1 overlaps with the affected range of DF2, then either DF1’s affected range is fully contained in DF2’s affected range, or the other way around.

The nearest enclosing diagnostic filter for source location _L_ and triggering rule _TR_, if one exists, is the diagnostic filter _DF(AR,NS,TR)_ where:

*   _L_ falls in the affected range _AR_, and

*   If there is another filter _DF'(AR',NS',TR)_ where _L_ falls in _AR'_, then _AR_ is contained in _AR'_.

Because affected ranges nest, the nearest enclosing diagnostic:

*   is a unique [range diagnostic filter](#range-diagnostic-filter),

*   otherwise is one of a set of duplicate (non-[conflicting](#diagnostic-conflict)) [global diagnostic filters](#global-diagnostic-filter),

*   otherwise does not exist.

### 2.4. Limits[](#limits)

A WGSL implementation [will](#behavioral-requirements) support shaders that satisfy the following limits. A WGSL implementation may support shaders that go beyond the specified limits.

Note: A WGSL implementation should issue an error if it does not support a shader that goes beyond the specified limits.

Quantifiable shader complexity limits
| Limit | Minimum supported value | Maximum number of members in a [structure](#structure) type | 1023 | | Maximum [nesting depth](#nesting-depth) of a [composite](#composite) type | 15 | | Maximum nesting depth of brace-enclosed statements in a function | 127 | | Maximum number of [parameters](#formal-parameter) for a function | 255 | | Maximum number of case selector values in a [switch](#statement-switch) statement. The sum of, for each case statement, the number of case values, including the [default clause](#default-clause). | 1023 | | Maximum combined [byte-size](#byte-size) of all [variables](#variable) instantiated in the [private](#address-spaces-private) address space that are [statically accessed](#statically-accessed) by a single [shader](#shader) | 8192 | | Maximum combined [byte-size](#byte-size) of all [variables](#variable) instantiated in the [function](#address-spaces-function) address space that are declared in a single [function](#function-function) | 8192 | | Maximum combined [byte-size](#byte-size) of all [variables](#variable) instantiated in the [workgroup](#address-spaces-workgroup) address space that are [statically accessed](#statically-accessed) by a single [shader](#shader) For the purposes of this limit, a [fixed-footprint](#fixed-footprint) array is treated as a [creation-fixed footprint](#creation-fixed-footprint) array when substituting the override value. This maps the WebGPU [maxComputeWorkgroupStorageSize](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-supported-limits-maxcomputeworkgroupstoragesize) limit into a standalone WGSL limit. | [16384](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-supported-limits-maxcomputeworkgroupstoragesize) | | Maximum [byte-size](#byte-size) of an [immediate data](#immediate-data)[variable](#variable). This maps the WebGPU [maxImmediateSize](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-supported-limits-maximmediatesize) limit into a standalone WGSL limit. | [64](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-supported-limits-maximmediatesize) | | Maximum number of elements in [value constructor](#value-constructor-builtin-function) expression of [array](#array) type | 2047 | |
| --- | --- |

## 3. Textual Structure[](#textual-structure)

The `text/wgsl` media type is used to identify content as a WGSL module. See [Appendix A: The text/wgsl Media Type](#text-wgsl-media-type).

A WGSL module is Unicode text using the UTF-8 encoding, with no byte order mark (BOM).

WGSL module text consists of a sequence of Unicode [code points](https://www.unicode.org/versions/Unicode14.0.0/UnicodeStandard-14.0.pdf#), grouped into contiguous non-empty sets forming:

*   [comments](#comment)

*   [tokens](#token)

*   [blankspaces](#blankspace)

The program text [must not](#shader-creation-error) include a null code point (`U+0000`).

### 3.1. Parsing[](#parsing)

To parse a WGSL module:

> 1.   Remove [comments](#comment):
> 
> 
>     *   Replace the first comment with a space code point (`U+0020`).
> 
>     *   Repeat until no comments remain.
> 
> 
> 2.   Find [template lists](#template-list), using the [algorithm](#template-list-discovery) in [§ 3.9 Template Lists](#template-lists-sec). This step disambiguates uses of `'<'` (U+003C) and `'>'` (U+003E) code points as template list delimiters versus other uses such as in comparison operators.
> 
> 3.   Parse the whole text, attempting to match the [translation_unit](#syntax-translation_unit) grammar rule. Parsing uses a LALR(1) parser (one token of lookahead) [[DeRemer1969]](https://www.w3.org/TR/WGSL/#biblio-deremer1969 "Practical Translators for LR(k) Languages"), with the following customization:
> 
> 
>     *   Tokenization is interleaved with parsing, and is context-aware. When the parser requests the next token:
> 
> 
>         *   Consume and ignore an initial sequence of [blankspace](#blankspace) code points.
> 
>         *   If the next code point is the start of a [template list](#template-list), consume it and return [_template_args_start](#syntax_sym-_template_args_start).
> 
>         *   If the next code point is the end of a [template list](#template-list), consume it and return [_template_args_end](#syntax_sym-_template_args_end).
> 
>         *   Otherwise:
> 
> 
>             *   A token candidate is any WGSL [token](#token) formed from the non-empty prefix of the remaining unconsumed code points.
> 
>             *   The token returned is the longest [token candidate](#token-candidate) that is also a valid lookahead token for the current parser state. [[VanWyk2007]](https://www.w3.org/TR/WGSL/#biblio-vanwyk2007 "Context-Aware Scanning for Parsing Extensible Languages")

A [shader-creation error](#shader-creation-error) results if:

*   the entire source text cannot be converted into a finite sequence of valid tokens, or

*   the [translation_unit](#syntax-translation_unit) grammar rule does not match the entire token sequence.

Note:The procedure given above describes [template list discovery](#template-list-discovery) as a discrete phase (step 2), performed before grammar-based parsing (step 3). This separation simplifies the specification. However, it may be inconvenient to map the above procedure to some tools because it inserts a distinct processing phase before tokenization.

An alternative approach is to interleave template list discovery with tokenization. In this approach, a synthetic token ([_disambiguate_template](#syntax_sym-_disambiguate_template)) is placed in a grammar rule at any place where a template list may occur. When the scanner attempts to match the [_disambiguate_template](#syntax_sym-_disambiguate_template) token:

*   The scanner runs the [template list discovery](#template-list-discovery) algorithm on the remaining text, recording the positions of template list delimiters.

*   The scanner signals a successful match of the `_disambiguate_template` token, with an empty string as the associated text.

Future token scanning steps will use the recorded template list delimiter positions to yield [_template_args_start](#syntax_sym-_template_args_start) and [_template_args_end](#syntax_sym-_template_args_end) tokens as indicated.

This alternative approach is non-normative. The normative grammar includes [_disambiguate_template](#syntax_sym-_disambiguate_template) tokens as a help to implementations using the alternative approach. A parser using the standard approach can either ignore the synthetic token, or equivalently, always successfully match it to an empty string.

### 3.2. Blankspace and Line Breaks[](#blankspace-and-line-breaks)

Blankspace is any combination of one or more of code points from the Unicode [Pattern_White_Space](https://www.unicode.org/reports/tr31/tr31-35.html#unicode-standard-annex-31-for-unicode-version-1400) property. The following is the set of code points in [Pattern_White_Space](https://www.unicode.org/reports/tr31/tr31-35.html#unicode-standard-annex-31-for-unicode-version-1400):

*   space (`U+0020`)

*   horizontal tab (`U+0009`)

*   line feed (`U+000A`)

*   vertical tab (`U+000B`)

*   form feed (`U+000C`)

*   carriage return (`U+000D`)

*   next line (`U+0085`)

*   left-to-right mark (`U+200E`)

*   right-to-left mark (`U+200F`)

*   line separator (`U+2028`)

*   paragraph separator (`U+2029`)

A line break is a contiguous sequence of [blankspace](#blankspace) code points indicating the end of a line. It is defined as the blankspace signalling a "mandatory break" as defined by [UAX14 Section 6.1 Non-tailorable Line Breaking Rules](https://www.unicode.org/reports/tr14#BreakingRules)[LB4](https://www.unicode.org/reports/tr14#LB4) and [LB5](https://www.unicode.org/reports/tr14#LB5). That is, a line break is any of:

*   line feed (`U+000A`)

*   vertical tab (`U+000B`)

*   form feed (`U+000C`)

*   carriage return (`U+000D`) when not also followed by line feed (`U+000A`)

*   carriage return (`U+000D`) followed by line feed (`U+000A`)

*   next line (`U+0085`)

*   line separator (`U+2028`)

*   paragraph separator (`U+2029`)

Note: Diagnostics that report source text locations in terms of line numbers should use [line breaks](#line-break) to count lines.

A is a span of text that does not influence the validity or meaning of a WGSL program, except that a comment can separate [tokens](#token). Shader authors can use comments to document their programs.

A is a kind of [comment](#comment) consisting of the two code points `//` (`U+002F` followed by `U+002F`) and the code points that follow, up until but not including:

*   the next [line break](#line-break), or

*   the end of the program.

A is a kind of [comment](#comment) consisting of:

*   The two code points `/*` (`U+002F` followed by `U+002A`)

*   Then any sequence of:

    *   A [block comment](#block-comment), or

    *   Text that does not contain either `*/` (`U+002A` followed by `U+002F`) or `/*` (`U+002F` followed by `U+002A`)

*   Then the two code points `*/` (`U+002A` followed by `U+002F`)

Note: Block comments can be nested. Since a block comment requires matching start and end text sequences, and allows arbitrary nesting, a block comment cannot be recognized with a regular expression. This is a consequence of the Pumping Lemma for Regular Languages.

EXAMPLE: Comments

const f = 1.5; // This is line-ending comment.
const g = 2.5; /* This is a block comment
 that spans lines.
 /* Block comments can nest.
 */
 But all block comments must terminate.
 */

### 3.4. Tokens[](#tokens)

A token is a contiguous sequence of code points forming one of:

*   a [literal](#literal).

*   a [keyword](#keyword).

*   a [reserved word](#reserved-word).

*   a [syntactic token](#syntactic-token).

*   an [identifier](#identifier).

*   a [context-dependent name](#context-dependent-name).

### 3.5. Literals[](#literals)

A literal is one of:

*   A boolean literal: either `true` or `false`.

*   A numeric literal: either an [integer literal](#integer-literal) or a [floating point literal](#floating-point-literal), and is used to represent a number.

#### 3.5.1. Boolean Literals[](#boolean-literals)

EXAMPLE: boolean literals

const a = true;
const b = false;

bool_literal :

`'true'`

|`'false'`

#### 3.5.2. Numeric Literals[](#numeric-literals)

The form of a [numeric literal](#numeric-literal) is defined via pattern-matching.

An integer literal is:

*   An integer specified as any of:

    *   `0`

    *   A sequence of decimal digits, where the first digit is not `0`.

    *   `0x` or `0X` followed by a sequence of hexadecimal digits.

*   Then an optional `i` or `u` suffix.

Note: A leading zero on a non-zero integer literal (e.g. 012) is forbidden, so as to avoid confusion with other languages' leading-zero-means-octal notation.

int_literal :

[decimal_int_literal](#syntax-decimal_int_literal)

|[hex_int_literal](#syntax-hex_int_literal)

decimal_int_literal :

`/0[iu]?/`

|`/[1-9][0-9]*[iu]?/`

EXAMPLE: decimal integer literals

const a = 1u;
const b = 123;
const c = 0;
const d = 0i;

hex_int_literal :

`/0[xX][0-9a-fA-F]+[iu]?/`

EXAMPLE: hexadecimal integer literals

const a = 0x123;
const b = 0X123u;
const c = 0x3f;

A floating point literal is either a [decimal floating point literal](#decimal-floating-point-literal) or a [hexadecimal floating point literal](#hexadecimal-floating-point-literal).

float_literal :

[decimal_float_literal](#syntax-decimal_float_literal)

|[hex_float_literal](#syntax-hex_float_literal)

A [floating point literal](#floating-point-literal) has two logical parts: a significand to represent a fraction, and an optional exponent. Roughly, the value of the literal is the significand multiplied by a base value raised to the given exponent. A significand digit is significant if it is non-zero, or if there are significand digits to its left and to its right that are both non-zero. Significant digits are counted from left-to-right: the _N_'th significant digit has _N_-1 significant digits to its left.

A decimal floating point literal is:

*   A significand, specified as a sequence of digits, with an optional decimal point (`.`) somewhere among them. The significand represents a fraction in base 10 notation.

*   Then an optional exponent suffix consisting of:

    *   `e` or `E`.

    *   Then an exponent specified as an decimal number with an optional leading sign (`+` or `-`).

    *   Then an optional `f` or `h` suffix.

*   At least one of the decimal point, or the exponent, or the `f` or `h` suffix [must](#shader-creation-error) be present. If none are, then the token is instead an [integer literal](#integer-literal).

decimal_float_literal :

`/0[fh]/`

|`/[1-9][0-9]*[fh]/`

|`/[0-9]*\.[0-9]+([eE][+-]?[0-9]+)?[fh]?/`

|`/[0-9]+\.[0-9]*([eE][+-]?[0-9]+)?[fh]?/`

|`/[0-9]+[eE][+-]?[0-9]+[fh]?/`

EXAMPLE: decimal floating point literals

const a = 0.e+4f;
const b = 01.;
const c = .01;
const d = 12.34;
const f = .0f;
const g = 0h;
const h = 1e-3;

The mathematical value of a [decimal floating point literal](#decimal-floating-point-literal) is computed as follows:

*   Compute effective_significand from significand:

    *   If significand has 20 or fewer [significant](#significand-significant) digits, then effective_significand is significand.

    *   Otherwise:

        *   Let truncated_significand be the same as significand except each digit to the right of the 20th significant digit is replaced with 0.

        *   Let truncated_significand_next be the same as significand except:

            *   the 20th significant digit is incremented by 1, and carries are propagated to the left as needed needed to ensure each digit remains in the range 0 through 9, and

            *   each digit to the right of the 20th significant digit is replaced with 0.

        *   Set effective_significand to either truncated_significand or truncated_significand_next. This is an implementation choice.

*   The mathematical value of the literal is the mathematical value of effective_significand as a decimal fraction, multiplied by 10 to the power of the exponent. When no exponent is specified, an exponent of 0 is assumed.

Note: The decimal significand is truncated after 20 decimal digits, preserving approximately log(10)/log(2)×20 ≈ 66.4 significant bits in the fraction.

A hexadecimal floating point literal is:

*   A `0x` or `0X` prefix

*   Then a significand, specified as a sequence of hexadecimal digits, with an optional hexadecimal point (`.`) somewhere among them. The significand represents a fraction in base 16 notation.

*   Then an optional exponent suffix consisting of:

    *   `p` or `P`

    *   Then an exponent specified as an decimal number with an optional leading sign (`+` or `-`).

    *   Then an optional `f` or `h` suffix.

*   At least one of the hexadecimal point, or the exponent [must](#shader-creation-error) be present. If neither are, then the token is instead an [integer literal](#integer-literal).

hex_float_literal :

`/0[xX][0-9a-fA-F]*\.[0-9a-fA-F]+([pP][+-]?[0-9]+[fh]?)?/`

|`/0[xX][0-9a-fA-F]+\.[0-9a-fA-F]*([pP][+-]?[0-9]+[fh]?)?/`

|`/0[xX][0-9a-fA-F]+[pP][+-]?[0-9]+[fh]?/`

EXAMPLE: hexadecimal floating point literals

const a = 0xa.fp+2;
const b = 0x1P+4f;
const c = 0X.3;
const d = 0x3p+2h;
const e = 0X1.fp-4;
const f = 0x3.2p+2h;

The mathematical value of a [hexadecimal floating point literal](#hexadecimal-floating-point-literal) is computed as follows:

*   Compute effective_significand from significand:

    *   If significand has 16 or fewer [significant](#significand-significant) digits, then effective_significand is significand.

    *   Otherwise:

        *   Let truncated_significand be the same as significand except each digit to the right of the 16th significant digit is replaced with 0.

        *   Let truncated_significand_next be the same as significand except:

            *   the 16th significant digit is incremented by 1, and carries are propagated to the left as needed needed to ensure each digit remains in the range 0 through `f`, and

            *   each digit to the right of the 16th significant digit is replaced with 0.

        *   Set effective_significand to either truncated_significand or truncated_significand_next. This is an implementation choice.

*   The mathematical value of the literal is the mathematical value of effective_significand as a hexadecimal fraction, multiplied by 2 to the power of the exponent. When no exponent is specified, an exponent of 0 is assumed.

Note: The hexadecimal significand is truncated after 16 hexadecimal digits, preserving approximately 4 ×16 = 64 significant bits in the fraction.

When a [numeric literal](#numeric-literal) has a suffix, the literal denotes a value in a specific [concrete](#type-concrete)[scalar](#scalar) type. Otherwise, the literal denotes a value one of the [abstract numeric types](#abstract-numeric-types) defined below. In either case, the value denoted by the literal is its mathematical value after conversion to the target type, following the rules in [§ 15.7.6 Floating Point Conversion](#floating-point-conversion).

Mapping numeric literals to types
| Numeric Literal | Suffix | Type | Examples | [integer literal](#integer-literal) | `i` | [i32](#i32) | 42i | | [integer literal](#integer-literal) | `u` | [u32](#u32) | 42u | | [integer literal](#integer-literal) | | [AbstractInt](#abstractint) | 124 | | [floating point literal](#floating-point-literal) | `f` | [f32](#f32) | 42f 1e5f 1.2f 0x1.0p10f | | [floating point literal](#floating-point-literal) | `h` | [f16](#f16) | 42h 1e5h 1.2h 0x1.0p10h | | [floating point literal](#floating-point-literal) | | [AbstractFloat](#abstractfloat) | 1e5 1.2 0x1.0p10 | |
| --- | --- | --- | --- |

A [shader-creation error](#shader-creation-error) results if:

*   An [integer literal](#integer-literal) with a `i` or `u` suffix cannot be represented by the target type.

*   A [hexadecimal floating point literal](#hexadecimal-floating-point-literal) with a `f` or `h` suffix overflows or cannot be exactly represented by the target type.

*   A [decimal floating point literal](#decimal-floating-point-literal) with a `f` or `h` suffix overflows the target type.

*   A [floating point literal](#floating-point-literal) with a `h` suffix is used while the [f16 extension](#extension-f16) is not enabled.

Note: The hexadecimal float value 0x1.00000001p0 requires 33 significand bits to be represented exactly, but [f32](#f32) only has 23 explicit significand bits.

Note: If you want to use an `f` suffix to force a hexadecimal float literal to be of type, the literal must also use a binary exponent. For example, write `0x1p0f`. In comparison, `0x1f` is a hexadecimal integer literal.

### 3.6. Keywords[](#keywords)

A keyword is a [token](#token) which refers to a predefined language concept. See [§ 16.1 Keyword Summary](#keyword-summary) for the list of WGSL keywords.

### 3.7. Identifiers[](#identifiers)

An identifier is a kind of [token](#token) used as a name. See [§ 5 Declaration and Scope](#declaration-and-scope).

WGSL uses two grammar nonterminals to separate use cases:

*   An [ident](#syntax-ident) is used to name a declared object.

*   A [member_ident](#syntax-member_ident) is used to name a [member](#member) of a [structure](#structure) type.

member_ident :

[ident_pattern_token](#syntax-ident_pattern_token)

The form of an identifier is based on the [Unicode Standard Annex #31](https://www.unicode.org/reports/tr31/tr31-35.html#unicode-standard-annex-31-for-unicode-version-1400) for [Unicode Version 14.0.0](#biblio-unicodeversion14 "The Unicode Standard, Version 14.0.0"), with the following elaborations.

Identifiers use the following profile described in terms of [UAX31 Grammar](https://www.unicode.org/reports/tr31/tr31-35.html#D1):

<Identifier> := <Start> <Continue>* (<Medial> <Continue>+)*

<Start> := XID_Start + U+005F
<Continue> := <Start> + XID_Continue
<Medial> :=

This means identifiers with non-ASCII code points like these are valid: `Δέλτα`, `réflexion`, `Кызыл`, `𐰓𐰏𐰇`, `朝焼け`, `سلام`, `검정`, `שָׁלוֹם`, `गुलाबी`, `փիրուզ`.

With the following exceptions:

*   An identifier [must not](#shader-creation-error) have the same spelling as a [keyword](#keyword) or as a [reserved word](#reserved-word).

*   An identifier [must not](#shader-creation-error) be `_` (a single underscore, `U+005F`).

*   An identifier [must not](#shader-creation-error) start with `__` (two underscores, `U+005F` followed by `U+005F`).

ident_pattern_token :

`/([_\p{XID_Start}][\p{XID_Continue}]+)|([\p{XID_Start}])/u`

[Unicode Character Database for Unicode Version 14.0.0](https://www.unicode.org/Public/14.0.0/ucd/DerivedCoreProperties.txt#unicode-character-database-for-unicode-version-1400) includes non-normative listing with all valid code points of both [XID_Start](https://www.unicode.org/reports/tr31/tr31-35.html#Table_Lexical_Classes_for_Identifiers) and [XID_Continue](https://www.unicode.org/reports/tr31/tr31-35.html#Table_Lexical_Classes_for_Identifiers).

Note: The [return type](#return-type) for some [built-in functions](#built-in-functions) are structure types whose name cannot be used WGSL source. Those structure types are described as if they were [predeclared](#predeclared) with a name starting with two underscores. The result value can be saved into newly declared `let` or `var` using type inferencing, or immediately have one of its members immediately extracted by name. See example usages in the description of `frexp` and `modf`.

#### 3.7.1. Identifier Comparison[](#identifier-comparison)

Two WGSL identifiers are the same if and only if they consist of the same sequence of code points.

Note: This specification does not permit Unicode normalization of values for the purposes of comparison. Values that are visually and semantically identical but use different Unicode character sequences will not match. Content authors are advised to use the same encoding sequence consistently or to avoid potentially troublesome characters when choosing values. For more information, see [[CHARMOD-NORM]](https://www.w3.org/TR/WGSL/#biblio-charmod-norm "Character Model for the World Wide Web: String Matching").

Note: A user agent should issue developer-visible warnings when the meaning of a WGSL module would change if all instances of an identifier are replaced with one of that identifier’s homographs. (A homoglyph is a sequence of code points that may appear the same to a reader as another sequence of code points. Examples of mappings to detect homoglyphs are the transformations, mappings, and matching algorithms mentioned in the previous paragraph. Two sequences of code points are homographs if the identifier can transform one into the other by repeatedly replacing a subsequence with its homoglyph.)

### 3.8. Context-Dependent Names[](#context-dependent-names)

A context-dependent name is a [token](#token) used to name a concept, but only in specific grammatical contexts. The spelling of the token may be the same as an [identifier](#identifier), but the token does not [resolve](#resolves) to a declared object. This section lists the tokens used as [context-dependent names](#context-dependent-name). The token must not be a [keyword](#keyword) or [reserved word](#reserved-word).

#### 3.8.1. Attribute Names[](#attribute-names)

See [§ 12 Attributes](#attributes).

The [attribute](#syntax-attribute) names are:

*   [`'align'`](#attribute-align)

*   [`'binding'`](#attribute-binding)

*   [`'builtin'`](#attribute-builtin)

*   [`'compute'`](#attribute-compute)

*   [`'const'`](#attribute-const)

*   [`'diagnostic'`](#attribute-diagnostic)

*   [`'fragment'`](#attribute-fragment)

*   [`'group'`](#attribute-group)

*   [`'id'`](#attribute-id)

*   [`'interpolate'`](#attribute-interpolate)

*   [`'invariant'`](#attribute-invariant)

*   [`'location'`](#attribute-location)

*   [`'blend_src'`](#attribute-blend_src)

*   [`'must_use'`](#attribute-must_use)

*   [`'size'`](#attribute-size)

*   [`'vertex'`](#attribute-vertex)

*   [`'workgroup_size'`](#attribute-workgroup_size)

*   [`'subgroup_size'`](#attribute-subgroup_size)

#### 3.8.2. Built-in Value Names[](#builtin-value-names)

A built-in value name-token is a [token](#token) used in the name of a [built-in value](#built-in-values).

See [§ 13.3.1.1 Built-in Inputs and Outputs](#builtin-inputs-outputs).

builtin_value_name :

[ident_pattern_token](#syntax-ident_pattern_token)

The [built-in value](#built-in-values) names are:

*   [`'vertex_index'`](#built-in-values-vertex_index)

*   [`'instance_index'`](#built-in-values-instance_index)

*   [`'position'`](#built-in-values-position)

*   [`'front_facing'`](#built-in-values-front_facing)

*   [`'frag_depth'`](#built-in-values-frag_depth)

*   [`'sample_index'`](#built-in-values-sample_index)

*   [`'sample_mask'`](#built-in-values-sample_mask)

*   [`'local_invocation_id'`](#built-in-values-local_invocation_id)

*   [`'local_invocation_index'`](#built-in-values-local_invocation_index)

*   [`'global_invocation_id'`](#built-in-values-global_invocation_id)

*   [`'global_invocation_index'`](#built-in-values-global_invocation_index)

*   [`'workgroup_id'`](#built-in-values-workgroup_id)

*   [`'workgroup_index'`](#built-in-values-workgroup_index)

*   [`'num_workgroups'`](#built-in-values-num_workgroups)

*   [`'subgroup_invocation_id'`](#built-in-values-subgroup_invocation_id)

*   [`'subgroup_size'`](#built-in-values-subgroup_size)

*   [`'primitive_index'`](#built-in-values-primitive_index)

*   [`'subgroup_id'`](#built-in-values-subgroup_id)

*   [`'num_subgroups'`](#built-in-values-num_subgroups)

#### 3.8.3. Diagnostic Rule Names[](#diagnostic-rule-names)

A diagnostic name-token is a [token](#token) used in the name of a diagnostic [triggering rule](#diagnostic-triggering-rule).

See [§ 2.3 Diagnostics](#diagnostics).

diagnostic_name_token :

[ident_pattern_token](#syntax-ident_pattern_token)

The pre-defined [diagnostic rule](#diagnostic-triggering-rule) names are:

*   [`'derivative_uniformity'`](#trigger-derivative_uniformity)

*   [`'subgroup_uniformity'`](#trigger-subgroup_uniformity)

#### 3.8.4. Diagnostic Severity Control Names[](#diagnostic-severity-control-names)

The valid [diagnostic filter](#diagnostic-filter) severity control names are listed in [§ 2.3 Diagnostics](#diagnostics) but have the same form as an [identifier](#identifier):

severity_control_name :

[ident_pattern_token](#syntax-ident_pattern_token)

The [diagnostic filter](#diagnostic-filter) severity control names are:

*   [`'error'`](#severity-error)

*   [`'warning'`](#severity-warning)

*   [`'info'`](#severity-info)

*   [`'off'`](#severity-off)

#### 3.8.5. Extension Names[](#extension-names)

The valid [enable-extension](#enable-extension) names are listed in [§ 4.1.1 Enable Extensions](#enable-extensions-sec) but in general have the same form as an [identifier](#identifier):

enable_extension_name :

[ident_pattern_token](#syntax-ident_pattern_token)

The [enable-extension](#enable-extension) names are:

*   [`'f16'`](#extension-f16)

*   [`'clip_distances'`](#extension-clip_distances)

*   [`'dual_source_blending'`](#extension-dual_source_blending)

*   [`'subgroups'`](#extension-subgroups)

*   [`'primitive_index'`](#extension-primitive_index)

*   [`'subgroup_size_control'`](#extension-subgroup_size_control)

The valid [language extension](#language-extension) names are listed in [§ 4.1.2 Language Extensions](#language-extensions-sec) but in general have the same form as an [identifier](#identifier):

language_extension_name :

[ident_pattern_token](#syntax-ident_pattern_token)

The [language extension](#language-extension) names are:

*   [`'readonly_and_readwrite_storage_textures'`](#language_extension-readonly_and_readwrite_storage_textures)

*   [`'packed_4x8_integer_dot_product'`](#language_extension-packed_4x8_integer_dot_product)

*   [`'unrestricted_pointer_parameters'`](#language_extension-unrestricted_pointer_parameters)

*   [`'pointer_composite_access'`](#language_extension-pointer_composite_access)

*   [`'uniform_buffer_standard_layout'`](#language_extension-uniform_buffer_standard_layout)

*   [`'subgroup_id'`](#language_extension-subgroup_id)

*   [`'subgroup_uniformity'`](#language_extension-subgroup_uniformity)

*   [`'texture_and_sampler_let'`](#language_extension-texture_and_sampler_let)

*   [`'texture_formats_tier1'`](#language_extension-texture_formats_tier1)

*   [`'linear_indexing'`](#language_extension-linear_indexing)

*   [`'immediate_address_space'`](#language_extension-immediate_address_space)

*   [`'fragment_depth'`](#language_extension-fragment_depth)

*   [`'buffer_view'`](#language_extension-buffer_view)

*   [`'swizzle_assignment'`](#language_extension-swizzle_assignment)

#### 3.8.6. Interpolation Type Names[](#interpolation-type-names)

An interpolation type name-token is a [token](#token) used in the name of an [interpolation type](#interpolation-type) for [interpolate_type_name](#syntax-interpolate_type_name).

See [§ 13.3.1.4 Interpolation](#interpolation).

The [interpolation type](#interpolation-type) names are:

*   [`'perspective'`](#interpolation-type-perspective)

*   [`'linear'`](#interpolation-type-linear)

*   [`'flat'`](#interpolation-type-flat)

#### 3.8.7. Interpolation Sampling Names[](#interpolation-sampling-names)

An interpolation sampling name-token is a [token](#token) used in the name of an [interpolation sampling](#interpolation-sampling).

See [§ 13.3.1.4 Interpolation](#interpolation).

interpolate_sampling_name :

[ident_pattern_token](#syntax-ident_pattern_token)

The [interpolation sampling](#interpolation-sampling) names are:

*   [`'center'`](#interpolation-sampling-center)

*   [`'centroid'`](#interpolation-sampling-centroid)

*   [`'sample'`](#interpolation-sampling-sample)

*   [`'first'`](#interpolation-sampling-first)

*   [`'either'`](#interpolation-sampling-either)

#### 3.8.8. Swizzle Names[](#swizzle-names)

The [swizzle](#swizzle) names are used in [vector access expressions](#vector-access-expr) and [swizzle view expressions](#swizzle-view-expr):

swizzle_name :

`/[rgba]/`

|`/[rgba][rgba]/`

|`/[rgba][rgba][rgba]/`

|`/[rgba][rgba][rgba][rgba]/`

|`/[xyzw]/`

|`/[xyzw][xyzw]/`

|`/[xyzw][xyzw][xyzw]/`

|`/[xyzw][xyzw][xyzw][xyzw]/`

#### 3.8.9. Depth Mode Names[](#depth-mode-names)

A depth mode name-token is a [token](#token) used in the [frag_depth](#built-in-values-frag_depth) builtin when the [fragment_depth](#language_extension-fragment_depth) feature is supported.

*   [`'less'`](#depth_mode-less)

*   [`'greater'`](#depth_mode-greater)

### 3.9. Template Lists[](#template-lists-sec)

Template parameterization is a way to specify parameters that modify a general concept. To write a template parameterization, write the general concept, followed by a [template list](#template-list).

Ignoring [comments](#comment) and [blankspace](#blankspace), a template list is:

*   An initial `'<'` (U+003C) code point, then

*   A [comma](#syntax_sym-comma)-separated list of one or more template parameters, then

*   An optional trailing [comma](#syntax_sym-comma), then

*   A terminating `'>'` (U+003E) code point.

The form of a [template parameter](#template-parameters) is implicitly defined by the [template list discovery](#template-list-discovery) algorithm below. Generally, they are names, expressions, or types.

Note: For example, the phrase `vec3<f32>` is a template parameterization where `vec3` is the general concept being modified, and `<f32>` is a template list containing one parameter, the [f32](#f32) type. Together, `vec3<f32>` denotes a specific [vector](#vector) type.

Note: For example, the phrase `var<storage,read_write>` modifies the general `var` concept with template parameters `storage` and `read_write`.

Note:For example, the phrase `array<vec4<f32>>` has two template parameterizations:

*   `vec4<f32>` modifies the general `vec4` concept with template parameter `f32`.

*   `array<vec4<f32>>` modifies the general `array` concept with template parameter `vec4<f32>`.

The `'<'` (U+003C) and `'>'` (U+003E) code points that delimit a template list are also used when spelling:

*   A comparison operator in a [relational_expression](#syntax-relational_expression).

*   A shift operator in a [shift_expression](#syntax-shift_expression).

*   A [compound_assignment_operator](#syntax-compound_assignment_operator) for performing a shift operation followed by an assignment.

The syntactic ambiguity is resolved in favour of template lists:

*   Template lists are discovered in an early phase of parsing, before [declarations](#declaration), [expressions](#expression), [statements](#statement) are parsed.

*   During tokenization in a later phase, the intial `'<'` (U+003C) of a template list is mapped to a [_template_args_start](#syntax_sym-_template_args_start) token, and the terminating `'>'` (U+003E) of a template list is mapped to a [_template_args_end](#syntax_sym-_template_args_end) token.

The [template list discovery](#template-list-discovery) algorithm is given below. It uses the following assumptions and properties:

1.   A [template parameter](#template-parameters) is an [expression](#expression), and therefore does not start with either a `'<'` (U+003C) or a `'='` (U+003D) code point.

2.   An expression does not contain code points `';'` (U+003B), `'{'` (U+007B), or `':'` (U+003A).

3.   An expression does not contain an [assignment](#statement-assignment).

4.   The only time a `'='` (U+003D) code point appears is as part of a comparison operation, i.e. in one of [`'<='`](#syntax_sym-less_than_equal), [`'>='`](#syntax_sym-greater_than_equal), [`'=='`](#syntax_sym-equal_equal), or [`'!='`](#syntax_sym-not_equal). Otherwise, a `'='` (U+003D) code point appears as part of an assignment.

5.   Template list delimiters respect nested expressions formed by parentheses '(...)', and array indexing '[...]'. The start and end of a template list must appear at the same nesting level.

> **Algorithm:**Template list discovery
> **Input:** The program source text.
> 
> 
> **Record types:**
> 
> 
> Let UnclosedCandidate be a record type containing:
> 
> 
> *   position, a location in the source text
> 
> *   depth, an integer, the expression nesting depth at position
> 
> 
> 
> Let TemplateList be a record type containing:
> 
> 
> *   start_position, the source location of the `'<'` (U+003C) code point that starts this template list.
> 
> *   end_position, the source location of the `'>'` (U+003E) code point that ends this template list.
> 
> 
> 
> **Output:**DiscoveredTemplateLists, a list of TemplateList records.
> 
> 
> **Procedure:**
> 
> 
> *   Initialize DiscoveredTemplateLists to an empty list.
> 
> *   Initialize a Pending variable to be an empty stack of UnclosedCandidate records.
> 
> *   Initialize a CurrentPosition integer variable to 0. It encodes the position of the code point currently being examined, as a count of the number of code points after the start of the source text.
> 
> 
>     *   This variable will advance forward in the text while executing the algorithm. When the end of text is reached, terminate the algorithm immediately and have it return DiscoveredTemplateLists.
> 
> 
> *   Initialize a NestingDepth integer variable to 0.
> 
> *   Repeat the following steps:
> 
> 
>     *   Advance CurrentPosition past [blankspace](#blankspace), [comments](#comment), and [literals](#literal).
> 
>     *   If [ident_pattern_token](#syntax-ident_pattern_token) matches the text at CurrentPosition, then:
> 
> 
>         *   Advance CurrentPosition past the [ident_pattern_token](#syntax-ident_pattern_token).
> 
>         *   Advance CurrentPosition past blankspace and comments, if present.
> 
>         *   If `'<'` (U+003C) appears at CurrentPosition, then:
> 
> 
>             *   Note: This code point is a candidate for being the start of a template list. Save enough state so it can be matched against a terminating `'>'` (U+003E) appearing later in the input.
> 
>             *   Push UnclosedCandidate(position=CurrentPosition,depth=NestingDepth) onto the Pending stack.
> 
>             *   Advance CurrentPosition to the next code point.
> 
>             *   If `'<'` (U+003C) appears at CurrentPosition, then:
> 
> 
>                 *   Note: From assumption 1, no template parameter starts with `'<'` (U+003C), so the previous code point cannot be the start of a template list. Therefore the current and previous code point must be [`'<<'`](#syntax_sym-shift_left) operator.
> 
>                 *   Pop the top entry from the Pending stack.
> 
>                 *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
>             *   If `'='` (U+003D) appears at CurrentPosition, then:
> 
> 
>                 *   Note: From assumption 1, no template parameter starts with `'='` (U+003C), so the previous code point cannot be the start of a template list. Assume the current and previous code point form a [`'<='`](#syntax_sym-less_than_equal) comparison operator. Skip over the `'='` (U+003D) code point so a later step does not mistake it for an assignment.
> 
>                 *   Pop the top entry from the Pending stack.
> 
>                 *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
> 
>         *   Start the next iteration of the loop.
> 
> 
>     *   If `'>'` (U+003E) appears at CurrentPosition then:
> 
> 
>         *   Note: This code point is a candidate for being the end of a template list.
> 
>         *   If Pending is not empty, then let T be its top entry, and if T.depth equals NestingDepth then:
> 
> 
>             *   Note: This code point ends the current template list whose start is recorded in T.
> 
>             *   Add TemplateList(start_position=T.position, end_position=CurrentPosition) to DiscoveredTemplateLists.
> 
>             *   Pop T off the Pending stack.
> 
>             *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
>         *   Otherwise, this code point does not end a template list:
> 
> 
>             *   Advance CurrentPosition past this code point.
> 
>             *   If `'='` (U+003D) appears at CurrentPosition then:
> 
> 
>                 *   Note: Assume the current and previous code points form a [`'>='`](#syntax_sym-greater_than_equal) comparison operator. Skip over the `'='` (U+003D) code point so a later step does not mistake it for an assignment.
> 
>                 *   Advance CurrentPosition past this code point.
> 
> 
>             *   Start the next iteration of the loop.
> 
> 
> 
>     *   If `'('` (U+0028) or `'['` (U+005B) appears at CurrentPosition then:
> 
> 
>         *   Note: Enter a nested expression.
> 
>         *   Add 1 to NestingDepth.
> 
>         *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
>     *   If `')'` (U+0029) or `']'` (U+005D) appears at CurrentPosition then:
> 
> 
>         *   Note: Exit a nested expression.
> 
>         *   Pop entries from the Pending stack until it is empty, or until the its top entry has depth<NestingDepth.
> 
>         *   Set NestingDepth to 0 or NestingDepth − 1, whichever is larger.
> 
>         *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
>     *   If `'!'` (U+0021) appears at CurrentPosition then:
> 
> 
>         *   Advance CurrentPosition past this code point.
> 
>         *   If `'='` (U+003D) appears at CurrentPosition then:
> 
> 
>             *   Note: Assume the current and previous code points form a [`'!='`](#syntax_sym-not_equal) comparison operator. Skip over the `'='` (U+003D) code point so a later step does not mistake it for an assignment.
> 
>             *   Advance CurrentPosition past this code point.
> 
> 
>         *   Start the next iteration of the loop.
> 
> 
>     *   If `'='` (U+003D) appears at CurrentPosition then:
> 
> 
>         *   Advance CurrentPosition past this code point.
> 
>         *   If `'='` (U+003D) appears at CurrentPosition then:
> 
> 
>             *   Note: Assume the current and previous code points form a [`'=='`](#syntax_sym-equal_equal) comparison operator. Skip over the `'='` (U+003D) code point so a later step does not mistake it for an assignment.
> 
>             *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
>         *   Note: Assume this code point is part of an assignment, which cannot appear as part of an expression, and therefore cannot appear in a template list. Clear pending unclosed candidates.
> 
>         *   Set NestingDepth to 0.
> 
>         *   Remove all entries from the Pending stack.
> 
>         *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
>     *   If `';'` (U+003B) or `'{'` (U+007B) or `':'` (U+003A) appears at CurrentPosition then:
> 
> 
>         *   Note: These cannot appear in the middle of an expression, and therefore cannot appear in a template list. Clear pending unclosed candidates.
> 
>         *   Set NestingDepth to 0.
> 
>         *   Remove all entries from the Pending stack.
> 
>         *   Advance CurrentPosition past this code point, and start the next iteration of the loop.
> 
> 
>     *   If [`'&&'`](#syntax_sym-and_and) or [`'||'`](#syntax_sym-or_or) matches the text at CurrentPosition then:
> 
> 
>         *   Note: These are operators that have lower precedence than comparisons. Reject any pending unclosed candidates at the current expression level.
> 
>         *   Note: With this rule, no template list will be found in the program fragment `a<b || c>d`. Instead it will be recognized as the short-circuiting disjunction of two comparisons.
> 
>         *   Pop entries from the Pending stack until it is empty, or until the its top entry has depth<NestingDepth.
> 
>         *   Advance CurrentPosition past the two code points, and start the next iteration of the loop.
> 
> 
>     *   Advance CurrentPosition past the current code point.

Note:The algorithm can be modified to find the source ranges for [template parameters](#template-parameters), as follows:

*   Modify UnclosedCandidate to add the following fields:

    *   parameters, a list of source ranges of template parameters.

    *   parameter_start_position, a source location.

*   Modify TemplateList to add a field:

    *   parameters, a list of source ranges of template parameters.

*   When pushing a new UnclosedCandidate onto the Pending stack:

    *   Set its parameters field to an empty list.

    *   Set parameter_start_position to one code point past CurrentPosition.

*   When adding a TemplateList, TL, to DiscoveredTemplateLists:

    *   Let T be the top of the Pending stack, as in the original algorithm.

    *   Push the source range starting at T.parameter_start_position and ending at CurrentPosition−1 onto T.parameters.

    *   Prepare TL as in the original algorithm.

    *   Set TL.parameters to T.parameters.

*   Insert a check at the end the loop, just before advancing past the current code point:

    *   If '`,`' (U+002C) appears at CurrentPosition and Pending is not empty, then:

        *   Let T be the top of the Pending stack.

        *   Push the source range starting at T.parameter_start_position and ending at CurrentPosition−1 onto T.parameters.

        *   Set T.parameter_start_position to CurrentPosition+1

Note: The algorithm explicitly skips past literals because some numeric literals end in a letter, for example `1.0f`. The terminating `f` should not be mistaken as the start of an [ident_pattern_token](#syntax-ident_pattern_token).

Note: In the phrase `A ( B < C, D > ( E ) )`, the segment `< C, D >` is a [template list](#template-list).

Note: The algorithm respects expression nesting: The start and end of a particular template list cannot appear at different expression nesting levels. For example, in `array<i32,select(2,3,a>b)>`, the template list has three parameters, where the last one is `select(2,3,a>b)`. The `'>'` in `a>b` does not terminate the template list because it is enclosed in a parenthesized part of the expression calling the `select` function.

Note: Both ends of a template list must appear within the same [indexing expression](#indexing-expression). For example `a[b<d]>()` does not contain a valid template list.

Note: In the phrase `A<B<<C>`, the phrase `B<<C` is parsed as `B` followed by the left-shift operator [`'<<'`](#syntax_sym-shift_left) followed by `C`. The template discovery algorithm starts examining `B` then '`<`' (U+003C) but then sees that the next `'<'` (U+003C) code point cannot start a template argument, and so the `'<'` immediately after the `B` is not the start of a template list. The initial `'<'` and final `'>'` are the only template list delimiters, and it has template parameter `B<<C`.

Note: The phrase `A<B<=C>` is analyzed similarly to the previous note, so the phrase `B<=C` is parsed as `B` followed by the less-than-or-equal operator [`'<='`](#syntax_sym-less_than_equal) followed by `C`. The template discovery algorithm starts examining `B` then `'<'` (U+003C) but then sees that the next `'='` (U+003D) code point cannot start a template argument, and so the `'<'` immediately after the `B` is not the start of a template list. The initial `'<'` and final `'>'` are the only template list delimiters, and it has template parameter `B<=C`.

Note: When examining the phrase `A<(B>=C)>`, there is one template list, starting at the first `'<'` (U+003C) code point and ending at the last `'>'` (U+003E) code point, and having template argument `B>=C`. After examining the first `'>'` (U+003C) code point (after `B`), the `'='` (U+003D) code point needs to be recognized specially so it isn’t assumed to be part of an assignment.

Note: When examining the phrase `A<(B!=C)>`, there is one template list, starting at the first `'<`' (U+003C) code point and ending at the last `'>'` (U+003E) code point, and having template argument `B!=C`. After examining the `'!'` (U+0021) code point (after `'B'`), the `'='` (U+003D) code point needs to be recognized specially so it isn’t assumed to be part of an assignment.

Note: When examining the phrase `A<(B==C)>`, there is one template list, starting at the first `'<'` (U+003C) code point and ending at the last `'>'` (U+003E) code point, and having template argument `B==C`. After examining the first `'='` (U+003D) code point (after `'B'`), the second `'='` (U+003D) code point needs to be recognized specially so neither are assumed to be part of an assignment.

After [template list discovery](#template-list-discovery) completes, [parsing](#parsing)[will](#behavioral-requirements) attempt to match each template list to the [template_list](#syntax-template_list) grammar rule.

template_arg_comma_list :

[template_arg_expression](#syntax-template_arg_expression) ( [`','`](#syntax_sym-comma)[template_arg_expression](#syntax-template_arg_expression) ) * [`','`](#syntax_sym-comma) ?

template_arg_expression :

[expression](#syntax-expression)

## 4. Directives[](#directives)

A directive is a [token](#token) sequence which modifies how a WGSL program is processed by a WebGPU implementation.

Directives are optional. If present, all directives [must](#shader-creation-error) appear before any [declarations](#declaration) or [const assertions](#assertions).

### 4.1. Extensions[](#extensions)

WGSL is expected to evolve over time.

An extension is a named grouping of a coherent set of modifications to the WGSL specification, consisting of any combination of:

*   Addition of new concepts and behaviors via new syntax, including:

    *   declarations, statements, attributes, and built-in functions.

*   Removal of restrictions in the current specification or in previously published extensions.

*   Syntax for reducing the set of permissible behaviors.

*   Syntax for limiting the features available to a part of the program.

*   A description of how the extension interacts with the existing specification, and optionally with other extensions.

Hypothetically, extensions could:

*   Add numeric scalar types, such as different bit width integers.

*   Add syntax to constrain floating point rounding mode.

*   Add syntax to signal that a shader does not use atomic types.

*   Add new kinds of statements.

*   Add new built-in functions.

*   Add syntax to constrain how shader invocations execute.

*   Add new shader stages.

There are two kinds of extensions: [enable-extensions](#enable-extension) and [language extensions](#language-extension).

#### 4.1.1. Enable Extensions[](#enable-extensions-sec)

An enable-extension is an [extension](#extension) whose functionality is available only if:

*   The implementation supports it, and

*   The shader explicitly requests it via an [enable directive](#enable-directive), and

*   The corresponding WebGPU `GPUFeatureName` was one of the required features requested when creating the `GPUDevice`.

[Enable-extensions](#enable-extension) are intended to expose hardware functionality that is not universally supported.

An enable directive is a [directive](#directive) that turns on support for one or more enable-extensions. A [shader-creation error](#shader-creation-error) results if the implementation does not support all the listed enable-extensions.

enable_directive :

`'enable'`[enable_extension_list](#syntax-enable_extension_list)[`';'`](#syntax_sym-semicolon)

enable_extension_list :

[enable_extension_name](#syntax-enable_extension_name) ( [`','`](#syntax_sym-comma)[enable_extension_name](#syntax-enable_extension_name) ) * [`','`](#syntax_sym-comma) ?

Like other directives, if an [enable directive](#enable-directive) is present, it must appear before all [declarations](#declaration) and [const assertions](#assertions). Extension names are not [identifiers](#identifier): they do not [resolve](#resolves) to [declarations](#declaration).

The valid [enable-extensions](#enable-extension) are listed in the following table.

Enable-extensions
| WGSL enable-extension | WebGPU `GPUFeatureName` | Description | `f16` | ["shader-f16"](../webgpu_spec/webgpu-5f71975aec.md#shader-f16) | The [f16](#f16) type is valid to use in the WGSL module. Otherwise, using [f16](#f16) (directly or indirectly) will result in a [shader-creation error](#shader-creation-error). | | `clip_distances` | ["clip-distances"](../webgpu_spec/webgpu-5f71975aec.md#dom-gpufeaturename-clip-distances) | The built-in variable [clip_distances](#built-in-values-clip_distances) is valid to use in the WGSL module. Otherwise, using [clip_distances](#built-in-values-clip_distances) will result in a [shader-creation error](#shader-creation-error). | | `dual_source_blending` | ["dual-source-blending"](../webgpu_spec/webgpu-5f71975aec.md#dom-gpufeaturename-dual-source-blending) | The attribute [blend_src](#attribute-blend_src) is valid to use in the WGSL module. Otherwise, using [blend_src](#attribute-blend_src) will result in a [shader-creation error](#shader-creation-error). | | `subgroups` | ["subgroups"](../WGPU/gpuweb-spec/gpuweb-spec.md#subgroups) | It is valid to use [subgroup built-in values](#builtin-inputs-outputs), [subgroup built-in functions](#subgroup-builtin-functions), and [quad built-in functions](#quad-builtin-functions) in a WGSL module. Otherwise, any use will result in a [shader-creation error](#shader-creation-error). | | `primitive_index` | `"primitive-index"` | The built-in variable [primitive_index](#built-in-values-primitive_index) is valid to use in the WGSL module. Otherwise, using [primitive_index](#built-in-values-primitive_index) will result in a [shader-creation error](#shader-creation-error). | | `subgroup_size_control` | `"subgroup-size-control"` | The attribute [subgroup_size](#attribute-subgroup_size) is valid to use in the WGSL module. Otherwise, using [subgroup_size](#attribute-subgroup_size) will result in a [shader-creation error](#shader-creation-error). The [subgroups](#extension-subgroups)[will](#behavioral-requirements) be automatically enabled when `subgroup_size_control` is enabled. | | `atomic_vec2u_min_max` | `"atomic-vec2u-min-max"` | The built-in functions [atomicStoreMin](#atomic-store-min) and [atomicStoreMax](#atomic-store-max) are valid to use on [atomic](#atomic-type)<[vec2](#vector)<[u32](#u32)>> types in the [storage](#address-spaces-storage) address space. Otherwise, using these will result in a [shader-creation error](#shader-creation-error). | |
| --- | --- | --- |

EXAMPLE: Using hypothetical enable-extensions

// Enable a hypothetical extension for arbitrary precision floating point types.
enable arbitrary_precision_float;
enable arbitrary_precision_float; // A redundant enable directive is ok.

// Enable a hypothetical extension to control the rounding mode.
enable rounding_mode;

// Assuming arbitrary_precision_float enables use of:
// - a type f<E,M>
// - as a type in function return, formal parameters and let-declarations
// - as a value constructor from AbstractFloat
// - operands to division operator: /
// Assuming @rounding_mode attribute is enabled by the rounding_mode enable directive.
@rounding_mode(round_to_even)
fn halve_it(x : f<8, 7>) -> f<8, 7> {
  let two = f<8, 7>(2);
  return x / 2; // uses round to even rounding mode.
}

#### 4.1.2. Language Extensions[](#language-extensions-sec)

A language extension is an [extension](#extension) which is automatically available if the implementation supports it. The program does not have to explicitly request it.

[Language extensions](#language-extension) embody functionality which could reasonably be supported on any WebGPU implementation. If the feature is not universally supported, that it is because some WebGPU implementation has not yet implemented it.

Note: For example, do-while loops could be a language extension.

The `wgslLanguageFeatures` member of the WebGPU `GPU` object lists the set of [language extensions](#language-extension) supported by the implementation.

A requires-directive is a [directive](#directive) that _documents_ the program’s use of one or more [language extensions](#language-extension). It does not change the functionality exposed by the implementation. A [shader-creation error](#shader-creation-error) results if the implementation does not support one of the required extensions.

A WGSL module _can_ use a [requires-directive](#requires-directive) to signal the potential for non-portability, and to signal the _intended_ minimum bar for portability.

Note: Tooling outside of a WebGPU implementation could check whether all the [language extensions](#language-extension) used by a program are covered by [requires-directives](#requires-directive) in the program.

requires_directive :

`'requires'`[language_extension_list](#syntax-language_extension_list)[`';'`](#syntax_sym-semicolon)

language_extension_list :

[language_extension_name](#syntax-language_extension_name) ( [`','`](#syntax_sym-comma)[language_extension_name](#syntax-language_extension_name) ) * [`','`](#syntax_sym-comma) ?

Like other directives, if a [requires-directive](#requires-directive) is present, it must appear before all [declarations](#declaration) and [const assertions](#assertions). Extension names are not [identifiers](#identifier): they do not [resolve](#resolves) to [declarations](#declaration).

Language extensions
| WGSL language extension | Description | readonly_and_readwrite_storage_textures | Allows the use of [read](#access-read) and [read_write](#access-read_write)[access modes](#access-mode) with [storage textures](#type-storage-texture). Additionally, adds the [textureBarrier](#textureBarrier-builtin) built-in function. | | packed_4x8_integer_dot_product | Supports using 32-bit integer scalars packing 4-component vectors of 8-bit integers as inputs to the dot product instructions with [dot4U8Packed](#dot4U8Packed-builtin) and [dot4I8Packed](#dot4I8Packed-builtin) built-in functions. Additionally, adds packing and unpacking instructions with packed 4-component vectors of 8-bit integers with [pack4xI8](#pack4xI8-builtin), [pack4xU8](#pack4xU8-builtin), [pack4xI8Clamp](#pack4xI8Clamp-builtin), [pack4xU8Clamp](#pack4xU8Clamp-builtin), [unpack4xI8](#unpack4xI8-builtin), and [unpack4xU8](#unpack4xU8-builtin) built-in functions. | | unrestricted_pointer_parameters | Removes the following [restrictions](#function-restriction) from [user-defined functions](#user-defined-function): For [user-defined functions](#user-defined-function), a parameter of pointer type [must](#shader-creation-error) be in one of the following address spaces: * [function](#address-spaces-function) * [private](#address-spaces-private) Each argument of pointer type to a [user-defined function](#user-defined-function)[must](#shader-creation-error) have the same [memory view](#memory-view) as its [root identifier](#root-identifier). * NOTE: This means no [vector](#vector), [matrix](#matrix), [array](#array), or [structure](#structure) access expressions can be applied to produce a [memory view](#memory-view) into the [root identifier](#root-identifier) when traced from the argument back through all the [let-declarations](#let-declaration). | | pointer_composite_access | Supports [composite-value decomposition expressions](#composite-value-decomposition-expr) where the root expression is a pointer, yielding a reference. For example, if `p` is a pointer to a structure with member `m`, then `p.m` is a reference to the memory locations for `m` inside the structure `p` points to. Similarly, if `pa` is a pointer to an array, then `pa[i]` is a reference to the memory locations for the `i`’th element of the array `pa` points to. | | uniform_buffer_standard_layout | Allow buffers in the [uniform](#address-spaces-uniform) address space to use the same [memory layout constraints](#address-space-layout-constraints) as other address spaces. | | subgroup_id | Allows the use of the [subgroup_id](#built-in-values-subgroup_id) and [num_subgroups](#built-in-values-num_subgroups) built-in values when the [subgroups](#extension-subgroups) extension is enabled. | | subgroup_uniformity | Adds an additional scope, subgroup, for [uniform control flow](#uniform-control-flow)[subgroup](#subgroup-builtin-functions) and [quad](#quad-builtin-functions) built-in functions to be all invocations in the same [subgroup](#subgroup). Note: The use of subgroup and quad built-in functions requires the [subgroups](#extension-subgroups) extension to be enabled. | | texture_and_sampler_let | Allows the [effective-value-type](#effective-value-type) of a [let-declaration](#let-declaration) to be a [texture](#texture-types) or [sampler](#sampler-types) type. | | texture_formats_tier1 | Supports additional [texel formats](#texel-format): [rgba16unorm](#texel-format-rgba16unorm), [rgba16snorm](#texel-format-rgba16snorm), [rg8unorm](#texel-format-rg8unorm), [rg8snorm](#texel-format-rg8snorm), [rg8uint](#texel-format-rg8uint), [rg8sint](#texel-format-rg8sint), [rg16unorm](#texel-format-rg16unorm), [rg16snorm](#texel-format-rg16snorm), [rg16uint](#texel-format-rg16uint), [rg16sint](#texel-format-rg16sint), [rg16float](#texel-format-rg16float), [r8unorm](#texel-format-r8unorm), [r8snorm](#texel-format-r8snorm), [r8uint](#texel-format-r8uint), [r8sint](#texel-format-r8sint), [r16unorm](#texel-format-r16unorm), [r16snorm](#texel-format-r16snorm), [r16uint](#texel-format-r16uint), [r16sint](#texel-format-r16sint), [r16float](#texel-format-r16float), [rgb10a2unorm](#texel-format-rgb10a2unorm), [rgb10a2uint](#texel-format-rgb10a2uint), [rg11b10ufloat](#texel-format-rg11b10ufloat) | | linear_indexing | Supports the [global_invocation_index](#built-in-values-global_invocation_index) and [workgroup_index](#built-in-values-workgroup_index)[built-in values](#built-in-values). | | immediate_address_space | Enables the [immediate](#address-spaces-immediate) address space, allowing variables to be declared with `var<immediate>` and bound to small amounts of frequently updated data passed directly from the command encoder via the WebGPU API. | | fragment_depth | Introduces a new [depth_mode](#depth-mode-name-token) built-in parameter for the [`frag-depth` builtin](#built-in-values-frag_depth) with modes [`less`](#depth_mode-less), and [`greater`](#depth_mode-greater) which are used when a [fragment](#fragment) shader is declaring it will only write depth values that are guaranteed to be less than (or greater than) the existing depth. | | buffer_view | Enables the use of [buffer](#buffer) types and the [buffer_view built-in functions](#buffer-view-builtin-functions). Allow the declaration of variables with an opaque store type that can be reinterpreted as other [host-shareable](#host-shareable) types. | | swizzle_assignment | Supports [swizzle view](#swizzle-view) types. This enables [swizzle assignments](#swizzle-assignment): a single assignment statement can update multiple components of a vector without having to update the entire vector. For example, if variable `v` is a 4-element vector, then `v.xz = vec2(1,2);` is a shorthand way of writing `v.x = 1; v.z = 2;`, while performing one read and one write. If [pointer_composite_access](#language_extension-pointer_composite_access) is also supported, then this also works on pointers. If `p` is a pointer to a vector of at least 3 elements, then `p.xz = vec2(1,2);` is shorthand for `(*p).x = 1; (*p).z = 2;`. | | atomic_vec2u_min_max | Supports the [atomicStoreMin](#atomic-store-min) and [atomicStoreMax](#atomic-store-max) built-in functions on [atomic<vec2<u32>>](#atomic-types) objects. | |
| --- | --- |

Note: The intent is that, over time, WGSL will define language extensions embodying all functionality in language extensions commonly supported at that time. In a [requires-directive](#requires-directive), these serve as a shorthand for listing all those common features. They represent progressively increasing sets of functionality, and can be thought of as language versions, of a sort.

### 4.2. Global Diagnostic Filter[](#global-diagnostic-directive)

A global diagnostic filter is a diagnostic filter whose [affected range](#affected-range) is the whole WGSL module. It is a [directive](#directive), thus appearing before any [module-scope](#module-scope) declarations. It is spelled like the attribute form, but without the leading `@` (U+0040) code point, and with a terminating semicolon.

diagnostic_directive :

`'diagnostic'`[diagnostic_control](#syntax-diagnostic_control)[`';'`](#syntax_sym-semicolon)

## 5. Declaration and Scope[](#declaration-and-scope)

A declaration associates an [identifier](#identifier) with one of the following kinds of objects:

*   a [type](#type)

*   a [type-generator](#type-generator)

*   a [value](#value-declaration)

*   a [variable](#variable)

*   a [function](#function-function)

*   a [formal parameter](#formal-parameter)

*   an [enumerant](#enumerant)

In other words, a declaration introduces a name for an object.

A declaration is at module scope if the declaration appears in the program source, but outside the text of any other declaration.

A [function](#function-function) declaration appears at module-scope. A function declaration contains declarations for formal parameters, if it has any, and it may contain [variable and value declarations](#var-and-value) inside its [body](#function-body). Those contained declarations are therefore not at module-scope.

Note: The only kind of declaration that contain another declaration is a [function declaration](#function-declaration).

Certain objects are provided by the WebGPU implementation, and are treated as if they have been declared before the start of the WGSL module source. We say such objects are predeclared. For example, WGSL predeclares:

*   [built-in functions](#built-in-functions),

*   built-in types such as [i32](#i32) and [f32](#f32),

*   built-in [type-generators](#type-generator) such as `array`, `ptr`, and `texture_2d`, and

*   [enumerants](#enumerant) such as [read_write](#access-read_write), [workgroup](#address-spaces-workgroup), and [rgba8unorm](#texel-format-rgba8unorm).

The scope of a declaration is the set of program source locations where a declared identifier potentially denotes its associated object. We say the identifier is in scope (of the declaration) at those source locations.

Where a declaration appears determines its scope:

*   Predeclared objects, and objects declared at module-scope, are [in scope](#in-scope) across the entire program source.

*   Each [formal parameter](#formal-parameter) of a user-declared function is [in scope](#in-scope) across the corresponding [function body](#function-body). See [§ 11.1 Declaring a User-defined Function](#function-declaration-sec).

*   Otherwise, the scope is a span of text beginning immediately after the end of the declaration. For details, see [§ 7 Variable and Value Declarations](#var-and-value).

Two declarations in the same WGSL source program [must not](#shader-creation-error) simultaneously:

*   introduce the same identifier name, and

*   have the same end-of-scope.

Note: A predeclared object does not have a declaration in the WGSL source. So a user-specified declaration at module-scope or inside a function can have the same name as a predeclared object.

Identifiers are used as follows, distinguished by grammatical context:

*   A token matching the [ident](#syntax-ident) grammar element is:

    *   Used in a [declaration](#declaration), as the name of the object being declared, or

    *   Used as a name, denoting an object declared elsewhere. This is the common case.

*   A token matching the [member_ident](#syntax-member_ident) grammar element is:

    *   Used in a [structure](#structure) type [declaration](#declaration), as the name of a [member](#member), or

    *   Used as a name, denoting a member of a structure value, or denoting a reference to a member of a structure. See [§ 8.5.4 Structure Access Expression](#struct-access-expr).

When an [ident](#syntax-ident) token appears as a name denoting an object declared elsewhere, it [must](#shader-creation-error) be [in scope](#in-scope) for some declaration. The object denoted by the identifier token is determined as follows:

*   If the token is in scope for at least one non-[module-scope](#module-scope) declaration, then the token denotes the object associated with the nearest of those declarations.

Note: The nearest such declaration appears before the identifier token.

*   Otherwise, if there is a module-scope declaration with that name, then the token denotes that declared object.

Note: The module-scope declaration may appear before **or after** the identifier token.

*   Otherwise, if there is a [predeclared](#predeclared) object with that name, then the token denotes that object.

When the above algorithm is used to map an identifier to a declaration, we say the identifier resolves to that declaration. Similarly, we also say the identifier [resolves](#resolves) to the declared object.

It is a [shader-creation error](#shader-creation-error) if any [module scope](#module-scope) declaration is recursive. That is, no cycles can exist among the declarations:

> Consider the directed graph where: 
> *   Each node corresponds to a declaration D.
> 
> *   There is an edge from declaration D to declaration T when the definition for D mentions an identifier which [resolves](#resolves) to T.
> 
> 
> 
> This graph must not have a cycle.

Note: The [function body](#function-body) is part of the [function declaration](#function-declaration), thus functions must not be recursive, either directly or indirectly.

Note: Non-[module scope](#module-scope) identifier declarations must precede their uses in the text.

EXAMPLE: Valid and invalid declarations

// Valid, user-defined variables can have the same name as a built-in function.
var<private> modf: f32 = 0.0;

// Valid, foo_1 is in scope for the entire program.
var<private> foo: f32 = 0.0; // foo_1

// Valid, bar_1 is in scope for the entire program.
var<private> bar: u32 = 0u; // bar_1

// Valid, my_func_1 is in scope for the entire program.
// Valid, foo_2 is in scope until the end of the function.
fn my_func(foo: f32) { // my_func_1, foo_2
  // Any reference to 'foo' resolves to the function parameter.

  // Invalid, modf resolves to the module-scope variable.
  let res = modf(foo);

  // Invalid, the scope of foo_2 ends at the of the function.
  var foo: f32; // foo_3

  // Valid, bar_2 is in scope until the end of the function.
  var bar: u32; // bar_2
  // References to 'bar' resolve to bar_2
  {
    // Valid, foo_4 is in scope until the end of the compound statement.
    var foo : f32; // foo_4

    // Valid, bar_3 is in scope until the end of the compound statement.
    var bar: u32; // bar_3
    // References to 'bar' resolve to bar_3

    // Invalid, bar_4 has the same end scope as bar_3.
    var bar: i32; // bar_4

    // Valid, i_1 is in scope until the end of the for loop
    for ( var i: i32 = 0; i < 10; i++ ) { // i_1
      // Invalid, i_2 has the same end scope as i_1.
      var i: i32 = 1; // i_2.
    }
  }

  // Invalid, bar_5 has the same end scope as bar_2.
  var bar: u32; // bar_5

  // Valid, later_def, a module scope declaration, is in scope for the entire program.
  var early_use : i32 = later_def;
}

// Invalid, bar_6 has the same scope as bar_1.
var<private> bar: u32 = 1u; // bar_6

// Invalid, my_func_2 has the same end scope as my_func_1.
fn my_func() { } // my_func_2

// Valid, my_foo_1 is in scope for the entire program.
fn my_foo( //my_foo_1
  // Valid, my_foo_2 is in scope until the end of the function.
  my_foo: i32 // my_foo_2
) { }

var<private> later_def : i32 = 1;

EXAMPLE: Shadowing predeclared objects

// This declaration hides the predeclared 'min' built-in function.
// Since this declaration is at module-scope, it is in scope over the entire
// source. The built-in function is no longer accessible.
fn min() -> u32 { return 0; }

const rgba8unorm = 12; // This shadows the predeclared 'rgba8unorm' enumerant.

## 6. Types[](#types)

Programs calculate values.

In WGSL, a type is a set of values, and each value belongs to exactly one type. A value’s type determines the syntax and semantics of operations that can be performed on that value.

For example, the mathematical number 1 corresponds to these distinct values in WGSL:

*   the 32-bit signed integer value `1i`,

*   the 32-bit unsigned integer value `1u`,

*   the 32-bit floating point value `1.0f`,

*   the 16-bit floating point value `1.0h` if the [f16 extension](#extension-f16) is enabled,

*   the [AbstractInt](#abstractint) value 1, and

*   the [AbstractFloat](#abstractfloat) value 1.0

WGSL treats these as different because their machine representation and operations differ.

Some types are opaque, meaning their values have an implementation-defined representation that cannot be directly inspected, decomposed, or manipulated within a WGSL program.

A type is either [predeclared](#predeclared), or created in WGSL source via a [declaration](#declaration).

Some types are expressed as [template parameterizations](#template-parameterization). A type-generator is a [predeclared](#predeclared) object which, when parameterized with a [template list](#template-list), denotes a type. For example, the type `atomic<u32>` combines the type-generator `atomic` with template list `<u32>`.

We distinguish between the _concept_ of a type and the _syntax_ in WGSL to denote that type. In many cases the spelling of a type in this specification is the same as its WGSL syntax. For example:

*   the set of 32-bit unsigned integer values is spelled `u32` in this specification, and also in a WGSL module.

*   the spelling is different for structure types, or types containing structures.

Some WGSL types are only used for analyzing a source program and for determining the program’s runtime behavior. This specification will describe such types, but they do not appear in WGSL source text.

Note:[Reference types](#reference-type) are not written in WGSL modules. See [§ 6.5.3 Reference and Pointer Types](#ref-ptr-types).

Note:[Swizzle view types](#swizzle-view-type) are not written in WGSL modules. See [§ 6.5.4 Swizzle View Types](#swizzle-view-types).

### 6.1. Type Checking[](#type-checking-section)

A WGSL value is computed by evaluating an expression. An expression is a segment of source text parsed as one of the WGSL grammar rules whose name ends with "`expression`". An expression E can contain subexpressions which are expressions properly contained in the outer expression E. A top-level expression is an expression that is not itself a subexpression. See [§ 8.19 Expression Grammar Summary](#expression-grammar).

The particular value produced by an expression evaluation depends on:

*   static context: the source text surrounding the expression, and

*   dynamic context: the state of the invocation evaluating the expression, and the execution context in which the invocation is running.

The values that may result from evaluating a particular expression will always belong to a specific WGSL type, known as the static type of the expression. The rules of WGSL are designed so that the static type of an expression depends only on the expression’s [static context](#static-context).

A type assertion is a mapping from some WGSL source expression to a WGSL type. The notation

> _e_: _T_

is a type assertion meaning _T_ is the static type of WGSL expression _e_.

Note: A type assertion is a statement of fact about the text of a program. It is not a runtime check.

Statements often use expressions, and may place requirements on the static types of those expressions. For example:

*   The condition expression of an `if` statement [must](#shader-creation-error) be of type [bool](#bool).

*   In a `let` declaration with an explicit type specified, the initializer expression [must](#shader-creation-error) evaluate to that type.

Type checking a successfully parsed WGSL module is the process of mapping each expression to its static type, and verifying that type requirements of each statement are satisfied. If type checking fails, a special case of a [shader-creation error](#shader-creation-error), called a type error, results.

Type checking can be performed by recursively applying [type rules](#type-rule) to syntactic phrases, where a syntactic phrase is either an [expression](#expression) or a [statement](#statements). A type rule describes how the [static context](#static-context) for a [syntactic phrase](#syntactic-phrase) determines the static type for expressions contained within that phrase. A [type rule](#type-rule) has two parts:

*   A conclusion.

    *   If the phrase is an expression, the conclusion is a [type assertion](#type-assertion) for the expression.

    *   If the phrase is a statement, the conclusion is a set of [type assertions](#type-assertion), one for each of the statement’s [top-level expressions](#top-level-expression).

    *   In both cases, the [syntactic phrases](#syntactic-phrase) are specified schematically, using _italicized_ names to denote subexpressions or other syntactically-determined parameters.

*   Preconditions, consisting of:

    *   For expressions:

        *   Type assertions for subexpressions, when it has subexpressions. Each may be satisfied directly, or via a [feasible automatic conversion](#feasible-automatic-conversion) (as defined in [§ 6.1.2 Conversion Rank](#conversion-rank)). WGSL [will](#behavioral-requirements) evaluate all [const-expressions](#const-expressions) required to determine the [static types](#static-type) of a program.

        *   How the expression is used in a statement.

    *   For statements:

        *   The syntactic form of the statement, and

        *   Type assertions for [top-level expressions](#top-level-expression) in the statement.

    *   Conditions on the other schematic parameters, if any.

    *   Optionally, other static context.

Type rules may have type parameters in their preconditions and conclusions. When a type rule’s conclusion or preconditions contain type parameters, we say it is parameterized. When they do not, we say the rule is fully elaborated. We can make a fully elaborated type rule from a parameterized one by substituting a type for each of its type parameters, using the same type for all occurrences of a given parameter in the rule. An assignment of types to a rule’s type parameters is called a substitution.

For example, here is the type rule for [logical negation](#logical-expr) (an expression of the form `!`e):

| Precondition | Conclusion | e: T T is bool or vec N<bool> | `!`e`:`T | |
| --- | --- |

This is a parameterized rule, because it contains the type parameter T, which can represent any one of four types [bool](#bool), `vec2<bool>`, `vec3<bool>`, or `vec4<bool>`. Applying the substitution that maps T to `vec3<bool>` produces the fully elaborated type rule:

| Precondition | Conclusion | e`: vec3<bool>` | `!`e`: vec3<bool>` | |
| --- | --- |

Each fully elaborated rule we can produce from a parameterized rule by applying some substitution that meets the rule’s other conditions is called an overload of the parameterized rule. For example, the boolean negation rule has four overloads, because there are four possible ways to assign a type to its type parameter T.

Note: In other words, a parameterized type rule provides the pattern for a collection of fully elaborated type rules, each one produced by applying a different substitution to the parameterized rule.

A type rule applies to a syntactic phrase when:

*   The rule’s conclusion matches a valid parse of the [syntactic phrase](#syntactic-phrase), and

*   The rule’s preconditions are satisfied.

A [parameterized](#parameterized) type rule applies to an expression if there exists a [substitution](#substitution) producing a [fully elaborated](#fully-elaborated) type rule that applies to the expression.

Consider the expression, `1u+2u`. It has two [literal subexpressions](#literal-expressions): `1u` and `2u`, both of type u32. The [top-level expression](#top-level-expression) is an addition. Referring to the rules in [§ 8.8 Arithmetic Expressions](#arithmetic-expr), the type rule for addition applies to the expression, because:

*   `1u+2u` matches a parse of the form e1+e2, with e1 standing for `1u` and e2 standing for `2u`, and

*   e1 is of type u32, and

*   e2 is of type u32, and

*   we can substitute u32 for the type parameter T in the type rule, resulting in a [fully elaborated](#fully-elaborated) rule that applies to the entire expression.

When analyzing a [syntactic phrase](#syntactic-phrase), three cases may occur:

*   No type rules apply to the expression. This results in a [type error](#type-error).

*   Exactly one [fully elaborated](#fully-elaborated) type rule applies to the expression. In this case, the rule’s [conclusion](#type-rule-conclusion) is asserted, determining the static type for the expression.

*   More than one type rule applies. That is, the preconditions for more than one [overload](#overload) are satisfied. In this case the tie-breaking procedure described in [§ 6.1.3 Overload Resolution](#overload-resolution-section) is used.

    *   If overload resolution succeeds, a single [overload](#overload) is determined to apply to the expression. The [type assertions](#type-assertion) in the [conclusion](#type-rule-conclusion) for that overload are asserted, and therefore determine the types for the expression or expressions in the [syntactic phrase](#syntactic-phrase).

    *   If overload resolution fails, a [type error](#type-error) results.

Continuing the example above, only one type rule applies to the expression `1u+2u`, and so type checking accepts the conclusion of that type rule, which is that `1u+2u` is of type u32.

A WGSL source program is well-typed when:

*   The static type can be determined for each expression in the program by applying the type rules, and

*   The type requirements for each statement are satisfied.

Otherwise there is a [type error](#type-error) and the source program is not a valid WGSL module.

WGSL is a statically typed language because type checking a WGSL module [will](#behavioral-requirements) either succeed or discover a type error, while only having to inspect the program source text.

#### 6.1.1. Type Rule Tables[](#typing-tables-section)

The WGSL [type rules](#type-rule) for expressions are organized into type rule tables, with one row per type rule.

The semantics of an expression is the effect of evaluating that expression, and is primarily the production of a result value. The _Description_ column of the type rule that applies to an expression will specify the expression’s semantics. The semantics usually depends on the values of the type rule parameters, including the assumed values of any subexpressions. Sometimes the semantics of an expression includes effects other than producing a result value, such as the non-result-value effects of its subexpressions.

EXAMPLE: Side-effect of an expression

fn foo(p : ptr<function, i32>) -> i32 {
  let x = *p;
  *p += 1;
  return x;
}

fn bar() {
  var a: i32;
  let x = foo(&a); // the call to foo returns a value
                   // and updates the value of a
}

#### 6.1.2. Conversion Rank[](#conversion-rank)

When a type assertion e:T is used as a [type rule precondition](#type-rule-preconditions), it is satisfied when:

*   e is already of type T, or

*   e is of type S, and type S is [automatically convertible](#feasible-automatic-conversion) to type T, as defined below.

The rule is codified by the ConversionRank function over pairs of types, defined in the table below. The [ConversionRank](#conversionrank) function expresses the preference and feasibility of automatically converting a value of one type (_Src_) to another type (_Dest_). Lower ranks are more desirable.

A feasible automatic conversion converts a value from type _Src_ to type _Dest_, and is allowed when [ConversionRank](#conversionrank)(_Src_,_Dest_) is finite. Such conversions are value-preserving, subject to limitations described in [§ 15.7 Floating Point Evaluation](#floating-point-evaluation).

Note: Automatic conversions only occur in two kinds of situations. First, when converting a [const-expression](#const-expressions) to its corresponding typed numeric value that can be used on the GPU. Second, when a load from a reference-to-memory occurs, yielding the value stored in that memory.

Note: A conversion of infinite rank is infeasible, i.e. not allowed.

Note: When no conversion is performed, the conversion rank is zero.

 ConversionRank from one type to another 
| Src | Dest | ConversionRank(Src,Dest) | Description | T | T | 0 | Identity. No conversion performed. | | ref<AS,T,AM> for [address space](#address-spaces)AS, and where [access mode](#access-mode)AM is [read](#access-read) or [read_write](#access-read_write). | T | 0 | Apply the [Load Rule](#load-rule) to load a value from a memory reference. | | swizzle<AS,S,N,K> | vec K<S> | 0 | Apply the [Swizzle View Load Rule](#swizzle-view-load-rule) to load a vector value from a [swizzle view](#swizzle-view). | | [AbstractFloat](#abstractfloat) | f32 | 1 | See [§ 15.7.6 Floating Point Conversion](#floating-point-conversion) | | [AbstractFloat](#abstractfloat) | f16 | 2 | See [§ 15.7.6 Floating Point Conversion](#floating-point-conversion) | | [AbstractInt](#abstractint) | i32 | 3 | Identity if the value is in [i32](#i32). Produces a [shader-creation error](#shader-creation-error) otherwise. | | [AbstractInt](#abstractint) | u32 | 4 | Identity if the value is in [u32](#u32). Produces a [shader-creation error](#shader-creation-error) otherwise. | | [AbstractInt](#abstractint) | [AbstractFloat](#abstractfloat) | 5 | See [§ 15.7.6 Floating Point Conversion](#floating-point-conversion) | | [AbstractInt](#abstractint) | f32 | 6 | Behaves as [AbstractInt](#abstractint) to [AbstractFloat](#abstractfloat), and then [AbstractFloat](#abstractfloat) to f32 | | [AbstractInt](#abstractint) | f16 | 7 | Behaves as [AbstractInt](#abstractint) to [AbstractFloat](#abstractfloat), and then [AbstractFloat](#abstractfloat) to f16 | | vec N<S> | vec N<T> | ConversionRank(S,T) | Inherit conversion rank from component type. | | mat C x R<S> | mat C x R<T> | ConversionRank(S,T) | Inherit conversion rank from component type. | | array<S,N> | array<T,N> | ConversionRank(S,T) | Inherit conversion rank from component type. Note: Only [fixed-size arrays](#fixed-size-array) may have an [abstract](#type-abstract) component type. | | __frexp_result_abstract | __frexp_result_f32 | 1 | | | __frexp_result_abstract | __frexp_result_f16 | 2 | | | __frexp_result_vecN_abstract | __frexp_result_vecN_f32 | 1 | | | __frexp_result_vecN_abstract | __frexp_result_vecN_f16 | 2 | | | __modf_result_abstract | __modf_result_f32 | 1 | | | __modf_result_abstract | __modf_result_f16 | 2 | | | __modf_result_vecN_abstract | __modf_result_vecN_f32 | 1 | | | __modf_result_vecN_abstract | __modf_result_vecN_f16 | 2 | | | ptr<AS, buffer<N1>, AM> where Src is the type of an argument to a [function call](#function-call) | ptr<AS, buffer<N2>, AM> where N1 and N2 are both [const-expressions](#const-expressions) and Dest is the type of the [formal parameter](#formal-parameter) for the argument in Src | 1 if N2<N1, infinity otherwise | Convert a [fixed-size buffer](#fixed-size-buffer) pointer argument to a smaller sized pointer parameter.1 | | ptr<AS, buffer<N>, AM> where Src is the type of an argument to a [function call](#function-call) | ptr<AS, buffer, AM> where Dest is the type of the [formal parameter](#formal-parameter) for the argument in Src | 1 | Convert a [fixed-size buffer](#fixed-size-buffer) pointer argument to a [runtime-sized buffer](#runtime-sized-buffer) pointer parameter.1 | | S | T where above cases don’t apply | infinity | There are no automatic conversions between other types. | |
| --- | --- | --- | --- |

1.   These conversions require the [unrestricted_pointer_parameters](#language_extension-unrestricted_pointer_parameters) and [buffer_view](#language_extension-buffer_view) language features.

The type `T` is the concretization of type `S` if:

*   `T` is [concrete](#type-concrete), and

*   `T` is not a [reference type](#reference-type), and

*   `T` is not a [swizzle view type](#swizzle-view-type), and

*   ConversionRank(`S`, `T`) is finite, and

*   For any other type `T2` satisfying the above criteria, ConversionRank(`S`, `T2`) > ConversionRank(`S`, `T`).

The concretization of a value`e` of type `T` is the value resulting from applying, to `e`, the feasible conversion that maps `T` to the concretization of `T`.

Note: Conversion to [f32](#f32) is always preferred over [f16](#f16), therefore automatic conversion will only ever produce an [f16](#f16) value if the [f16 extension](#extension-f16) is enabled in the module.

#### 6.1.3. Overload Resolution[](#overload-resolution-section)

When more than one [type rule applies to a syntactic phrase](#type-rule-applies-to-a-syntactic-phrase), a tie-breaking procedure is used to determine which one should take effect. This procedure is called overload resolution, and assumes type checking has already succeeded in finding static types for [subexpressions](#subexpressions).

Consider a [syntactic phrase](#syntactic-phrase)P, and all [type rules that apply](#type-rule-applies-to-a-syntactic-phrase) to P. The overload resolution algorithm calls these type rules overload candidates. For each candidate:

*   Its preconditions have been met either directly or through [automatic conversion](#feasible-automatic-conversion).

*   Its [conclusion](#type-rule-conclusion) has:

    *   A syntactic form matching a valid parse of P, and

    *   A [type assertion](#type-assertion) corresponding to each [top-level expression](#top-level-expression) in P.

Overload resolution for P proceeds as follows, with the goal of finding a single most [preferable](#preferable-candidate)[overload candidate](#overload-candidates):

1.   For each candidate C, enumerate conversion ranks for subexpressions in the syntactic phrase. The candidate’s preconditions have been met, and so for the i’th subexpression in the P:

    *   Its static type has been computed.

    *   There is a [feasible automatic conversion](#feasible-automatic-conversion) from the expression’s static type to the type required by the corresponding type assertion in the preconditions. Let C.R(i) be the [ConversionRank](#conversionrank) of that conversion.

2.   Eliminate any candidate where one of its subexpressions resolves to an [abstract](#type-abstract) type after [feasible automatic conversions](#feasible-automatic-conversion), but another of the candidate’s subexpressions is not a [const-expression](#const-expressions).

Note: As a consequence, if any subexpression in the phrase is not a [const-expression](#const-expressions), then all subexpressions in the phrase must have a [concrete](#type-concrete) type.

3.   Rank candidates: Given two overload candidates C1 and C2, C1 is preferred over C2 if:

    *   For each expression position i in P, C1.R(i) ≤ C2.R(i).

        *   That is, each expression conversion required to apply C1 to P is at least as preferable as the corresponding expression conversion required to apply C2 to P.

    *   There is at least one expression position i where C1.R(i) <C2.R(i).

        *   That is, there is at least one expression conversion required to apply C1 that is strictly more preferable than the corresponding conversion required to apply C2.

4.   If there is a single candidate C which is [preferred](#preferable-candidate) over all the others, then overload resolution succeeds, yielding the candidate type rule C. Otherwise, overload resolution fails.

### 6.2. Plain Types[](#plain-types-section)

[Plain types](#plain-type) are types for the machine representation of boolean values, numbers, vectors, matrices, or aggregations of such values.

A plain type is either a [scalar](#scalar) type, an [atomic](#atomic-type) type, or a [composite](#composite) type.

Note: Plain types in WGSL are similar to Plain-Old-Data types in C++, but also include atomic types and abstract numeric types.

#### 6.2.1. Abstract Numeric Types[](#abstract-types)

These types cannot be spelled in WGSL source. They are only used by [type checking](#type-checking).

Certain expressions are evaluated at [shader-creation time](#shader-module-creation), and with a numeric range and precision that may be larger than directly implemented by the GPU.

WGSL defines two abstract numeric types for these evaluations:

*   The AbstractInt type is the set of integers representable in the 64-bit two’s complement format, with the sign bit in the most significant bit position.

*   The AbstractFloat type is the set of finite floating point numbers representable in the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary64](#ieee754-binary64) (double precision) format.

An evaluation of an expression in one of these types [must not](#shader-creation-error) overflow or produce an infinite or NaN value.

A type is abstract if it is an abstract numeric type or contains an abstract numeric type. A type is concrete if it is not abstract.

A [numeric literal](#numeric-literal) without a suffix denotes a value in an [abstract numeric type](#abstract-numeric-types):

*   An [integer literal](#integer-literal) without an `i` or `u` suffix denotes an [AbstractInt](#abstractint) value.

*   A [floating point literal](#floating-point-literal) without an `f` or `h` suffix denotes an [AbstractFloat](#abstractfloat) value.

Example: The expression `log2(32)` is analyzed as follows:

*   `log2(32)` is parsed as a function call to the `log2` builtin function with operand [AbstractInt](#abstractint) value 32.

*   There is no overload of `log2` with an [integer scalar](#integer-scalar) formal parameter.

*   Instead [overload resolution](#overload-resolution) applies, considering three possible overloads and [feasible automatic conversions](#feasible-automatic-conversion):

    *   [AbstractInt](#abstractint) to [AbstractFloat](#abstractfloat). (Conversion rank 4)

    *   [AbstractInt](#abstractint) to [f32](#f32). (Conversion rank 5)

    *   [AbstractInt](#abstractint) to [f16](#f16). (Conversion rank 6)

*   The resulting computation occurs as an [AbstractFloat](#abstractfloat) (e.g. `log2(32.0)`).

Example: The expression `1 + 2.5` is analyzed as follows:

*   `1 + 2.5` is parsed as an addition operation with subexpressions [AbstractInt](#abstractint) value 1, and [AbstractFloat](#abstractfloat) value 2.5.

*   There is no overload for e+f where e is integer type and f is floating point.

*   However, using feasible automatic conversions, there are three potential overloads:

    *   `1` is converted to [AbstractFloat](#abstractfloat) value `1.0` (rank 4) and `2.5` remains an [AbstractFloat](#abstractfloat) (rank 0).

    *   `1` is converted to [f32](#f32) value `1.0f` (rank 5) and `2.5` is converted to [f32](#f32) value `2.5f` (rank 1).

    *   `1` is converted to [f16](#f16) value `1.0f` (rank 6) and `2.5` is converted to [f16](#f16) value `2.5h` (rank 2).

*   The first overload is the [preferable candidate](#preferable-candidate) and type checking succeeds.

*   The resulting computation occurs as an [AbstractFloat](#abstractfloat)`1.0 + 2.5`.

Example: `let x = 1 + 2.5;`

*   This example is similar to the above, except that `x` cannot resolve to an [abstract numeric type](#abstract-numeric-types).

*   Therefore, there are two viable overload candidates: addition using [f32](#f32) or [f16](#f16).

*   The [preferable candidate](#preferable-candidate) uses [f32](#f32).

*   The effect of the declaration is as if it were written `let x : f32 = 1.0f + 2.5f;`.

Example: `1u + 2.5` results in a [shader-creation error](#shader-creation-error):

*   The `1u` term is an expression of type [u32](#u32).

*   The `2.5` term is an expression of type [AbstractFloat](#abstractfloat).

*   There are no valid overload candidates:

    *   There is no feasible automatic conversion from a GPU-materialized [integer scalar](#integer-scalar) type to a floating point type.

    *   No type rule matches _e_`+`_f_ with _e_ in an [integer scalar](#integer-scalar) type, and _f_ in a floating point type.

Example: `-1 * i32(-2147483648)` does not result in a [shader-creation error](#shader-creation-error):

*   The `-1` term is an expression of type [AbstractInt](#abstractint).

*   The `i32(-2147483648)` term is an expression of type [i32](#i32).

*   There is no overload of the multiply operator for these two types and the [i32](#i32) term cannot be up-converted to [AbstractInt](#abstractint).

*   The only feasible automatic conversion is converting the [AbstractInt](#abstractint) to [i32](#i32) so:

    *   The resulting computation is a multiplication operation between [i32](#i32).

    *   [i32](#i32) operations use two’s complement arithmetic and have defined overflow behavior.

    *   Wrapping occurs.

EXAMPLE: Type inference for literals

// Explicitly-typed unsigned integer literal.
var u32_1 = 1u; // variable holds a u32

// Explicitly-typed signed integer literal.
var i32_1 = 1i; // variable holds a i32

// Explicitly-typed floating point literal.
var f32_1 = 1f; // variable holds a f32

// Explicitly-typed unsigned integer literal cannot be negated.
var u32_neg = -1u; // invalid: unary minus does not support u32

// When a concrete type is required, but no part of the statement or
// expression forces a particular concrete type, an integer literal is
// interpreted as an i32 value:
// Initializer for a let-declaration must be constructible (or pointer).
// The most preferred automatic conversion from AbstractInt to a constructible type
// is AbstractInt to i32, with conversion rank 2. So '1' is inferred as i32.
let some_i32 = 1; // like let some_i32: i32 = 1i;

// Inferred from declaration type.
var i32_from_type : i32 = 1; // variable holds i32. AbstractInt to i32, conversion rank 2
var u32_from_type : u32 = 1; // variable holds u32. AbstractInt to u32, conversion rank 3

// Unsuffixed integer literal can convert to floating point when needed:
// Automatically convert AbstractInt to f32, with conversion rank 5.
var f32_promotion : f32 = 1; // variable holds f32

// Invalid: no feasible conversion from floating point to integer
var i32_demotion : i32 = 1.0; // Invalid

// Inferred from expression.
var u32_from_expr = 1 + u32_1; // variable holds u32
var i32_from_expr = 1 + i32_1; // variable holds i32

// Values must be representable.
let u32_too_large   : u32 = 1234567890123456890; // invalid, overflow
let i32_too_large   : i32 = 1234567890123456890; // invalid, overflow
let u32_large : u32 = 2147483649; // valid
let i32_large : i32 = 2147483649; // invalid, overflow
let f32_out_of_range1 = 0x1p500; // invalid, out of range
let f32_hex_lost_bits = 0x1.0000000001p0; // invalid, not exactly representable in f32

// Minimum integer: unary negation over AbstractInt, then infer i32.
// Most preferred conversion from AbstractInt to a constructible type (with lowest
// conversion rank) is AbstractInt to i32.
let i32_min = -2147483648;  // has type i32

// Invalid. Select AbstractInt to i32 as above, but the value is out of
// range, producing shader-creation error.
let i32_too_large_2 = 2147483648; // Invalid.

// Subexpressions can resolve to AbstractInt and AbstractFloat.
// The following examples are all valid and the value of the variable is 6u.
var u32_expr1 = (1 + (1 + (1 + (1 + 1)))) + 1u;
var u32_expr2 = 1u + (1 + (1 + (1 + (1 + 1))));
var u32_expr3 = (1 + (1 + (1 + (1u + 1)))) + 1;
var u32_expr4 = 1 + (1 + (1 + (1 + (1u + 1))));

// Inference based on built-in function parameters.

// Most-preferred candidate is clamp(i32,i32,i32)->i32
let i32_clamp = clamp(1, -5, 5);
// Most preferred candidate is clamp(u32,u32,u32).
// Literals use automatic conversion AbstractInt to u32.
let u32_clamp = clamp(5, 0, u32_from_expr);
// Most preferred candidate is clamp(f32,f32,f32)->f32
// literals use automatic conversion AbstractInt to f32.
let f32_clamp = clamp(0, f32_1, 1);

// The following examples all promote to f32 with an initial value of 10f.
let f32_promotion1 = 1.0 + 2 + 3 + 4;
let f32_promotion2 = 2 + 1.0 + 3 + 4;
let f32_promotion3 = 1f + ((2 + 3) + 4);
let f32_promotion4 = ((2 + (3 + 1f)) + 4);

// Type rule violations.

// Invalid, the initializer can only resolve to f32:
// No feasible automatic conversion from AbstractFloat to u32.
let mismatch : u32 = 1.0;

// Invalid. There is no overload of clamp that allows mixed sign parameters.
let ambiguous_clamp = clamp(1u, 0, 1i);

// Inference completes at the statement level.

// Initializer for a let-declaration must be constructible (or pointer).
// The most preferred automatic conversion from AbstractInt to a constructible type
// is AbstractInt to i32, with conversion rank 2. So '1' is inferred as i32.
let some_i32 = 1; // like let some_i32: i32 = 1i;

let some_f32 : f32 = some_i32; // Type error: i32 cannot be assigned to f32

// Another overflow case
let overflow_u32 = (1 -2) + 1u; // invalid, -1 is out of range of u32

// Ideal value out of range of 32-bits, but brought back into range
let out_and_in_again = (0x1ffffffff / 8);

// Similar, but invalid
let out_of_range = (0x1ffffffff / 8u); // requires computation is done in 32-bits,
                                       // making 0x1ffffffff out of range.

#### 6.2.2. Boolean Type[](#bool-type)

The bool type contains the values `true` and `false`.

Boolean literal type rules
| Precondition | Conclusion | Description | | `true`: bool | The true value. | | | `false`: bool | The false value. | |
| --- | --- | --- |

#### 6.2.3. Integer Types[](#integer-types)

The u32 type is the set of 32-bit unsigned integers.

The i32 type is the set of 32-bit signed integers. It uses the two’s complement representation, with the sign bit in the most significant bit position.

[Expressions](#arithmetic-expr) on [concrete](#type-concrete) integer types that overflow produce a result that is modulo 2 _bitwidth_

Extreme values for integer types
| Type | Lowest value | Highest value | i32 | i32(-2147483648) | 2147483647i | | i32(-0x80000000) | 0x7fffffffi | | u32 | 0u | 4294967295u | | 0x0u | 0xffffffffu | |
| --- | --- | --- |

Note:[AbstractInt](#abstractint) is also an integer type.

#### 6.2.4. Floating Point Types[](#floating-point-types)

The f32 type is the set of 32-bit floating point values of the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary32](#ieee754-binary32) (single precision) format. See [§ 15.7 Floating Point Evaluation](#floating-point-evaluation) for details.

The f16 type is the set of 16-bit floating point values of the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary16](#ieee754-binary16) (half precision) format. It is a [shader-creation error](#shader-creation-error) if the [f16](#f16) type is used unless the program contains the `enable f16;` directive to enable the [f16 extension](#extension-f16). See [§ 15.7 Floating Point Evaluation](#floating-point-evaluation) for details.

The following table lists certain extreme values for floating point types. Each has a corresponding negative value.

Extreme values for floating point types
| Type | Smallest positive [subnormal](#ieee754-subnormal) | Smallest positive [normal](#ieee754-normal) | Largest positive finite | Largest finite power of 2 | f32 | 1.40129846432481707092e-45f | 1.17549435082228750797e-38f | 3.40282346638528859812e+38f | 0x1p+127f | | 0x1p-149f | 0x1p-126f | 0x1.fffffep+127f | | f16 | 5.9604644775390625e-8h | 0.00006103515625h | 65504.0h | 0x1p+15h | | 0x1p-24h | 0x1p-14h | 0x1.ffcp+15h | |
| --- | --- | --- | --- | --- |

Note:[AbstractFloat](#abstractfloat) is also a floating point type.

#### 6.2.5. Scalar Types[](#scalar-types)

The scalar types are [bool](#bool), [AbstractInt](#abstractint), [AbstractFloat](#abstractfloat), [i32](#i32), [u32](#u32), [f32](#f32), and [f16](#f16).

The numeric scalar types are [AbstractInt](#abstractint), [AbstractFloat](#abstractfloat), [i32](#i32), [u32](#u32), [f32](#f32), and [f16](#f16).

The integer scalar types are [AbstractInt](#abstractint), [i32](#i32), and [u32](#u32).

A scalar conversion maps a value in one scalar type to a value in a different scalar type. Generally the result value is close to the original value, within the limitations of the destination type. Scalar conversions occur either:

*   By explicitly invoking a [value constructor](#value-constructor-builtin-function), or

*   When converting a [const-expression](#const-expressions) in an [abstract numeric type](#abstract-numeric-types) to another type, via a [feasible automatic conversion](#feasible-automatic-conversion).

#### 6.2.6. Vector Types[](#vector-types)

A vector is a grouped sequence of 2, 3, or 4 [scalar](#scalar) components.

| Type | Description | vec _N_<_T_> | Vector of _N_ components of type _T_. _N_ must be in {2, 3, 4} and _T_[must](#shader-creation-error) be one of the [scalar](#scalar) types. We say _T_ is the component type of the vector. | |
| --- | --- |

A vector is a numeric vector if its component type is a [numeric scalar](#numeric-scalar).

Key use cases of a vector include:

*   to express both a direction and a magnitude.

*   to express a position in space.

*   to express a color in some color space. For example, the components could be intensities of red, green, and blue, while the fourth component could be an alpha (opacity) value.

Many operations on vectors (and [matrices](#matrix)) act component-wise, i.e. the result is formed by operating on each scalar component independently.

EXAMPLE: Vector

vec2<f32>  // is a vector of two f32s.

EXAMPLE: Component-wise addition

let x : vec3<f32> = a + b; // a and b are vec3<f32>
// x[0] = a[0] + b[0]
// x[1] = a[1] + b[1]
// x[2] = a[2] + b[2]

WGSL also [predeclares](#predeclared) the following [type aliases](#type-alias):

| Predeclared alias | Original type | Restrictions | vec2i | vec2<i32> | | | vec3i | vec3<i32> | | | vec4i | vec4<i32> | | | vec2u | vec2<u32> | | | vec3u | vec3<u32> | | | vec4u | vec4<u32> | | | vec2f | vec2<f32> | | | vec3f | vec3<f32> | | | vec4f | vec4<f32> | | | vec2h | vec2<f16> | Requires the [f16 extension](#extension-f16). | | vec3h | vec3<f16> | | vec4h | vec4<f16> | |
| --- | --- | --- |

#### 6.2.7. Matrix Types[](#matrix-types)

A matrix is a grouped sequence of 2, 3, or 4 floating point vectors.

| Type | Description | mat C x R<T> | Matrix of C columns and R rows of type T, where C and R are both in {2, 3, 4}, and T must be [f32](#f32), [f16](#f16), or [AbstractFloat](#abstractfloat). Equivalently, it can be viewed as C column vectors of type vec R<_T_>. | |
| --- | --- |

The key use case for a matrix is to embody a linear transformation. In this interpretation, the vectors of a matrix are treated as column vectors.

The product operator (`*`) is used to either:

*   scale the transformation by a scalar magnitude.

*   apply the transformation to a vector.

*   combine the transformation with another matrix.

See [§ 8.8 Arithmetic Expressions](#arithmetic-expr).

EXAMPLE: Matrix

mat2x3<f32>  // This is a 2 column, 3 row matrix of 32-bit floats.
             // Equivalently, it is 2 column vectors of type vec3<f32>.

WGSL also [predeclares](#predeclared) the following [type aliases](#type-alias):

| Predeclared alias | Original type | Restrictions | mat2x2f | mat2x2<f32> | | | mat2x3f | mat2x3<f32> | | | mat2x4f | mat2x4<f32> | | | mat3x2f | mat3x2<f32> | | | mat3x3f | mat3x3<f32> | | | mat3x4f | mat3x4<f32> | | | mat4x2f | mat4x2<f32> | | | mat4x3f | mat4x3<f32> | | | mat4x4f | mat4x4<f32> | | | mat2x2h | mat2x2<f16> | Requires the [f16 extension](#extension-f16). | | mat2x3h | mat2x3<f16> | | mat2x4h | mat2x4<f16> | | mat3x2h | mat3x2<f16> | | mat3x3h | mat3x3<f16> | | mat3x4h | mat3x4<f16> | | mat4x2h | mat4x2<f16> | | mat4x3h | mat4x3<f16> | | mat4x4h | mat4x4<f16> | |
| --- | --- | --- |

#### 6.2.8. Atomic Types[](#atomic-types)

An atomic type encapsulates a [concrete](#type-concrete)[integer](https://www.w3.org/TR/css-values-4/#integer) type such that:

*   atomic objects provide [certain guarantees](#memory-model) to concurrent observers, and

*   the only valid operations on atomic objects are the [atomic builtin functions](#atomic-builtin-functions).

| Type | Description | atomic<T> | Atomic of type T. T[must](#shader-creation-error) be either [u32](#u32) or [i32](#i32). | | atomic<[vec2](#vector)<u32>> | Atomic of type `vec2`<`u32`>. A value of this type denotes an unsigned [64-bit integer](#64-bit-integer) type, with the 32 least significant bits in vector component 0, and the 32 most significant bits in vector component 1. Enabled by the [atomic_vec2u_min_max](#extension-atomic_vec2u_min_max) extension. | |
| --- | --- |

An expression [must not](#shader-creation-error) evaluate to an atomic type.

Atomic types may only be instantiated by variables in the [workgroup](#address-spaces-workgroup) address space or by [storage buffer](#storage-buffer) variables with a [read_write](#access-read_write) access mode. If the [store type](#store-type) is or contains `atomic<vec2<u32>>` then the variable [must](#shader-creation-error) be in the [storage](#address-spaces-storage)[address space](#address-spaces).

The [memory scope](#memory-scope) of operations on the type is determined by the [address space](#address-spaces) it is instantiated in. Atomic types in the [workgroup](#address-spaces-workgroup) address space have a [memory scope](#scoped-operations) of `Workgroup`, while those in the [storage](#address-spaces-storage) address space have a memory scope of `QueueFamily`.

An atomic modification is any [operation](#memory-operation) on an atomic object which sets the content of the object. The operation counts as a modification even if the new value is the same as the object’s existing value.

In WGSL, atomic modifications are mutually ordered, for each object. That is, during execution of a shader stage, for each atomic object _A_, all agents observe the same order of modification operations applied to _A_. The ordering for distinct atomic objects may not be related in any way; no causality is implied. Note that variables in [workgroup](#address-spaces-workgroup) space are shared within a [workgroup](#compute-shader-stage-workgroup), but are not shared between different workgroups.

#### 6.2.9. Array Types[](#array-types)

An array is an indexable sequence of element values.

| Type | Description | array<E,N> | A fixed-size array with N elements of type E. N is called the element count of the array. | | array<E> | A runtime-sized array of elements of type E. These may only appear in specific contexts. | |
| --- | --- |

The first element in an array is at index 0, and each successive element is at the next integer index. See [§ 8.5.3 Array Access Expression](#array-access-expr).

An expression [must not](#shader-creation-error) evaluate to a runtime-sized array type.

The element count expression N of a fixed-size array is subject to the following constraints:

*   It [must](#shader-creation-error) be an [override-expression](#override-expressions).

*   It [must](#shader-creation-error) evaluate to a [concrete](#type-concrete)[integer scalar](#integer-scalar).

*   If N is not greater than zero:

    *   It is a [shader-creation error](#shader-creation-error) if N is a [const-expression](#const-expressions).

    *   Otherwise, it is a [pipeline-creation error](#pipeline-creation-error).

Note: The element count value is fully determined at [pipeline creation](#pipeline-creation) time if N depends on any [override-declarations](#override-declaration), and [shader module creation](#shader-module-creation) otherwise.

Note: To qualify for type-equivalency, any override expression that is not a const expression must be an **identifier**. See [Workgroup variables sized by overridable constants](#example-workgroup-variables-sized-by-override)

The number of elements in a runtime-sized array is determined by the size of buffer binding associated with the corresponding [storage buffer](#storage-buffer) variable. See [§ 13.3.4 Buffer Binding Determines Runtime-Sized Array Element Count](#buffer-binding-determines-runtime-sized-array-element-count).

An array element type [must](#shader-creation-error) be one of:

*   a [scalar](#scalar) type

*   a [vector](#vector) type

*   a [matrix](#matrix) type

*   an [atomic](#atomic-type) type

*   an [array](#array) type having a [creation-fixed footprint](#creation-fixed-footprint)

*   a [structure](#structure) type having a [creation-fixed footprint](#creation-fixed-footprint).

Note: An array element type cannot be a [buffer](#buffer) type.

Note: The element type must be a [plain type](#plain-type).

Two array types are the same if and only if all of the following are true:

*   They have the same element type.

*   Their element count specifications match, i.e. one of the following is true:

    *   They are both runtime-sized.

    *   They are both fixed-sized with [creation-fixed footprint](#creation-fixed-footprint), and equal-valued element counts, even if one is signed and the other is unsigned. (Signed and unsigned values are comparable in this case because element counts are always positive.)

    *   They are both fixed-sized with element counts specified as identifiers [resolving](#resolves) to the same declaration of a [pipeline-overridable](#pipeline-overridable) constant.

EXAMPLE: Example fixed-size array types, non-overridable element count

// array<f32,8> and array<i32,8> are different types:
// different element types
var<private> a: array<f32,8>;
var<private> b: array<i32,8>;
var<private> c: array<i32,8u>;  // array<i32,8> and array<i32,8u> are the same type

const width = 8;
const height = 8;

// array<i32,8>, array<i32,8u>, and array<i32,width> are the same type.
// Their element counts evaluate to 8.
var<private> d: array<i32,width>;

// array<i32,height> and array<i32,width> are the same type.
var<private> e: array<i32,width>;
var<private> f: array<i32,height>;

Note: The only valid use of an array type sized by an overridable constant is as a [memory view](#memory-view) in the [workgroup](#address-spaces-workgroup) address space. This includes the [store type](#store-type) of a workgroup variable. See [§ 7 Variable and Value Declarations](#var-and-value).

EXAMPLE: Workgroup variables sized by overridable constants

override blockSize = 16;

var<workgroup> odds: array<i32,blockSize>;
var<workgroup> evens: array<i32,blockSize>; // Same type

// None of the following have the same type as 'odds' and 'evens'.

// Different type: Not the identifier 'blockSize'
var<workgroup> evens_0: array<i32,16>;
// Different type: Uses arithmetic to express the element count.
var<workgroup> evens_1: array<i32,(blockSize * 2 / 2)>;
// Different type: Uses parentheses, not just an identifier.
var<workgroup> evens_2: array<i32,(blockSize)>;

// An invalid example, because the overridable element count may only occur
// at the outer level.
// var<workgroup> both: array<array<i32,blockSize>,2>;

// An invalid example, because the overridable element count is only
// valid for workgroup variables.
// var<private> bad_address_space: array<i32,blockSize>;

#### 6.2.10. Structure Types[](#struct-types)

A structure is a named grouping of named member values.

| Type | Description | `struct`AStructName{ M 1 : T 1, ... M N : T N, } | A declaration of a structure type named by the [identifier](#identifier)AStructName and having N members, where member i is named by the identifier M i and is of the type T i. N[must](#shader-creation-error) be at least 1. Two members of the same structure type [must not](#shader-creation-error) have the same name. | |
| --- | --- |

Structure types are declared at [module scope](#module-scope). Elsewhere in the program source, a structure type is denoted by its identifier name. See [§ 5 Declaration and Scope](#declaration-and-scope).

Two structure types are the same if and only if they have the same name.

A structure member type [must](#shader-creation-error) be one of:

*   a [scalar](#scalar) type

*   a [vector](#vector) type

*   a [matrix](#matrix) type

*   an [atomic](#atomic-type) type

*   a [fixed-size array](#fixed-size-array) type with [creation-fixed footprint](#creation-fixed-footprint)

*   a [runtime-sized](#runtime-sized) array type, but only if it is the last member of the structure

*   a [structure](#structure) type that has a [creation-fixed footprint](#creation-fixed-footprint)

Note: A structure member type cannot be a [buffer](#buffer) type.

Note: All user-declared structure types are [concrete](#type-concrete).

Note: Each member type must be a [plain type](#plain-type).

Some consequences of the restrictions structure member and array element types are:

*   A pointer, texture, or sampler [must not](#shader-creation-error) appear in any level of nesting within an array or structure.

*   When a [runtime-sized](#runtime-sized) array is part of a larger type, it may only appear as the last element of a structure, which itself cannot be part of an enclosing array or structure.

EXAMPLE: Structure

// A structure with three members.
struct Data {
  a: i32,
  b: vec2<f32>,
  c: array<i32,10>, // last comma is optional
}

// Declare a variable storing a value of type Data.
var<private> some_data: Data;

struct_decl :

`'struct'`[ident](#syntax-ident)[struct_body_decl](#syntax-struct_body_decl)

struct_body_decl :

[`'{'`](#syntax_sym-brace_left)[struct_member](#syntax-struct_member) ( [`','`](#syntax_sym-comma)[struct_member](#syntax-struct_member) ) * [`','`](#syntax_sym-comma) ? [`'}'`](#syntax_sym-brace_right)

struct_member :

[attribute](#syntax-attribute) * [member_ident](#syntax-member_ident)[`':'`](#syntax_sym-colon)[type_specifier](#syntax-type_specifier)

The following attributes can be applied to structure members:

*   [align](#attribute-align)

*   [builtin](#attribute-builtin)

*   [location](#attribute-location)

*   [blend_src](#attribute-blend_src)

*   [interpolate](#attribute-interpolate)

*   [invariant](#attribute-invariant)

*   [size](#attribute-size)

Attributes [builtin](#attribute-builtin), [location](#attribute-location), [blend_src](#attribute-blend_src), [interpolate](#attribute-interpolate), and [invariant](#attribute-invariant) are [IO attributes](#io-attributes). An [IO attribute](#io-attributes) on a member of a structure _S_ has effect only when _S_ is used as the type of a [formal parameter](#formal-parameter) or [return type](#return-type) of an [entry point](#entry-point). See [§ 13.3.1 Inter-stage Input and Output Interface](#stage-inputs-outputs).

Attributes [align](#attribute-align) and [size](#attribute-size) are [layout attributes](#layout-attributes), and may be required if the structure type is used to define a [uniform buffer](#uniform-buffer) or a [storage buffer](#storage-buffer). See [§ 14.4 Memory Layout](#memory-layouts).

EXAMPLE: Structure declaration

struct my_struct {
  a: f32,
  b: vec4<f32>
}

EXAMPLE: Structure used to declare a buffer

// Runtime Array
alias RTArr = array<vec4<f32>>;
struct S {
  a: f32,
  b: f32,
  data: RTArr
}
@group(0) @binding(0) var<storage> buffer: S;

#### 6.2.11. Composite Types[](#composite-types)

A type is composite if it has internal structure expressed as a composition of other types. The internal parts do not overlap, and are called components. A composite value may be decomposed into its components. See [§ 8.5 Composite Value Decomposition Expressions](#composite-value-decomposition-expr).

The composite types are:

*   [vector](#vector) type

*   [matrix](#matrix) type

*   [array](#array) type

*   [structure](#structure) type

For a composite type T, the nesting depth of T, written _NestDepth_(T) is:

*   1 for a vector type

*   2 for a matrix type

*   1 + _NestDepth_(E) for an array type with element type E

*   1 + max(_NestDepth_(_M_ 1),..., _NestDepth_(_M_ N)) if T is a structure type with member types _M_ 1,...,_M_ N

#### 6.2.12. Constructible Types[](#constructible-types)

Many kinds of values can be created, loaded, stored, passed into functions, and returned from functions. We call these [constructible](#constructible).

A type is constructible if it is one of:

*   a [scalar](#scalar) type

*   a [vector](#vector) type

*   a [matrix](#matrix) type

*   a [fixed-size array](#fixed-size-array) type, if it has [creation-fixed footprint](#creation-fixed-footprint) and its element type is constructible.

*   a [structure](#structure) type, if all its members are constructible.

Note: All constructible types have a [creation-fixed footprint](#creation-fixed-footprint).

Note: Atomic types and runtime-sized array types are not constructible. Composite types containing atomics and runtime-sized arrays are not constructible.

#### 6.2.13. Fixed-Footprint Types[](#fixed-footprint-types)

The memory footprint of a variable is the number of [memory locations](#memory-locations) used to store the contents of the variable. The memory footprint of a variable depends on its [store type](#store-type) and becomes finalized at some point in the [shader lifecycle](#shader-lifecycle). Most variables are sized very early, at [shader creation](#shader-module-creation) time. Some variables may be sized later, at [pipeline creation](#pipeline-creation) time, and others as late as the [start of shader execution](#shader-execution-start).

A type has a creation-fixed footprint if its [concretization](#feasible-automatic-conversion) has a size that is fully determined at [shader creation](#shader-module-creation) time.

A type has a fixed footprint if its size is fully determined at [pipeline creation](#pipeline-creation) time.

Note: All [concrete](#type-concrete) creation-fixed footprint and fixed footprint types are [storable](#storable).

Note: Pipeline creation depends on shader creation, so a type with [creation-fixed footprint](#creation-fixed-footprint) also has [fixed footprint](#fixed-footprint).

The types with [creation-fixed footprint](#creation-fixed-footprint) are:

*   a [scalar](#scalar) type

*   a [vector](#vector) type

*   a [matrix](#matrix) type

*   an [atomic](#atomic-type) type

*   a [fixed-size array](#fixed-size-array) type, when:

    *   its [element count](#element-count) is a [const-expression](#const-expressions).

*   a [structure](#structure) type, if all its members have [creation-fixed footprint](#creation-fixed-footprint).

*   a [fixed-size buffer](#fixed-size-buffer) type, when:

    *   its size is a [const-expression](#const-expressions).

Note: A [constructible](#constructible) type has a [creation-fixed footprint](#creation-fixed-footprint).

The types with a [fixed footprint](#fixed-footprint) are any of:

*   a type with [creation-fixed footprint](#creation-fixed-footprint)

*   a [fixed-size array](#fixed-size-array) type (without further constraining its [element count](#element-count))

*   a [fixed-size buffer](#fixed-size-buffer) type (without further constraining its size)

Note: The only valid use of a fixed-size array with an element count that is an [override-expression](#override-expressions) that is not a [const-expression](#const-expressions) is as a [memory view](#memory-view) in the [workgroup](#address-spaces-workgroup) address space. This includes the [store type](#store-type) of a workgroup variable.

Note: A fixed-footprint type may contain an [atomic](#atomic-type) type, either directly or indirectly, while a [constructible](#constructible) type cannot.

Note: Fixed-footprint types exclude [runtime-sized](#runtime-sized) arrays, runtime-sized buffers, and any structure that contains a runtime-sized array.

### 6.3. Buffer Types[](#buffer-types)

These types require the [buffer_view](#language_extension-buffer_view) language feature.

A buffer value denotes memory whose contents can be interpreted as another [host-shareable](#host-shareable) type. Buffer values are otherwise [opaque](#opaque). They are useful when the data in a variable needs to be accessed as multiple different types or the shader author wishes to sub-divide one variable into multiple logical variables.

Buffer types are not [constructible](#constructible) and can only be accessed after interpreting their data as an non-opaque, [host-shareable](#host-shareable) type via the [buffer_view built-in functions](#buffer-view-builtin-functions).

| Type | Description | buffer<N> | A fixed-size buffer with N bytes of storage. N[must](#shader-creation-error) be an [override-expression](#override-expressions). | | buffer | A runtime-sized buffer. | |
| --- | --- |

An [expression](#expression)[must not](#shader-creation-error) evaluate to a buffer type.

Fixed-size buffers may only be instantiated by variables in the [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), and [workgroup](#address-spaces-workgroup) address spaces. In the storage and uniform address spaces, the size [must](#shader-creation-error) be a [const-expression](#const-expressions). Runtime-sized buffers can only be instantiated by variables in the storage address space.

If N is not greater than 0:

*   It is a [shader-creation error](#shader-creation-error) if N is a [const-expression](#const-expressions).

*   Otherwise, It is a [pipeline-creation error](#pipeline-creation-error).

If the [f16 extension](#extension-f16) is enabled and N is not evenly divisible by 2:

*   It is a [shader-creation error](#shader-creation-error) if N is a [const-expression](#const-expressions).

*   Otherwise, It is a [pipeline-creation error](#pipeline-creation-error).

If the [f16 extension](#extension-f16) is not enabled and N is not evenly divisible by 4:

*   It is a [shader-creation error](#shader-creation-error) if N is a [const-expression](#const-expressions).

*   Otherwise, It is a [pipeline-creation error](#pipeline-creation-error).

Two buffer types are the same if and only if any of the following conditions hold:

*   They are both runtime-sized.

*   They are both fixed-sized with a [creation-fixed footprint](#creation-fixed-footprint), and equal-valued sizes, even if one is signed and the other is unsigned. (Signed and unsigned values are comparable in this case because sizes are always positive.)

*   They are both fixed-sized with sizes specified as identifiers resolving to the same declaration of a [pipeline-overridable](#pipeline-overridable) constant.

### 6.4. Enumeration Types[](#enumeration-types)

An enumeration type is a limited set of named values. An enumeration is used to distinguish among the set of possibilities for a specific concept, such as the set of valid [texel formats](#texel-format).

An enumerant is one of the named values in an [enumeration](#enumeration). Each [enumerant](#enumerant) is distinct from all other enumerants, and distinct from all other kinds of values.

There is no mechanism for declaring new enumerants or new enumeration types in WGSL source.

Note: Enumerants are used as [template parameters](#template-parameters).

Note: There is no way to copy or to create an alternative name for an enumerant:

*   A [variable or value](#var-and-value) declaration cannot have an enumeration as its [store type](#store-type) or its [effective-value-type](#effective-value-type).

*   A function formal parameter cannot be an enumeration type, in part because enumerations are not [constructible](#constructible).

#### 6.4.1. Predeclared enumerants[](#predeclared-enumerants)

The following table lists the [enumeration](#enumeration) types in WGSL, their [predeclared](#predeclared)[enumerants](#enumerant) and the required [language extensions](#language-extension) for the [enumeration](#enumeration) types. The enumeration types exist, but cannot be spelled in WGSL source.

 Predeclared enumerants 
| Enumeration (Cannot be spelled in WGSL) | Predeclared enumerant | Required language extension | [access mode](#access-mode) | [read](#access-read) | | | [write](#access-write) | | [read_write](#access-read_write) | | [address space](#address-spaces) Note: The `handle` address space is never written in a WGSL source. | [function](#address-spaces-function) | | | [private](#address-spaces-private) | | [workgroup](#address-spaces-workgroup) | | [uniform](#address-spaces-uniform) | | [storage](#address-spaces-storage) | | [texel format](#texel-format) | [rgba8unorm](#texel-format-rgba8unorm) | | | [rgba8snorm](#texel-format-rgba8snorm) | | [rgba8uint](#texel-format-rgba8uint) | | [rgba8sint](#texel-format-rgba8sint) | | [rgba16unorm](#texel-format-rgba16unorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rgba16snorm](#texel-format-rgba16snorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rgba16uint](#texel-format-rgba16uint) | | | [rgba16sint](#texel-format-rgba16sint) | | [rgba16float](#texel-format-rgba16float) | | [rg8unorm](#texel-format-rg8unorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg8snorm](#texel-format-rg8snorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg8uint](#texel-format-rg8uint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg8sint](#texel-format-rg8sint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg16unorm](#texel-format-rg16unorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg16snorm](#texel-format-rg16snorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg16uint](#texel-format-rg16uint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg16sint](#texel-format-rg16sint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg16float](#texel-format-rg16float) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r32uint](#texel-format-r32uint) | | | [r32sint](#texel-format-r32sint) | | [r32float](#texel-format-r32float) | | [rg32uint](#texel-format-rg32uint) | | [rg32sint](#texel-format-rg32sint) | | [rg32float](#texel-format-rg32float) | | [rgba32uint](#texel-format-rgba32uint) | | [rgba32sint](#texel-format-rgba32sint) | | [rgba32float](#texel-format-rgba32float) | | [bgra8unorm](#texel-format-bgra8unorm) | | [r8unorm](#texel-format-r8unorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r8snorm](#texel-format-r8snorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r8uint](#texel-format-r8uint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r8sint](#texel-format-r8sint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r16unorm](#texel-format-r16unorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r16snorm](#texel-format-r16snorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r16uint](#texel-format-r16uint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r16sint](#texel-format-r16sint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [r16float](#texel-format-r16float) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rgb10a2unorm](#texel-format-rgb10a2unorm) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rgb10a2uint](#texel-format-rgb10a2uint) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | [rg11b10ufloat](#texel-format-rg11b10ufloat) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | |
| --- | --- | --- |

### 6.5. Memory Views[](#memory-views)

In addition to calculating with [plain](#plain-type) values, a WGSL program will also often read values from [memory](#memory) or write values to memory, via [memory access](#memory-access) operations. Each memory access is performed via a [memory view](#memory-view).

A memory view comprises:

*   a set of [memory locations](#memory-locations) in a particular [address space](#address-spaces),

*   a [memory model reference](#memory-model-reference),

*   an interpretation of the contents of those locations as a WGSL [type](#type), known as the store type, and

*   an [access mode](#access-mode).

The access mode of a memory view [must](#shader-creation-error) be supported by the address space. See [§ 7 Variable and Value Declarations](#var-and-value).

#### 6.5.1. Storable Types[](#storable-types)

The value contained in a [variable](#variable)[must](#shader-creation-error) be of a [storable](#storable) type. A storable type may have an explicit representation defined by WGSL, as described in [§ 14.4.4 Internal Layout of Values](#internal-value-layout), or it may be [opaque](#opaque), such as for [textures](#texture-resource) and [samplers](#sampler-resource).

A type is storable if it is both [concrete](#type-concrete) and one of:

*   a [scalar](#scalar) type

*   a [vector](#vector) type

*   a [matrix](#matrix) type

*   an [atomic](#atomic-type) type

*   an [array](#array) type

*   a [structure](#structure) type

*   a [texture](#texture) type

*   a [sampler](#sampler) type

*   a [buffer](#buffer) type

Note: That is, the storable types are the [concrete](#type-concrete)[plain types](#plain-type), texture types, sampler types, and buffer types.

#### 6.5.2. Host-shareable Types[](#host-shareable-types)

Host-shareable types are used to describe the contents of buffers which are shared between the host and the GPU, or copied between host and GPU without format translation. When used for this purpose, the type may additionally have [layout attributes](#layout-attributes) applied as described in [§ 14.4 Memory Layout](#memory-layouts). As described in [§ 7.3 var Declarations](#var-decls), the [store type](#store-type) of [uniform buffer](#uniform-buffer) and [storage buffer](#storage-buffer) variables [must](#shader-creation-error) be host-shareable.

A type is host-shareable if it is both [concrete](#type-concrete) and one of:

*   a [numeric scalar](#numeric-scalar) type

*   a [numeric vector](#numeric-vector) type

*   a [matrix](#matrix) type

*   an [atomic](#atomic-type) type

*   a [fixed-size array](#fixed-size-array) type, if it has [creation-fixed footprint](#creation-fixed-footprint) and its element type is host-shareable

*   a [runtime-sized](#runtime-sized) array type, if its element type is host-shareable

*   a [structure](#structure) type, if all its members are host-shareable

*   a [buffer](#buffer) type

Note: Restrictions on the types of inter-stage inputs and outputs are described in [§ 13.3.1 Inter-stage Input and Output Interface](#stage-inputs-outputs) and subsequent sections. Those types are also sized, but the counting differs.

Note:[Textures and samplers](#texture-sampler-types) can also be shared between the host and the GPU, but their contents are [opaque](#opaque). The host-shareable types in this section are specifically for use in [storage](#storage-buffer) and [uniform](#uniform-buffer) buffers.

#### 6.5.3. Reference and Pointer Types[](#ref-ptr-types)

WGSL has two kinds of types for representing [memory views](#memory-view): [reference types](#reference-type) and [pointer types](#pointer-type).

| Constraint | Type | Description | AS is an [address space](#address-spaces), T is a [storable](#storable) type, AM is an [access mode](#access-mode) | ref<AS,T,AM> | The reference type identified with the set of [memory views](#memory-view) for memory locations in AS holding values of type T, supporting memory accesses described by mode AM. Here, T is the [store type](#store-type). Reference types are not written in WGSL source; instead they are used to analyze a WGSL module. | | AS is an [address space](#address-spaces), T is a [storable](#storable) type, AM is an [access mode](#access-mode) | ptr<AS,T,AM> | The pointer type identified with the set of [memory views](#memory-view) for memory locations in AS holding values of type T, supporting memory accesses described by mode AM. Here, T is the [store type](#store-type). Pointer types may appear in WGSL source. | |
| --- | --- | --- |

Two pointer types are the same if and only if they have the same address space, store type, and access mode.

When _analyzing_ a WGSL module, reference and pointer types are fully parameterized by an address space, a storable type, and an access mode. In code examples in this specification, the comments show this fully parameterized form.

However, in WGSL _source_ text:

*   Reference types [must not](#shader-creation-error) appear.

*   Pointer types may appear.

    *   A pointer type is spelled with parameterization by:

        *   [address space](#address-spaces),

        *   [store type](#store-type), and

        *   sometimes by [access mode](#access-mode), as specified in [§ 14.3 Address Spaces](#address-space).

    *   If a pointer type appears in the program source, it [must](#shader-creation-error) also be valid to [declare a variable](#variable-declaration) or return that type from a [function call](#function-call), somewhere in the program, with the pointer type’s [address space](#address-spaces), [store type](#store-type), and [access mode](#access-mode).

Note: This restriction forbids the declaration of certain [type aliases](#type-alias) and function [formal parameters](#formal-parameter) that can never be used at runtime. Without the restriction, it would be valid to declare an alias to a pointer type, but never be able to create a pointer value of that type. Similarly, it would be valid to declare a function with a pointer formal parameter, but never be able to call that function.

EXAMPLE: Pointer type

fn my_function(
  /* 'ptr<function,i32,read_write>' is the type of a pointer value that references
 memory for keeping an 'i32' value, using memory locations in the 'function'
 address space. Here 'i32' is the store type.
 The implied access mode is 'read_write'.
 See "Address Space" section for defaults. */
  ptr_int: ptr<function,i32>,

  // 'ptr<private,array<f32,50>,read_write>' is the type of a pointer value that
  // refers to memory for keeping an array of 50 elements of type 'f32', using
  // memory locations in the 'private' address space.
  // Here the store type is 'array<f32,50>'.
  // The implied access mode is 'read_write'.
  // See the "Address space section for defaults.
  ptr_array: ptr<private, array<f32, 50>>
) { }

Reference types and pointer types are both sets of memory views: a particular memory view is associated with a unique reference value and also a unique pointer value:

> Each pointer value pof type ptr<AS,T,AM>corresponds to a unique reference value rof type ref<AS,T,AM>, and vice versa, where pand rdescribe the same memory view.

#### 6.5.4. Swizzle View Types[](#swizzle-view-types)

[Swizzle views](#swizzle-view) can be used to access a subset of the components of a vector in memory, permuting them when reading, and scattering them when writing.

Swizzle views are enabled by the [swizzle_assignment](#language_extension-swizzle_assignment) language extension.

A swizzle view is a pair (p,IndexList) where:

*   p is a pointer to a vector of type vec N<S>, with [read_write](#access-read_write) access mode.

*   IndexList = «Idx 0, ..., Idx K−1 », a sequence of indices where:

    *   Each Idx i is in [0,N−1].

    *   vec K<S> is a valid [vector](#vector) type. That is, K is in {2,3,4}.

> **Algorithm:**SwizzleViewRead
> 
> 
> Yield a vector formed by selecting and optionally permuting the components of a vector read via pointer p.
> 
> 
> Note: Reading via a swizzle view reads the entire vector from memory, even if some vector components do not appear in the result.
> 
> 
> **Input**: [Swizzle view](#swizzle-view) (p, IndexList) of type swizzle<AS,S,N,K>
> 
> 
> **Output**: Vector value v of type vec K<S>, the result of reading (p, IndexList).
> 
> 
> **Procedure:**
> 
> 
> 1.   By convention IndexList = «Idx 0,...,Idx K−1»
> 
> 2.   Read vector u from memory referenced by p. u has type vec N<S>.
> 
> 3.   Form value v of type vec K<S> where:
> 
> 
>     *   Component i of v equals the value of component Idx i of u. Using [indexing syntax](#vector-single-component): v[i] = u[Idx i]

> **Algorithm:**SwizzleViewWrite
> 
> 
> Write components of an update vector into specified components of the vector in memory referenced by pointer p.
> 
> 
> 
> Note: Writing via a swizzle view writes the entire vector in memory, even if component values are unchanged by the process.
> 
> 
> See below for a discussion of how swizzle view writes interact with uniformity analysis and the memory model.
> 
> 
> **Input**:
> 
> 
> *   [Swizzle view](#swizzle-view) (p, IndexList) of type swizzle<AS,S,N,K>
> 
> *   Vector old_contents of type vec N<S>
> 
> 
>     *   old_contents is intended to be the vector stored in the memory referenced by p at some point in the past.
> 
> 
> *   Vector update of type vec K<S>
> 
> 
> 
> All indices in IndexList[must](#shader-creation-error) be distinct from each other. This requirement implies K ≤ N.
> 
> 
> **Variables:**
> 
> 
> *   new of type vec N<S>
> 
> 
> 
> **Procedure:**
> 
> 
> 1.   By convention IndexList = «Idx 0,...,Idx K−1»
> 
> 2.   Initialize variable new to old_contents.
> 
> 3.   For each i in 0..K-1:
> 
> 
>     *   Set component Idx i of new to the value of component i of update. Using [indexing syntax](#vector-single-component): new[Idx i] = update[i].
> 
> 
> 4.   Write new to the memory referenced by p.
> 
> 
> 
> Note: Requiring Idx i to all be distinct guarantees that Step 3 updates each component of new at most once.
> 
> 
> 
> Note: Steps 2 and 3 can be replaced with the following declarative rule:
> 
> 
> Form new, a vector of type vec N<S>, where component i of new is:
> 
> 
> *   Component j of update, if i = Idx j for some j in 0...K−1.
> 
> *   Component i of old_contents, otherwise.

Swizzle views have swizzle view types:

| Constraint | Type | Description | S is a [concrete](#type-concrete)[scalar](#scalar) type, N and K are integers such that both vec N<S> and vec K<S> are valid [vector](#vector) types. ptr<AS,vec N<S>,[read_write](#access-read_write)> is a valid pointer type. | swizzle<AS,S,N,K> | The swizzle view type identified with the set of [swizzle views](#swizzle-view) (p, IndexList) where: * p is of type ptr<AS,vec N<S>,read_write> * IndexList = «Idx 0,...,Idx K−1» * (p,IndexList) supports a [swizzle view read](#swizzle-view-read) operation, yielding a vector of type vec K<S>. * (p,IndexList) supports a [swizzle view write](#swizzle-view-write) operation that writes a vector of type vec K<S>. Swizzle view types are not written in WGSL source; instead they are used to analyze a WGSL module. | |
| --- | --- | --- |

A [swizzle view](#swizzle-view) is formed by:

*   Applying a multi-letter [swizzle](#swizzle) name to a reference or pointer value with [read_write](#access-read_write) access mode and whose store type is a vector, or

*   Applying a multi-letter [swizzle](#swizzle) name to a swizzle view.

By these rules, the IndexList part of a swizzle view is fully determined at [shader creation](#shader-module-creation) time.

See [§ 8.6 Swizzle View Expression](#swizzle-view-expr) for details.

EXAMPLE: Reading and writing via swizzle views on references

fn swizzle_read_and_write() {
  var v: vec4u;

  // Same as: v.y = 1; v.z = 2;
  // However, the vector is read from memory and written to memory exactly once.
  v.yz = vec2u(1,2);

  // Same as: let u = vec3(v.a, v.g, v.b);
  // Expression v.agb is a swizzle view of type swizzle<function,u32,4,3>.
  // The effective-value-type of a let declaration must be concrete constructible
  // or a pointer type. So the swizzle view is automatically converted to vec3u
  // by invoking the Swizzle View Load Rule.
  let u = v.agb;

  // Swizzles can be chained.
  // Same as: v.zy = vec2(99,100);
  v.yz.yx = vec2(99,100);

  // Applying a single letter on a swizzle view yields a reference
  // to a scalar component of the underlying vector.
  // Same as: v.z = 99;
  v.yz.y = 99;

  // Indexing a swizzle view yields a reference to one of the vector's
  // components. It acts as if forming a single-letter vector access,
  // but the index chooses which letter to use from the swizzle name.
  v.zy[1] = 50; // Same as v.y = 50;
}

EXAMPLE: Reading and writing via swizzle views on pointers

// This example assumes support for pointer_composite_access in addition to
// swizzle_assignment.
requires pointer_composite_access;

fn swizzle_read_and_write_via_pointer(p: ptr<function,vec4u>) {
  // Same as: (*p).y = 1; (*p).z = 2;
  p.yz = vec2u(1,2);

  // Same as: let u = vec3((*p).a, (*p).g, (*p).b);
  let u = p.agb;

  // Swizzles can be chained.
  // Same as: p.zy = vec2(99,100);
  p.yz.yx = vec2(99,100);

  // A swizzle view can be constructed from a pointer.
  // Applying a single letter to a swizzle view yields a reference
  // to a scalar component of the underlying vector.
  // Same as: (*p).z = 99;
  p.yz.y = 99;

  // Indexing a swizzle view yields a reference to one of the vector's
  // components. It acts as if forming a single-letter vector access,
  // but the index chooses which letter to use from the swizzle name.
  p.zy[1] = 50; // Same as (*p).y = 50;
}

EXAMPLE: Invalid swizzle views

fn invalid_swizzle_cases() {
  var v: vec2u;

  // Invalid: cannot assign to swizzles that repeat components
  v.xx = vec2u(1,2);

  // Invalid: 'z' is out of bounds for the target vector.
  v.xz = vec2u(1,2);
  let u = v.xz;

  // Invalid: Must not mix letter schemes xyzw vs. rgba
  v.xr = vec2u(1,2);

  // It is not possible to take the address of a swizzle view.
  // Here, v.xy is a swizzle view (&v,`01`)
  // The & operator does not apply to swizzle views, so type checking fails.
  let p = &v.xy;
}

For the purposes of uniformity analysis, a [swizzle view write](#swizzle-view-write) may only affect the value uniformity of the updated components. This motivates the distinction between [full swizzle views](#full-swizzle-view) and [partial swizzle views](#partial-swizzle-view).

However, writing all components of the underlying vector is significant for the memory model. Two different invocations that concurrently update different components of the same vector in memory will induce a data race.

EXAMPLE: Swizzle writes to different vector components may race

var<workgroup> w: vec4u;

@compute @workgroup_size(2)
fn this_races(@builtin(local_invocation_index) gid: u32) {
  if (gid == 0) {
    w.xy = vec2u(0,1);  // Writes the whole vector, races with other invocation.
  } else {
    w.zw = vec2u(2,3);  // Writes the whole vector, races with other invocation.
  }
}

#### 6.5.5. Valid and Invalid Memory References[](#valid-invalid-memory-references)

A [reference](#reference-type) value is either [valid](#valid-reference) or [invalid](#invalid-memory-reference).

References are formed as described in detail in [§ 6.5.9 Forming Reference and Pointer Values](#forming-references-and-pointers). Generally, a valid reference is formed by:

*   naming a variable, or

*   applying the [indirection](#indirection) (unary `*`) operation to a [valid pointer](#valid-pointer), or

*   a [named component expression](#named-component-expression) where the [base](#decomposition-base) is a valid [memory view](#memory-view), or

*   an [indexing expression](#indexing-expression) where the [base](#decomposition-base) is a valid [memory view](#memory-view), and using an [in-bounds index](#in-bounds-index).

Generally, an invalid memory reference is formed by:

*   applying the indirection operator to an [invalid pointer](#invalid-pointer), or

*   a [named component expression](#named-component-expression) where the [base](#decomposition-base) is an invalid memory reference, or

*   an [indexing expression](#indexing-expression) where the base is a [memory view](#memory-view), and either:

    *   the [base](#decomposition-base) is an invalid memory reference, or

    *   the index is [out-of-bounds](#out-of-bounds-index).

An invalid pointer is formed by:

*   applying the [address-of](#address-of) operator (unary `&`) to an [invalid memory reference](#invalid-memory-reference), or

*   calling a [bufferView](#bufferview-builtin) or [bufferArrayView](#bufferarrayview-builtin) built-in function when the [memory view](#memory-view) of the resulting pointer would otherwise include [memory locations](#memory-locations)[outside the bounds](#out-of-bounds-access) of the memory view of buffer pointer argument.

A valid pointer is a pointer that corresponds to a [valid reference](#valid-reference).

A valid swizzle view is a [swizzle view](#swizzle-view) whose pointer value is [valid](#valid-pointer). An invalid swizzle view is a [swizzle view](#swizzle-view) whose pointer value is [invalid](#invalid-pointer).

#### 6.5.6. Originating Variable[](#originating-variable-section)

The originating variable for a reference value R is defined as follows:

*   It is the variable, when R is a variable.

*   It is the originating variable of the pointer value P, when R is the application of the indirection operator (unary *) on P.

*   It is the originating variable of the [base](#decomposition-base), when R is a [named component expression](#named-component-expression) or an [indexing expression](#indexing-expression).

The [originating variable](#originating-variable) of a pointer value is defined as the originating variable of the corresponding reference value.

The [originating variable](#originating-variable) of a [swizzle view](#swizzle-view) is defined as the originating variable of the swizzle view’s pointer.

Note: The originating variable is a dynamic concept. The originating variable for a formal parameter of a function depends on the [call sites](#call-site) for the function. Different call sites may supply pointers into different originating variables.

A [valid reference](#valid-reference) always corresponds to a non-empty memory view for some or all of the memory locations for some variable.

A [valid swizzle view](#valid-swizzle-view) always corresponds to the memory locations of a vector inside some variable.

Note: A reference can correspond to memory locations inside a variable, and still be invalid. This can occur when an index is too large for the type being indexed, but the referenced locations would be inside a subsequent sibling data member.

In the following example, the reference `the_particle.position[i]` is valid if and only if `i` is 0 or 1. When `i` is 2, the reference will be an [invalid memory reference](#invalid-memory-reference), but would otherwise correspond the memory locations for `the_particle.color_index`.

EXAMPLE: Invalid memory reference still inside a variable

struct Particle {
   position: vec2f,
   velocity: vec2f,
   color_index: i32,
}

@group(0) @binding(0)
var<storage,read_write> the_particle: Particle;

fn particle_velocity_component(p: Particle, i: i32) -> f32 {
  return the_particle.velocity[i]; // A valid reference when i is 0 or 1.
}

#### 6.5.7. Out-of-Bounds Access[](#out-of-bounds-access-sec)

An operation that [accesses](#memory-access) an [invalid memory reference](#invalid-memory-reference) or an [invalid swizzle view](#invalid-swizzle-view) is an out-of-bounds access.

An out-of-bounds access is a program defect, because if it _were_ performed as written, it would typically:

*   read or write [memory locations](#memory-locations) outside of a variable, or

*   interpret the contents of those locations as the wrong [store type](#store-type), or

*   cause an unintended data race.

For this reason, an implementation [will not](#behavioral-requirements) perform the access as written. Executing an [out-of-bounds access](#out-of-bounds-access) generates a [dynamic error](#dynamic-error).

Note: An example of interpreting the store type incorrectly occurs in [the example from the previous section](#example-invalid-ref). When `i` is 2, the expression `the_particle.velocity[i]` has type `ref<storage,f32,read_write>`, meaning it is a memory view with [f32](#f32) as its [store type](#store-type). However, the memory locations are allocated to the `color_index` member, so the stored value is actually of type [i32](#i32).

Note:An out-of-bounds access causes a dynamic error, which allows for many possible outcomes.

Those outcomes include, but are not limited to, the following:

Trap
The shader invocation immediately terminates, and [shader stage outputs](#shader-stage-output) are set to zero values.

Invalid Load
[Loads](#load-rule) from an invalid reference may return one of:

*   when the [originating variable](#originating-variable) is a [uniform buffer](#uniform-buffer) or a [storage buffer](#storage-buffer), the value from any [memory location(s)](#memory-locations) of the WebGPU `GPUBuffer` bound to the originating variable

*   when the originating variable is not a [uniform buffer](#uniform-buffer) or [storage buffer](#storage-buffer), a value from any [memory location(s)](#memory-locations) in the originating variable

*   the [zero value](#zero-value) for store type of the reference

*   if the loaded value is a vector, the value (0, 0, 0, x), where x is:

    *   0, 1, or the maximum positive value for integer components

    *   0.0 or 1.0 for floating-point components

Invalid Store
[Stores](#statement-assignment) to an invalid reference may do one of:

*   when the [originating variable](#originating-variable) is a [storage buffer](#storage-buffer), store the value to any [memory location(s)](#memory-locations) of the WebGPU `GPUBuffer` bound to the [originating variable](#originating-variable)

*   when the [originating variable](#originating-variable) is not a [storage buffer](#storage-buffer), store the value to any [memory locations(s)](#memory-locations) in the originating variable

*   not be executed.

A data race may occur if an invalid load or store is redirected to access different locations inside a variable in a shared address space. For example, the accesses of several concurrently executing invocations may be redirected to the first element in an array. If at least one access is a write, and they are not otherwise synchronized, then the result is a data race, and hence a dynamic error.

An out-of-bounds access invalidates the assumptions of [uniformity analysis](#uniformity). For example, if an invocation terminates early due to an out-of-bounds access, then it can no longer particpate in collective operations. In particular, a call to [workgroupBarrier](#sync-builtin-functions) may hang the shader, and derivatives may yield invalid results.

#### 6.5.8. Use Cases for References and Pointers[](#ref-ptr-use-cases)

References and pointers are distinguished by how they are used:

*   The type of a [variable](#variable) is a reference type.

*   The [address-of](#address-of) operation (unary `&`) converts a reference value to its corresponding pointer value.

*   The [indirection](#indirection) operation (unary `*`) converts a pointer value to its corresponding reference value.

*   A [let-declaration](#let-declaration) can be of pointer type, but not of reference type.

*   A [formal parameter](#formal-parameter) can be of pointer type, but not of reference type.

*   A [simple assignment](#simple-assignment) statement performs a [write access](#write-access) to update the contents of memory via a reference, where:

    *   The [left-hand side](#left-hand-side) of the simple assignment statement [must](#shader-creation-error) be of reference type, with access mode [write](#access-write) or [read_write](#access-read_write).

    *   The [right-hand side](#right-hand-side) of the simple assignment statement [must](#shader-creation-error) evaluate to the store type of the left-hand side.

*   A [swizzle view](#swizzle-view) can be formed by applying a multi-letter [swizzle](#swizzle) name to a reference or pointer value with [read_write](#access-read_write) access mode and whose [store type](#store-type) is a vector.

*   A [swizzle assignment](#swizzle-assignment) statement updates two or more components of a vector in memory via a [swizzle view](#swizzle-view).

    *   A swizzle view is created from a pointer or reference, as above, or from another swizzle view. See [§ 8.6 Swizzle View Expression](#swizzle-view-expr).

*   The Load Rule: Inside a function, a reference is automatically dereferenced (read from) to satisfy type rules:

    *   In a function, when a reference expression r with store type T is used in a statement or an expression, where:

        *   r has an access mode of [read](#access-read) or [read_write](#access-read_write), and

        *   The only potentially matching type rules require r to have a value of type T,

    *   Then that type rule requirement is considered to have been met, and

    *   The result of evaluating r in that context is the value (of type T) stored in the memory locations referenced by r at the time of evaluation. That is, a [read access](#read-access) is performed to produce the result value.

*   Similarly there is a Swizzle View Load Rule: Inside a function, a [swizzle view read](#swizzle-view-read) is performed to satisfy type rules:

    *   In a function, when a [swizzle view](#swizzle-view)sv is used in a statement or an expression, where:

        *   sv is (p, IndexList) and of type swizzle<AS,S,N,K>, and

        *   The only potentially matching type rules require sv to have a value of type vec K<S>,

    *   Then that type rule requirement is considered to have been met, and

    *   The result of evaluating sv in that context is the result of performing a [swizzle view read](#swizzle-view-read) on sv at that time.

        *   The result value has type vec K<S>.

        *   This operation performs one [read access](#read-access) of the whole vector referenced by p.

Defining references in this way enables simple idiomatic use of variables:

EXAMPLE: Reference types enable simple use of variables

@compute @workgroup_size(1)
fn main() {
  // 'i' has reference type ref<function,i32,read_write>
  // The memory locations for 'i' store the i32 value 0.
  var i: i32 = 0;

  // 'i + 1' can only match a type rule where the 'i' subexpression is of type i32.
  // So the expression 'i + 1' has type i32, and at evaluation, the 'i' subexpression
  // evaluates to the i32 value stored in the memory locations for 'i' at the time
  // of evaluation.
  let one: i32 = i + 1;

  // Update the value in the locations referenced by 'i' so they hold the value 2.
  i = one + 1;

  // Update the value in the locations referenced by 'i' so they hold the value 5.
  // The evaluation of the right-hand-side occurs before the assignment takes effect.
  i = i + 3;
}

EXAMPLE: Returning a reference returns the value loaded via the reference

var<private> age: i32;
fn get_age() -> i32 {
  // The type of the expression in the return statement must be 'i32' since it
  // must match the declared return type of the function.
  // The 'age' expression is of type ref<private,i32,read_write>.
  // Apply the Load Rule, since the store type of the reference matches the
  // required type of the expression, and no other type rule applies.
  // The evaluation of 'age' in this context is the i32 value loaded from the
  // memory locations referenced by 'age' at the time the return statement is
  // executed.
  return age;
}

fn caller() {
  age = 21;
  // The copy_age constant will get the i32 value 21.
  let copy_age: i32 = get_age();
}

Defining pointers in this way enables two key use cases:

*   Using a let-declaration with pointer type, to form a short name for part of the contents of a variable.

*   Using a formal parameter of a function to refer to the memory of a variable that is accessible to the [calling function](#calling-function).

    *   The call to such a function [must](#shader-creation-error) supply a pointer value for that operand. This often requires using an [address-of](#address-of) operation (unary `&`) to get a pointer to the variable’s contents.

EXAMPLE: Using a pointer as a short name for part of a variable

struct Particle {
  position: vec3<f32>,
  velocity: vec3<f32>
}
struct System {
  active_index: i32,
  timestep: f32,
  particles: array<Particle,100>
}
@group(0) @binding(0) var<storage,read_write> system: System;

@compute @workgroup_size(1)
fn main() {
  // Form a pointer to a specific Particle in storage memory.
  let active_particle = &system.particles[system.active_index];

  let delta_position: vec3<f32> = (*active_particle).velocity * system.timestep;
  let current_position: vec3<f32>  = (*active_particle).position;
  (*active_particle).position = delta_position + current_position;
}

EXAMPLE: Using a pointer as a formal parameter

fn add_one(x: ptr<function,i32>) {
  /* Update the locations for 'x' to contain the next higher integer value,
 (or to wrap around to the largest negative i32 value).
 On the left-hand side, unary '*' converts the pointer to a reference that
 can then be assigned to. It has a read_write access mode, by default.
 /* On the right-hand side:
 - Unary '*' converts the pointer to a reference, with a read_write
 access mode.
 - The only matching type rule is for addition (+) and requires '*x' to
 have type i32, which is the store type for '*x'. So the Load Rule
 applies and '*x' evaluates to the value stored in the memory for '*x'
 at the time of evaluation, which is the i32 value for 0.
 - Add 1 to 0, to produce a final value of 1 for the right-hand side. */
 Store 1 into the memory for '*x'. */
  *x = *x + 1;
}

@compute @workgroup_size(1)
fn main() {
  var i: i32 = 0;

  // Modify the contents of 'i' so it will contain 1.
  // Use unary '&' to get a pointer value for 'i'.
  // This is a clear signal that the called function has access to the memory
  // for 'i', and may modify it.
  add_one(&i);
  let one: i32 = i;  // 'one' has value 1.
}

#### 6.5.9. Forming Reference and Pointer Values[](#forming-references-and-pointers)

A reference value is formed in one of the following ways:

*   The [identifier](#identifier)[resolving](#resolves) to an [in-scope](#in-scope) variable _v_ denotes the reference value for _v_'s memory.

*   Use the [indirection](#indirection) (unary `*`) operation on a pointer.

*   Use a [named component expression](#named-component-expression) on a [memory view](#memory-view) to a composite, or on a [swizzle view](#swizzle-view):

    *   Given either a memory view with a [vector](#vector) store type, or given a swizzle view, appending a single-letter vector access phrase results in a reference to the named component of the vector. See [§ 8.5.1.3 Component Reference from Vector Memory View or Swizzle View](#component-reference-from-vector-memory-view).

    *   Given a memory view with a [structure](#structure) store type, appending a member access phrase results in a reference to the named member of the structure. See [§ 8.5.4 Structure Access Expression](#struct-access-expr).

*   Use an [indexing expression](#indexing-expression) on a [memory view](#memory-view) to a composite, or on a [swizzle view](#swizzle-view):

    *   Given a memory view with a [vector](#vector) store type, appending an array index access phrase results in a reference to the indexed component of the vector. See [§ 8.5.1.3 Component Reference from Vector Memory View or Swizzle View](#component-reference-from-vector-memory-view).

    *   Given a swizzle view, appending an array index access phrase results in a reference to a component of the vector. In this case the indexing is indirect: the given index selects which member of the swizzle view’s IndexList to use as the index of the component. See [§ 8.5.1.3 Component Reference from Vector Memory View or Swizzle View](#component-reference-from-vector-memory-view).

    *   Given a memory view with a [matrix](#matrix) store type, appending an array index access phrase results in a reference to the indexed column vector of the matrix. See [§ 8.5.2 Matrix Access Expression](#matrix-access-expr).

    *   Given a memory view with an [array](#array) store type, appending an array index access phrase results in a reference to the indexed element of the array. See [§ 8.5.3 Array Access Expression](#array-access-expr).

In all cases, the [access mode](#access-mode) of the result is the same as the access mode of the original reference.

EXAMPLE: Component reference from a composite reference

struct S {
    age: i32,
    weight: f32
}
var<private> person: S;
// Elsewhere, 'person' denotes the reference to the memory underlying the variable,
// and will have type ref<private,S,read_write>.

fn f() {
    var uv: vec2<f32>;
    // For the remainder of this function body, 'uv' denotes the reference
    // to the memory underlying the variable, and will have type
    // ref<function,vec2<f32>,read_write>.

    // Evaluate the left-hand side of the assignment:
    // Evaluate 'uv.x' to yield a reference:
    // 1. First evaluate 'uv', yielding a reference to the memory for
    // the 'uv' variable. The result has type ref<function,vec2<f32>,read_write>.
    // 2. Then apply the '.x' vector access phrase, yielding a reference to
    // the memory for the first component of the vector pointed at by the
    // reference value from the previous step.
    // The result has type ref<function,f32,read_write>.
    // Evaluating the right-hand side of the assignment yields the f32 value 1.0.
    // Store the f32 value 1.0 into the storage memory locations referenced by uv.x.
    uv.x = 1.0;

    // Evaluate the left-hand side of the assignment:
    // Evaluate 'uv[1]' to yield a reference:
    // 1. First evaluate 'uv', yielding a reference to the memory for
    // the 'uv' variable. The result has type ref<function,vec2<f32>,read_write>.
    // 2. Then apply the '[1]' array index phrase, yielding a reference to
    // the memory for second component of the vector referenced from
    // the previous step. The result has type ref<function,f32,read_write>.
    // Evaluating the right-hand side of the assignment yields the f32 value 2.0.
    // Store the f32 value 2.0 into the storage memory locations referenced by uv[1].
    uv[1] = 2.0;

    var m: mat3x2<f32>;
    // When evaluating 'm[2]':
    // 1. First evaluate 'm', yielding a reference to the memory for
    // the 'm' variable. The result has type ref<function,mat3x2<f32>,read_write>.
    // 2. Then apply the '[2]' array index phrase, yielding a reference to
    // the memory for the third column vector pointed at by the reference
    // value from the previous step.
    // Therefore the 'm[2]' expression has type ref<function,vec2<f32>,read_write>.
    // The 'let' declaration is for type vec2<f32>, so the declaration
    // statement requires the initializer to be of type vec2<f32>.
    // The Load Rule applies (because no other type rule can apply), and
    // the evaluation of the initializer yields the vec2<f32> value loaded
    // from the memory locations referenced by 'm[2]' at the time the declaration
    // is executed.
    let p_m_col2: vec2<f32> = m[2];

    var A: array<i32,5>;
    // When evaluating 'A[4]'
    // 1. First evaluate 'A', yielding a reference to the memory for
    // the 'A' variable. The result has type ref<function,array<i32,5>,read_write>.
    // 2. Then apply the '[4]' array index phrase, yielding a reference to
    // the memory for the fifth element of the array referenced by
    // the reference value from the previous step.
    // The result value has type ref<function,i32,read_write>.
    // The let-declaration requires the right-hand-side to be of type i32.
    // The Load Rule applies (because no other type rule can apply), and
    // the evaluation of the initializer yields the i32 value loaded from
    // the memory locations referenced by 'A[4]' at the time the declaration
    // is executed.
    let A_4_value: i32 = A[4];

    // When evaluating 'person.weight'
    // 1. First evaluate 'person', yielding a reference to the memory for
    // the 'person' variable declared at module scope.
    // The result has type ref<private,S,read_write>.
    // 2. Then apply the '.weight' member access phrase, yielding a reference to
    // the memory for the second member of the memory referenced by
    // the reference value from the previous step.
    // The result has type ref<private,f32,read_write>.
    // The let-declaration requires the right-hand-side to be of type f32.
    // The Load Rule applies (because no other type rule can apply), and
    // the evaluation of the initializer yields the f32 value loaded from
    // the memory locations referenced by 'person.weight' at the time the
    // declaration is executed.
    let person_weight: f32 = person.weight;

    // Alternatively, references can also be formed from pointers using
    // the same syntax.

    let uv_ptr = &uv;
    // For the remainder of this function body, 'uv_ptr' denotes a pointer
    // to the memory underlying 'uv', and will have the type
    // ptr<function,vec2<f32>,read_write>.

    // Evaluate the left-hand side of the assignment:
    // Evaluate '*uv_ptr' to yield a reference:
    // 1. First evaluate 'uv_ptr', yielding a pointer to the memory for
    // the 'uv' variable. The result has type ptr<function,vec2<f32>,read_write>.
    // 2. Then apply the indirection expression operator, yielding a
    // reference to memory for 'uv'.
    // Evaluating the right-hand side of the assignment yields the vec2<f32> value (1.0, 2.0).
    // Store the value (1.0, 2.0) into the storage memory locations referenced by uv.
    *uv_ptr = vec2f(1.0, 2.0);

    // Evaluate the left-hand side of the assignment:
    // Evaluate 'uv_ptr.x' to yield a reference:
    // 1. First evaluate 'uv_ptr', yielding a pointer to the memory for
    // the 'uv' variable. The result has type ptr<function,vec2<f32>,read_write>.
    // 2. Then apply the '.x' vector access phrase, yielding a reference to
    // the memory for the first component of the vector pointed at by the
    // reference value from the previous step.
    // The result has type ref<function,f32,read_write>.
    // Evaluating the right-hand side of the assignment yields the f32 value 1.0.
    // Store the f32 value 1.0 into the storage memory locations referenced by uv.x.
    uv_ptr.x = 1.0;

    // Evaluate the left-hand side of the assignment:
    // Evaluate 'uv_ptr[1]' to yield a reference:
    // 1. First evaluate 'uv_ptr', yielding a pointer to the memory for
    // the 'uv' variable. The result has type ptr<function,vec2<f32>,read_write>.
    // 2. Then apply the '[1]' array index phrase, yielding a reference to
    // the memory for second component of the vector referenced from
    // the previous step. The result has type ref<function,f32,read_write>.
    // Evaluating the right-hand side of the assignment yields the f32 value 2.0.
    // Store the f32 value 2.0 into the storage memory locations referenced by uv[1].
    uv_ptr[1] = 2.0;

    let m_ptr = &m;
    // When evaluating 'm_ptr[2]':
    // 1. First evaluate 'm_ptr', yielding a pointer to the memory for
    // the 'm' variable. The result has type ptr<function,mat3x2<f32>,read_write>.
    // 2. Then apply the '[2]' array index phrase, yielding a reference to
    // the memory for the third column vector pointed at by the reference
    // value from the previous step.
    // Therefore the 'm[2]' expression has type ref<function,vec2<f32>,read_write>.
    // The 'let' declaration is for type vec2<f32>, so the declaration
    // statement requires the initializer to be of type vec2<f32>.
    // The Load Rule applies (because no other type rule can apply), and
    // the evaluation of the initializer yields the vec2<f32> value loaded
    // from the memory locations referenced by 'm[2]' at the time the declaration
    // is executed.
    let p_m_col2: vec2<f32> = m_ptr[2];

    let A_ptr = &A;
    // When evaluating 'A[4]'
    // 1. First evaluate 'A', yielding a pointer to the memory for
    // the 'A' variable. The result has type ptr<function,array<i32,5>,read_write>.
    // 2. Then apply the '[4]' array index phrase, yielding a reference to
    // the memory for the fifth element of the array referenced by
    // the reference value from the previous step.
    // The result value has type ref<function,i32,read_write>.
    // The let-declaration requires the right-hand-side to be of type i32.
    // The Load Rule applies (because no other type rule can apply), and
    // the evaluation of the initializer yields the i32 value loaded from
    // the memory locations referenced by 'A[4]' at the time the declaration
    // is executed.
    let A_4_value: i32 = A_ptr[4];

    let person_ptr = &person;
    // When evaluating 'person.weight'
    // 1. First evaluate 'person_ptr', yielding a pointer to the memory for
    // the 'person' variable declared at module scope.
    // The result has type ptr<private,S,read_write>.
    // 2. Then apply the '.weight' member access phrase, yielding a reference to
    // the memory for the second member of the memory referenced by
    // the reference value from the previous step.
    // The result has type ref<private,f32,read_write>.
    // The let-declaration requires the right-hand-side to be of type f32.
    // The Load Rule applies (because no other type rule can apply), and
    // the evaluation of the initializer yields the f32 value loaded from
    // the memory locations referenced by 'person.weight' at the time the
    // declaration is executed.
    let person_weight: f32 = person_ptr.weight;
}

A pointer value is formed in one of the following ways:

*   Use the [address-of](#address-of) (unary `&`) operator on a reference.

    *   The result is a [valid pointer](#valid-pointer) if and only if the original reference is [valid](#valid-reference).

    *   The [originating variable](#originating-variable) of a valid result is defined as the originating variable of the reference.

*   If a function [formal parameter](#formal-parameter) has pointer type, then when the function is invoked at runtime the uses of the formal parameter denote the pointer value provided to the corresponding operand at the [call site](#call-site) in the [calling function](#calling-function).

    *   The value denoted by the formal parameter (at runtime) is a [valid pointer](#valid-pointer) if and only if the pointer value at the call site is [valid](#valid-pointer).

    *   The [originating variable](#originating-variable) of a [valid pointer](#valid-pointer) formal parameter (at runtime) is defined as the originating variable of the pointer operand at the call site.

*   The result of a [bufferView](#bufferview-builtin) or [bufferArrayView](#bufferarrayview-builtin) built-in function call.

In all cases, the [access mode](#access-mode) of the result is the same as the access mode of the original pointer.

EXAMPLE: Pointer from a variable

// Declare a variable in the private address space, for storing an f32 value.
var<private> x: f32;

fn f() {
    // Declare a variable in the function address space, for storing an i32 value.
    var y: i32;

    // The name 'x' resolves to the module-scope variable 'x',
    // and has reference type ref<private,f32,read_write>.
    // Applying the unary '&' operator converts the reference to a pointer.
    // The access mode is the same as the access mode of the original variable, so
    // the fully specified type is ptr<private,f32,read_write>. But read_write
    // is the default access mode for function address space, so read_write does not
    // have to be spelled in this case
    let x_ptr: ptr<private,f32> = &x;

    // The name 'y' resolves to the function-scope variable 'y',
    // and has reference type ref<private,i32,read_write>.
    // Applying the unary '&' operator converts the reference to a pointer.
    // The access mode defaults to 'read_write'.
    let y_ptr: ptr<function,i32> = &y;

    // A new variable, distinct from the variable declared at module scope.
    var x: u32;

    // Here, the name 'x' resolves to the function-scope variable 'x' declared in
    // the previous statement, and has type ref<function,u32,read_write>.
    // Applying the unary '&' operator converts the reference to a pointer.
    // The access mode defaults to 'read_write'.
    let inner_x_ptr: ptr<function,u32> = &x;
}

#### 6.5.10. Comparison with References and Pointers in Other Languages[](#pointers-other-languages)

This section is informative, not normative.

References and pointers in WGSL are more restricted than in other languages. In particular:

*   In WGSL a reference can’t directly be declared as an alias to another reference or variable, either as a variable or as a formal parameter.

*   In WGSL pointers and references are not [storable](#storable). That is, the content of a WGSL [variable declaration](#variable-declaration) may not contain a pointer or a reference.

*   In WGSL a function [must not](#shader-creation-error) return a pointer or reference.

*   In WGSL there is no way to convert between integer values and pointer values.

*   In WGSL there is no way to forcibly change the type of a pointer value into another pointer type.

    *   A composite component reference expression is different: it takes a reference to a composite value and yields a reference to one of the components or elements inside the composite value. These are considered different references in WGSL, even though they may have the same machine address at a lower level of implementation abstraction.

*   In WGSL there is no way to forcibly change the type of a reference value into another reference type.

*   In WGSL there is no way to change the access mode of a pointer or reference.

    *   By comparison, C++ automatically converts a non-const pointer to a const pointer, and has a `const_cast` to convert a const value to a non-const value.

*   In WGSL there is no way to allocate new memory from a "heap".

*   In WGSL there is no way to explicitly destroy a variable. The memory for a WGSL variable becomes inaccessible only when the variable goes out of scope.

Note: From the above rules, it is not possible to form a "dangling" pointer, i.e. a pointer that does not reference the memory for a "live" originating variable. A [memory view](#memory-view) may be an [invalid memory reference](#invalid-memory-reference), but it [will never](#behavioral-requirements) access [memory locations](#memory-locations) not associated with the [originating variable](#originating-variable) or buffer.

### 6.6. Texture and Sampler Types[](#texture-sampler-types)

A texel is a scalar or vector used as the smallest independently accessible element of a [texture](#texture). The word _texel_ is short for _texture element_.

A texture is a collection of texels supporting special operations useful for rendering. In WGSL, those operations are invoked via texture builtin functions. See [§ 17.7 Texture Built-in Functions](#texture-builtin-functions) for a complete list.

A WGSL texture corresponds to a WebGPU `GPUTexture`.

A texture has the following features:

[texel format](#texel-format)
The data representation of each texel. See [§ 6.6.1 Texel Formats](#texel-formats).

dimensionality
The number of dimensions in the grid coordinates, and how the coordinates are interpreted. The number of dimensions is 1, 2, or 3. Most textures use cartesian coordinates. Cube textures have six square faces, and are sampled with a three dimensional coordinate interpreted as a direction vector from the origin toward the cube centered on the origin.

See `GPUTextureViewDimension`.

size
The extent of grid coordinates along each dimension. This is a function of [mip level](#mip-level).

mip level count
The mip level count is at least 1 for [sampled textures](#type-sampled-texture) and [depth textures](#type-depth-texture), and equal to 1 for [storage textures](#type-storage-texture).  
Mip level 0 contains a full size version of the texture. Each successive mip level contains a filtered version of the previous mip level at half the size (within rounding) of the previous mip level.  
 When sampling a texture, an explicit or implicitly-computed level-of-detail is used to select the mip levels from which to read texel data. These are then combined via filtering to produce the sampled value.

arrayed
Whether the texture is arrayed.

*   A non-arrayed texture is a grid of texels.

*   An arrayed texture is a homogeneous array of grids of texels.

array size
The number of homogeneous grids, if the texture is [arrayed](#texture-arrayed).

sample count
The number of samples, if the texture is [multisampled](#multisampled-texture-type).

Each texel in a texture is associated with a unique logical texel address, which is an integer tuple having:

*   A [mip level](#mip-level) in [0, [mip level count](#texture-mip-level-count)).

*   A number of components, controlled by the [dimensionality](#texture-dimensionality), with each component value in [0, _S_ i), where _S_ i is the [size](#texture-size) in the _i_'th component.

*   An array index in [0, [array size](#texture-array-size)), if the texture is [arrayed](#texture-arrayed). Note that [size](#texture-size) is a function of [mip level](#mip-level).

*   A sample index in [0, [sample count](#texture-sample-count)), if the texture is [multisampled](#multisampled-texture-type).

A texture’s physical organization is typically optimized for rendering operations. To achieve this, many details are hidden from the programmer, including data layouts, data types, and internal operations that cannot be expressed directly in the shader language.

As a consequence, a shader does not have direct access to the texel memory within a [texture variable](#texture-resource). Instead, access is mediated through an [opaque](#opaque) handle:

*   Within the shader:

    *   Declare a module-scope variable where the [store type](#store-type) is one of the texture types described in later sections. The variable stores an opaque handle to the underlying texture memory, and is automatically placed in the [handle](#address-spaces-handle) address space.

    *   Inside a function, call one of the texture builtin functions, and provide the texture variable or function parameter as the builtin function’s first parameter.

*   When constructing the WebGPU pipeline, the texture variable’s store type and binding [must](#shader-creation-error) be compatible with the corresponding bind group layout entry.

In this way, the set of supported operations for a texture type is determined by the availability of [texture built-in functions](#texture-builtin-functions) having a [formal parameter](#formal-parameter) with that texture type.

Note: The handle stored by a texture variable cannot be changed by the shader. That is, the variable is read-only, even if the underlying texture to which it provides access may be mutable (e.g. a write-only [storage texture](#type-storage-texture)).

The texture types are the set of types defined in:

*   [§ 6.6.2 Sampled Texture Types](#sampled-texture-type)

*   [§ 6.6.3 Multisampled Texture Types](#multisampled-texture-type)

*   [§ 6.6.4 External Sampled Texture Types](#external-texture-type)

*   [§ 6.6.5 Storage Texture Types](#texture-storage)

*   [§ 6.6.6 Depth Texture Types](#texture-depth)

A [sampler](#sampler) is an [opaque](#opaque) handle that controls how [texels](#texel) are accessed from a [sampled texture](#type-sampled-texture) or a [depth texture](#type-depth-texture).

A WGSL sampler maps to a WebGPU `GPUSampler`.

Texel access is controlled via several properties of the sampler:

addressing mode 
Controls how texture boundaries and out-of-bounds coordinates are resolved. The addressing mode for each texture dimension can be set independently. See WebGPU `GPUAddressMode`.

filter mode 
Controls which texels are accessed to produce the final result. Filtering can either use the nearest texel or interpolate between multiple texels. Multiple filter modes can be set independently. See WebGPU `GPUFilterMode`.

LOD clamp 
Controls the min and max levels of details that are accessed.

comparison 
Controls the type of comparison done for [comparison sampler](#type-sampler_comparison). See WebGPU `GPUCompareFunction`.

max anisotropy 
Controls the maximum anisotropy value used by the sampler.

Samplers cannot be created in WGSL modules and their state (e.g. the properties listed above) are immutable within a shader and can only be set by the WebGPU API.

It is a [pipeline-creation error](#pipeline-creation-error) if a filtering sampler (i.e. any sampler using interpolative filtering) is used with texture that has a non-filterable format.

Note: The handle stored by a sampler variable cannot be changed by the shader.

#### 6.6.1. Texel Formats[](#texel-formats)

In WGSL, certain texture types are parameterized by texel format.

A texel format is characterized by:

channels
Each channel contains a scalar. A texel format has up to four channels: `r`, `g`, `b`, and `a`, normally corresponding to the concepts of red, green, blue, and alpha channels.

channel format
The number of bits in the channel, and how those bits are interpreted.

Each texel format in WGSL corresponds to a WebGPU `GPUTextureFormat` with the same name.

Only certain texel formats are used in WGSL source code. The channel formats used to define those texel formats are listed in the Channel Formats table. The second last column specifies the conversion from the stored channel bits to the value used in the shader. This is also known as the channel transfer function, or CTF. The third column specifies the conversion from the shader value to the stored channel bits. This is also known as the inverse channel transfer function, or ICTF. The last column specifies the required [language extension](#language-extension) for the texel format.

Note: The channel transfer function for 8unorm maps {0,...,255} to the floating point interval [0.0, 1.0].

Note: The channel transfer function for 8snorm maps {-128,...,127} to the floating point interval [-1.0, 1.0].

Channel Formats
| Channel format | Number of stored bits | Interpretation of stored bits | Shader type | Shader value (Channel Transfer Function) | Write value `T` (Inverse Channel Transfer Function) | 8unorm | 8 | unsigned integer v ∈ {0,...,255} | f32 | v ÷ 255 | max(0, min(1, `T`)) | | 8snorm | 8 | signed integer v ∈ {-128,...,127} | f32 | v ÷ 127 | max(-1, min(1, `T`)) | | 8uint | 8 | unsigned integer v ∈ {0,...,255} | u32 | v | min(255, `T`) | | 8sint | 8 | signed integer v ∈ {-128,...,127} | i32 | v | max(-128, min(127, `T`)) | | 16unorm | 16 | unsigned integer v ∈ {0,...,65535} | f32 | v ÷ 65535 | max(0, min(1, `T`)) | | 16snorm | 16 | signed integer v ∈ {-32768,...,32767} | f32 | v ÷ 32767 | max(-1, min(1, `T`)) | | 16uint | 16 | unsigned integer v ∈ {0,...,65535} | u32 | v | min(65535, `T`) | | 16sint | 16 | signed integer v ∈ {-32768,...,32767} | i32 | v | max(-32768, min(32767, `T`)) | | 16float | 16 | [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary16](#ieee754-binary16) 16-bit floating point value v | f32 | v | `quantizeToF16(T)` | | 32uint | 32 | 32-bit unsigned integer value v | u32 | v | `T` | | 32sint | 32 | 32-bit signed integer value v | i32 | v | `T` | | 32float | 32 | [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary32](#ieee754-binary32) 32-bit floating point value v | f32 | v | `T` | | 2unorm | 2 | unsigned integer v ∈ {0,...,3} | f32 | v ÷ 3 | max(0, min(1, `T`)) | | 2uint | 2 | unsigned integer v ∈ {0,...,3} | u32 | v | min(3, `T`) | | 10unorm | 10 | unsigned integer v ∈ {0,...,1023} | f32 | v ÷ 1023 | max(0, min(1, `T`)) | | 10uint | 10 | unsigned integer v ∈ {0,...,1023} | u32 | v | min(1023, `T`) | | 10float | 10 | 10-bit floating point value: 5 bits of biased exponent, 5 bits of fraction v | f32 | v | max(0, `T`) | | 11float | 11 | 11-bit floating point value: 5 bits of biased exponent, 6 bits of fraction v | f32 | v | max(0, `T`) | |
| --- | --- | --- | --- | --- | --- |

The texel formats listed in the Texel Formats for Storage Textures table correspond to the [WebGPU plain color formats](../webgpu_spec/webgpu-5f71975aec.md#plain-color-formats) which support the WebGPU `STORAGE_BINDING` usage with at least one [access mode](#access-mode). These texel formats are used to parameterize the [storage texture](#type-storage-texture) types defined in [§ 6.6.5 Storage Texture Types](#texture-storage).

When the texel format does not have all four channels, then:

*   When reading the texel, the [channel transfer function](#channel-transfer-function) is applied [component-wise](#component-wise):

    *   If the texel format has no green channel, then the second component of the shader value is 0.

    *   If the texel format has no blue channel, then the third component of the shader value is 0.

    *   If the texel format has no alpha channel, then the fourth component of the shader value is 1.

*   When writing the texel, the [inverse channel transfer function](#inverse-channel-transfer-function) is applied [component-wise](#component-wise) and shader value components for missing channels are ignored.

The last column in the table below uses the format-specific [channel transfer function](#channel-transfer-function) from the [channel formats](#channel-formats) table.

Texel Formats for Storage Textures
| Texel format | Channel format | Channels in memory order | Corresponding shader value | Required language extension | rgba8unorm | 8unorm | r, g, b, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | | rgba8snorm | 8snorm | r, g, b, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | rgba8uint | 8uint | r, g, b, a | vec4<u32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | rgba8sint | 8sint | r, g, b, a | vec4<i32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | rgba16unorm | 16unorm | r, g, b, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rgba16snorm | 16snorm | r, g, b, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rgba16uint | 16uint | r, g, b, a | vec4<u32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | | rgba16sint | 16sint | r, g, b, a | vec4<i32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | rgba16float | 16float | r, g, b, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | rg8unorm | 8unorm | r, g | vec4<f32>(CTF(r), CTF(g), 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg8snorm | 8snorm | r, g | vec4<f32>(CTF(r), CTF(g), 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg8uint | 8uint | r, g | vec4<u32>(CTF(r), CTF(g), 0u, 1u) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg8sint | 8sint | r, g | vec4<i32>(CTF(r), CTF(g), 0, 1) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg16unorm | 16unorm | r, g | vec4<f32>(CTF(r), CTF(g), 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg16snorm | 16snorm | r, g | vec4<f32>(CTF(r), CTF(g), 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg16uint | 16uint | r, g | vec4<u32>(CTF(r), CTF(g), 0u, 1u) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg16sint | 16sint | r, g | vec4<i32>(CTF(r), CTF(g), 0, 1) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg16float | 16float | r, g | vec4<f32>(CTF(r), CTF(g), 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r32uint | 32uint | r | vec4<u32>(CTF(r), 0u, 0u, 1u) | | | r32sint | 32sint | r | vec4<i32>(CTF(r), 0, 0, 1) | | r32float | 32float | r | vec4<f32>(CTF(r), 0.0, 0.0, 1.0) | | rg32uint | 32uint | r, g | vec4<u32>(CTF(r), CTF(g), 0u, 1u) | | rg32sint | 32sint | r, g | vec4<i32>(CTF(r), CTF(g), 0, 1) | | rg32float | 32float | r, g | vec4<f32>(CTF(r), CTF(g), 0.0, 1.0) | | rgba32uint | 32uint | r, g, b, a | vec4<u32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | rgba32sint | 32sint | r, g, b, a | vec4<i32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | rgba32float | 32float | r, g, b, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | bgra8unorm | 8unorm | b, g, r, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | | r8unorm | 8unorm | r | vec4<f32>(CTF(r), 0.0, 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r8snorm | 8snorm | r | vec4<f32>(CTF(r), 0.0, 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r8uint | 8uint | r | vec4<u32>(CTF(r), 0u, 0u, 1u) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r8sint | 8sint | r | vec4<i32>(CTF(r), 0, 0, 1) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r16unorm | 16unorm | r | vec4<f32>(CTF(r), 0.0, 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r16snorm | 16snorm | r | vec4<f32>(CTF(r), 0.0, 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r16uint | 16uint | r | vec4<u32>(CTF(r), 0u, 0u, 1u) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r16sint | 16sint | r | vec4<i32>(CTF(r), 0, 0, 1) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | r16float | 16float | r | vec4<f32>(CTF(r), 0.0, 0.0, 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rgb10a2unorm | r, g, b: 10unorm a: 2unorm | r, g, b, a | vec4<f32>(CTF(r), CTF(g), CTF(b), CTF(a)) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rgb10a2uint | r, g, b: 10uint a: 2uint | r, g, b, a | vec4<u32>(CTF(r), CTF(g), CTF(b), CTF(a)) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | | rg11b10ufloat | r, g: 11float b: 10float | r, g, b | vec4<f32>(CTF(r), CTF(g), CTF(b), 1.0) | [texture_formats_tier1](#language_extension-texture_formats_tier1) | |
| --- | --- | --- | --- | --- |

WGSL [predeclares](#predeclared) an [enumerant](#enumerant) for each of the texel formats in the table.

#### 6.6.2. Sampled Texture Types[](#sampled-texture-type)

A sampled texture is capable of being [accessed](#memory-access) in conjunction with a [sampler](#type-sampler). It can also be accessed without the use of a sampler. Sampled textures only allow [read accesses](#read-access).

The [texel format](#texel-format) is the `format` attribute of the `GPUTexture` bound to the texture variable. WebGPU [validates](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-validating-shader-binding) compatibility between the texture, the `sampleType` of the bind group layout, and the [sampled type](#sampled-type) of the texture variable.

The texture is parameterized by a sampled type and [must](#shader-creation-error) be `f32`, `i32`, or `u32`.

| Type | [Dimensionality](#texture-dimensionality) | [Arrayed](#texture-arrayed)| texture_1d<_T_> | `1D` | No | | texture_2d<_T_> | `2D` | No | | texture_2d_array<_T_> | `2D` | Yes | | texture_3d<_T_> | `3D` | No | | texture_cube<_T_> | `Cube` | No | | texture_cube_array<_T_> | `Cube` | Yes | |
| --- | --- | --- |

*   _T_ is the [sampled type](#sampled-type).

*   The parameterized type for the images is the type after conversion from sampling. E.g. you can have an image with texels with 8bit unorm components, but when you sample them you get a 32-bit float result (or vec-of-f32).

#### 6.6.3. Multisampled Texture Types[](#multisampled-texture-type)

A multisampled texture has a [sample count](#texture-sample-count) of 1 or more. Despite the name, it cannot be used with a [sampler](#sampler). It effectively stores multiple [texels](#texel) worth of data per [logical texel address](#logical-texel-address) if the sample index is ignored.

The [texel format](#texel-format) is the `format` attribute of the `GPUTexture` bound to the texture variable. WebGPU [validates](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-validating-shader-binding) compatibility between the texture, the `sampleType` of the bind group layout, and the [sampled type](#sampled-type) of the texture variable.

`texture_multisampled_2d` is parameterized by a [sampled type](#sampled-type) and [must](#shader-creation-error) be `f32`, `i32`, or `u32`.

| Type | [Dimensionality](#texture-dimensionality) | [Arrayed](#texture-arrayed)| texture_multisampled_2d<_T_> | `2D` | No | | texture_depth_multisampled_2d | `2D` | No | |
| --- | --- | --- |

*   _T_ is the [sampled type](#sampled-type).

#### 6.6.4. External Sampled Texture Types[](#external-texture-type)

An External texture is an [opaque](#opaque) two-dimensional float-[sampled texture](#type-sampled-texture) type similar to `texture_2d<f32>` but potentially with a different representation. It can be read using [textureLoad](#textureload) or [textureSampleBaseClampToEdge](#textureSampleBaseClampToEdge) built-in functions, which handle these different representations.

See [WebGPU § 6.4 GPUExternalTexture](../webgpu_spec/webgpu-5f71975aec.md#gpuexternaltexture).

| Type | [Dimensionality](#texture-dimensionality) | [Arrayed](#texture-arrayed)| texture_external | `2D` | No | |
| --- | --- | --- |

#### 6.6.5. Storage Texture Types[](#texture-storage)

A storage texture supports [accessing](#memory-access) individual texel values without the use of a sampler.

*   A write-only storage texture supports [writing](#write-access) individual texels, with automatic conversion of the shader value to a stored texel value.

*   A read-only storage texture supports [reading](#read-access) individual texels, with automatic conversion of the stored texel value to a shader texel value.

*   A read-write storage texture supports [reading](#read-access) and [writing](#write-access) individual texels, with automatic conversion between shader and stored texel values.

A storage texture type [must](#shader-creation-error) be parameterized by one of the [texel formats for storage textures](#storage-texel-formats). The texel format determines the conversion function as specified in [§ 6.6.1 Texel Formats](#texel-formats).

When writing texels to a storage texture the _inverse_ of the conversion function is used to convert the shader value to the stored texel.

| Type | [Dimensionality](#texture-dimensionality) | [Arrayed](#texture-arrayed)| texture_storage_1d<_Format_, _Access_> | `1D` | No | | texture_storage_2d<_Format_, _Access_> | `2D` | No | | texture_storage_2d_array<_Format_, _Access_> | `2D` | Yes | | texture_storage_3d<_Format_, _Access_> | `3D` | No | |
| --- | --- | --- |

*   _Format_[must](#shader-creation-error) be an [enumerant](#enumerant) for one of the [texel formats for storage textures](#storage-texel-formats)

*   _Access_[must](#shader-creation-error) be an [enumerant](#enumerant) for one of the [access modes](#access-mode).

*   No [shader-creation error](#shader-creation-error) occurs due to an invalid combination of _Format_ and _Access_. Combinations of _Format_ with _Access_ are checked in the [shader binding validation](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-validating-shader-binding) step during pipeline creation. An invalid combination [will](#behavioral-requirements) result in a [pipeline-creation error](#pipeline-creation-error).

#### 6.6.6. Depth Texture Types[](#texture-depth)

A depth texture is capable of being [accessed](#memory-access) in conjunction with a [sampler_comparison](#type-sampler_comparison). It can also be accessed without the use of a sampler. Depth textures only allow [read accesses](#read-access).

The [texel format](#texel-format) of the texture is defined in the `GPUTextureBindingLayout`.

| Type | [Dimensionality](#texture-dimensionality) | [Arrayed](#texture-arrayed)| texture_depth_2d | `2D` | No | | texture_depth_2d_array | `2D` | Yes | | texture_depth_cube | `Cube` | No | | texture_depth_cube_array | `Cube` | Yes | |
| --- | --- | --- |

#### 6.6.7. Sampler Type[](#sampler-type)

A sampler mediates access to a [sampled texture](#type-sampled-texture) or a [depth texture](#type-depth-texture), by performing a combination of:

*   coordinate transformation.

*   optionally modifying mip-level selection.

*   for a [sampled texture](#type-sampled-texture), optionally filtering retrieved texel values.

*   for a [depth texture](#type-depth-texture), determining the comparison function applied to the retrieved texel.

A sampler types are:

*   [sampler](#type-sampler)

*   [sampler_comparison](#type-sampler_comparison)

| Type | Description | sampler | Sampler. Mediates access to a [sampled texture](#type-sampled-texture). | | sampler_comparison | Comparison sampler. Mediates access to a [depth texture](#type-depth-texture). | |
| --- | --- |

Samplers are parameterized when created in the WebGPU API. They cannot be modified by a WGSL module.

Samplers can only be used by the [texture built-in functions](#texture-builtin-functions).

sampler
sampler_comparison

### 6.7. AllTypes Type[](#alltypes-type)

The AllTypes type is the set of all WGSL [types](#type).

There is no way to write the AllTypes type in WGSL source.

See [§ 6.10 Predeclared Types and Type-Generators Summary](#predeclared-types) for the list of all [predeclared](#predeclared) types and [type-generators](#type-generator).

Note:A type is not a value in an ordinary sense. It is not data that is manipulated by a shader at runtime.

Instead, the AllTypes type exists so [type checking](#type-checking) rules will apply to any phrase that _may_ contain an ordinary value. WGSL makes the rules consistent by defining a type to be a kind of value, and allowing an expression to denote a type.

The motivating case is a [template parameter](#template-parameters), which in various contexts may denote several kinds of things, including a [type](#type), an [enumerant](#enumerant), or a [plain](#plain-type) value. In particular, the [template_arg_expression](#syntax-template_arg_expression) grammar rule expands to the [expression](#syntax-expression) grammar nonterminal.

### 6.8. Type Aliases[](#type-aliases)

A type alias declares a new name for an existing type. The declaration [must](#shader-creation-error) appear at [module scope](#module-scope), and its [scope](#scope) is the entire program.

When type _T_ is defined as a [type alias](#type-alias) for a structure type _S_, all properties of the members of _S_, including attributes, carry over to the members of _T_.

Note: If the type being aliased supports [value constructor](#value-constructor) built-in functions, then those functions can be called via the alias name instead of the original type specifier name, when the type alias is [in scope](#in-scope) and it is otherwise valid to call the function.

type_alias_decl :

`'alias'`[ident](#syntax-ident)[`'='`](#syntax_sym-equal)[type_specifier](#syntax-type_specifier)

EXAMPLE: Type Alias

alias Arr = array<i32, 5>;

alias RTArr = array<vec4<f32>>;

alias single = f32;     // Declare an alias for f32
const pi_approx: single = 3.1415;
fn two_pi() -> single {
  return single(2) * pi_approx;
}

### 6.9. Type Specifier Grammar[](#type-specifiers)

See [§ 8.18 Type Expressions](#type-expr).

type_specifier :

[template_elaborated_ident](#syntax-template_elaborated_ident)

template_elaborated_ident :

[ident](#syntax-ident)[template_list](#syntax-template_list) ?

Note: An [expression](#expression) can also denote a type, by expanding via the [primary_expression](#syntax-primary_expression) grammar rule to [template_elaborated_ident](#syntax-template_elaborated_ident), and via [parenthesization](#parenthesized-expressions).

### 6.10. Predeclared Types and Type-Generators Summary[](#predeclared-types)

The [predeclared](#predeclared)[types](#type) that can be spelled in WGSL source are:

*   [bool](#bool)

*   [f16](#f16)

*   [f32](#f32)

*   [i32](#i32)

*   [sampler](#type-sampler)

*   [sampler_comparison](#type-sampler_comparison)

*   [texture_depth_2d](#type-texture_depth_2d)

*   [texture_depth_2d_array](#type-texture_depth_2d_array)

*   [texture_depth_cube](#type-texture_depth_cube)

*   [texture_depth_cube_array](#type-texture_depth_cube_array)

*   [texture_depth_multisampled_2d](#type-texture_depth_multisampled_2d)

*   [texture_external](#type-texture_external)

*   [u32](#u32)

WGSL also predeclares the return types for the [frexp](#frexp-builtin), [modf](#modf-builtin), and [atomicCompareExchangeWeak](#atomic-rmw) built-in functions. However, they cannot be spelled in WGSL source.

The predeclared [type-generators](#type-generator) are listed in the following table:

 Predeclared type generators 
| Predeclared type-generator | Cross-reference | array | See [§ 6.2.9 Array Types](#array-types) | | atomic | See [§ 6.2.8 Atomic Types](#atomic-types) | | mat2x2 | See [§ 6.2.7 Matrix Types](#matrix-types), which also lists predeclared [aliases](#type-alias) for matrix types. Note: These are also used in [value constructor](#value-constructor) expressions to create matrices. | | mat2x3 | | mat2x4 | | mat3x2 | | mat3x3 | | mat3x4 | | mat4x2 | | mat4x3 | | mat4x4 | | ptr | See [§ 6.5.3 Reference and Pointer Types](#ref-ptr-types) | | texture_1d | See [§ 6.6.2 Sampled Texture Types](#sampled-texture-type) | | texture_2d | | texture_2d_array | | texture_3d | | texture_cube | | texture_cube_array | | texture_multisampled_2d | See [§ 6.6.3 Multisampled Texture Types](#multisampled-texture-type) | | texture_storage_1d | See [§ 6.6.5 Storage Texture Types](#texture-storage) | | texture_storage_2d | | texture_storage_2d_array | | texture_storage_3d | | vec2 | See [§ 6.2.6 Vector Types](#vector-types), which also lists predeclared [aliases](#type-alias) for vector types. Note: These are also used in [value constructor](#value-constructor) expressions to create vectors. | | vec3 | | vec4 | |
| --- | --- |

## 7. Variable and Value Declarations[](#var-and-value)

[Variable](#variable-declaration) and [value](#value-declaration) declarations provide names for data values.

A value declaration creates a name for a value, and that value is immutable once it has been declared. The four kinds of value declarations are `const`, `override`, `let`, and formal parameter declarations, further described below (see [§ 7.2 Value Declarations](#value-decls)).

A variable declaration creates a name for [memory locations](#memory-locations) for storing a value; the value stored there may be updated, if the variable has a [read_write](#access-read_write) access mode. There is one kind of variable declaration, `var`, but it has options for [address space](#address-spaces) and [access modes](#access-mode) in various combinations, described below (see [§ 7.3 var Declarations](#var-decls)).

Note: A value declaration does not have associated memory locations. For example, no WGSL expression can form a pointer to the value.

A declaration appearing outside of any function definition is at [module scope](#module-scope). Its name is [in scope](#in-scope) for the entire program.

A declaration appearing within a function definition is in function scope. The name is available for use in the statement immediately after its declaration until the end of the brace-delimited list of statements immediately enclosing the declaration. A function-scope declaration is a [dynamic context](#dynamic-context).

NOTE:

Variable and value declarations have a similar overall syntax. The following non-normative illustration shows the general form of variable and value declarations, where `[...]` denotes optional parts, `...*` denotes zero or more repetitions of the preceding, and `...+` denotes one or more repetitions of the preceding. For specific syntactic rules, see the respective sections for the elements.

// Specific value declarations.
             const    name [: type]  = initializer ;
[attribute]* override name [: type] [= initializer];
             let      name [: type]  = initializer ;

// General variable form.
[attribute]* var[<address_space[, access_mode]>] name [: type] [= initializer];

// Specific variable declarations.
// Function scope.
             var[<function>] name [: type] [= initializer];

// Module scope.
             var<private>    name [: type] [= initializer];
             var<workgroup>  name : type;
[attribute]+ var<uniform>    name : type;
[attribute]+ var             name : texture_type;
[attribute]+ var             name : sampler_type;
[attribute]+ var<storage[, access_mode]> name : type;

Each such declaration [must](#shader-creation-error) have an explicitly specified type or an initializer. Both a type and an initializer may be specified. Each such declaration determines the type for the associated data value, known as the effective-value-type for the declaration. The effective-value-type of the declaration is:

*   The declared type, if explicitly specified.

*   Otherwise, if the initializer expression has type `T`:

    *   For a `const` declaration, the effective-value-type is `T` itself.

    *   For a `override`, `let`, or `var` declaration, the effective-value-type is the [concretization](#concretization) of `T`.

Each kind of value or variable declaration may place additional constraints on the form of the initializer expression, if present, and on the effective-value-type.

 Variable and Value Declaration Feature Summary. 
| Declaration | Mutability | Scope | [Effective-value-type](#effective-value-type)1 | Initializer Support | Initializer Expression 2 | Part of Resource Interface | [const](#const-declaration) | Immutable | [Module](#module-scope) or [function](#function-scope) | [Constructible](#constructible) ([Concrete](#type-concrete) or [abstract](#type-abstract)) | Required | [const-expression](#const-expressions) | No | | [override](#override-declaration) | Immutable | [Module](#module-scope) | [Concrete](#type-concrete)[scalar](#scalar) | Optional 3 | [const-expression](#const-expressions) or [override-expression](#override-expressions) | No 4 | | [let](#let-declaration) | Immutable | [Function](#function-scope) | [Concrete](#type-concrete)[constructible](#constructible) or [pointer type](#pointer-type). Additionally, if the [texture_and_sampler_let](#language_extension-texture_and_sampler_let) feature is supported, [texture](#texture-types) or [sampler](#sampler-types) types. | Required | [const-expression](#const-expressions), [override-expression](#override-expressions), or [runtime expression](#runtime-expression) | No | | [var](#variable)<[storage](#address-spaces-storage), read> [var](#variable)<[storage](#address-spaces-storage)> | Immutable | [Module](#module-scope) | [Concrete](#type-concrete)[host-shareable](#host-shareable) | Disallowed | | Yes. [storage buffer](#storage-buffer) | | [var](#variable)<[storage](#address-spaces-storage), read_write>5,6 | Mutable | [Module](#module-scope) | [Concrete](#type-concrete)[host-shareable](#host-shareable) | Disallowed | | Yes. [storage buffer](#storage-buffer) | | [var](#variable)<[uniform](#address-spaces-uniform)> | Immutable | [Module](#module-scope) | [Concrete](#type-concrete)[constructible](#constructible)[host-shareable](#host-shareable) or [fixed-size buffer](#fixed-size-buffer) | Disallowed | | Yes. [uniform buffer](#uniform-buffer) | | [var](#variable)<[immediate](#address-spaces-immediate)> | Immutable | [Module](#module-scope) | [Concrete](#type-concrete)[constructible](#constructible)[host-shareable](#host-shareable), excluding arrays and structures containing array members | Disallowed | | Yes. [immediate data](#immediate-data) | | [var](#variable)5 | Immutable 7 | [Module](#module-scope) | [Texture](#texture-types) | Disallowed | | Yes. [texture resource](#texture-resource) | | [var](#variable) | Immutable | [Module](#module-scope) | [Sampler](#sampler-types) | Disallowed | | Yes. [sampler resource](#sampler-resource) | | [var](#variable)<[workgroup](#address-spaces-workgroup)>6,8 | Mutable | [Module](#module-scope) | [Concrete](#type-concrete)[plain type](#plain-type) with a [fixed footprint](#fixed-footprint) or a [fixed-size buffer](#fixed-size-buffer)9 | Disallowed 10 | | No | | [var](#variable)<[private](#address-spaces-private)> | Mutable | [Module](#module-scope) | [Concrete](#type-concrete)[constructible](#constructible) | Optional 10 | [const-expression](#const-expressions) or [override-expression](#override-expressions) | No | | [var](#variable)<[function](#address-spaces-function)> [var](#variable) | Mutable | [Function](#function-scope) | [Concrete](#type-concrete)[constructible](#constructible) | Optional 10 | [const-expression](#const-expressions), [override-expression](#override-expressions), or [runtime expression](#runtime-expression) | No | |
| --- | --- | --- | --- | --- | --- | --- |

1.   Only [const-declarations](#const-declaration) can be [abstract](#type-abstract) types, and only when the type is not explicitly specified.

2.   The type of the expression must be [feasibly converted](#feasible-automatic-conversion) to the [effective-value-type](#effective-value-type).

3.   If an initializer is not specified, a value must be provided at [pipeline-creation time](#pipeline-creation).

4.   [Override-declarations](#override-declaration) are part of the shader interface, but are not bound resources.

5.   [Storage buffers](#storage-buffer) and [storage textures](#type-storage-texture) with an access mode other than [read](#access-read) cannot be [statically accessed](#statically-accessed) in a [vertex shader stage](#vertex-shader-stage). See WebGPU `createBindGroupLayout()`.

6.   [Atomic types](#atomic-type) can only appear in mutable storage buffers or workgroup variables.

7.   The data in [storage textures](#texture-storage) with a [write](#access-write) or [read_write](#access-read_write)[access mode](#access-mode) is mutable, but can only be modified via [textureStore](#texturestore) built-in function. The variable itself cannot be modified.

8.   Variables in the [workgroup](#address-spaces-workgroup) address space can only be [statically accessed](#statically-accessed) in a [compute shader stage](#compute-shader-stage).

9.   The [element count](#element-count) of the outermost [array](#array) or the size of the [buffer](#buffer) may be an [override-expression](#override-expressions).

10.   If there is no initializer, the variable is [default initialized](#default-initial-value).

### 7.1. Variables vs Values[](#var-vs-value)

[Variable declarations](#variable-declaration) are the only mutable data in a WGSL module. [Value declarations](#value-declaration) are always immutable. Variables can be the basis of [reference](#reference-type) and [pointer](#pointer-type) values because variables have associated [memory locations](#memory-locations), whereas a value declaration cannot be the basis of a pointer or reference value.

Using variables is generally more expensive than using value declarations, because using a variable requires extra operations to [read](#read-access) or [write](#write-access) to the [memory locations](#memory-locations) associated with the variable.

Generally speaking, an author should prefer using declarations in the following order, with the most preferred option listed first:

*   [const-declaration](#const-declaration)

*   [override-declaration](#override-declaration)

*   [let-declaration](#let-declaration)

*   [variable declaration](#variable-declaration)

This will generally result in the best overall performance of a shader.

### 7.2. Value Declarations[](#value-decls)

When an [identifier](#identifier)[resolves](#resolves) to a [value declaration](#value-declaration), the identifier denotes that value.

WGSL provides multiple kinds of value declarations. The value for each kind of declaration is fixed at a different point in the [shader lifecycle](#shader-lifecycle). The different kinds of value declarations and when their values are fixed are:

*   [const-declarations](#const-declaration), at [shader-creation time](#shader-module-creation)

*   [override-declarations](#override-declaration), at [pipeline-creation time](#pipeline-creation)

*   [let-declarations](#let-declaration), when they are executed

*   [formal parameter](#formal-parameter) declarations, when the associated [function call](#function-call) argument is executed

Note:[Formal parameters](#formal-parameter) are described in [§ 11 Functions](#functions).

#### 7.2.1. `const` Declarations[](#const-decls)

A const-declaration specifies a name for a data value that is fixed at [shader-creation time](#shader-module-creation). Each const-declaration requires an initializer. A const-declaration can be declared in [module](#module-scope) or [function](#function-scope) scope. The initializer expression [must](#shader-creation-error) be a [const-expression](#const-expressions). The type of a const-declaration must be a [concrete](#type-concrete) or [abstract](#type-abstract)[constructible](#constructible) type. const-declarations are the only declarations where the [effective-value-type](#effective-value-type) may be [abstract](#type-abstract).

Note: Since [abstract numeric types](#abstract-numeric-types) cannot be spelled in WGSL, they can only be used via type inference.

EXAMPLE: const-declarations at module scope

const a = 4;                  // AbstractInt with a value of 4.
const b : i32 = 4;            // i32 with a value of 4.
const c : u32 = 4;            // u32 with a value of 4.
const d : f32 = 4;            // f32 with a value of 4.
const e = vec3(a, a, a);      // vec3 of AbstractInt with a value of (4, 4, 4).
const f = 2.0;                // AbstractFloat with a value of 2.
const g = mat2x2(a, f, a, f); // mat2x2 of AbstractFloat with a value of:
                              // ((4.0, 2.0), (4.0, 2.0)).
                              // The AbstractInt a converts to AbstractFloat.
                              // An AbstractFloat cannot convert to AbstractInt.
const h = array(a, f, a, f);  // array of AbstractFloat with 4 components:
                              // (4.0, 2.0, 4.0, 2.0).

#### 7.2.2. `override` Declarations[](#override-decls)

An override-declaration specifies a name for a [pipeline-overridable](#pipeline-overridable) constant value. An override-declaration [must](#shader-creation-error) only be declared at [module scope](#module-scope). The value of a pipeline-overridable constant is fixed at [pipeline-creation time](#pipeline-creation). The value is one provided by the WebGPU pipeline-creation method, if specified, and otherwise is the value of its [concretized](#concretization-of-a-value) initializer expression. The [effective-value-type](#effective-value-type) of an override-declaration must be a [concrete](#type-concrete)[scalar](#scalar) type.

An initializer expression is optional. If present, it must be an [override-expression](#override-expressions) and represents the pipeline-overridable constant default value. If no initializer is specified, it is a [pipeline-creation error](#pipeline-creation-error) if a value is not provided at pipeline-creation time.

If the declaration has an [id](#attribute-id) attribute applied, the literal operand is known as the pipeline constant ID, and must be a unique integer between 0 and 65535 inclusive. That is, two override-declarations must not use the same pipeline constant ID.

The application can specify its own value for an override-declaration at [pipeline-creation time](#pipeline-creation). The pipeline creation API accepts a mapping from overridable constants to a value of the constant’s type. The constant is identified by a pipeline-overridable constant identifier string, which is the base-10 representation of the [pipeline constant ID](#pipeline-constant-id) if specified, and otherwise the declared [name](#name) of the constant.

EXAMPLE: Module constants, pipeline-overrideable

@id(0)    override has_point_light: bool = true;  // Algorithmic control
@id(1200) override specular_param: f32 = 2.3;     // Numeric control
@id(1300) override gain: f32;                     // Must be overridden
          override width: f32 = 0.0;              // Specified at the API level using
                                                  // the name "width".
          override depth: f32;                    // Specified at the API level using
                                                  // the name "depth".
                                                  // Must be overridden.
          override height = 2 * depth;            // The default value
                                                  // (if not set at the API level),
                                                  // depends on another
                                                  // overridable constant.

#### 7.2.3. `let` Declarations[](#let-decls)

A let-declaration specifies a name for a value that is fixed each time the statement is executed at runtime. A let-declaration must only be declared in [function scope](#function-scope), and as such, is a [dynamic context](#dynamic-context). A let-declaration must have an initializer expression. The value is the [concretized](#concretization-of-a-value) value of the initializer. The [effective-value-type](#effective-value-type) of a let-declaration [must](#shader-creation-error) be either a [concrete](#type-concrete)[constructible](#constructible) type or a [pointer type](#pointer-type). If the [texture_and_sampler_let](#language_extension-texture_and_sampler_let) feature is supported, the effective-value-type may also be a [texture](#texture-types) or [sampler](#sampler-types) type.

Note: Since [buffer](#buffer) types are not [constructible](#constructible), only pointers to buffers can be let-declarations.

EXAMPLE: let-declared constants at function scope

// 'blockSize' denotes the i32 value 1024.
let blockSize: i32 = 1024;

// 'row_size' denotes the u32 value 16u. The type is inferred.
let row_size = 16u;

### 7.3. `var` Declarations[](#var-decls)

A variable is a named reference to memory that can contain a value of a particular [storable](#storable) type.

Two types are associated with a variable: its [store type](#store-type) (the type of value that may be placed in the referenced memory) and its [reference type](#reference-type) (the type of the variable itself). If a variable has store type `T`, [address space](#address-spaces)`AS`, and [access mode](#access-mode)`AM`, then its reference type is `ref<AS,T,AM>`. The store type of a variable is always [concrete](#type-concrete).

A variable declaration:

*   Specifies the variable’s [name](#name).

*   Determines the variable’s [address space](#address-spaces), [store type](#store-type), and [access mode](#access-mode). Together these comprise the variable’s [reference type](#reference-type).

    *   The store type is the [effective-value-type](#effective-value-type) of the variable’s declaration.

*   Ensures the execution environment allocates memory for a value of the store type, in the specified address space, supporting the given access mode, for the [lifetime](#lifetime) of the variable.

*   Optionally has an initializer expression if the variable is in the [private](#address-spaces-private) or [function](#address-spaces-function) address spaces. If present, the initializer must evaluate to the variable’s store type. If present, the initializer for a [private](#address-spaces-private) variable must be a [const-expression](#const-expressions) or an [override-expression](#override-expressions). Variables in address spaces other than [function](#address-spaces-function) or [private](#address-spaces-private)[must not](#shader-creation-error) have an initializer.

When an [identifier](#identifier)[resolves](#resolves) to a variable declaration, the identifier is an expression denoting the reference [memory view](#memory-view) for the variable’s memory, and its type is the variable’s [reference type](#reference-type). See [§ 8.12 Variable Identifier Expression](#var-identifier-expr).

If the [address space](#address-spaces) or [access mode](#access-mode) for a variable declaration are specified in program source, they are written as a [template list](#template-list) after the `var` keyword:

*   The [address space](#address-spaces) is specified first, as one of the [predeclared](#predeclared) address space [enumerants](#enumerant).

*   The [access mode](#access-mode) is specified second, if present, as one of the [predeclared](#predeclared) address mode [enumerants](#enumerant).

    *   The address space must be specified if the access mode is specified.

Variables in the [private](#address-spaces-private), [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), [workgroup](#address-spaces-workgroup), and [handle](#address-spaces-handle) address spaces must only be declared in [module scope](#module-scope), while variables in the [function](#address-spaces-function) address space must only be declared in [function scope](#function-scope). The address space [must](#shader-creation-error) be specified for all address spaces except handle and function. The handle address space [must not](#shader-creation-error) be specified. Specifying the function address space is optional.

The [access mode](#access-mode) always has a default value, and except for variables in the [storage](#address-spaces-storage) address space, [must not](#shader-creation-error) be specified in the WGSL source. See [§ 14.3 Address Spaces](#address-space).

A variable in the [uniform](#address-spaces-uniform) address space is a uniform buffer variable. Its [store type](#store-type) must be a [host-shareable](#host-shareable)[constructible](#constructible) type or a [fixed-size buffer](#fixed-size-buffer) type, and must satisfy the [address space layout constraints](#address-space-layout-constraints).

A variable in the [storage](#address-spaces-storage) address space is a storage buffer variable. Its [store type](#store-type) must be a [host-shareable](#host-shareable) type and must satisfy the [address space layout constraints](#address-space-layout-constraints). The variable may be declared with a [read](#access-read) or [read_write](#access-read_write) access mode; the default is read.

A variable in the [immediate](#address-spaces-immediate) address space is an immediate data variable. Its [store type](#store-type)[must](#shader-creation-error) be a [host-shareable](#host-shareable)[constructible](#constructible) type, excluding arrays and structures that contain array members. Each [entry point](#entry-point)[must](#shader-creation-error)[statically access](#statically-accessed) at most one immediate data variable. The value of an immediate variable is set via [setImmediates](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-gpubindingcommandsmixin-setimmediates) commands recorded by the WebGPU API command encoder, and remains constant during shader execution. The variable size is limited by the pipeline layout’s [immediateSize](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-gpupipelinelayoutdescriptor-immediatesize) configuration.

The [AccessibleSlots](#accessible-slots) exclude padding bytes between structure members and at the end of structures. Only the accessible slots need to be initialized via the WebGPU API before the immediate data variable is accessed in a shader.

A texture resource is a variable whose [effective-value-type](#effective-value-type) is a [texture type](#texture-types). It is declared at [module scope](#module-scope). It holds an [opaque](#opaque) handle which is used to access the underlying grid of [texels](#texel) in a [texture](#texture). The handle itself is in the [handle](#address-spaces-handle) address space and is always read-only. In many cases the underlying texels are read-only, and we say the texture variable immutable. For [write-only storage textures](#type-write-only-storage-texture) and [read-write storage textures](#type-read-write-storage-texture), the underlying texels are mutable, and by convention we say the texture variable is mutable.

A sampler resource is a variable whose [effective-value-type](#effective-value-type) is a [sampler type](#sampler-types). It is declared at [module scope](#module-scope), exists in the [handle](#address-spaces-handle) address space, and is immutable.

As described in [§ 13.3.2 Resource Interface](#resource-interface), uniform buffers, storage buffers, textures, and samplers form the [resource interface of a shader](#resource-interface-of-a-shader).

The lifetime of a variable is the period during shader execution for which the [memory locations](#memory-locations) are associated with the variable. The lifetime of a [module scope](#module-scope) variable is the entire execution of the shader stage. There is an independent version of a variable in the [private](#address-spaces-private) and [function](#address-spaces-function) address spaces for each invocation. [Function-scope](#function-scope) variables are a [dynamic context](#dynamic-context). The lifetime of a function-scope variable is determined by its scope:

*   It starts when control enters the variable’s declaration.

*   It ends when the name is no longer [in scope](#in-scope) of any part of the [dynamic context](#dynamic-context). That is, the lifetime includes any functions [called](#function-call) while the name is in scope.

Two [resource](#resource) variables may have [overlapping memory](#overlap) locations, but it is a [dynamic error](#dynamic-error) if either of those variables is mutable. Other variables with overlapping lifetimes [will](#behavioral-requirements) not have overlapping memory locations. When a variable’s lifetime ends, its memory may be used for another variable.

Note: WGSL ensures the contents of a variable are only observable during the variable’s lifetime.

When a variable in the [private](#address-spaces-private), [function](#address-spaces-function), or [workgroup](#address-spaces-workgroup) address spaces is created, it [will](#behavioral-requirements) have an initial value. If no initializer is specified the initial value is the default initial value. The initial values are computed as follows:

*   For variables in the function address space:

    *   The [zero value](#zero-value) of the [store type](#store-type), if the variable declaration did not specify an initializer.

    *   Otherwise it is the result of evaluating the [concretized](#concretization-of-a-value) initializer expression at that point in program execution.

*   For variables in the private address space:

    *   The [zero value](#zero-value) of the [store type](#store-type), if the variable declaration did not specify an initializer.

    *   Otherwise it is the result of evaluating the [concretized](#concretization-of-a-value) initializer expression. The initializer must be an [override-expression](#override-expressions), and so its value is fixed no later than [pipeline-creation time](#pipeline-creation).

*   For variables in the workgroup address space:

    *   When the [store type](#store-type) is [constructible](#constructible), the [zero value](#zero-value) for the store type.

    *   If the [store type](#store-type) is an [atomic type](#atomic-type), the [zero value](#zero-value) is that of the underlying type ([concrete](#type-concrete)[integer scalar](#integer-scalar)).

    *   If the [store type](#store-type) is a [buffer](#buffer) type, the [zero value](#zero-value) is all zero bytes.

    *   Otherwise, if the [store type](#store-type) is not [constructible](#constructible), the [zero value](#zero-value) is determined by recursively applying these rules to each [component](#components) of the [composite](#composite) until a [constructible](#constructible) type is encountered.

        *   Note: This commonly occurs when using an [array](#array) with a [pipeline-overridable](#pipeline-overridable)[element count](#element-count) or a [composite](#composite) that contains an [atomic type](#atomic-type).

Variables in other address spaces are [resources](#resource) set by bindings in the [draw command](#draw-command) or [dispatch command](#dispatch-command).

Consider the following snippet of WGSL:

EXAMPLE: Variable initial values

var i: i32;         // Initial value is 0. Not recommended style.
loop {
  var twice: i32 = 2 * i;   // Re-evaluated each iteration.
  i++;
  if i == 5 { break; }
}

 The loop body will execute six times. Variable `i` will take on values 0, 1, 2, 3, 4, 5, and variable `twice` will take on values 0, 2, 4, 6, and 8. 
Consider the following snippet of WGSL:

EXAMPLE: Reading a variable multiple times

var x: f32 = 1.0;
let y = x * x + x + 1;

 Because `x` is a variable, all accesses to it turn into load and store operations. However, it is expected that either the browser or the driver optimizes this intermediate representation such that the redundant loads are eliminated. 

EXAMPLE: Module scope variable declarations

var<private> decibels: f32;
var<workgroup> worklist: array<i32,10>;

struct Params {
  specular: f32,
  count: i32
}

// Uniform buffer. Always read-only, and has more restrictive layout rules.
@group(0) @binding(2)
var<uniform> param: Params;    // A uniform buffer

// A storage buffer, for reading and writing
@group(0) @binding(0)
var<storage,read_write> pbuf: array<vec2<f32>>;

// Textures and samplers are always in "handle" space.
@group(0) @binding(1)
var filter_params: sampler;

EXAMPLE: Access modes for buffers

// Storage buffers
@group(0) @binding(0)
var<storage,read> buf1: Buffer;       // Can read, cannot write.
@group(0) @binding(0)
var<storage> buf2: Buffer;            // Can read, cannot write.
@group(0) @binding(1)
var<storage,read_write> buf3: Buffer; // Can both read and write.

struct ParamsTable {weight: f32}

// Uniform buffer. Always read-only, and has more restrictive layout rules.
@group(0) @binding(2)
var<uniform> params: ParamsTable;     // Can read, cannot write.

EXAMPLE: Function scope variables and constants

fn f() {
   var<function> count: u32;  // A variable in function address space.
   var delta: i32;            // Another variable in the function address space.
   var sum: f32 = 0.0;        // A function address space variable with initializer.
   var pi = 3.14159;          // Infer the f32 store type from the initializer.
}

### 7.4. Variable and Value Declaration Grammar Summary[](#var-and-value-decl-grammar)

variable_or_value_statement :

[variable_decl](#syntax-variable_decl)

|[variable_decl](#syntax-variable_decl)[`'='`](#syntax_sym-equal)[expression](#syntax-expression)

|`'let'`[optionally_typed_ident](#syntax-optionally_typed_ident)[`'='`](#syntax_sym-equal)[expression](#syntax-expression)

|`'const'`[optionally_typed_ident](#syntax-optionally_typed_ident)[`'='`](#syntax_sym-equal)[expression](#syntax-expression)

optionally_typed_ident :

[ident](#syntax-ident) ( [`':'`](#syntax_sym-colon)[type_specifier](#syntax-type_specifier) ) ?

global_variable_decl :

[attribute](#syntax-attribute) * [variable_decl](#syntax-variable_decl) ( [`'='`](#syntax_sym-equal)[expression](#syntax-expression) ) ?

global_value_decl :

`'const'`[optionally_typed_ident](#syntax-optionally_typed_ident)[`'='`](#syntax_sym-equal)[expression](#syntax-expression)

|[attribute](#syntax-attribute) * `'override'`[optionally_typed_ident](#syntax-optionally_typed_ident) ( [`'='`](#syntax_sym-equal)[expression](#syntax-expression) ) ?

## 8. Expressions[](#expressions)

[Expressions](#expression) specify how values are computed.

The different kinds of value expressions provide a tradeoff between when they are evaluated and how expressive they can be. The sooner the evaluation, the more constrained the operations, but also the more places the value can be used. This tradeoff leads to different flexibility with each kind of value declaration. [const-expressions](#const-expressions) and [override-expressions](#override-expressions) are evaluated prior to execution on the GPU, so only the result of the computation of the expression is necessary in the final GPU code. Additionally, because [const-expressions](#const-expressions) are evaluated at [shader-creation time](#shader-module-creation) they can be used in more situations than [override-expressions](#override-expressions), for example, to size [arrays](#array) in [function scope](#function-scope)[variables](#variable-declaration). A runtime expression is an expression that is neither a [const-expression](#const-expressions) nor an [override-expression](#override-expressions). A runtime expression is computed on the GPU during shader execution. While runtime expressions can be used by fewer grammar elements, they can be computed from a larger class of expressions, for example, other runtime values.

### 8.1. Early Evaluation Expressions[](#early-eval-exprs)

WGSL defines two types of expressions that can be evaluated before runtime:

*   [const-expressions](#const-expressions), at [shader-creation time](#shader-module-creation)

*   [override-expressions](#override-expressions), at [pipeline-creation time](#pipeline-creation)

#### 8.1.1. `const` Expressions[](#const-expr)

Expressions that can be evaluated at [shader-creation time](#shader-module-creation) are called const-expressions. An expression is a const-expression if all its [identifiers](#identifier)[resolve](#resolves) to:

*   [const-declarations](#const-declaration), or

*   [const-functions](#const-functions), or

*   [type aliases](#type-alias), or

*   [structure](#structure) names.

The type of a `const` expression [must](#shader-creation-error)[resolve](#type-rule) to a type with a [creation-fixed footprint](#creation-fixed-footprint).

Note:[Abstract types](#type-abstract) can be the inferred type of a const-expression.

A const-expression E[will](#behavioral-requirements) be evaluated if and only if:

*   E is [top-level expression](#top-level-expression),

*   E is a [subexpression](#subexpressions) of an expression OuterE, and OuterE[will](#behavioral-requirements) be evaluated, and evaluation of OuterE requires E to be evaluated,

*   E is a [subexpression](#subexpressions) of an expression OuterE such that evaluation of E is required to determine the [static type](#static-type) of OuterE, or

*   E is a [subexpression](#subexpressions) of an expression OuterE such that OuterE requires E to be evaluated to produce a [shader-creation error](#shader-creation-error) (e.g. [integer division](#arithmetic-expr)).

Note: The evaluation rule implies that short-circuiting operators `&&` and `||` guard evaluation of their right-hand side subexpressions unless there is a [subexpression](#subexpressions) that requires evaluation to determine a [static type](#static-type).

A const-expression may be evaluated by the CPU implementing the WebGPU API methods. Therefore accuracy requirements for operations on [AbstractFloat](#abstractfloat) values are _no more strict_ than required for common WebGPU runtime environments, such as WebAssembly [[WASM-CORE-2]](https://www.w3.org/TR/WGSL/#biblio-wasm-core-2 "WebAssembly Core Specification") and ECMAScript [[ECMASCRIPT]](https://www.w3.org/TR/WGSL/#biblio-ecmascript "ECMAScript Language Specification"). Accuracy requirements for [concrete](#type-concrete) floating point types (such as f32) are specified in [§ 15.7.4.1 Accuracy of Concrete Floating Point Expressions](#concrete-float-accuracy).

Example: `(42)` is analyzed as follows:

*   The term `42` is the [AbstractInt](#abstractint) value 42.

*   Surrounding that term with parentheses produces a new expression `(42)` that is of type [AbstractInt](#abstractint) with value 42.

Example: `-5` is analyzed as follows:

*   The term `5` is the [AbstractInt](#abstractint) value 5.

*   Preceding that term with '`-`' produces a new expression `-5` that is of type [AbstractInt](#abstractint) with value -5.

Example: `-2147483648` is analyzed as follows:

*   The term `2147483648` is the [AbstractInt](#abstractint) value 2147483648. Note that this value does **not** fit in a 32-bit signed integer.

*   Preceding that term with '`-`' produces a new expression `-2147483648` that is of type [AbstractInt](#abstractint) with value -2147483648.

Example: `const minint = -2147483648;` is analyzed as follows:

*   As above, `-2147483648` evaluates to a [AbstractInt](#abstractint) value -2147483648.

*   A [const-declaration](#const-declaration) allows the initializer to be an [abstract numeric type](#abstract-numeric-types).

*   The result is that `minint` is declared to be the [AbstractInt](#abstractint) value -2147483648.

Example: `let minint = -2147483648;` is analyzed as follows:

*   As above, `-2147483648` evaluates to a [AbstractInt](#abstractint) value -2147483648.

*   A [let-declaration](#let-declaration) requires the initializer to be a [concrete](#type-concrete)[constructible](#constructible) type or a pointer type.

*   The let-declaration does not have an explicit type, so [overload resolution](#overload-resolution) is used. The overload candidates that apply use [feasible automatic conversions](#feasible-automatic-conversion) from [AbstractInt](#abstractint) to either [i32](#i32), [u32](#u32), or [f32](#f32). The one of lowest rank is to [i32](#i32), and so [AbstractInt](#abstractint) -2147483648 value is converted to the [i32](#i32) value -2147483648.

*   The result is that `minint` is declared to be the i32 value -2147483648.

Example: `false && (10i < i32(5 * 1000 * 1000 * 1000))` is analyzed as follows:

*   The entire expression is a const-expression.

*   However, the short-circuiting rules of the `&&` operator apply: the left-hand side evaluates to `false`, and so the right-hand side is _not evaluated_.

*   Evaluation of i32(5 * 1000 * 1000 * 1000) would have caused a [shader-creation error](#shader-creation-error) because the [AbstractInt](#abstractint) value 5000000000 overflows the [i32](#i32) type.

Example: `false && array<u32, 1 + 2>(0, 1, 2)[0] == 0`

*   The entire expression is a const-expression.

*   Type checking requires the `e1 : bool && e2 : bool`:

    *   `false` is a bool value.

    *   Type checking proceeds on the right-hand side and eventually evaluates `1 + 2` in the array element count expression.

*   `1 + 2` evaluates to an i32 value of `3`.

    *   The array is typed `array<u32, 3i>`.

*   Neither the array access expression nor the equality operator are evaluated.

#### 8.1.2. `override` Expressions[](#override-expr)

Expressions that can be evaluated at [pipeline creation](#pipeline-creation) time are called override-expressions. An expression is an override-expression if all its [identifiers](#identifier)[resolve](#resolves) to:

*   [override-declarations](#override-declaration), or

*   [const-declarations](#const-declaration), or

*   [const-functions](#const-functions), or

*   [type aliases](#type-alias), or

*   [structure](#structure) names.

Note: All [const-expressions](#const-expressions) are also override-expressions.

Override-expressions other than const-expressions are only validated or evaluated during [pipeline creation](#pipeline-creation), and only after any API-provided values are substituted for [override-declarations](#override-declaration). If an [override-declaration](#override-declaration) has its value substituted via the API, its initializer expression, if present, will not be evaluated. Otherwise, an override-expression E[will](#behavioral-requirements) be evaluated if and only if:

*   E forms part of the [shader](#shader) for the [entry point](#entry-point) specified by the `GPUProgrammableStage`, and:

*   Any of the following are true:

    *   E is [top-level expression](#top-level-expression) (after value substitution), or

    *   E is a [subexpression](#subexpressions) of an expression OuterE, and OuterE[will](#behavioral-requirements) be evaluated, and evaluation of OuterE requires E to be evaluated, or

    *   E is a [subexpression](#subexpressions) of an expression OuterE such that OuterE requires E to be evaluated to produce a [pipeline-creation error](#pipeline-creation-error) (e.g. [integer division](#arithmetic-expr)).

Note: Not all override-expressions may be usable as the initializer for an [override-declaration](#override-declaration), because such initializers must [resolve](#type-rule) to a [concrete](#type-concrete)[scalar](#scalar) type.

Example: `override x = 42;` is analyzed as follows:

*   The term `42` is the [AbstractInt](#abstractint) value 42.

*   An [override-declaration](#override-declaration) requires a [concrete](#type-concrete)[scalar](#scalar) type.

*   `42` is converted to [i32](#i32) via a [feasible automatic conversion](#feasible-automatic-conversion).

Example: `let y = x + 1;` is analyzed as follows:

*   From above, `x` has a type of [i32](#i32).

*   The expression `x + 1` is an override-expression because it is composed of an [override-declaration](#override-declaration) and an [integer literal](#integer-literal).

*   The expression has a type of [i32](#i32) and is evaluated at [pipeline creation](#pipeline-creation) time. Its value depends on whether or not `x` is overridden at pipeline creation time.

Example: `vec3(x,x,x)` is analyzed as follows:

*   From above, `x` is an [override-declaration](#override-declaration) with the type [i32](#i32).

*   `vec3(x,x,x)` is an override-expression because the only identifiers [resolve](#resolves) to override-declarations.

*   The type of the expression is a [vector](#vector) of 3 components of [i32](#i32) (`vec3<i32>`).

EXAMPLE: Shader-creation errors from override-expressions

override a : i32 = 0;
override b = a / 0; // shader-creation error,
                    // regardless of attempting to override c

EXAMPLE: Pipeline-creation errors from override-expressions

override a : i32 = 0;
override b = 1 / a;

// b is a part of the frag1 shader. When compiling frag1 into a pipeline
// the following cases may occur:
// * if b is overridden, no error occurs.
// * if a is overridden to a non-zero value, no error occurs.
// * if a is 0 and b is not overridden, a pipeline-creation error occurs.
@fragment
fn frag1() {
  _ = b;
}

// b is not part of the frag2 shader. When compiling frag2 into a pipeline
// no errors occur even if b is not overridden and the value of a is 0.
@fragment
fn frag2() {
}

### 8.2. Indeterminate values[](#indeterminate-values)

In limited cases, an evaluation of a [runtime expression](#runtime-expression) can occur using unsupported values for its [subexpressions](#subexpressions).

In such a case, the result of that evaluation is an indeterminate value of the expression’s [static type](#static-type), meaning some arbitrary implementation-chosen value of the static type.

A distinct value may be produced for each unique [dynamic context](#dynamic-context) in which the expression is evaluated. For example, if the evaluation occurs once per iteration of a loop, a distinct value may be computed for each loop iteration.

Note: If the type is a floating point type and the implementation supports NaN values, then the indeterminate value produced at runtime may be a NaN value.

EXAMPLE: Indeterminate value example

fn fun() {
   var extracted_values: array<i32,2>;
   const v = vec2<i32>(0,1);

   for (var i: i32 = 0; i < 2 ; i++) {
      // A runtime-expression used to index a vector, but outside the
      // indexing bounds of the vector, produces an indeterminate value
      // of the vector component type.
      let extract = v[i+5];

      // Now 'extract' is any value of type i32.

      // Save it for later.
      extracted_values[i] = extract;

      if extract == extract {
         // This is always executed
      }
      if extract < 2 {
         // This might be executed, but might not be executed.
         // Even though the original vector components are 0 and 1,
         // the extracted value might not be either of those values.
      }
   }
   if extracted_values[0] == extracted_values[1] {
      // This might be executed, but might not be executed.
   }
}

fn float_fun(runtime_index: u32) {
   const v = vec2<f32>(0,1); // A vector of floating point values

   // As in the previous example, 'float_extract' is an indeterminate value.
   // Since it is a floating point type, it may be a NaN.
   let float_extract: f32 = v[runtime_index+5];

   if float_extract == float_extract {
      // This *might not* be executed, because:
      // - 'float_extract' may be NaN, and
      // - a NaN is never equal to any other floating point number,
      // even another NaN.
   }
}

### 8.3. Literal Value Expressions[](#literal-expressions)

Scalar literal type rules
| Precondition | Conclusion | Description | | `true`: bool | `true` boolean value. | | | `false`: bool | `false` boolean value. | | e is an [integer literal](#integer-literal) with no suffix | e: AbstractInt | Abstract integer literal value. | | e is a [floating point literal](#floating-point-literal) with no suffix | e: AbstractFloat | Abstract float literal value. | | e is an [integer literal](#integer-literal) with `i` suffix | e: i32 | 32-bit signed integer literal value. | | e is an [integer literal](#integer-literal) with `u` suffix | e: u32 | 32-bit unsigned integer literal value. | | e is an [floating point literal](#floating-point-literal) with `f` suffix | e: f32 | 32-bit floating point literal value. | | e is an [floating point literal](#floating-point-literal) with `h` suffix | e: f16 | 16-bit floating point literal value. | |
| --- | --- | --- |

### 8.4. Parenthesized Expressions[](#parenthesized-expressions)

Parenthesized expression type rules
| Precondition | Conclusion | Description | e : T | `(`e`)` : T | Evaluates to e. Use parentheses to isolate an expression from the surrounding text. | |
| --- | --- | --- |

### 8.5. Composite Value Decomposition Expressions[](#composite-value-decomposition-expr)

This section describes expressions for:

*   getting a [component](#components) of a [composite](#composite) value,

*   getting a [reference](#reference-type) to a [component](#components) from a [memory view](#memory-view) to the containing composite value,

*   getting a [reference](#reference-type) to a vector [component](#components) from a [swizzle view](#swizzle-view) of that vector in memory.

For this discussion, the composite value, or the memory view to the composite value, or the swizzle view is known as the base.

There are two ways of forming such expressions:

named component expression
The expression for the [base](#decomposition-base)_B_ is followed by a period `'.'` (U+002D), and then the name of the component.

*   This is supported when _B_ is of [vector](#vector) or [structure](#structure) type, a memory view to a vector or structure type, or a swizzle view.

*   The valid names depend on _B_'s type.

indexing expression
The expression for the base is followed by `'['` (U+005B), then the expression for an index then `']'` (U+005D).

*   The base may be a [vector](#vector), [matrix](#matrix), or [fixed-size array](#fixed-size-array) type, or a [memory view](#memory-view) to a vector, matrix, fixed-size array, or [runtime-sized](#runtime-sized) array type. The base may also be a [swizzle view](#swizzle-view), as a special case of a memory view.

*   The index expression [must](#shader-creation-error) be of [integer scalar](#integer-scalar) type.

Syntactically, these two forms are embodied by uses of the [component_or_swizzle_specifier](#syntax-component_or_swizzle_specifier) grammar rule.

The index value i of an [indexing expression](#indexing-expression) is an in-bounds index if 0 ≤ i<N, where N is the number of components (elements) of the composite type:

*   N is the number of components of the [vector](#vector) type, when the base is a vector or a [memory view](#memory-view) to a vector.

*   N is the number of columns of the [matrix](#matrix) type, when the base is a matrix or a memory view to a matrix.

*   N is the [element count](#element-count) of the [fixed-size array](#fixed-size-array) type, when the base is a fixed-size array or a memory view to a fixed-size array.

*   N is [NRuntime](#nruntime) for the base, when the base is a memory view to a [runtime-sized](#runtime-sized) array.

The index value is an out-of-bounds index when it is not an [in-bounds index](#in-bounds-index). An out-of-bounds index is often a programming defect, and will often cause a [error](#errors). See below for details.

Additionally, vector types support a [swizzling](#swizzle) syntax for creating a new vector value from the components of another vector.

#### 8.5.1. Vector Access Expression[](#vector-access-expr)

Accessing components of a vector can be done either:

*   Using array subscripting (e.g. `v[2]`), or

*   Using a swizzle name, a [context-dependent name](#context-dependent-name) written as a sequence of convenience names, each mapping to a component of the source vector.

    *   The color set of convenience names: `r`, `g`, `b`, `a` for vector components 0, 1, 2, and 3 respectively.

    *   The dimensional set of convenience names: `x`, `y`, `z`, `w` for vector components 0, 1, 2, and 3, respectively.

The convenience names are accessed using the `.` notation. (e.g. `color.bgra`).

The convenience letterings [must not](#shader-creation-error) be mixed. For example, you cannot use `.rybw`.

A convenience letter [must not](#shader-creation-error) access a component past the end of the vector.

The convenience letterings can be applied in any order, including duplicating letters as needed. The provided number of letters [must](#shader-creation-error) be between 1 and 4. That is, using convenience letters can only produce a scalar type or a valid vector type.

The result type depends on the number of letters provided. Assuming a `vec4<f32>`

| Accessor | Result type | r | `f32` | | rg | `vec2<f32>` | | rgb | `vec3<f32>` | | rgba | `vec4<f32>` | |
| --- | --- |

var a: vec3<f32> = vec3<f32>(1., 2., 3.);
var b: f32 = a.y;          // b = 2.0
var c: vec2<f32> = a.bb;   // c = (3.0, 3.0)
var d: vec3<f32> = a.zyx;  // d = (3.0, 2.0, 1.0)
var e: f32 = a[1];         // e = 2.0

##### 8.5.1.1. Vector Single Component Selection[](#vector-single-component)

Vector decomposition: single component selection
| Precondition | Conclusion | Description | e: vec N<T> | e`.x`: T e`.r`: T | Select the first component of e This is a single-letter [swizzle](#swizzle). | | e: vec N<T> | e`.y`: T e`.g`: T | Select the second component of e This is a single-letter [swizzle](#swizzle). | | e: vec N<T> N is 3 or 4 | e`.z`: T e`.b`: T | Select the third component of e This is a single-letter [swizzle](#swizzle). | | e: vec4<T> | e`.w`: T e`.a`: T | Select the fourth component of e This is a single-letter [swizzle](#swizzle). | | e: vec N<T> i: i32 or u32 T is [concrete](#type-concrete) | e[i]: T | Select the i'th component of vector The first component is at index i=0. If i is outside the range [0,N-1]: * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). * Otherwise an [indeterminate value](#indeterminate-value) for T may be returned. | | e: vec N<T> i: i32 or u32 T is [abstract](#type-abstract) i is a [const-expression](#const-expressions) | e[i]: T | Select the i'th component of vector The first component is at index i=0. It is a [shader-creation error](#shader-creation-error) if i is outside the range [0,N-1]. Note: When an abstract vector value e is indexed by an expression that is not a [const-expression](#const-expressions), then the vector is [concretized](#concretization-of-a-value) before the index is applied. | |
| --- | --- | --- |

##### 8.5.1.2. Vector Multiple Component Selection[](#vector-multi-component)

The expressions in this section apply a multi-letter [swizzle](#swizzle) to an inner expression:

*   If the inner expression is a [vector](#vector), the result is a vector. See the tables below.

*   If the inner expression is a [pointer](#pointer-type) or [reference](#reference-type) with a [vector](#vector)[store type](#store-type), then:

    *   If the [swizzle_assignment](#language_extension-swizzle_assignment) language extension is not supported, the result is a vector. See the tables below.

    *   If the [swizzle_assignment](#language_extension-swizzle_assignment) language extension is supported, see [§ 8.6 Swizzle View Expression](#swizzle-view-expr) instead.

Note: If the [swizzle_assignment](#language_extension-swizzle_assignment) language extension is not supported, then a multi-letter [swizzle](#swizzle) cannot appear on the left-hand side of an [assignment](#statement-assignment): The left-hand side of an assignment must be of [reference type](#reference-type), but without the extension a multi-letter swizzle expression always yields a value of [vector](#vector) type.

Vector decomposition: multiple component selection 
| Precondition | Conclusion | Description | e: vec N<T> I is the letter `x`, `y`, `z`, or `w` J is the letter `x`, `y`, `z`, or `w` | e`.`I J: vec2<T> | Computes the two-component vector with first component e.I, and second component e.J. Letter `z` is valid only when N is 3 or 4. Letter `w` is valid only when N is 4. | | e: vec N<T> I is the letter `r`, `g`, `b`, or `a` J is the letter `r`, `g`, `b`, or `a` | e`.`I J: vec2<T> | Computes the two-component vector with first component e.I, and second component e.J. Letter `b` is valid only when N is 3 or 4. Letter `a` is valid only when N is 4. | | e: vec N<T> I is the letter `x`, `y`, `z`, or `w` J is the letter `x`, `y`, `z`, or `w` K is the letter `x`, `y`, `z`, or `w` | e`.`I J K: vec3<T> | Computes the three-component vector with first component e.I, second component e.J, and third component e.K. Letter `z` is valid only when N is 3 or 4. Letter `w` is valid only when N is 4. | | e: vec N<T> I is the letter `r`, `g`, `b`, or `a` J is the letter `r`, `g`, `b`, or `a` K is the letter `r`, `g`, `b`, or `a` | e`.`I J K: vec3<T> | Computes the three-component vector with first component e.I, second component e.J, and third component e.K. Letter `b` is only valid when N is 3 or 4. Letter `a` is only valid when N is 4. | | e: vec N<T> I is the letter `x`, `y`, `z`, or `w` J is the letter `x`, `y`, `z`, or `w` K is the letter `x`, `y`, `z`, or `w` L is the letter `x`, `y`, `z`, or `w` | e`.`I J K L: vec4<T> | Computes the four-component vector with first component e.I, second component e.J, third component e.K, and fourth component e.L. Letter `z` is valid only when N is 3 or 4. Letter `w` is valid only when N is 4. | | e: vec N<T> I is the letter `r`, `g`, `b`, or `a` J is the letter `r`, `g`, `b`, or `a` K is the letter `r`, `g`, `b`, or `a` L is the letter `r`, `g`, `b`, or `a` | e`.`I J K L: vec4<T> | Computes the four-component vector with first component e.I, second component e.J, third component e.K, and fourth component e.L. Letter `b` is only valid when N is 3 or 4. Letter `a` is only valid when N is 4. | |
| --- | --- | --- |

Vector memory view decomposition: multiple component selection, when swizzle assignment is not supported 
| Precondition | Conclusion | Description | [swizzle_assignment](#language_extension-swizzle_assignment) is not supported pr: ref<AS,vec N<T,AM>> or ptr<AS,vec N<T,AM>> I is the letter `x`, `y`, `z`, or `w` J is the letter `x`, `y`, `z`, or `w` AM is `read` or `read_write` | pr`.`I J: vec2<T> | Computes e.I J, where e is the vector stored in the memory locations referenced by pr at the time of evaluation. Letter `z` is valid only when N is 3 or 4. Letter `w` is valid only when N is 4. | | [swizzle_assignment](#language_extension-swizzle_assignment) is not supported pr: ref<AS,vec N<T,AM>> or ptr<AS,vec N<T,AM>> I is the letter `r`, `g`, `b`, or `a` J is the letter `r`, `g`, `b`, or `a` AM is `read` or `read_write` | pr`.`I J: vec2<T> | Computes e.I J, where e is the vector stored in the memory locations referenced by pr at the time of evaluation. Letter `b` is valid only when N is 3 or 4. Letter `a` is valid only when N is 4. | | [swizzle_assignment](#language_extension-swizzle_assignment) is not supported pr: ref<AS,vec N<T,AM>> or ptr<AS,vec N<T,AM>> I is the letter `x`, `y`, `z`, or `w` J is the letter `x`, `y`, `z`, or `w` K is the letter `x`, `y`, `z`, or `w` AM is `read` or `read_write` | pr`.`I J K: vec3<T> | Computes e.I J K, where e is the vector stored in the memory locations referenced by pr at the time of evaluation. Letter `z` is valid only when N is 3 or 4. Letter `w` is valid only when N is 4. | | [swizzle_assignment](#language_extension-swizzle_assignment) is not supported pr: ref<AS,vec N<T,AM>> or ptr<AS,vec N<T,AM>> I is the letter `r`, `g`, `b`, or `a` J is the letter `r`, `g`, `b`, or `a` K is the letter `r`, `g`, `b`, or `a` AM is `read` or `read_write` | pr`.`I J K: vec3<T> | Computes e.I J K, where e is the vector stored in the memory locations referenced by pr at the time of evaluation. Letter `b` is only valid when N is 3 or 4. Letter `a` is only valid when N is 4. | | [swizzle_assignment](#language_extension-swizzle_assignment) is not supported pr: ref<AS,vec N<T,AM>> or ptr<AS,vec N<T,AM>> I is the letter `x`, `y`, `z`, or `w` J is the letter `x`, `y`, `z`, or `w` K is the letter `x`, `y`, `z`, or `w` L is the letter `x`, `y`, `z`, or `w` AM is `read` or `read_write` | pr`.`I J K L: vec4<T> | Computes e.I J K L, where e is the vector stored in the memory locations referenced by pr at the time of evaluation. Letter `z` is valid only when N is 3 or 4. Letter `w` is valid only when N is 4. | | [swizzle_assignment](#language_extension-swizzle_assignment) is not supported pr: ref<AS,vec N<T,AM>> or ptr<AS,vec N<T,AM>> I is the letter `r`, `g`, `b`, or `a` J is the letter `r`, `g`, `b`, or `a` K is the letter `r`, `g`, `b`, or `a` L is the letter `r`, `g`, `b`, or `a` AM is `read` or `read_write` | pr`.`I J K L: vec4<T> | Computes e.I J K L, where e is the vector stored in the memory locations referenced by pr at the time of evaluation. Letter `b` is only valid when N is 3 or 4. Letter `a` is only valid when N is 4. | |
| --- | --- | --- |

##### 8.5.1.3. Component Reference from Vector Memory View or Swizzle View[](#component-reference-from-vector-memory-view)

The expressions in this section form a [reference](#reference-type) to a single component of a [vector](#vector) in memory from the [memory view](#memory-view) of the whole vector or from a [swizzle view](#swizzle-view).

The WGSL [type rules](#type-rule) imply that such expressions can appear:

*   on the left-hand side of an [assignment](#statement-assignment), to write to that component in memory, or

*   any place where a reference to a vector component can appear. Since the [Load Rule](#load-rule) may apply, this includes any place where a scalar value can appear.

A [write access](#write-access) to a component of a vector **may** access all of the [memory locations](#memory-locations) associated with that vector.

Note: This means accesses to different components of a vector in memory by different invocations must be synchronized if at least one access is a [write access](#write-access). See [§ 17.11 Synchronization Built-in Functions](#sync-builtin-functions).

Getting a reference to a component from a memory view to a vector
| Precondition | Conclusion | Description | r: ref<AS,vec N<T>,AM> or ptr<AS,vec N<T>,AM> | r`.x`: ref<AS,T,AM> r`.r`: ref<AS,T,AM> | Compute a reference to the first component of the vector referenced by the [memory view](#memory-view)r. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | | r: ref<AS,vec N<T>,AM> or ptr<AS,vec N<T>,AM> | r`.y`: ref<AS,T,AM> r`.g`: ref<AS,T,AM> | Compute a reference to the second component of the vector referenced by the [memory view](#memory-view)r. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | | r: ref<AS,vec N<T>,AM> or ptr<AS,vec N<T>,AM> N is 3 or 4 | r`.z`: ref<AS,T,AM> r`.b`: ref<AS,T,AM> | Compute a reference to the third component of the vector referenced by the [memory view](#memory-view)r. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | | r: ref<AS,vec4<T>,AM> or ptr<AS,vec4<T>,AM> | r`.w`: ref<AS,T,AM> r`.a`: ref<AS,T,AM> | Compute a reference to the fourth component of the vector referenced by the [memory view](#memory-view)r. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | | r: ref<AS,vec N<T>,AM> or ptr<AS,vec N<T>,AM> i: i32 or u32 | r[i] : ref<AS,T,AM> | Compute a reference to the i'th component of the vector referenced by the [memory view](#memory-view)r. If i is outside the range [0,N-1]: * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). * Otherwise, the expression evaluates to an [invalid memory reference](#invalid-memory-reference). The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | |
| --- | --- | --- |

Getting a reference to a component from a swizzle view
| Precondition | Conclusion | Description | sv : swizzle<AS,S,N,K> | sv.`x`: ref<AS,S,read_write> sv.`r`: ref<AS,S,read_write> | Let sv be the [swizzle view](#swizzle-view) (p, «Idx 0,...,Idx K−1»). The result is a reference to the component with index Idx 0 inside the memory view for pointer p. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of sv. | | sv : swizzle<AS,S,N,K> | sv.`y`: ref<AS,S,read_write> sv.`g`: ref<AS,S,read_write> | Let sv be the [swizzle view](#swizzle-view) (p, «Idx 0,...,Idx K−1»). The result is a reference to the component with index Idx 1 inside the memory view for pointer p. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of sv. | | sv : swizzle<AS,S,N,K> where K ≥ 3 | sv.`z`: ref<AS,S,read_write> sv.`b`: ref<AS,S,read_write> | Let sv be the [swizzle view](#swizzle-view) (p, «Idx 0,...,Idx K−1»). The result is a reference to the component with index Idx 2 inside the memory view for pointer p. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of sv. | | sv : swizzle<AS,S,N,K> where K = 4 | sv.`w`: ref<AS,S,read_write> sv.`a`: ref<AS,S,read_write> | Let sv be the [swizzle view](#swizzle-view) (p, «Idx 0,...,Idx K−1»). The result is a reference to the component with index Idx 3 inside the memory view for pointer p. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of sv. | | sv : swizzle<AS,S,N,K> i : i32 or u32 | sv[i]: ref<AS,S,read_write> | Let sv be the [swizzle view](#swizzle-view) (p, «Idx 0,...,Idx K−1»). If i is in [0, K), the expression is the reference > (*p)[ Idxi] Note: The result is an invalid memory reference if sv is an [invalid swizzle view](#invalid-swizzle-view). If i is outside [0,K): * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). * Otherwise the result is an [invalid memory reference](#invalid-memory-reference). The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of sv. | |
| --- | --- | --- |

#### 8.5.2. Matrix Access Expression[](#matrix-access-expr)

Column vector extraction
| Precondition | Conclusion | Description | e: mat C x R<T> i: i32 or u32 T is [concrete](#type-concrete) | e[i]: vec R<T> | The result is the i'th column vector of e. If i is outside the range [0,C-1]: * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). * Otherwise, an [indeterminate value](#indeterminate-value) for vec R<T> may be returned. | | e: mat C x R<T> i: i32 or u32 T is [abstract](#type-abstract) i is a [const-expression](#const-expressions) | e[i]: vec R<T> | The result is the i'th column vector of e. It is a [shader-creation error](#shader-creation-error) if i is outside the range [0,C-1]. Note: When an abstract matrix value e is indexed by an expression that is not a [const-expression](#const-expressions), then the matrix is [concretized](#concretization-of-a-value) before the index is applied. | |
| --- | --- | --- |

Getting a reference to a column vector from a memory view to a matrix
| Precondition | Conclusion | Description | r: ref<AS,mat C x R<T>,AM> or ptr<AS,mat C x R<T>,AM> i: i32 or u32 | r[i] : ref<AS,vec R<T>,AM> | Compute a reference to the i'th column vector of the matrix referenced by the [memory view](#memory-view)r. If i is outside the range [0,C-1]: * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). * Otherwise, the expression evaluates to an [invalid memory reference](#invalid-memory-reference). The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | |
| --- | --- | --- |

#### 8.5.3. Array Access Expression[](#array-access-expr)

Array element extraction
| Precondition | Conclusion | Description | e: array<T,N> i: i32 or u32 T is [concrete](#type-concrete) | e[i] : T | The result is the value of the i'th element of the array value e. If i is outside the range [0,N-1]: * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). * Otherwise, an [indeterminate value](#indeterminate-value) for T may be returned. | | e: array<T,N> i: i32 or u32 T is [abstract](#type-abstract) i is a [const-expression](#const-expressions) | e[i] : T | The result is the value of the i'th element of the array value e. It is a [shader-creation error](#shader-creation-error) if i is outside the range [0,N-1]. Note: When an abstract array value e is indexed by an expression that is not a [const-expression](#const-expressions), then the array is [concretized](#concretization-of-a-value) before the index is applied. | |
| --- | --- | --- |

Getting a reference to an array element from a memory view to an array
| Precondition | Conclusion | Description | r: ref<AS,array<T,N>,AM> or ptr<AS,array<T,N>,AM> i: i32 or u32 | r[i] : ref<AS,T,AM> | Compute a reference to the i'th element of the array referenced by the [memory view](#memory-view)r. If i is outside the range [0,N-1]: * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). * Otherwise, the expression evaluates to an [invalid memory reference](#invalid-memory-reference). The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | | r: ref<AS,array<T>,AM> or ptr<AS,array<T>,AM> i: i32 or u32 | r[i] : ref<AS,T,AM> | Compute a reference to the i'th element of the runtime-sized array referenced by the [memory view](#memory-view)r. If at runtime the array has N elements, and i is outside the range [0,N-1], then the expression evaluates to an [invalid memory reference](#invalid-memory-reference). If i is a signed integer, and i is less than 0: * It is a [shader-creation error](#shader-creation-error) if i is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if i is an [override-expression](#override-expressions). The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | |
| --- | --- | --- |

#### 8.5.4. Structure Access Expression[](#struct-access-expr)

Structure member extraction
| Precondition | Conclusion | Description | S is a structure type M is the identifier name of a member of S, having type T e: S | e.M: T | The result is the value of the member with name M from the structure value e. | |
| --- | --- | --- |

Getting a reference to a structure member from a memory view to a structure
| Precondition | Conclusion | Description | S is a structure type M is the identifier name of a member of S, having type T r: ref<AS,S,AM> or ptr<AS,S,AM> | r.M: ref<AS,T,AM> | Given a memory view to a structure, the result is a reference to the structure member with identifier name M. The [originating variable](#originating-variable) of the resulting reference is the same as the originating variable of r. | |
| --- | --- | --- |

### 8.6. Swizzle View Expression[](#swizzle-view-expr)

Swizzle view expressions are enabled by the [swizzle_assignment](#language_extension-swizzle_assignment) language extension.

A [swizzle view](#swizzle-view) is formed by:

*   Applying a multi-letter [swizzle](#swizzle) name to a [reference](#reference-type) or [pointer](#pointer-type) value with [read_write](#access-read_write) access mode and whose [store type](#store-type) is a vector, or

*   Applying a multi-letter [swizzle](#swizzle) name to a swizzle view.

By these rules, the index list part of a swizzle view is fully determined at [shader-creation](#shader-module-creation) time.

In this section the swizzle index function SI is defined as:

*   SI(`x`) = 0

*   SI(`y`) = 1

*   SI(`z`) = 2

*   SI(`w`) = 3

*   SI(`r`) = 0

*   SI(`g`) = 1

*   SI(`b`) = 2

*   SI(`a`) = 3

We say a [swizzle](#swizzle) name Z represents the K indices «Idx 0, ..., Idx K−1 » if:

*   One of the following is true:

    *   Each letter in Z is `x`, `y`, `z`, or `w`, or

    *   Each letter in Z is `r`, `g`, `b`, or `a`

*   Each Idx i equals SI(L), where L is the i’th letter in Z.

Note: For example, the swizzle `wzyx` represents the four indices «3, 2, 1, 0», and the swizzle `rb` represents the two indices «0, 2». The swizzle `rgbz` does not represent any index sequence, since it mixes `rgba` and `xyzw` letters.

Forming a swizzle view from a reference
| Precondition | Conclusion | Description | [swizzle_assignment](#language_extension-swizzle_assignment) is supported r: ref<AS,T,read_write> T is vec N<S> The swizzle name Z represents the K indices I = «Idx 0, ..., Idx K−1 » K in {2,3,4} | r.Z: swizzle<AS,S,N,K> | Result is the [swizzle view](#swizzle-view) (&r, I). Each index in I[must](#shader-creation-error) be less than N. If r is an [invalid memory reference](#invalid-memory-reference), then the result is an [invalid swizzle view](#invalid-swizzle-view). | |
| --- | --- | --- |

Forming a swizzle view from a pointer
| Precondition | Conclusion | Description | [swizzle_assignment](#language_extension-swizzle_assignment) is supported [pointer_composite_access](#language_extension-pointer_composite_access) is supported p: ptr<AS,T,read_write> T is vec N<S> The swizzle name Z represents the K indices I = «Idx 0, ..., Idx K−1 » K in {2,3,4} | p.Z: swizzle<AS,S,N,K> | Result is the [swizzle view](#swizzle-view) (p, I) Each index in I[must](#shader-creation-error) be less than N. If p is an [invalid pointer](#invalid-pointer), then the result is an [invalid swizzle view](#invalid-swizzle-view). | |
| --- | --- | --- |

Forming a swizzle view from a swizzle view
| Precondition | Conclusion | Description | sv: swizzle<AS,S,N,K in> The swizzle name Z represents the K Z indices I Z = «I Z[0],...,I Z[K Z−1]» K Z in {2,3,4} | sv.Z: swizzle<AS,S,N,K Z> | Let sv be the [swizzle view](#swizzle-view) (p, I in). By definition, the sequence I in has K in items. Let I out be the sequence «I in [I Z [0]], ..., I in [I Z [K Z -1]]». The expression result is the [swizzle view](#swizzle-view) (p, I out). Each index in I Z[must](#shader-creation-error) be less than K in. If sv is an [invalid swizzle view](#invalid-swizzle-view), then the result is an [invalid swizzle view](#invalid-swizzle-view). | |
| --- | --- | --- |

### 8.7. Logical Expressions[](#logical-expr)

Unary logical operations
| Precondition | Conclusion | Description | e: T T is bool or vec N<bool> | `!`e: T | Logical negation. The result is `true` when e is `false` and `false` when e is `true`. [Component-wise](#component-wise) when T is a vector. | |
| --- | --- | --- |

Binary logical expressions
| Precondition | Conclusion | Description | e1: bool e2: bool | e1`||`e2`: bool` | Short-circuiting "or". Yields `true` if either e1 or e2 are true; evaluates e2 only if e1 is false. | | e1: bool e2: bool | e1`&&`e2`: bool` | Short-circuiting "and". Yields `true` if both e1 and e2 are true; evaluates e2 only if e1 is true. | | e1: T e2: T T is bool or vec N<bool> | e1`|`e2`:`T | Logical "or". [Component-wise](#component-wise) when T is a vector. Evaluates both e1 and e2. | | e1: T e2: T T is bool or vec N<bool> | e1`&`e2`:`T | Logical "and". [Component-wise](#component-wise) when T is a vector. Evaluates both e1 and e2. | |
| --- | --- | --- |

### 8.8. Arithmetic Expressions[](#arithmetic-expr)

Unary arithmetic expressions
| Precondition | Conclusion | Description | e: T T is AbstractInt, AbstractFloat, i32, f32, f16, vec N<AbstractInt>, vec N<AbstractFloat>, vec N<i32>, vec N<f32>, or vec N<f16> | `-`e`:`T | Negation. [Component-wise](#component-wise) when T is a vector. If T is an [integer scalar](#integer-scalar) type and e evaluates to the largest negative value, then the result is e. | |
| --- | --- | --- |

Binary arithmetic expressions
| Precondition | Conclusion | Description | e1 : T e2 : T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> | e1`+`e2 : T | Addition. [Component-wise](#component-wise) when T is a vector. If T is a floating point type, the scalar [domain](#domain) is the set of all pairs of [extended reals](#extended-real) (x,y) except: * (−∞,+∞) * (+∞,−∞) | | e1 : T e2 : T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> | e1`-`e2 : T | Subtraction [Component-wise](#component-wise) when T is a vector. If T is a floating point type, the scalar [domain](#domain) is the set of all pairs of [extended reals](#extended-real) (x,y) except: * (−∞,−∞) * (+∞,+∞) | | e1 : T e2 : T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> | e1`*`e2 : T | Multiplication. [Component-wise](#component-wise) when T is a vector. If T is a floating point type, the scalar [domain](#domain) is the set of all pairs of [extended reals](#extended-real) (x,y) except: * (0,−∞) * (0,+∞) * (−∞, 0) * (+∞, 0) | | e1 : T e2 : T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> | e1`/`e2 : T | Division. [Component-wise](#component-wise) when T is a vector. If T is a signed [integer scalar](#integer-scalar) type, evaluates to: * If e2 is zero: * It is a [shader-creation error](#shader-creation-error) if e2 is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e2 is an [override-expression](#override-expressions). * Otherwise, e1. * If e1 is most negative value in T, and e2 is -1: * It is a [shader-creation error](#shader-creation-error) if e1 and e2 are [const-expressions](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e1 and e2 are [override-expressions](#override-expressions). * Otherwise, e1. * [truncate](#truncate)(x) otherwise, where x is the real-valued quotient e1÷e2. Note: The need to ensure truncation behavior may require an implementation to perform more operations than when computing an unsigned division. Use unsigned division when both operands are known to have the same sign. If T is an unsigned [integer scalar](#integer-scalar) type, evaluates to: * If e2 is zero: * It is a [shader-creation error](#shader-creation-error) if e2 is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e2 is an [override-expression](#override-expressions). * Otherwise, e1. * Otherwise, the integer q such that e1=q×e2+r, where 0 ≤ r<e2. If T is a floating point type, the scalar [domain](#domain) is the set of all pairs of [extended reals](#extended-real) (x,y) except: * (0,0) * (−∞,−∞) * (−∞,+∞) * (+∞,−∞) * (+∞,+∞) | | e1 : T e2 : T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> | e1`%`e2 : T | Remainder. [Component-wise](#component-wise) when T is a vector. If T is a signed [integer scalar](#integer-scalar) type, evaluates e1 and e2 once, and evaluates to: * if e2 is zero: * It is a [shader-creation error](#shader-creation-error) if e2 is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e2 is an [override-expression](#override-expressions). * Otherwise, 0. * If e1 is the most negative value in T, and e2 is -1: * It is a [shader-creation error](#shader-creation-error) if e1 and e2 are [const-expressions](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e1 and e2 are [override-expressions](#override-expressions). * Otherwise, 0. * Otherwise, e1-[truncate](#truncate)(e1÷e2)×e2 where the quotient is computed as a real value. Note: When non-zero, the result has the same sign as e1. Note: The need to ensure consistent behavior may require an implementation to perform more operations than when computing an unsigned remainder. If T is an unsigned [integer scalar](#integer-scalar) type, evaluates to: * if e2 is zero: * It is a [shader-creation error](#shader-creation-error) if e2 is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e2 is an [override-expression](#override-expressions). * Otherwise, 0. * Otherwise, the integer r such that e1=q×e2+r, where q is an integer and 0 ≤ r<e2. If T is a floating point type, the result is equal to: e1 - e2 * trunc(e1 / e2). If T is a floating point type, the scalar [domain](#domain) is the set of all pairs of [extended reals](#extended-real) (x,y) except: * Cases outside the domain of x / y: * (0,0) * (−∞,−∞) * (−∞,+∞) * (+∞,−∞) * (+∞,+∞) * Additional cases outside the domain of y * trunc(x / y): * y is infinite, and x is finite, implying trunc(x / y) is 0. * y is 0, and x is infinite, implying trunc(x / y) is infinite. | |
| --- | --- | --- |

Binary arithmetic expressions with mixed scalar and vector operands
| Preconditions | Conclusions | Semantics | S is one of AbstractInt, AbstractFloat, f32, f16, i32, u32 V is vec N<S> es: S ev: V | ev`+`es: V | ev`+`V(es) | | es`+`ev: V | V(es) `+`ev | | ev`-`es: V | ev`-`V(es) | | es`-`ev: V | V(es) `-`ev | | ev`*`es: V | ev`*`V(es) | | es`*`ev: V | V(es) `*`ev | | ev`/`es: V | ev`/`V(es) | | es`/`ev: V | V(es) `/`ev | | ev`%`es: V | ev`%`V(es) | | es`%`ev: V | V(es) `%`ev | |
| --- | --- | --- |

Matrix arithmetic
| Preconditions | Conclusions | Semantics | e1, e2: mat C x R<T> T is AbstractFloat, f32, or f16 | e1`+`e2: mat C x R<T> | Matrix addition: results are computed [component-wise](#component-wise), column i of the result is e1[i] + e2[i] | | e1`-`e2: mat C x R<T> | Matrix subtraction: results are computed [component-wise](#component-wise), column i of the result is e1[i] - e2[i] | | m: mat C x R<T> s: T T is AbstractFloat, f32, or f16 | m`*`s: mat C x R<T> | [Component-wise](#component-wise) scaling: (m`*`s)[i][j] is m[i][j] `*`s | | s`*`m: mat C x R<T> | [Component-wise](#component-wise) scaling: (s`*`m)[i][j] is m[i][j] `*`s | | m: mat C x R<T> v: vec C<T> T is AbstractFloat, f32, or f16 | m`*`v: vec R<T> | Linear algebra matrix-column-vector product: Component i of the result is `dot`(transpose(m)[i],v) | | m: mat C x R<T> v: vec R<T> T is AbstractFloat, f32, or f16 | v`*`m: vec C<T> | Linear algebra row-vector-matrix product: [transpose](#transpose)(transpose(m) `*` transpose(v)) | | e1: mat K x R<T> e2: mat C x K<T> T is AbstractFloat, f32, or f16 | e1`*`e2: mat C x R<T> | Linear algebra matrix product. | |
| --- | --- | --- |

### 8.9. Comparison Expressions[](#comparison-expr)

Comparisons
| Precondition | Conclusion | Description | e1: T e2: T S is AbstractInt, AbstractFloat, bool, i32, u32, f32, or f16 T is S or vec N<S> TB is vec N<bool> if T is a vector, otherwise TB is bool | e1`==`e2`:`TB | Equality. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: T S is AbstractInt, AbstractFloat, bool, i32, u32, f32, or f16 T is S or vec N<S> TB is vec N<bool> if T is a vector, otherwise TB is bool | e1`!=`e2`:`TB | Inequality. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> TB is vec N<bool> if T is a vector, otherwise TB is bool | e1`<`e2`:`TB | Less than. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> TB is vec N<bool> if T is a vector, otherwise TB is bool | e1`<=`e2`:`TB | Less than or equal. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> TB is vec N<bool> if T is a vector, otherwise TB is bool | e1`>`e2`:`TB | Greater than. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: T S is AbstractInt, AbstractFloat, i32, u32, f32, or f16 T is S, or vecN<S> TB is vec N<bool> if T is a vector, otherwise TB is bool | e1`>=`e2`:`TB | Greater than or equal. [Component-wise](#component-wise) when T is a vector. | |
| --- | --- | --- |

### 8.10. Bit Expressions[](#bit-expr)

Unary bitwise operations
| Precondition | Conclusion | Description | e: T S is AbstractInt, i32, or u32 T is S or vecN<S> | `~`e : T | Bitwise complement on e. Each bit in the result is the opposite of the corresponding bit in e. [Component-wise](#component-wise) when T is a vector. | |
| --- | --- | --- |

Binary bitwise operations
| Precondition | Conclusion | Description | e1: T e2: T S is AbstractInt, i32, or u32 T is S or vecN<S> | e1`|`e2: T | Bitwise-or. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: T S is AbstractInt, i32, or u32 T is S or vecN<S> | e1`&`e2: T | Bitwise-and. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: T S is AbstractInt, i32, or u32 T is S or vecN<S> | e1`^`e2: T | Bitwise-exclusive-or. [Component-wise](#component-wise) when T is a vector. | |
| --- | --- | --- |

Bit shift expressions
| Precondition | Conclusion | Description | e1: T e2: TS S is i32 or u32 T is S or vec N<S> TS is u32 when T is S, otherwise TS is vec N<u32> | e1`<<`e2: T | Shift left (shifted value is concrete): Shift e1 left, inserting zero bits at the least significant positions, and discarding the most significant bits. The number of bits to shift is the value of e2, modulo the bit width of e1. If e2 is greater than or equal to the bit width of e1, then: * It is a [shader-creation error](#shader-creation-error) if e2 is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e2 is an [override-expression](#override-expressions). When both e1 and e2 are known before [shader execution start](#shader-execution-start), the result must not overflow: * If T is a signed integer type, and the e2+1 most significant bits of e1 do not have the same bit value, then: * It is a [shader-creation error](#shader-creation-error) if e1 and e2 are [const-expressions](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e1 and e2 are [override-expressions](#override-expressions). * If T is an unsigned integer type, and any of the e2 most significant bits of e1 are 1, then: * It is a [shader-creation error](#shader-creation-error) if e1 and e2 are [const-expressions](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e1 and e2 are [override-expressions](#override-expressions). [Component-wise](#component-wise) when T is a vector. | | e1: T e2: TS T is AbstractInt or vec N<AbstractInt> TS is u32 when T is AbstractInt, otherwise TS is vec N<u32> | e1`<<`e2: T | Shift left (shifted value abstract): Shift e1 left, inserting zero bits at the least significant positions, and discarding the most significant bits. The number of bits to shift is the value of e2. The e2+1 most significant bits of e1[must](#shader-creation-error) have the same bit value. Otherwise overflow would occur. Note: This condition means all the discarded bits must be the same as the sign bit of the original value, and the same as the sign bit of the final value. [Component-wise](#component-wise) when T is a vector. | | e1: T e2: TS S is i32 or u32 T is S or vec N<S> TS is u32 when T is S, otherwise TS is vec N<u32> | e1>>e2: T | Shift right (shifted value is concrete). Shift e1 right, discarding the least significant bits. If S is an unsigned type, insert zero bits at the most significant positions. If S is a signed type: * If e1 is negative, each inserted bit is 1, and so the result is also negative. * Otherwise, each inserted bit is 0. The number of bits to shift is the value of e2, modulo the bit width of e1. If e2 is greater than or equal to the bit width or e1, then: * It is a [shader-creation error](#shader-creation-error) if e2 is a [const-expression](#const-expressions). * It is a [pipeline-creation error](#pipeline-creation-error) if e2 is an [override-expression](#override-expressions). [Component-wise](#component-wise) when T is a vector. | | e1: T e2: TS T is AbstractInt or vec N<AbstractInt> TS is u32 when T is AbstractInt, otherwise TS is vec N<u32> | e1>>e2: T | Shift right (abstract). Shift e1 right, discarding the least significant bits. If e1 is negative, each inserted bit is 1, and so the result is also negative. Otherwise, each inserted bit is 0. The number of bits to shift is the value of e2. [Component-wise](#component-wise) when T is a vector. | |
| --- | --- | --- |

### 8.11. Function Call Expression[](#function-call-expr)

A function call expression executes a [function call](#function-call) where the called function has a [return type](#return-type). If the called function does not return a value, a function call statement should be used instead. See [§ 9.5 Function Call Statement](#function-call-statement).

### 8.12. Variable Identifier Expression[](#var-identifier-expr)

Getting a reference from a variable name
| Precondition | Conclusion | Description | v is an [identifier](#identifier)[resolving](#resolves) to an [in-scope](#in-scope) variable declared in [address space](#address-spaces)AS with [store type](#store-type)T and [access mode](#access-mode)AM | v: ref<AS,T,AM> | Result is a reference to the memory for the named variable v. | |
| --- | --- | --- |

### 8.13. Formal Parameter Expression[](#formal-parameter-expr)

Getting the value of an identifier declared as a formal parameter to a function
| Precondition | Conclusion | Description | a is an [identifier](#identifier)[resolving](#resolves) to an [in-scope](#in-scope) formal parameter declaration with type T | a: T | Result is the value supplied for the corresponding function call operand at the [call site](#call-site) invoking this instance of the function. | |
| --- | --- | --- |

### 8.14. Address-Of Expression[](#address-of-expr)

The address-of operator converts a reference to its corresponding pointer.

Getting a pointer from a reference
| Precondition | Conclusion | Description | r: ref<AS,T,AM> | `&`r: ptr<AS,T,AM> | Result is the pointer value corresponding to the same [memory view](#memory-view) as the reference value r. If r is an [invalid memory reference](#invalid-memory-reference), then the resulting pointer is also an invalid memory reference. It is a [shader-creation error](#shader-creation-error) if AS is the [handle](#address-spaces-handle) address space. It is a [shader-creation error](#shader-creation-error) if r is a [reference to a vector component](#component-reference-from-vector-memory-view). | |
| --- | --- | --- |

### 8.15. Indirection Expression[](#indirection-expr)

The indirection operator converts a pointer to its corresponding reference.

Getting a reference from a pointer
| Precondition | Conclusion | Description | p: ptr<AS,T,AM> | `*`p: ref<AS,T,AM> | Result is the reference value corresponding to the same [memory view](#memory-view) as the pointer value p. If p is an [invalid memory reference](#invalid-memory-reference), then the resulting reference is also an invalid memory reference. | |
| --- | --- | --- |

### 8.16. Identifier Expressions for Value Declarations[](#value-identifier-expr)

Getting the value of a `const`-, `override`-, or `let`-declared identifiers
| Precondition | Conclusion | Description | c is an [identifier](#identifier)[resolving](#resolves) to an [in-scope](#in-scope)[const-declaration](#const-declaration) with type T | c: T | Result is the value computed for the initializer expression. The expression is a [const-expression](#const-expressions), and is evaluated at [shader-creation](#shader-module-creation) time. | | c is an [identifier](#identifier)[resolving](#resolves) to an [in-scope](#in-scope)[override-declaration](#override-declaration) with type T | c: T | If pipeline creation specified a value for the [constant ID](#pipeline-constant-id), then the result is that value. This value may be different for different pipeline instances. Otherwise, the result is the value computed for the initializer expression. Pipeline-overridable constants appear at module-scope, so evaluation occurs before the shader begins execution. Note: Pipeline creation fails if no initial value was specified in the API call and the `let`-declaration has no initializer expression. | | c is an [identifier](#identifier)[resolving](#resolves) to an [in-scope](#in-scope)[let-declaration](#let-declaration) with type T | c: T | Result is the value computed for the initializer expression. A [let-declaration](#let-declaration) appears inside a function body, and its initializer is evaluated each time control flow reaches the declaration. | |
| --- | --- | --- |

### 8.17. Enumeration Expressions[](#enum-expr)

Enumeration expressions
| Precondition | Conclusion | Description | e is an [identifier](#identifier)[resolving](#resolves) to a [predeclared](#predeclared)[enumerant](#enumerant) belonging to [enumeration](#enumeration) type E | e : E | See [§ 6.4.1 Predeclared enumerants](#predeclared-enumerants) | |
| --- | --- | --- |

### 8.18. Type Expressions[](#type-expr)

Type expressions
| Precondition | Conclusion | Description | t is an [identifier](#identifier)[resolving](#resolves) to a [predeclared](#predeclared)[type](#type) | t : [AllTypes](#alltypes) | See [§ 6.10 Predeclared Types and Type-Generators Summary](#predeclared-types) | | a is an [identifier](#identifier)[resolving](#resolves) to a [type alias](#type-alias). | a : [AllTypes](#alltypes) | Additionally, a denotes the type to which it is aliased. | | s is an [identifier](#identifier)[resolving](#resolves) to the declaration of a [structure](#structure) type. | s : [AllTypes](#alltypes) | Additionally, s denotes the structure type. | | tg is an [identifier](#identifier)[resolving](#resolves) to a [type-generator](#type-generator) e1: T1 ... eN: TN | tg[_template_args_start](#syntax_sym-_template_args_start) e1, ..., eN [_template_args_end](#syntax_sym-_template_args_end) : [AllTypes](#alltypes) | Each [type-generator](#type-generator) has its own requirements on the template parameters it requires and accepts, and defines how the template parameters help determine the resulting type. The expressions e1 through eN are the [template parameters](#template-parameters) for the type-generator. For example, the type expression `vec2<f32>` is the [vector](#vector) of two [f32](#f32) elements. See [§ 6.10 Predeclared Types and Type-Generators Summary](#predeclared-types) for the list of predeclared type-generators. Note: The two variants here differ only in whether they have a trailing comma after eN. | | tg[_template_args_start](#syntax_sym-_template_args_start) e1, ..., eN, [_template_args_end](#syntax_sym-_template_args_end) : [AllTypes](#alltypes) | |
| --- | --- | --- |

### 8.19. Expression Grammar Summary[](#expression-grammar)

When an [identifier](#identifier) is the first [token](#token) in a [call_phrase](#syntax-call_phrase), it is one of:

*   The name of a [user-defined function](#user-defined-function) or [built-in function](#built-in-functions), as part of a [function call](#function-call).

*   The name of a [type](#type), [type alias](#type-aliases), or [type-generator](#type-generator), as part of a [value constructor](#value-constructor) expression.

[Declaration and scope](#declaration-and-scope) rules ensure those names are always distinct.

call_expression :

[call_phrase](#syntax-call_phrase)

 Note: The [call_expression](#syntax-call_expression) rule exists to ensure [type checking](#type-checking) applies to the call expression. 

paren_expression :

[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`')'`](#syntax_sym-paren_right)

argument_expression_list :

[`'('`](#syntax_sym-paren_left)[expression_comma_list](#syntax-expression_comma_list) ? [`')'`](#syntax_sym-paren_right)

expression_comma_list :

[expression](#syntax-expression) ( [`','`](#syntax_sym-comma)[expression](#syntax-expression) ) * [`','`](#syntax_sym-comma) ?

singular_expression :

[primary_expression](#syntax-primary_expression)[component_or_swizzle_specifier](#syntax-component_or_swizzle_specifier) ?

core_lhs_expression :

[ident](#syntax-ident)

|[`'('`](#syntax_sym-paren_left)[lhs_expression](#syntax-lhs_expression)[`')'`](#syntax_sym-paren_right)

|[call_expression](#syntax-call_expression)

multiplicative_operator :

[`'*'`](#syntax_sym-star)

|[`'/'`](#syntax_sym-forward_slash)

|[`'%'`](#syntax_sym-modulo)

additive_operator :

[`'+'`](#syntax_sym-plus)

|[`'-'`](#syntax_sym-minus)

binary_or_expression :

[unary_expression](#syntax-unary_expression)

|[binary_or_expression](#syntax-binary_or_expression)[`'|'`](#syntax_sym-or)[unary_expression](#syntax-unary_expression)

binary_and_expression :

[unary_expression](#syntax-unary_expression)

|[binary_and_expression](#syntax-binary_and_expression)[`'&'`](#syntax_sym-and)[unary_expression](#syntax-unary_expression)

binary_xor_expression :

[unary_expression](#syntax-unary_expression)

|[binary_xor_expression](#syntax-binary_xor_expression)[`'^'`](#syntax_sym-xor)[unary_expression](#syntax-unary_expression)

### 8.20. Operator Precedence and Associativity[](#operator-precedence-associativity)

This entire subsection is non-normative.

Operator precedence and associativity in [right-hand side WGSL expressions](#syntax-expression) emerge from their grammar in summary. Right-hand expressions group operators to organize them, as illustrated by the following diagram:

Operator precedence and associativity graph

To promote readability through verbosity, the following groups do not associate with other groups:

*   [Short-circuit OR](#syntax-short_circuit_or_expression) (can associate with [self](#syntax-short_circuit_or_expression) and [relational](#syntax-relational_expression) weakly),

*   [Short-circuit AND](#syntax-short_circuit_and_expression) (can associate with [self](#syntax-short_circuit_and_expression) and [relational](#syntax-relational_expression) weakly),

*   [Binary OR](#syntax-binary_or_expression) (can associate with [self](#syntax-binary_or_expression) and [unary](#syntax-unary_expression) weakly),

*   [Binary AND](#syntax-binary_and_expression) (can associate with [self](#syntax-binary_and_expression) and [unary](#syntax-unary_expression) weakly),

*   [Binary XOR](#syntax-binary_xor_expression) (can associate with [self](#syntax-binary_xor_expression) and [unary](#syntax-unary_expression) weakly).

And the following groups do not associate with themselves:

*   [Shift](#syntax-shift_expression) (can associate with [unary](#syntax-unary_expression) weakly),

*   [Relational](#syntax-relational_expression) (can associate with [additive](#syntax-additive_expression) and [shift](#syntax-shift_expression) weakly).

Associating both group sections above requires parentheses to set the relationship explicitly. The following exemplifies where these rules render expressions invalid in comments:

EXAMPLE: Operator precedence corner cases

let a = x & (y ^ (z | w)); // Invalid: x & y ^ z | w
let b = (x + y) << (z >= w); // Invalid: x + y << z >= w
let c = x < (y > z); // Invalid: x < y > z
let d = x && (y || z); // Invalid: x && y || z

Emergent precedence controls the implicit parentheses of an expression, where the stronger binding operator will act as if it is surrounded by parentheses when together with operators of weaker precedence. For example, stronger binding multiplicative operators than additive will infer `(a + (b * c))` from `a + b * c` expression. Similarly, the emergent associativity controls the direction of these implicit parentheses. For example, a left-to-right association will infer `((a + b) + c)` from `a + b + c` expression, whereas a right-to-left association will infer `(* (* a))` from `* * a` expression.

The following table summarizes operator precedence, associativity, and binding, sorting by starting with strongest to weakest. The binding column contains the stronger expression of the given operator, meaning, for example, if "All above" is the value, then this operator can include any of the stronger expressions. But, for example, if "Unary" is the value, then anything weaker than unary but stronger than the operator at row would require parentheses to bind with this operator. This column is necessary for linearly listing operators.

 Operator precedence, associativity, and binding for right-hand side expressions, sorted from strong to weak  

| Name | Operators | Associativity | Binding | [Parenthesized](#syntax-paren_expression) | `(...)` | | | | [Primary](#syntax-primary_expression) | `a()`, `a[]`, `a.b` | Left-to-right | | | [Unary](#syntax-unary_expression) | `-a`, `!a`, `~a`, `*a`, `&a` | Right-to-left | All above | | [Multiplicative](#syntax-multiplicative_expression) | `a*b`, `a/b`, `a%b` | Left-to-right | All above | | [Additive](#syntax-additive_expression) | `a+b`, `a-b` | Left-to-right | All above | | [Shift](#syntax-shift_expression) | `a<<b`, `a>>b` | Requires parentheses | Unary | | [Relational](#syntax-relational_expression) | `a<b`, `a>b`, `a<=b`, `a>=b`, `a==b`, `a!=b` | Requires parentheses | All above | | [Binary AND](#syntax-binary_and_expression) | `a&b` | Left-to-right | Unary | | [Binary XOR](#syntax-binary_xor_expression) | `a^b` | Left-to-right | Unary | | [Binary OR](#syntax-binary_or_expression) | `a|b` | Left-to-right | Unary | | [Short-circuit AND](#syntax-short_circuit_and_expression) | `a&&b` | Left-to-right | Relational | | [Short-circuit OR](#syntax-short_circuit_or_expression) | `a||b` | Left-to-right | Relational | |
| --- | --- | --- | --- |

## 9. Statements[](#statements)

A statement is a program fragment that controls execution. Statements are generally executed in sequential order; however, [control flow statements](#control-flow) may cause a program to execute in non-sequential order.

### 9.1. Compound Statement[](#compound-statement-section)

A compound statement is a brace-enclosed sequence of zero or more statements. When a [declaration](#declaration) is one of those statements, its [identifier](#identifier) is [in scope](#in-scope) from the start of the next statement until the end of the compound statement.

compound_statement :

[attribute](#syntax-attribute) * [`'{'`](#syntax_sym-brace_left)[statement](#syntax-statement) * [`'}'`](#syntax_sym-brace_right)

The [continuing_compound_statement](#syntax-continuing_compound_statement) is a special form of compound statement that forms the body of a [continuing](#continuing-statement) statement, and allows an optional [break-if](#break-if-statement) statement at the end.

### 9.2. Assignment Statement[](#assignment)

An assignment evaluates an expression, and optionally stores the result in memory (thus updating the contents of a variable).

assignment_statement :

[lhs_expression](#syntax-lhs_expression) ( [`'='`](#syntax_sym-equal) | [compound_assignment_operator](#syntax-compound_assignment_operator) ) [expression](#syntax-expression)

|[`'_'`](#syntax_sym-underscore)[`'='`](#syntax_sym-equal)[expression](#syntax-expression)

The text to the left of the operator token is the left-hand side, and the expression to the right of the operator token is the right-hand side.

#### 9.2.1. Simple Assignment[](#simple-assignment-section)

An [assignment](#statement-assignment) is a simple assignment when the [left-hand side](#left-hand-side) is a [reference](#reference-type) expression, and the operator is the equal ([`'='`](#syntax_sym-equal)) token. In this case the value of the [right-hand side](#right-hand-side) is written to the memory referenced by the left-hand side.

| Precondition | Statement | Description | e: T, T is a [concrete](#type-concrete)[constructible](#constructible) type, r: ref<AS,T,AM>, AS is a writable [address space](#address-spaces), [access mode](#access-mode)AM is [write](#access-write) or [read_write](#access-read_write) | r = e | Evaluates r, then evaluates e, then writes the value computed for e into the [memory locations](#memory-locations) referenced by r. Note: If the reference is an [invalid memory reference](#invalid-memory-reference), the write may not execute, or may write to a different memory location than expected. | |
| --- | --- | --- |

In the simplest case, the left hand side is the name of a variable. See [§ 6.5.9 Forming Reference and Pointer Values](#forming-references-and-pointers) for other cases.

EXAMPLE: Assignments

struct S {
    age: i32,
    weight: f32
}
var<private> person: S;

fn f() {
    var a: i32 = 20;
    a = 30;           // Replace the contents of 'a' with 30.

    person.age = 31;  // Write 31 into the age field of the person variable.

    var uv: vec2<f32>;
    uv.y = 1.25;      // Place 1.25 into the second component of uv.

    let uv_x_ptr: ptr<function,f32> = &uv.x;
    *uv_x_ptr = 2.5;  // Place 2.5 into the first component of uv.

    var sibling: S;
    // Copy the contents of the 'person' variable into the 'sibling' variable.
    sibling = person;
}

#### 9.2.2. Swizzle Assignment[](#swizzle-assignment-section)

This section only applies when the [swizzle_assignment](#language_extension-swizzle_assignment) language extension is supported.

An [assignment](#statement-assignment) is a swizzle assignment when the [left-hand side](#left-hand-side) is a [swizzle view](#swizzle-view), and the operator is the equal ([`'='`](#syntax_sym-equal)) token. In this case a [swizzle view write](#swizzle-view-write) is performed on the [left-hand side](#left-hand-side), using the value of the [right-hand side](#right-hand-side) as the update vector.

| Precondition | Statement | Description | sv : swizzle<AS,S,N,K> e : vec K<S> [Address space](#address-spaces)AS is writable, | sv = e | By convention sv = (p, IndexList) Constraints: * The indices in IndexList[must](#shader-creation-error) be all distinct from each other. Note: The swizzle view expression rules ensure that each index in IndexList will be in [0,N-1]. Perform the following steps. 1. Evaluate p. 2. Evaluate e, yielding vector update. 3. Read the memory referenced by p, yielding vector old_contents with type vec N<S>. 4. Perform [SwizzleViewWrite](#swizzle-view-write)(p, IndexList, old_contents, update) Note: If the swizzle view is an [invalid swizzle view](#invalid-swizzle-view), steps 3 and 4 are [out-of-bounds accesses](#out-of-bounds-access), and therefore may not execute, or may write to different memory locations than expected. Note: It may seem unnatural to evaluate e before reading the old contents of p. However, the swizzle write in step 4 must preserve the vector components _not_ listed in IndexList, and yet those components may have been modified during the evaluation of e itself. | |
| --- | --- | --- |

EXAMPLE: Swizzle assignment order of evaluation

var<private> v: array<vec4u,1>;

fn update_and_index() -> u32 {
  v[0] += vec4u(2,4,8,10);
  return 0;
}

fn update_and_rhs() -> vec2u {
  v[0].x = 900;
  v[0].z = 100;
  return vec2u(55,66);
}

fn eval_order_swizzle_assignment() {
  v[0] = vec4u(0,0,0,0);

  // 1. Evaluate the pointer p, which evaluates
  // the index on the left handside,
  // setting v[0] = vec4u(2,4,8,10) as a side effect
  // and yielding 0 for the index.
  // 2. Evaluate the right-hand size, setting
  // v[0].x = 900
  // v[0].z = 100
  // and yielding vec2u(55,66).
  // 3. The swizzle assignment then updates only v[0].x and v[0].y,
  // preserving v[0].z and v[0].w.

  v[update_and_index()].yx = update_and_rhs();

  // Now v[0] equals vec4u(66,55,100,10);
}

#### 9.2.3. Phony Assignment[](#phony-assignment-section)

An [assignment](#statement-assignment) is a phony assignment when the [left-hand side](#left-hand-side) is the underscore ([`'_'`](#syntax_sym-equal)) token. In this case the [right-hand side](#right-hand-side) is evaluated, and then ignored.

| Precondition | Statement | Description | e: T, T is [constructible](#constructible), a [pointer type](#pointer-type), a [texture](#texture) type, or a [sampler](#sampler) type | _ = e | Evaluates e. Note: The resulting value is not stored. The `_` token is not an identifier, and therefore cannot be used in an expression. | |
| --- | --- | --- |

A phony-assignment is useful for:

*   Calling a function that returns a value, but clearly expressing that the resulting value is not needed.

*   [Statically accessing](#statically-accessed) a variable, thus establishing it as a part of the [shader’s resource interface](#resource-interface-of-a-shader).

Note: A buffer variable’s store type may not be constructible, e.g. it contains an atomic type, or a runtime-sized array. In these cases, use a pointer to the variable’s contents instead.

EXAMPLE: Using phony-assignment to throw away an un-needed function result

var<private> counter: i32;

fn increment_and_yield_previous() -> i32 {
  let previous = counter;
  counter = counter + 1;
  return previous;
}

fn user() {
  // Increment the counter, but don't use the result.
  _ = increment_and_yield_previous();
}

EXAMPLE: Using phony-assignment to occupy bindings without using them

struct BufferContents {
    counter: atomic<u32>,
    data: array<vec4<f32>>
}
@group(0) @binding(0) var<storage> buf: BufferContents;
@group(0) @binding(1) var t: texture_2d<f32>;
@group(0) @binding(2) var s: sampler;

@fragment
fn shade_it() -> @location(0) vec4<f32> {
  // Declare that buf, t, and s are part of the shader interface, without
  // using them for anything.
  _ = &buf;
  _ = t;
  _ = s;
  return vec4<f32>();
}

#### 9.2.4. Compound Assignment[](#compound-assignment-sec)

An [assignment](#statement-assignment) is a compound assignment when the [left-hand side](#left-hand-side) is a [reference](#reference-type) expression or a [swizzle view](#swizzle-view), and the operator is one of the [compound_assignment_operators](#syntax-compound_assignment_operator).

compound_assignment_operator :

[`'+='`](#syntax_sym-plus_equal)

|[`'-='`](#syntax_sym-minus_equal)

|[`'*='`](#syntax_sym-times_equal)

|[`'/='`](#syntax_sym-division_equal)

|[`'%='`](#syntax_sym-modulo_equal)

|[`'&='`](#syntax_sym-and_equal)

|[`'|='`](#syntax_sym-or_equal)

|[`'^='`](#syntax_sym-xor_equal)

|[_shift_right_assign](#syntax_sym-_shift_right_assign)

|[_shift_left_assign](#syntax_sym-_shift_left_assign)

The type requirements, semantics, and behavior of each statement is defined as if the compound assignment expands as in the following table, except that:

*   If the expression e1 is a [reference](#reference-type) expression:

    *   The [reference type](#reference-type) for e1[must](#shader-creation-error) have a [read_write](#access-read_write)[access mode](#access-mode).

    *   Perform the following steps.

        1.   Evaluate &e1, yielding pointer p.

        2.   Read the memory referenced by p, yielding value old_contents.

Use old_contents as the value for e1 in the expansion given below.

        3.   Evaluate e2.

        4.   Compute update by performing the specified binary operation on old_contents and e2.

            *   For example, if the compound assignment is `v += w` then the specified operation is addition.

        5.   Write update to memory through pointer p.

*   If the expression e1 is a [swizzle view](#swizzle-view) expression:

    *   By convention swizzle view e1 can be written (p, IndexList)

        *   Note: The type for p has a [read_write](#access-read_write)[access mode](#access-mode).

    *   The same constraints apply as for [swizzle assignment](#swizzle-assignment):

        *   The indices in IndexList[must](#shader-creation-error) be all distinct from each other.

        *   Note: The swizzle view expression rules ensure that each index in IndexList will be in [0,N-1].

    *   Perform the following steps.

        1.   Evaluate p.

        2.   Perform [SwizzleViewRead](#swizzle-view-read)(p, IndexList), yielding vector viewed_contents of type vec K<S>.

This is the value for e1 when used as the left operand of the binary operator in the expansion given below. To ensure left-to-right evaluation of the binary expression, this must occur before the evaluation of e2.

        3.   Evaluate e2.

        4.   Read the memory referenced by p, yielding vector old_contents of type vec N<S>.

        5.   Compute update by performing the specified binary operation on viewed_contents and e2.

            *   For example, if the swizzle assignment is `v.xy += w` then the specified operation is addition.

        6.   Perform [SwizzleViewWrite](#swizzle-view-write)(p, IndexList, old_contents, update).

| Statement | Expansion | e1 += e2 | e1 = e1 + (e2) | | e1 -= e2 | e1 = e1 - (e2) | | e1 *= e2 | e1 = e1 * (e2) | | e1 /= e2 | e1 = e1 / (e2) | | e1 %= e2 | e1 = e1 % (e2) | | e1&= e2 | e1 = e1& (e2) | | e1 |= e2 | e1 = e1 | (e2) | | e1 ^= e2 | e1 = e1 ^ (e2) | | e1>>= e2 | e1 = e1>> (e2) | | e1<<= e2 | e1 = e1<< (e2) | |
| --- | --- |

Note: The syntax does not allow a [compound assignment](#compound-assignment) to also be a [phony assignment](#phony-assignment).

Note: When e1 is a [reference](#reference-type), it is evaluated once, but its underlying memory is accessed twice: first a [read access](#read-access) gets the old value, and then a [write access](#write-access) stores the updated value.

EXAMPLE: Compound assignment

var<private> next_item: i32 = 0;

fn advance_item() -> i32 {
   next_item += 1;   // Adds 1 to next_item.
   return next_item - 1;
}

fn bump_item() {
  var data: array<f32,10>;
  next_item = 0;
  // Adds 5.0 to data[0], calling advance_item() only once.
  data[advance_item()] += 5.0;
  // next_item will be 1 here.
}

fn precedence_example() {
  var value = 1;
  // The right-hand side of a compound assignment is its own expression.
  value *= 2 + 3; // Same as value = value * (2 + 3);
  // 'value' now holds 5.
}

Note: When e1 is a [swizzle view](#swizzle-view), then as specified, e1 is evaluated once to compute its corresponding pointer, but its underlying memory is accessed three times:

*   A first [read access](#read-access) gets the old vector, to get the components used in the binary operator expression.

*   A second [read access](#read-access) gets the vector after evaluation of e2. The evaluation of e2 may modify vector components that will _not_ be affected by the final swizzle write. This read gets those components so they can be preserved.

*   Finally, a [write access](#write-access) stores the updated vector. This may consist of updated components taken from the result of the binary operation, and preserved components taken from the second read.

EXAMPLE: Compound swizzle assignment order of evaluation

var<private> v: array<vec4u,1>;

fn update_and_index() -> u32 {
  v[0] += vec4u(2,4,8,10);
  return 0;
}

fn update_and_rhs() -> vec2u {
  v[0].x = 900;
  v[0].z = 100;
  return vec2u(55,66);
}

fn eval_order_compound_swizzle_assignment() {
  v[0] = vec4u(0,0,0,0);

  // 1. Evaluate the pointer p, which evaluates
  // the index on the left handside,
  // setting v[0] = vec4u(2,4,8,10) as a side effect
  // and yielding 0 for the index.
  // 2. The swizzle name is .yx and so IndexList is the list 1,0.
  // Perform SwizzleViewRead(p,IndexList),
  // yielding view_contents = vec2u(4,2).
  // 3. Evaluate the right-hand size, setting
  // v[0].x = 900
  // v[0].z = 100
  // and yielding vec2u(55,66).
  // 4. Compute update vector as
  // view_contents + vec2u(55,66)
  // = vec2u(4,2) + vec2u(55,66)
  // = vec2u(59,68)
  // 5. The swizzle assignment then updates only v[0].x and v[0].y,
  // preserving v[0].z and v[0].w.

  v[update_and_index()].yx += update_and_rhs();

  // Now v[0] equals vec4u(68,59,100,10);
}

Note: A compound assignment to a [reference](#reference-type) can be rewritten as different WGSL code that uses a [simple assignment](#simple-assignment) instead. The idea is to use a pointer to hold the result of evaluating the reference once.

For example, when e1 is _not_ a reference to a component inside a vector, then

> e1`+=`e2;

can be rewritten as

> `{ let p = &(`e1`); *p = *p + (`e2`); }`

where the identifier `p` is chosen to be different from all other identifiers in the program.

When e1 is a reference to a component inside a vector, the above technique needs to be modified because WGSL does not allow [taking the address](#address-of-expr) in that case. For example, if ev is a reference to a vector, the statement

> ev`[`c`] +=`e2;

can be rewritten as

> `{ let p = &(`ev`); let c0 =`c`; (*p)[c0] = (*p)[c0] + (`e2`); }`

where identifiers `c0` and `p` are chosen to be different from all other identifiers in the program.

### 9.3. Increment and Decrement Statements[](#increment-decrement)

An increment statement adds 1 to the contents of a variable. A decrement statement subtracts 1 from the contents of a variable.

increment_statement :

[lhs_expression](#syntax-lhs_expression)[`'++'`](#syntax_sym-plus_plus)

decrement_statement :

[lhs_expression](#syntax-lhs_expression)[`'--'`](#syntax_sym-minus_minus)

The expression [must](#shader-creation-error) evaluate to a reference with a [concrete](#type-concrete)[integer scalar](#integer-scalar)[store type](#store-type) and [read_write](#access-read_write)[access mode](#access-mode).

| Precondition | Statement | Description | r : ref<AS,T,[read_write](#access-read_write)>, T is a [concrete](#type-concrete)[integer scalar](#integer-scalar) | r`++` | Adds 1 to the contents of memory referenced by r. Same as r += T(1) | | r : ref<AS,T,[read_write](#access-read_write)>, T is a [concrete](#type-concrete)[integer scalar](#integer-scalar) | r`--` | Subtracts 1 from the contents of memory referenced by r. Same as r -= T(1) | |
| --- | --- | --- |

EXAMPLE: Increment and decrement

fn f() {
    var a: i32 = 20;
    a++;
    // Now a contains 21
    a--;
    // Now a contains 20
}

### 9.4. Control Flow[](#control-flow)

Control flow statements may cause the program to execute in non-sequential order.

#### 9.4.1. If Statement[](#if-statement)

An if statement conditionally executes at most one [compound statement](#compound-statement) based on the evaluation of condition expressions.

An `if` statement has an `if` clause, followed by zero or more `else if` clauses, followed by an optional `else` clause.

if_statement :

[attribute](#syntax-attribute) * [if_clause](#syntax-if_clause)[else_if_clause](#syntax-else_if_clause) * [else_clause](#syntax-else_clause) ?

if_clause :

`'if'`[expression](#syntax-expression)[compound_statement](#syntax-compound_statement)

else_if_clause :

`'else'``'if'`[expression](#syntax-expression)[compound_statement](#syntax-compound_statement)

else_clause :

`'else'`[compound_statement](#syntax-compound_statement)

[Type rule precondition](#type-rule-preconditions): The expression in each `if` and `else if` clause [must](#shader-creation-error) be of [bool](#bool) type.

An `if` statement is executed as follows:

*   The condition associated with the `if` clause is evaluated. If the result is `true`, control transfers to the first compound statement (immediately after the condition expression).

*   Otherwise, the condition of the next `else if` clause in textual order (if one exists) is evaluated and, if the result is `true`, control transfers to the associated compound statement.

    *   This behavior is repeated for all `else if` clauses until one of the conditions evaluates to `true`.

*   If no condition evaluates to `true`, then control transfers to the compound statement associated with the `else` clause (if it exists).

#### 9.4.2. Switch Statement[](#switch-statement)

A switch statement transfers control to one of a set of [case clauses](#case-clause), or to the [default clause](#default-clause), depending on the evaluation of a selector expression.

switch_statement :

[attribute](#syntax-attribute) * `'switch'`[expression](#syntax-expression)[switch_body](#syntax-switch_body)

switch_body :

[attribute](#syntax-attribute) * [`'{'`](#syntax_sym-brace_left)[switch_clause](#syntax-switch_clause) + [`'}'`](#syntax_sym-brace_right)

switch_clause :

[case_clause](#syntax-case_clause)

|[default_alone_clause](#syntax-default_alone_clause)

case_clause :

`'case'`[case_selectors](#syntax-case_selectors)[`':'`](#syntax_sym-colon) ? [compound_statement](#syntax-compound_statement)

default_alone_clause :

`'default'`[`':'`](#syntax_sym-colon) ? [compound_statement](#syntax-compound_statement)

case_selectors :

[case_selector](#syntax-case_selector) ( [`','`](#syntax_sym-comma)[case_selector](#syntax-case_selector) ) * [`','`](#syntax_sym-comma) ?

case_selector :

`'default'`

|[expression](#syntax-expression)

A case clause is the [`'case'`](#syntax_kw-case) token followed by a comma-separated list of [case selectors](#syntax-case_selector) and a body in the form of a [compound statement](#compound-statement).

A default-alone clause is the [`'default'`](#syntax_kw-default) token followed by a body in the form of a [compound statement](#compound-statement).

A default clause is either:

*   a [case clause](#case-clause) where [`'default'`](#syntax_kw-default) appears as one of its selectors, or

*   a [default-alone clause](#default-alone-clause).

Each switch statement [must](#shader-creation-error) have exactly one [default clause](#default-clause).

The [`'default'`](#syntax_kw-default) token [must](#shader-creation-error) not appear more than once in a single [case_selector](#syntax-case_selector) list.

[Type rule precondition](#type-rule-preconditions): For a single switch statement, the selector expression and all case selector expressions [must](#shader-creation-error) be of the same [concrete](#type-concrete)[integer scalar](#integer-scalar) type.

The expressions in the [case_selectors](#syntax-case_selectors)[must](#shader-creation-error) be [const-expressions](#const-expressions).

Two different case selector expressions in the same switch statement [must not](#shader-creation-error) have the same value.

If the selector value equals the value of an expression in a [case_selector](#syntax-case_selector) list, then control is transferred to the body of that [case clause](#case-clause). If the selector value does not equal any of the case selector values, then control is transferred to the body of the [default clause](#default-clause).

When control reaches the end of the body of a clause, control transfers to the first statement after the switch statement.

When one of the statements in the body of a clause is a [declaration](#declaration), it follows the normal [scope](#scope) and [lifetime](#lifetime) rules of a declaration in a [compound statement](#compound-statement). That is, the body is a sequence of statements, and if one of those is a declaration then the scope of that declaration extends from the start of the next statement in the sequence until the end of the body. The declaration executes when it is reached, creating a new instance of the [variable](#variable-declaration) or [value](#value-declaration), and initializes it.

EXAMPLE: WGSL Switch

var a : i32;
let x : i32 = generateValue();
switch x {
  case 0: {      // The colon is optional
    a = 1;
  }
  default {      // The default need not appear last
    a = 2;
  }
  case 1, 2, {   // Multiple selector values can be used
    a = 3;
  }
  case 3, {      // The trailing comma is optional
    a = 4;
  }
  case 4 {
    a = 5;
  }
}

EXAMPLE: WGSL Switch with default combined

const c = 2;
var a : i32;
let x : i32 = generateValue();
switch x {
  case 0: {
    a = 1;
  }
  case 1, c {       // Const-expression can be used in case selectors
    a = 3;
  }
  case 3, default { // The default keyword can be used with other clauses
    a = 4;
  }
}

#### 9.4.3. Loop Statement[](#loop-statement)

loop_statement :

[attribute](#syntax-attribute) * `'loop'`[attribute](#syntax-attribute) * [`'{'`](#syntax_sym-brace_left)[statement](#syntax-statement) * [continuing_statement](#syntax-continuing_statement) ? [`'}'`](#syntax_sym-brace_right)

A loop statement repeatedly executes a loop body; the loop body is specified as a [compound statement](#compound-statement). Each execution of the loop body is called an iteration.

This repetition can be interrupted by a [break](#statement-break), or [return](#statement-return) statement.

Optionally, the last statement in the loop body may be a [continuing](#statement-continuing) statement.

A [dynamic error](#dynamic-error) occurs if the [loop](#statement-loop) would execute an unbounded number of [iterations](#iteration). This may result in early termination of the loop, other non-local effects, or even [device loss](../WGPU/gpuweb-spec/gpuweb-spec.md#lose-the-device).

When one of the statements in the loop body is a [declaration](#declaration), it follows the normal [scope](#scope) and [lifetime](#lifetime) rules of a declaration in a [compound statement](#compound-statement). That is, the loop body is a sequence of statements, and if one of those is a declaration then the scope of that declaration extends from the start of the next statement in the sequence until the end of the loop body. The declaration executes each time it is reached, so each new iteration creates a new instance of the [variable](#variable-declaration) or [value](#value-declaration), and re-initializes it.

Note: The loop statement is a specialized construct, you probably want the `for` or `while` statements. The loop statement is one of the biggest differences from other shader languages.

This design directly expresses loop idioms commonly found in compiled code. In particular, placing the loop update statements at the end of the loop body allows them to naturally use values defined in the loop body.

EXAMPLE: for loop

var a: i32 = 2;
for (var i: i32 = 0; i < 4; i++) {
  a *= 2;
}

EXAMPLE: loop

var a: i32 = 2;
var i: i32 = 0;      // <1>
loop {
  if i >= 4 { break; }

  a = a * 2;

  i++;
}

*   <1> The initialization is listed before the loop.

EXAMPLE: for loop with continue

var a: i32 = 2;
let step: i32 = 1;
for (var i: i32 = 0; i < 4; i += step) {
  if (i % 2 == 0) { continue; }
  a *= 2;
}

EXAMPLE: loop with continue

var a: i32 = 2;
var i: i32 = 0;
loop {
  if i >= 4 { break; }

  let step: i32 = 1;

  i = i + step;
  if i % 2 == 0 { continue; }

  a = a * 2;
}

EXAMPLE: loop with continue and continuing

var a: i32 = 2;
var i: i32 = 0;
loop {
  if i >= 4 { break; }

  let step: i32 = 1;

  if i % 2 == 0 { continue; }

  a = a * 2;

  continuing {   // <2>
    i = i + step;
  }
}

*   <2> The continue construct is placed at the end of the `loop`

#### 9.4.4. For Statement[](#for-statement)

for_statement :

[attribute](#syntax-attribute) * `'for'`[`'('`](#syntax_sym-paren_left)[for_header](#syntax-for_header)[`')'`](#syntax_sym-paren_right)[compound_statement](#syntax-compound_statement)

The for statement is syntactic sugar over a [compound statement](#compound-statement) containing a [loop](#statement-loop) statement. In general, the `for` statement takes the form

> `for (`_initializer_`;`_condition_`;`_update\_part_`) {`_body_`}`

When the condition expression is present, the `for` statement desugars to a loop of the form:

> {  
> _initializer_;  
> loop {  
> if !(_condition_) { break; }  
> _body_ 
> continuing { _update\_part_}  
> }  
> }

 When the condition expression is absent, the `for` statement desugars to a loop of the form: 
> {  
> _initializer_;  
> loop {  
> _body_ 
> continuing { _update\_part_}  
> }  
> }

Additionally:

*   If `initializer` is non-empty, it is executed inside an additional [scope](#scope) before the first [iteration](#iteration). The scope of a declaration in the initializer extends to the end of the loop body.

*   [Type rule precondition](#type-rule-preconditions): If the condition is non-empty, it [must](#shader-creation-error) be an expression of [bool](#bool) type.

    *   If present, the condition is evaluated immediately before executing the for-loop body. If the condition is false, then a [§ 9.4.6 Break Statement](#break-statement) is executed, finishing execution of the loop. This check is performed at the start of each loop iteration.

*   If `update_part` is non-empty, it becomes a [continuing](#statement-continuing) statement at the end of the loop construct.

*   Desugaring [will](#behavioral-requirements) rename identifiers declared in the `body` as needed to ensure all identifiers in the `update_part` still [resolve](#resolves) to the same declarations they did before desugaring occurred.

The `initializer` of a for loop is executed once prior to executing the loop. When a [declaration](#declaration) appears in the initializer, its [identifier](#identifier) is [in scope](#in-scope) until the end of the `body`. Unlike declarations in the `body`, the declaration is not re-initialized each iteration.

The `condition`, `body` and `update_part` execute in that order to form a loop [iteration](#iteration). The `body` is a special form of [compound statement](#compound-statement). The identifier of a declaration in the `body` is [in scope](#in-scope) from the start of the next statement until the end of the `body`. The declaration is executed each time it is reached, so each new iteration creates a new instance of the variable or constant, and re-initializes it.

EXAMPLE: For to Loop transformation, with a condition: before

var a: i32 = 2;
for (var i: i32 = 0; i < 4; i++) {
  if a == 0 {
    continue;
  }
  a = a + 2;
}

Converts to:

EXAMPLE: For to Loop transformation, with a condition: after

var a: i32 = 2;
{ // Introduce new scope for loop variable i
  var i: i32 = 0;
  loop {
    if !(i < 4) {
      break;
    }

    if a == 0 {
      continue;
    }
    a = a + 2;

    continuing {
      i++;
    }
  }
}

EXAMPLE: For to Loop transformation, without a condition: before

var a: i32 = 2;
for (var i: i32 = 0; ; i++) {
  if a == 0 {
    continue;
  }
  if i == 4 { break; }
  a = a + 2;
}

Converts to:

EXAMPLE: For to Loop transformation, without a condition: after

var a: i32 = 2;
{ // Introduce new scope for loop variable i
  var i: i32 = 0;
  loop {
    // Note: Desugaring does not introduce an if clause here.

    if a == 0 {
      continue;
    }
    if i == 4 { break; }
    a = a + 2;

    continuing {
      i++;
    }
  }
}

A [dynamic error](#dynamic-error) occurs if the [for](#statement-for) loop would execute an unbounded number of [iterations](#iteration). This may result in early termination of the loop, other non-local effects, or even [device loss](../WGPU/gpuweb-spec/gpuweb-spec.md#lose-the-device).

#### 9.4.5. While Statement[](#while-statement)

while_statement :

[attribute](#syntax-attribute) * `'while'`[expression](#syntax-expression)[compound_statement](#syntax-compound_statement)

The while statement is a kind of loop parameterized by a condition. At the start of each loop [iteration](#iteration), a boolean condition is evaluated. If the condition is false, the while loop ends execution. Otherwise, the rest of the iteration is executed.

[Type rule precondition](#type-rule-preconditions): The condition [must](#shader-creation-error) be of [bool](#bool) type.

A while loop can be viewed as syntactic sugar over either a [loop](#statement-loop) or [for](#statement-for) statement. The following statement forms are equivalent:

*   `while`_condition_`{`_body\_statements_`}`

*   `loop { if !`_condition_`{break;}`_body\_statements_`}`

*   `for (;`_condition_`;) {`_body\_statements_`}`

A [dynamic error](#dynamic-error) occurs if the [while](#statement-while) loop would execute an unbounded number of [iterations](#iteration). This may result in early termination of the loop, other non-local effects, or even [device loss](../WGPU/gpuweb-spec/gpuweb-spec.md#lose-the-device).

#### 9.4.6. Break Statement[](#break-statement)

break_statement :

`'break'`

A break statement transfers control to immediately after the body of the nearest-enclosing loop or [switch](#statement-switch) statement, thus ending execution of the loop or switch statement.

A `break` statement [must](#shader-creation-error) only be used within [loop](#statement-loop), [for](#statement-for), [while](#statement-while), and [switch](#statement-switch) statements.

A `break` statement [must not](#shader-creation-error) be placed such that it would exit from a loop’s [continuing](#continuing-statement) statement. Use a [break-if](#break-if-statement) statement instead.

EXAMPLE: WGSL Invalid loop break from a continuing clause

var a: i32 = 2;
var i: i32 = 0;
loop {
  let step: i32 = 1;

  if i % 2 == 0 { continue; }

  a = a * 2;

  continuing {
    i = i + step;
    if i >= 4 { break; } // Invalid. Use break-if instead.
  }
}

#### 9.4.7. Break-If Statement[](#break-if-statement)

break_if_statement :

`'break'``'if'`[expression](#syntax-expression)[`';'`](#syntax_sym-semicolon)

A break-if statement evaluates a boolean condition; If the condition is true, control is transferred to immediately after the body of the nearest-enclosing [loop](#statement-loop) statement, ending execution of that loop.

[Type rule precondition](#type-rule-preconditions): The condition [must](#shader-creation-error) be of [bool](#bool) type.

Note: A break-if statement may only appear as the last statement in the body of a [continuing](#continuing-statement) statement.

EXAMPLE: WGSL Valid loop break-if from a continuing clause

var a: i32 = 2;
var i: i32 = 0;
loop {
  let step: i32 = 1;

  if i % 2 == 0 { continue; }

  a = a * 2;

  continuing {
    i = i + step;
    break if i >= 4;
  }
}

#### 9.4.8. Continue Statement[](#continue-statement)

continue_statement :

`'continue'`

A continue statement transfers control in the nearest-enclosing [loop](#statement-loop):

*   forward to the [continuing](#statement-continuing) statement at the end of the body of that loop, if it exists.

*   otherwise backward to the first statement in the loop body, starting the next [iteration](#iteration).

A `continue` statement [must](#shader-creation-error) only be used in a [loop](#statement-loop), [for](#statement-for) or [while](#statement-while) statement. A `continue` statement [must not](#shader-creation-error) be placed such that it would transfer control to an enclosing [continuing](#statement-continuing) statement. (It is a _forward_ branch when branching to a `continuing` statement.)

A `continue` statement [must not](#shader-creation-error) be placed such that it would transfer control past a declaration used in the targeted [continuing](#statement-continuing) statement.

Note: A `continue` can only be used in a `continuing` statement if it is used for transferring control flow within another loop nested in the `continuing` statement. That is, a `continue` cannot be used to transfer control to the start of the currently executing `continuing` statement.

EXAMPLE: Invalid continue bypasses declaration

var i: i32 = 0;
loop {
  if i >= 4 { break; }
  if i % 2 == 0 { continue; } // <3>

  let step: i32 = 2;

  continuing {
    i = i + step;
  }
}

*   <3> The `continue` is invalid because it bypasses the declaration of `step` used in the `continuing` construct

#### 9.4.9. Continuing Statement[](#continuing-statement)

continuing_statement :

`'continuing'`[continuing_compound_statement](#syntax-continuing_compound_statement)

continuing_compound_statement :

[attribute](#syntax-attribute) * [`'{'`](#syntax_sym-brace_left)[statement](#syntax-statement) * [break_if_statement](#syntax-break_if_statement) ? [`'}'`](#syntax_sym-brace_right)

A continuing statement specifies a [compound statement](#compound-statement) to be executed at the end of a loop [iteration](#iteration). The construct is optional.

The compound statement [must not](#shader-creation-error) contain a [return](#statement-return) at any compound statement nesting level.

#### 9.4.10. Return Statement[](#return-statement)

return_statement :

`'return'`[expression](#syntax-expression) ?

A return statement ends execution of the current function. If the function is an [entry point](#entry-point), then the current shader invocation is terminated. Otherwise, evaluation continues with the next expression or statement after the evaluation of the [call site](#call-site) of the current function invocation.

If the function does not have a [return type](#return-type), then the [return](#statement-return) statement is optional. If the return statement is provided for such a function, it [must not](#shader-creation-error) supply a value. Otherwise the expression [must](#shader-creation-error) be present, and is called the return value. In this case the call site of this function invocation evaluates to the return value. The type of the return value [must](#shader-creation-error) match the return type of the function.

#### 9.4.11. Discard Statement[](#discard-statement)

A discard statement converts the invocation into a [helper invocation](#helper-invocation) and throws away the fragment output. The `discard` statement [must](#shader-creation-error) only be used in a [fragment](#fragment) shader stage.

More precisely, executing a `discard` statement [will](#behavioral-requirements):

*   convert the current invocation into a [helper invocation](#helper-invocation), and

*   prevent the current fragment output from being processed downstream in the [GPURenderPipeline](#gpurenderpipeline).

Only statements executed prior to the `discard` statement [will](#behavioral-requirements) have observable effects.

Note: A `discard` statement may be executed by any [function in a fragment stage](#functions-in-a-shader-stage) and the effect is the same: the fragment output will be thrown away.

EXAMPLE: Using the discard statement to throw away a fragment

@group(0) @binding(0)
var<storage, read_write> will_emit_color : u32;

fn discard_if_shallow(pos: vec4<f32>) {
  if pos.z < 0.001 {
    // If this is executed, then the will_emit_color variable will
    // never be set to 1 because helper invocations will not write
    // to shared memory.
    discard;
  }
  will_emit_color = 1;
}

@fragment
fn main(@builtin(position) coord_in: vec4<f32>)
  -> @location(0) vec4<f32>
{
  discard_if_shallow(coord_in);

  // Set the value to 1 and emit red, but only if the helper function
  // did not execute the discard statement.
  will_emit_color = 1;
  return vec4<f32>(1.0, 0.0, 0.0, 1.0);
}

### 9.5. Function Call Statement[](#function-call-statement)

func_call_statement :

[call_phrase](#syntax-call_phrase)

A function call statement executes a [function call](#function-call).

A [shader-creation error](#shader-creation-error) results if the called function has the [must_use](#attribute-must_use) attribute.

Note: If the function [returns a value](#return-value), and the function does not have the [must_use](#attribute-must_use) attribute, that value is ignored.

### 9.6. Statements Grammar Summary[](#statements-summary)

The [statement](#syntax-statement) rule matches statements that can be used in most places inside a function body.

variable_updating_statement :

[assignment_statement](#syntax-assignment_statement)

|[increment_statement](#syntax-increment_statement)

|[decrement_statement](#syntax-decrement_statement)

Additionally, certain statements may only be used in very specific contexts:

*   [break_if_statement](#syntax-break_if_statement)

*   [continuing_compound_statement](#syntax-continuing_compound_statement)

### 9.7. Statements Behavior Analysis[](#behaviors)

#### 9.7.1. Rules[](#behaviors-rules)

Some statements affecting control-flow are only valid in some contexts. For example, [continue](#statement-continue) is invalid outside of a [loop](#statement-loop), [for](#statement-for), or [while](#statement-while). Additionally, the uniformity analysis (see [§ 15.2 Uniformity](#uniformity)) needs to know when control flow can exit a statement in multiple different ways.

Both goals are achieved by a system for summarizing execution behaviors of statements. Behavior analysis maps each statement to the set of possible ways execution proceeds after evaluation of the statement completes. As with type analysis for values and expressions, behavior analysis proceeds bottom up: first determine behaviors for certain basic statements, and then determine behavior for higher level constructs by applying combining rules.

A behavior is a set, whose elements may be:

*   Return

*   Break

*   Continue

*   Next

Each of those correspond to a way to exit a compound statement: either through a keyword, or by falling to the next statement ("Next").

We note "_s_: _B_" to say that _s_ respects the rules regarding behaviors, and has [behavior](#behavior)_B_.

For each function:

*   Its body [must](#shader-creation-error) be a valid statement by these rules.

*   If the function has a return type, the [behavior](#behavior) of its body [must](#shader-creation-error) be {Return}.

*   Otherwise, the [behavior](#behavior) of its body [must](#shader-creation-error) be a subset of {Next, Return}.

We assign a [behavior](#behavior) to each function: it is its body’s [behavior](#behavior) (treating the body as a regular statement), with any "Return" replaced by "Next". As a consequence of the rules above, a function behavior is always one of {}, or {Next}.

Behavior analysis [must](#shader-creation-error) be able to determine a non-empty [behavior](#behavior) for each statement, and function.

Rules for analyzing and validating the behaviors of statements
| Statement | Preconditions | Resulting behavior | _empty statement_ | | {Next} | | {s} | s: B | B | | s1 s2 Note:s1 often ends in a semicolon. | s1: B1 Next in B1 s2: B2 | (B1∖{Next}) ∪ B2 | | s1: B1 Next not in B1 s2: B2 | B1 | | var x:T; | | {Next} | | let x = e; | | {Next} | | var x = e; | | {Next} | | x = e; | | {Next} | | _ = e; | | {Next} | | f(e1, ..., en); | f has behavior B | B | | return; | | {Return} | | return e; | | {Return} | | discard; | | {Next} | | break; | | {Break} | | break if e; | | {Break, Next} | | continue; | | {Continue} | | const_assert e; | | {Next} | | if e s1 else s2 | s1: B1 s2: B2 | B1 ∪ B2 | | loop {s1 continuing {s2}} | s1: B1 s2: B2 B1 = {Return} None of {Continue, Return} are in B2 | {Return} | | s1: B1 s2: B2 B1 ≠ {Return} None of {Continue, Return} are in B2 Break is not in (B1 ∪ B2) | (B1 ∪ B2)∖{Continue, Next} | | s1: B1 s2: B2 B1 ≠ {Return} None of {Continue, Return} are in B2 Break is in (B1 ∪ B2) | (B1 ∪ B2 ∪ {Next})∖{Break, Continue} | | switch e {case c1: s1 ... case cn: sn} | s1: B1 ... sn: Bn Break is not in (B1 ∪ ... ∪ Bn) | B1 ∪ ... ∪ Bn | | s1: B1 ... sn: Bn Break is in (B1 ∪ ... ∪ Bn) | (B1 ∪ ... ∪ Bn ∪ {Next})∖Break | |
| --- | --- | --- |

Note: ∪ is a set union operation and ∖ is a set difference operation.

Note: The empty statement case occurs when a `loop` has an empty body, or when a `for` loop lacks an initialization or update statement.

For the purpose of this analysis:

*   `for` loops get desugared (see [§ 9.4.4 For Statement](#for-statement))

*   `while` loops get desugared (see [§ 9.4.5 While Statement](#while-statement))

*   `loop {s}` is treated as `loop {s continuing {}}`

*   `if` statements without an `else` branch are treated as if they had an empty else branch, i.e. ended in `else {}`; this adds Next to their [behavior](#behavior)

*   `if` statements with `else if` branches are treated as if they were nested simple `if/else` statements

*   a [switch_clause](#syntax-switch_clause) starting with `default` behaves just like a [switch_clause](#syntax-switch_clause) starting with `case _:`

Each [built-in function](#built-in-functions) has a [behavior](#behavior) of {Next}. And each operator application not listed in the table above has the same [behavior](#behavior) as if it were a function call with the same operands and with a function’s [behavior](#behavior) of {Next}.

The behavior of a function [must](#shader-creation-error) satisfy the rules given above.

Note: The rules above imply that the behavior of a loop is {Next}, {Return}, or {Next,Return}.

Note: It is unnecessary to analyze the behavior of expressions because they will always be {Next} or a previously analyzed function will have produced a error.

#### 9.7.2. Notes[](#behaviors-notes)

This section is informative, non-normative.

Behavior analysis can cause a program to be rejected in the following ways (restating requirements from above):

*   The body of a function (treated as a regular statement) has a behavior not included in {Next, Return}.

*   The body of a function with a return type has a behavior which is not {Return}.

*   The behavior of a continuing block contains any of Continue, or Return.

*   Some obviously infinite loops have an empty behavior set, and are therefore invalid.

This analysis can be run in linear time, by analyzing the call-graph bottom-up (since the behavior of a function call can depend on the function’s code).

#### 9.7.3. Examples[](#behaviors-examples)

Here are some examples showing this analysis in action:

EXAMPLE: Trivially dead code is allowed

fn simple() -> i32 {
  var a: i32;
  return 0;  // Behavior: {Return}
  a = 1;     // Valid, statically unreachable code.
             // Statement behavior: {Next}
             // Overall behavior (due to sequential statements): {Return}
  return 2;  // Valid, statically unreachable code. Behavior: {Return}
} // Function behavior: {Return}

EXAMPLE: Compound statements are supported

fn nested() -> i32 {
  var a: i32;
  {             // The start of a compound statement.
    a = 2;      // Behavior: {Next}
    return 1;   // Behavior: {Return}
  }             // The compound statement as a whole has behavior {Return}
  a = 1;        // Valid, statically unreachable code.
                // Statement behavior: {Next}
                // Overall behavior (due to sequential statements): {Return}
  return 2;     // Valid, statically unreachable code. Behavior: {Return}
}

EXAMPLE: if/then behaves as if there is an empty else

fn if_example() {
  var a: i32 = 0;
  loop {
    if a == 5 {
      break;      // Behavior: {Break}
    }             // Behavior of the whole if compound statement: {Break, Next},
                  // as the if has an implicit empty else
    a = a + 1;    // Valid, as the previous statement had "Next" in its behavior
  }
}

EXAMPLE: if/then/else has the behavior of both sides

fn if_example() {
  var a: i32 = 0;
  loop {
    if a == 5 {
      break;      // Behavior: {Break}
    } else {
      continue;   // Behavior: {Continue}
    }             // Behavior of the whole if compound statement: {Break, Continue}
    a = a + 1;    // Valid, statically unreachable code.
                  // Statement behavior: {Next}
                  // Overall behavior: {Break, Continue}
  }
}

EXAMPLE: if/else if/else behaves like a nested if/else

fn if_example() {
  var a: i32 = 0;
  loop {
    // if e1 s1 else if e2 s2 else s3
    // is identical to
    // if e1 else { if e2 s2 else s3 }
    if a == 5 {
      break;      // Behavior: {Break}
    } else if a == 42 {
      continue;   // Behavior: {Continue}
    } else {
      return;     // Behavior {Return}
    }             // Behavior of the whole if compound statement:
                  // {Break, Continue, Return}
  }               // Behavior of the whole loop compound statement {Next, Return}
}                 // Behavior of the whole function {Next}

EXAMPLE: Break in switch becomes Next

fn switch_example() {
  var a: i32 = 0;
  switch a {
    default: {
      break;   // Behavior: {Break}
    }
  }            // Behavior: {Next}, as switch replaces Break by Next
  a = 5;       // Valid, as the previous statement had Next in its behavior
}

EXAMPLE: Obviously infinite loops

fn invalid_infinite_loop() {
  loop { }     // Behavior: { }. Invalid because it's empty.
}

EXAMPLE: Discard will not terminate a loop

fn invalid_infinite_loop() {
  loop {
    discard; // Behavior { Next }.
  }          // Invalid, behavior of the whole loop is { }.
}

EXAMPLE: A conditional continue with continuing statement

fn conditional_continue() {
  var a: i32;
  loop {
    if a == 5 { break; } // Behavior: {Break, Next}
    if a % 2 == 1 {      // Valid, as the previous statement has Next in its behavior
      continue;          // Behavior: {Continue}
    }                    // Behavior: {Continue, Next}
    a = a * 2;           // Valid, as the previous statement has Next in its behavior
    continuing {         // Valid as the continuing statement has behavior {Next}
                         // which does not include any of:
                         // {Break, Continue, Return}
      a = a + 1;
    }
  }                      // The loop as a whole has behavior {Next},
                         // as it absorbs "Continue" and "Next",
                         // then replaces "Break" with "Next"
}

EXAMPLE: A redundant continue with continuing statement

fn redundant_continue_with_continuing() {
  var a: i32;
  loop {
    if a == 5 { break; }
    continue;   // Valid. This is redundant, branching to the next statement.
    continuing {
      a = a + 1;
    }
  }
}

EXAMPLE: A continue at the end of a loop body

fn continue_end_of_loop_body() {
  for (var i: i32 = 0; i < 5; i++ ) {
    continue;   // Valid. This is redundant,
                // branching to the end of the loop body.
  }             // Behavior: {Next},
                // as loops absorb "Continue",
                // and "for" loops always add "Next"
}

`for` loops desugar to `loop` with a conditional break. As shown in a previous example, the conditional break has [behavior](#behavior) {Break, Next}, which leads to adding "Next" to the loop’s [behavior](#behavior). 

EXAMPLE: return required in functions that have a return type

fn missing_return () -> i32 {
  var a: i32 = 0;
  if a == 42 {
    return a;       // Behavior: {Return}
  }                 // Behavior: {Next, Return}
}                   // Error: Next is invalid in the body of a
                    // function with a return type

EXAMPLE: continue must be in a loop

fn continue_out_of_loop () {
  var a: i32 = 0;
  if a > 0  {
    continue;       // Behavior: {Continue}
  }                 // Behavior: {Next, Continue}
}                   // Error: Continue is invalid in the body of a function

 The same example would also be invalid for the same reason if `continue` was replaced by `break`. 
## 10. Assertions[](#assertions)

An assertion is a check that ensures a boolean condition is satisfied.

global_assert :

[const_assert](#syntax-const_assert)[`';'`](#syntax_sym-semicolon)

WGSL defines one kind of [assertion](#assertion): the [const assertion](#const-assert-statement).

const_assert :

`'const_assert'`[expression](#syntax-expression)

[Type rule precondition](#type-rule-preconditions): The expression [must](#shader-creation-error) be of [bool](#bool) type.

### 10.1. Const Assertion Statement[](#const-assert-statement)

A const assertion statement is an [assertion](#assertion) that produces a [shader-creation error](#shader-creation-error) if the expression evaluates to `false`. The expression [must](#shader-creation-error) be a [const-expression](#const-expressions). The statement can satisfy [static access](#statically-accessed) conditions in a shader, but otherwise has no effect on the compiled shader. A const assertion can appear at [module scope](#module-scope) or as a [function scope](#function-scope)[statement](#statement).

assert_statement :

[const_assert](#syntax-const_assert)

EXAMPLE: Static assertion examples

const x = 1;
const y = 2;
const_assert x < y; // valid at module-scope.
const_assert(y != 0); // parentheses are optional.

fn foo() {
  const z = x + y - 2;
  const_assert z > 0; // valid in functions.
  let a  = 3;
  const_assert a != 0; // invalid, the expression must be a const-expression.
}

## 11. Functions[](#functions)

A function performs computational work when invoked.

A function is invoked in one of the following ways:

*   By evaluating a function call expression. See [§ 8.11 Function Call Expression](#function-call-expr).

*   By executing a function call statement. See [§ 9.5 Function Call Statement](#function-call-statement).

*   An [entry point](#entry-point) function is invoked by the WebGPU implementation to perform the work of a [shader stage](#shader-stages) in a [pipeline](#pipeline). See [§ 13 Entry Points](#entry-points)

Functions in WGSL may be defined in any order, including later in the source than they are used. Because of this, function prototypes or forward declarations are not needed, and there is no way to do so.

There are two kinds of functions:

*   A [built-in function](#built-in-functions) is provided by the WGSL implementation, and is always available to a WGSL module. See [§ 17 Built-in Functions](#builtin-functions).

*   A [user-defined function](#user-defined-function) is declared in a WGSL module.

### 11.1. Declaring a User-defined Function[](#function-declaration-sec)

A function declaration creates a user-defined function, by specifying:

*   An optional set of [attributes](#attribute).

*   The name of the function.

*   The formal parameter list: an ordered sequence of zero or more [formal parameter](#formal-parameter) declarations, separated by commas, and surrounded by parentheses.

    *   If the function is an [entry point](#entry-point), then the parameters may have attributes, to specify the parameters as [shader stage inputs](#shader-stage-input).

*   An optional return type.

    *   If the function is an [entry point](#entry-point), then the return type may have attributes, to specify [shader stage outputs](#shader-stage-output).

*   The function body. This is the set of statements to be executed when the function is [called](#function-call).

A function declaration [must](#shader-creation-error) only occur at [module scope](#module-scope). A function name is [in scope](#in-scope) for the entire program.

Note: Each [user-defined function](#user-defined-function) only has one [overload](#overload).

A formal parameter[declaration](#declaration) specifies an [identifier](#identifier) name and a type for a value that [must](#shader-creation-error) be provided when invoking the function. A formal parameter of an [entry point](#entry-point) function may have attributes. See [§ 11.2 Function Calls](#function-calls). The [scope](#scope) of the identifier is the [function body](#function-body). Two formal parameters for a given function [must not](#shader-creation-error) have the same name.

Note: Some built-in functions may allow parameters to be [abstract numeric types](#abstract-numeric-types); however, this functionality is not currently supported for user-declared functions.

The [return type](#return-type), if specified, [must](#shader-creation-error) be [constructible](#constructible).

WGSL defines the following attributes that can be applied to function declarations:

*   the [shader stage attributes](#shader-stage-attributes): [vertex](#attribute-vertex), [fragment](#attribute-fragment), and [compute](#attribute-compute)

*   [workgroup_size](#attribute-workgroup_size)

*   [subgroup_size](#attribute-subgroup_size)

param_list :

[param](#syntax-param) ( [`','`](#syntax_sym-comma)[param](#syntax-param) ) * [`','`](#syntax_sym-comma) ?

EXAMPLE: Simple functions

// Declare the add_two function.
// It has two formal parameters, i and b.
// It has a return type of i32.
// It has a body with a return statement.
fn add_two(i: i32, b: f32) -> i32 {
  return i + 2;  // A formal parameter is available for use in the body.
}

// A compute shader entry point function, 'main'.
// It has no specified return type.
// It invokes the add_two function, and captures
// the resulting value in the named value 'six'.
@compute @workgroup_size(1)
fn main() {
   let six: i32 = add_two(4, 5.0);
}

### 11.2. Function Calls[](#function-calls)

A function call is a statement or expression which invokes a function.

The function containing the function call is the calling function, or caller. The function being invoked is the called function, or callee.

The function call:

*   Names the [called function](#called-function), and

*   Provides a parenthesized, comma-separated list of argument value expressions.

The function call [must](#shader-creation-error) supply the same number of argument values as there are [formal parameters](#formal-parameter) in the [called function](#called-function). Each argument value [must](#shader-creation-error) evaluate to the same type as the corresponding formal parameter, by position.

In summary, when calling a function:

1.   Execution of the [calling function](#calling-function) is suspended.

2.   The [called function](#called-function) executes until it [returns](#returns).

3.   Execution of the [calling function](#calling-function) resumes.

A called function returns as follows:

*   A [built-in function](#built-in-functions) returns when its work has completed.

*   A [user-defined function](#user-defined-function) with a [return type](#return-type) returns when it executes a [return](#statement-return) statement.

*   A [user-defined function](#user-defined-function) with no [return type](#return-type) returns when it executes a [return](#statement-return) statement, or when execution reaches the end of its [function body](#function-body).

In detail, when a function call is executed the following steps occur:

1.   Function call argument values are evaluated. The relative order of evaluation is left-to-right.

2.   Execution of the [calling function](#calling-function) is suspended. All [function scope](#function-scope) variables and constants maintain their current values.

3.   If the called function is [user-defined](#user-defined-function), memory is allocated for each function scope variable in the called function.

    *   Initialization occurs as described in [§ 7.3 var Declarations](#var-decls).

4.   Values for the formal parameters of the called function are determined by matching the function call argument values by position. For example, the first formal parameter of the called function will have the value of the first argument at the [call site](#call-site).

5.   Control is transferred to the called function. If the called function is [user-defined](#user-defined-function), execution proceeds starting from the first statement in the [body](#function-body).

6.   The called function is executed, until it [returns](#returns).

7.   Control is transferred back to the calling function, and the called function’s execution is unsuspended. If the called function [returns a value](#return-value), that value is supplied for the value of the function call expression.

The location of a function call is referred to as a call site, specifically the location of the first [token](#token) in the parsed instance of the [call_phrase](#syntax-call_phrase) grammar rule. Call sites are a [dynamic context](#dynamic-context). As such, the same textual location may represent multiple call sites.

Note: It is possible that a function call in a [fragment](#fragment) shader never returns if all of the invocations in a [quad](#quad) are [discarded](#statement-discard). In such a case, control will not be tranferred back to the calling function.

### 11.3. `const` Functions[](#const-funcs)

A function declared with a [const](#attribute-const) attribute can be evaluated at [shader-creation time](#shader-module-creation). These functions are called const-functions. Calls to these functions can be part of [const-expressions](#const-expressions).

It is a [shader-creation error](#shader-creation-error) if the function contains any expressions that are not [const-expressions](#const-expressions), or any declarations that are not [const-declarations](#const-declaration).

Note: The [const](#attribute-const) attribute cannot be applied to user-declared functions.

EXAMPLE: const-functions

const first_one = firstLeadingBit(1234 + 4567); // Evaluates to 12
                                                // first_one has the type i32, because
                                                // firstLeadingBit cannot operate on
                                                // AbstractInt

@id(1) override x : i32;
override y = firstLeadingBit(x); // const-expressions can be
                                 // used in override-expressions.
                                 // firstLeadingBit(x) is not a
                                 // const-expression in this context.

fn foo() {
  var a : array<i32, firstLeadingBit(257)>; // const-functions can be used in
                                            // const-expressions if all their
                                            // parameters are const-expressions.
}

### 11.4. Restrictions on Functions[](#function-restriction)

*   A [vertex](#vertex) shader [must](#shader-creation-error) return the [position](#built-in-values-position)[built-in output value](#built-in-output-value).

*   An entry point [must](#shader-creation-error) never be the target of a [function call](#function-call).

*   If a function has a return type, it [must](#shader-creation-error) be a [constructible](#constructible) type.

*   A [function parameter](#formal-parameter)[must](#shader-creation-error) be one the following types:

    *   a constructible type

    *   a pointer type

    *   a texture type

    *   a sampler type

*   Each function call argument [must](#shader-creation-error) evaluate to the type of the corresponding function parameter.

    *   In particular, an argument that is a pointer [must](#shader-creation-error) agree with the formal parameter on [address space](#address-spaces), [store type](#store-type), and [access mode](#access-mode).

Note: Recursion is disallowed because cycles are not permitted among any kinds of declarations.

EXAMPLE: Valid and invalid pointer arguments

fn bar(p : ptr<function, f32>) {
}

fn baz(p : ptr<private, i32>) {
}

fn bar2(p : ptr<function, f32>) {
  let a = &*&*(p);

  bar(p); // Valid
  bar(a); // Valid
}

fn baz2(p : ptr<storage, f32>) {
}

struct S {
  x : i32
}

@group(0) @binding(0)
var<storage> ro_storage : f32;
@group(0) @binding(1)
var<storage, read_write> rw_storage : f32;

var usable_priv : i32;
var unusable_priv : array<i32, 4>;
fn foo() {
  var usable_func : f32;
  var unusable_func : S;
  var i32_func : i32;

  let a_priv = &usable_priv;
  let b_priv = a_priv;
  let c_priv = &*&usable_priv;
  let d_priv = &(unusable_priv.x);
  let e_priv = d_priv;

  let a_func = &usable_func;
  let b_func = &unusable_func;
  let c_func = &(*b_func)[0];
  let d_func = c_func;
  let e_func = &*a_func;

  baz(&usable_priv); // Valid, address-of a variable.
  baz(a_priv);       // Valid, effectively address-of a variable.
  baz(b_priv);       // Valid, effectively address-of a variable.
  baz(c_priv);       // Valid, effectively address-of a variable.
  baz(d_priv);       // Valid, memory view has changed.
  baz(e_priv);       // Valid, memory view has changed.
  baz(&i32_func);    // Invalid, address space mismatch.

  bar(&usable_func); // Valid, address-of a variable.
  bar(c_func);       // Valid, memory view has changed.
  bar(d_func);       // Valid, memory view has changed.
  bar(e_func);       // Valid, effectively address-of a variable.

  baz2(&ro_storage); // Valid, address-of a variable.
  baz2(&rw_storage); // Invalid, access mode mismatch.
}

#### 11.4.1. Alias Analysis[](#alias-analysis)

##### 11.4.1.1. Root Identifier[](#root-ident-sec)

[Memory locations](#memory-locations) can be accessed during the execution of a function using [memory views](#memory-view) or [swizzle views](#swizzle-view). Within a function, each [memory view](#memory-view) has a particular root identifier, which names the variable or formal parameter that first provides access to that memory in that function. Similarly, the [root identifier](#root-identifier) of a [swizzle view](#swizzle-view) is the root identifier for the swizzle view’s pointer.

Locally derived expressions of [reference](#reference-type) or [pointer](#pointer-type) type may introduce new names for a particular root identifier, but each expression has a statically determinable root identifier.

Given an expression E of [pointer](#pointer-type) or [reference type](#reference-type), the [root identifier](#root-identifier) is the [originating variable](#originating-variable) or [formal parameter](#formal-parameter) of [pointer type](#pointer-type) found as follows:

*   If E is an identifier [resolving](#resolves) to a variable, then the root identifier is that variable.

*   If E is an identifier [resolving](#resolves) to a formal parameter of pointer type, then the root identifier is that formal parameter.

*   If E is an identifier [resolving](#resolves) to a [let-declaration](#let-declaration) with initializer E2, then the root identifier is the root identifier of E2.

*   If E is of the form `(`E2`)`, `&`E2, `*`E2, or E2`[`Ei`]` then the root identifier is the root identifier of E2.

*   If E is a [vector access expression](#vector-access-expr) of the form E2.swiz, where swiz is a [swizzle](#swizzle) name, then the root identifer is the root identifier of E2.

*   If E is a [structure access expression](#struct-access-expr) of the form E2.member_name, then the root identifer is the root identifier of E2.

*   If E is a [bufferView](#bufferview-builtin) or [bufferArrayView](#bufferarrayview-builtin) built-in call, then the root identifier is the root identifier of the pointer argument.

##### 11.4.1.2. Aliasing[](#aliasing)

While the [originating variable](#originating-variable) of a [root identifier](#root-identifier) is a dynamic concept that depends on the [call sites](#call-site) for the function, WGSL modules can be statically analyzed to determine the set of all possible [originating variables](#originating-variable) for each root identifier.

Two [root identifiers](#root-identifier)alias when they have the same [originating variable](#originating-variable). Execution of a WGSL function [must not](#shader-creation-error) potentially access memory through aliased root identifiers, where one access is a write and the other is a read or a write. This is determined by analyzing the program from the leaves of the callgraph upwards (i.e. topological order). For each function the analysis records the following sets:

*   [Module-scope](#module-scope) variables that are [written](#write-access). This includes any module-scope variables that are written in functions called from this function.

*   [Module-scope](#module-scope) variables that are [read](#read-access). This includes any module-scope variables that are read in functions called from this function.

*   Pointer parameters used as root identifiers of [memory views](#memory-view) or [swizzle views](#swizzle-view) that are [written](#write-access) in this function or in called functions.

*   Pointer parameters used as root identifiers of [memory views](#memory-view) or [swizzle views](#swizzle-view) that are [read](#read-access) in this function or in called functions.

At each [call site](#call-site) of a function, it is a [shader-creation error](#shader-creation-error) if any of the following occur:

*   Two arguments of pointer type have the same root identifier and either corresponding parameter is in the written parameter set.

*   An argument of pointer type whose root identifier is a module-scope variable where:

    *   the corresponding pointer parameter is in the set of written pointer parameters, and

    *   the module-scope variable is in the read set for the called function.

*   An argument of pointer type whose root identifier is a module-scope variable where:

    *   the corresponding pointer parameter is in the set of written pointer parameters, and

    *   the module-scope variable is in the written set for the called function.

*   An argument of pointer type whose root identifier is a module-scope variable where:

    *   the corresponding pointer parameter is in the set of read pointer parameters, and

    *   the module-scope variable is in the written set for the called function.

EXAMPLE: Alias analysis

var<private> x : i32 = 0;

fn f1(p1 : ptr<function, i32>, p2 : ptr<function, i32>) {
  *p1 = *p2;
}

fn f2(p1 : ptr<function, i32>, p2 : ptr<function, i32>) {
  f1(p1, p2);
}

fn f3() {
  var a : i32 = 0;
  f2(&a, &a);  // Invalid. Cannot pass two pointer parameters
               // with the same root identifier when one or
               // more are written (even by a subfunction).
}

fn f4(p1 : ptr<function, i32>, p2 : ptr<function, i32>) -> i32 {
  return *p1 + *p2;
}

fn f5() {
  var a : i32 = 0;
  let b = f4(&a, &a); // Valid. p1 and p2 in f4 are both only read.
}

fn f6(p : ptr<private, i32>) {
  x = *p;
}

fn f7(p : ptr<private, i32>) -> i32 {
  return x + *p;
}

fn f8() {
  let a = f6(&x); // Invalid. x is written as a global variable and
                  // read as a parameter.
  let b = f7(&x); // Valid. x is only read as both a parameter and
                  // a variable.
}

## 12. Attributes[](#attributes)

An attribute modifies an object. WGSL provides a unified syntax for applying attributes. Attributes are used for a variety of purposes such as specifying the interface with the API.

Generally speaking, from the language’s point-of-view, attributes can be ignored for the purposes of type and semantic checking. Additionally, the attribute name is a [context-dependent name](#context-dependent-name), and some attribute parameters are also context-dependent names.

Unless explicitly permitted in an attribute’s description, an attribute [must not](#shader-creation-error) be specified more than once per object or type.

### 12.1. `align`[](#align-attr)

align_attr :

[`'@'`](#syntax_sym-attr)`'align'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`align` Attribute Description Constrains the placement of a structure member in memory. 
[Must](#shader-creation-error) only be applied to a member of a [structure](#structure) type.

This attribute influences how a value of the enclosing structure type can appear in memory: it constrains the byte addresses at which the structure itself and its component members can appear.

If `align(`n`)` is applied to a member of S with type T, and S can be the [store type](#store-type) for a variable in address space AS, where AS is not [uniform](#address-spaces-uniform), then n[must](#shader-creation-error) satisfy:

> n=k×[RequiredAlignOf](#requiredalignof)(T,AS) for some positive integer k.

The rules for alignment and size are mutually recursive. However, the above constraint is well defined because it depends on the required alignment of a _nested_ type, and types have bounded [nesting depth](#nesting-depth).

If the start address of the memory bound to the [uniform](#uniform-buffer) or [storage](#storage-buffer) buffer has a lower alignment than the value specified in the attribute, the resulting alignment will be the minimum of the two. An implementation will only satisfy the attribute relative to the base address of the variable.

See [§ 14.4 Memory Layout](#memory-layouts).
Parameters[Must](#shader-creation-error) be a [const-expression](#const-expressions) that [resolves](#type-rule) to an [i32](#i32) or [u32](#u32).  
[Must](#shader-creation-error) be positive.  
[Must](#shader-creation-error) be a power of 2.

### 12.2. `binding`[](#binding-attr)

binding_attr :

[`'@'`](#syntax_sym-attr)`'binding'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`binding` Attribute Description Specifies the binding number of the resource in a bind [group](#attribute-group). See [§ 13.3.2 Resource Interface](#resource-interface). 
[Must](#shader-creation-error) only be applied to a [resource](#resource) variable.
Parameters[Must](#shader-creation-error) be a [const-expression](#const-expressions) that [resolves](#type-rule) to an [i32](#i32) or [u32](#u32).  
[Must](#shader-creation-error) be non-negative.

### 12.3. `blend_src`[](#blend-src-attr)

blend_src_attr :

[`'@'`](#syntax_sym-attr)`'blend_src'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`blend_src` Attribute Description Specifies a part of the [fragment](#fragment) output when the feature [dual_source_blending](#extension-dual_source_blending) is enabled. See [§ 13.3.1.3 Input-output Locations](#input-output-locations). 
[Must](#shader-creation-error) only be applied to a member of a [structure](#structure) type with a [location](#attribute-location) attribute. [Must](#shader-creation-error) only be applied to declarations of objects with [numeric scalar](#numeric-scalar) or [numeric vector](#numeric-vector) type. [Must not](#shader-creation-error) be included in a [shader stage input](#shader-stage-input). [Must not](#shader-creation-error) be included in a [shader stage output](#shader-stage-output), except for the [fragment](#fragment) shader stage.
Parameters[Must](#shader-creation-error) be a [const-expression](#const-expressions) that [resolves](#resolves) to an [i32](#i32) or [u32](#u32) with value of `0` or `1`.

### 12.4. `builtin`[](#builtin-attr)

builtin_attr :

[`'@'`](#syntax_sym-attr)`'builtin'`[`'('`](#syntax_sym-paren_left)[builtin_value_name](#syntax-builtin_value_name)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`builtin` Attribute Description Specifies that the associated object is a built-in value, as denoted by the specified [token](#token). See [§ 13.3.1.1 Built-in Inputs and Outputs](#builtin-inputs-outputs). 
[Must](#shader-creation-error) only be applied to an entry point function parameter, entry point return type, or member of a [structure](#structure).
Parameters[Must](#shader-creation-error) be a [built-in value name-token](#built-in-value-name-token) for a [built-in value](#built-in-values).

### 12.5. `const`[](#const-attr)

`const` Attribute Description Specifies that the function can be used as a [const-function](#const-functions). This attribute [must not](#shader-creation-error) be applied to a user-defined function. 
[Must](#shader-creation-error) only be applied to function declarations.

Note: This attribute is used as a notational convention to describe which built-in functions can be used in [const-expressions](#const-expressions).
Parameters _None_

### 12.6. `diagnostic`[](#diagnostic-attr)

diagnostic_attr :

[`'@'`](#syntax_sym-attr)`'diagnostic'`[diagnostic_control](#syntax-diagnostic_control)

diagnostic_control :

[`'('`](#syntax_sym-paren_left)[severity_control_name](#syntax-severity_control_name)[`','`](#syntax_sym-comma)[diagnostic_rule_name](#syntax-diagnostic_rule_name)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`diagnostic` Attribute Description Specifies a [range diagnostic filter](#range-diagnostic-filter). See [§ 2.3 Diagnostics](#diagnostics). 
More than one [diagnostic](#attribute-diagnostic) attribute may be specified on a syntactic form, but they [must](#shader-creation-error) specify different [triggering rules](#diagnostic-triggering-rule).
Parameters The first parameter is a [severity_control_name](#syntax-severity_control_name). 
The second parameter is a [diagnostic_rule_name](#syntax-diagnostic_rule_name) token specifying a [triggering rule](#diagnostic-triggering-rule).

### 12.7. `group`[](#group-attr)

group_attr :

[`'@'`](#syntax_sym-attr)`'group'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`group` Attribute Description Specifies the binding group of the resource. See [§ 13.3.2 Resource Interface](#resource-interface). 
[Must](#shader-creation-error) only be applied to a [resource](#resource) variable.
Parameters[Must](#shader-creation-error) be a [const-expression](#const-expressions) that [resolves](#type-rule) to an [i32](#i32) or [u32](#u32).  
[Must](#shader-creation-error) be non-negative.

### 12.8. `id`[](#id-attr)

id_attr :

[`'@'`](#syntax_sym-attr)`'id'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`id` Attribute Description Specifies a numeric identifier as an alternate name for a [pipeline-overridable](#pipeline-overridable) constant. 
[Must](#shader-creation-error) only be applied to an [override-declaration](#override-declaration) of [scalar](#scalar) type.
Parameters[Must](#shader-creation-error) be a [const-expression](#const-expressions) that [resolves](#type-rule) to an [i32](#i32) or [u32](#u32).  
[Must](#shader-creation-error) be non-negative.

### 12.9. `interpolate`[](#interpolate-attr)

interpolate_attr :

[`'@'`](#syntax_sym-attr)`'interpolate'`[`'('`](#syntax_sym-paren_left)[interpolate_type_name](#syntax-interpolate_type_name)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

|[`'@'`](#syntax_sym-attr)`'interpolate'`[`'('`](#syntax_sym-paren_left)[interpolate_type_name](#syntax-interpolate_type_name)[`','`](#syntax_sym-comma)[interpolate_sampling_name](#syntax-interpolate_sampling_name)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

interpolate_type_name :

[ident_pattern_token](#syntax-ident_pattern_token)

`interpolate` Attribute Description Specifies how the user-defined IO [must](#shader-creation-error) be interpolated. See [§ 13.3.1.4 Interpolation](#interpolation). 
[Must](#shader-creation-error) only be applied to a declaration that has a [location](#attribute-location) attribute applied.

When present, the attribute is only significant on user-defined [vertex](#vertex) outputs and [fragment](#fragment) inputs.
Parameters The first parameter [must](#shader-creation-error) be an [interpolation type name-token](#interpolation-type-name-token) for an [interpolation type](#interpolation-type). 
The second parameter, if present, [must](#shader-creation-error) be an [interpolation sampling name-token](#interpolation-sampling-name-token) for the [interpolation sampling](#interpolation-sampling).

### 12.10. `invariant`[](#invariant-attr)

invariant_attr :

[`'@'`](#syntax_sym-attr)`'invariant'`

`invariant` Attribute Description When applied to the [position](#built-in-values-position)[built-in output value](#built-in-output-value) of a vertex shader, the computation of the result is invariant across different programs and different invocations of the same entry point. That is, if the data and control flow match for two `position` outputs in different entry points, then the result values are guaranteed to be the same. There is no effect on a `position`[built-in input value](#built-in-input-value). 
[Must](#shader-creation-error) only be applied to the [position](#built-in-values-position) built-in value.

Note: This attribute maps to the `precise` qualifier in HLSL, and the `invariant` qualifier in GLSL.
Parameters _None_

### 12.11. `location`[](#location-attr)

location_attr :

[`'@'`](#syntax_sym-attr)`'location'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`location` Attribute Description Specifies a part of the user-defined IO of an entry point. See [§ 13.3.1.3 Input-output Locations](#input-output-locations). 
[Must](#shader-creation-error) only be applied to an entry point function parameter, entry point return type, or member of a [structure](#structure) type. [Must](#shader-creation-error) only be applied to declarations of objects with [numeric scalar](#numeric-scalar) or [numeric vector](#numeric-vector) type. [Must not](#shader-creation-error) be included in [compute](#compute)[shader stage inputs](#shader-stage-input).
Parameters[Must](#shader-creation-error) be a [const-expression](#const-expressions) that [resolves](#type-rule) to an [i32](#i32) or [u32](#u32).  
[Must](#shader-creation-error) be non-negative.

### 12.12. `must_use`[](#must-use-attr)

must_use_attr :

[`'@'`](#syntax_sym-attr)`'must_use'`

`must_use` Attribute Description Specifies that a [call](#function-call) to this function [must](#shader-creation-error) be used as an [expression](#expression). That is, a call to this function [must](#shader-creation-error) not be the entirety of a [function call statement](#function-call-statement). 
[Must](#shader-creation-error) only be applied to the declaration of a [function](#function-function) with a [return type](#return-type).

Note: Many functions return a value and do not have side effects. It is often a programming defect to call such a function as the only thing in a function call statement. Built-in functions with these properties are declared as `@must_use`. User-defined functions can also have the `@must_use` attribute.

Note: To deliberately work around the `@must_use` rule, use a [phony assignment](#phony-assignment) or [declare a value](#value-declaration) using the function call as the initializer.
Parameters _None_

### 12.13. `size`[](#size-attr)

size_attr :

[`'@'`](#syntax_sym-attr)`'size'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`size` Attribute Description Specifies the number of bytes reserved for a structure member. 
This number [must](#shader-creation-error) be at least the [byte-size](#byte-size) of the type of the member:

If `size(`n`)` is applied to a member with type T, then [SizeOf](#sizeof)(T)≤n.

See [§ 14.4 Memory Layout](#memory-layouts).

[Must](#shader-creation-error) only be applied to a member of a [structure](#structure) type. The member type [must](#shader-creation-error) have [creation-fixed footprint](#creation-fixed-footprint).
Parameters[Must](#shader-creation-error) be a [const-expression](#const-expressions) that [resolves](#type-rule) to an [i32](#i32) or [u32](#u32).  
[Must](#shader-creation-error) be positive.

### 12.14. `subgroup_size`[](#subgroup-size-attr)

subgroup_size_attr :

[`'@'`](#syntax_sym-attr)`'subgroup_size'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`subgroup_size` Attribute Description Specifies the subgroup size for a compute shader invocation. 
[Must](#shader-creation-error) only be applied to a [compute shader](#compute-shader-stage) entry point function.
Requires[Must](#shader-creation-error) only be used when the [subgroup_size_control](#extension-subgroup_size_control) extension is enabled.
Parameters[must](#shader-creation-error) be a [const-expression](#const-expressions) or an [override-expression](#override-expressions) that [resolves](#type-rule) to an [i32](#i32) or [u32](#u32). 
If the value is not a power of two, then:

*   It is a [shader-creation error](#shader-creation-error) if the expression is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if the expression is an [override-expression](#override-expressions).

A [pipeline-creation error](#pipeline-creation-error) results if the x-dimension of the entry point’s `workgroup_size` is not a multiple of the `subgroup_size` value.

A [pipeline-creation error](#pipeline-creation-error) results if the value is greater than `subgroupMaxSize` or smaller than `subgroupMinSize`.

Pipeline creation may result in an [uncategorized error](#uncategorized-error) due to register pressure or specific hardware limitations even when the value is between `subgroupMinSize` and `subgroupMaxSize`.

### 12.15. `workgroup_size`[](#workgroup-size-attr)

workgroup_size_attr :

[`'@'`](#syntax_sym-attr)`'workgroup_size'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

|[`'@'`](#syntax_sym-attr)`'workgroup_size'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

|[`'@'`](#syntax_sym-attr)`'workgroup_size'`[`'('`](#syntax_sym-paren_left)[expression](#syntax-expression)[`','`](#syntax_sym-comma)[expression](#syntax-expression)[`','`](#syntax_sym-comma)[expression](#syntax-expression)[`','`](#syntax_sym-comma) ? [`')'`](#syntax_sym-paren_right)

`workgroup_size` Attribute Description Specifies the x, y, and z dimensions of the [workgroup grid](#workgroup-grid) for the compute shader. 
The first parameter specifies the x dimension. The second parameter, if provided, specifies the y dimension, otherwise is assumed to be 1. The third parameter, if provided, specifies the z dimension, otherwise is assumed to be 1.

[Must](#shader-creation-error) only be applied to a [compute shader](#compute-shader-stage) entry point function. [Must not](#shader-creation-error) be applied to any other object.
Parameters Takes one, two, or three parameters. 
Each parameter [must](#shader-creation-error) be a [const-expression](#const-expressions) or an [override-expression](#override-expressions). All parameters [must](#shader-creation-error) be the same type, either [i32](#i32) or [u32](#u32).

A [shader-creation error](#shader-creation-error) results if any specified parameter is a [const-expression](#const-expressions) that evaluates to a non-positive value.

A [pipeline-creation error](#pipeline-creation-error) results if any specified parameter evaluates to a non-positive value or exceeds an upper bound specified by the WebGPU API, or if the product of the parameter values exceeds the upper bound specified by the WebGPU API (see [WebGPU § 3.6.2 Limits](../webgpu_spec/webgpu-5f71975aec.md#limits)).

### 12.16. Shader Stage Attributes[](#shader-stage-attr)

The shader stage attributes below designate a function as an [entry point](#entry-point) for a particular [shader stage](#shader-stages). These attributes [must](#shader-creation-error) only be applied to [function declarations](#function-declaration), and at most one may be present on a given function. They take no parameters.

#### 12.16.1. `vertex`[](#vertex-attr)

vertex_attr :

[`'@'`](#syntax_sym-attr)`'vertex'`

The `vertex` attribute declares the function to be an [entry point](#entry-point) for the [vertex shader stage](#vertex-shader-stage) of a [render pipeline](#gpurenderpipeline).

#### 12.16.2. `fragment`[](#fragment-attr)

fragment_attr :

[`'@'`](#syntax_sym-attr)`'fragment'`

The `fragment` attribute declares the function to be an [entry point](#entry-point) for the [fragment shader stage](#fragment-shader-stage) of a [render pipeline](#gpurenderpipeline).

#### 12.16.3. `compute`[](#compute-attr)

compute_attr :

[`'@'`](#syntax_sym-attr)`'compute'`

The `compute` attribute declares the function to be an [entry point](#entry-point) for the [compute shader stage](#compute-shader-stage) of a [compute pipeline](#gpucomputepipeline).

## 13. Entry Points[](#entry-points)

An entry point is a [user-defined function](#user-defined-function) that performs the work for a particular [shader stage](#shader-stages).

### 13.1. Shader Stages[](#shader-stages-sec)

WebGPU issues work to the GPU in the form of [draw](#draw-command) or [dispatch commands](#dispatch-command). These commands execute a pipeline in the context of a set of shader stage [inputs](#shader-stage-input), [outputs](#shader-stage-output), and attached [resources](#resource).

A pipeline describes the work to be performed on the GPU, as a sequence of stages, some of which are programmable. In WebGPU, a pipeline is created before scheduling a draw or dispatch command for execution. There are two kinds of pipelines: GPUComputePipeline, and GPURenderPipeline.

A [dispatch command](#dispatch-command) uses a GPUComputePipeline to run a compute shader stage over a logical grid of points with a controllable amount of parallelism, while reading and possibly updating buffer and image resources.

A [draw command](#draw-command) uses a GPURenderPipeline to run a multi-stage process with two programmable stages among other fixed-function stages:

*   A vertex shader stage maps input attributes for a single vertex into output attributes for the vertex.

*   Fixed-function stages map vertices into graphic primitives (such as triangles) which are then rasterized to produce rasterization fragments. Each rasterization fragment represents the overlap between the primitive being drawn, and a particular pixel in the [framebuffer](../WGPU/gpuweb-spec/gpuweb-spec.md#framebuffer).

*   A fragment shader stage processes each fragment, possibly producing a fragment output.

    *   Typically, one fragment shader invocation is created for each [rasterization fragment](#rasterization-fragments). More than one fragment invocation may be created if the rasterization fragment covers multiple samples. See [WebGPU § 23.2.10 Per-Sample Shading](../webgpu_spec/webgpu-5f71975aec.md#per-sample-shading).

    *   If the rasterization fragment is near the boundary of the primitive, then additional [helper invocations](#helper-invocation) may also be created. See [§ 15.4 Fragment Shaders and Helper Invocations](#fragment-shaders-helper-invocations).

*   Fixed-function stages consume a fragment output, possibly updating external state such as color attachments and depth and stencil buffers.

The WebGPU specification describes pipelines in greater detail.

WGSL defines three shader stages, corresponding to the programmable parts of pipelines:

*   compute

*   vertex

*   fragment

Each shader stage has its own set of features and constraints, described elsewhere.

### 13.2. Entry Point Declaration[](#entry-point-decl)

To create an [entry point](#entry-point), declare a [user-defined function](#user-defined-function) with a [shader stage attribute](#shader-stage-attributes).

When configuring a [pipeline](#pipeline) in the WebGPU API, the entry point’s function name maps to the `entryPoint` attribute of the WebGPU `GPUProgrammableStage` object.

The entry point’s [formal parameters](#formal-parameter) denote the stage’s [shader stage inputs](#shader-stage-input). A structure type can be used to group [user-defined inputs](#user-defined-input-datum) with each other and optionally with [built-in inputs](#built-in-input-value). Each parameter [must](#shader-creation-error) either be a shader stage input, or it [must](#shader-creation-error) be declared with a structure type where each structure member is a shader stage input.

If specified, the entry point’s [return type](#return-type) and its attributes denotes the stage’s [shader stage outputs](#shader-stage-output). A structure type can be used to group [user-defined outputs](#user-defined-output-datum) with each other and optionally with [built-in outputs](#built-in-output-value). If present, the return type and its attributes [must](#shader-creation-error) be a shader stage output, or it [must](#shader-creation-error) be a structure type where each structure member is a shader stage output.

Note:[Compute](#compute) entry points never have a return type.

EXAMPLE: Entry Point

@vertex
fn vert_main() -> @builtin(position) vec4<f32> {
  return vec4<f32>(0.0, 0.0, 0.0, 1.0);
}

@fragment
fn frag_main(@builtin(position) coord_in: vec4<f32>) -> @location(0) vec4<f32> {
  return vec4<f32>(coord_in.x, coord_in.y, 0.0, 1.0);
}

@compute @workgroup_size(1)
fn comp_main() { }

The set of functions in a shader stage is the union of:

*   The entry point function for the stage.

*   The targets of function calls from within the body of a function in the shader stage, whether or not that call is executed.

The union is applied repeatedly until it stabilizes. It will stabilize in a finite number of steps.

#### 13.2.1. Function Attributes for Entry Points[](#entry-point-attributes)

WGSL defines the following attributes that can be applied to entry point declarations:

*   the [shader stage attributes](#shader-stage-attributes): [vertex](#attribute-vertex), [fragment](#attribute-fragment), and [compute](#attribute-compute)

*   [workgroup_size](#attribute-workgroup_size)

*   [subgroup_size](#attribute-subgroup_size)

EXAMPLE: workgroup_size Attribute

@compute @workgroup_size(8,4,1)
fn sorter() { }

@compute @workgroup_size(8u)
fn reverser() { }

// Using an pipeline-overridable constant.
@id(42) override block_width = 12u;
@compute @workgroup_size(block_width)
fn shuffler() { }

// Error: workgroup_size must be specified on compute shader
@compute
fn bad_shader() { }

### 13.3. Shader Interface[](#shader-interface)

The shader interface is the set of objects through which the shader accesses data external to the [shader stage](#shader-stages), either for reading or writing, and the [pipeline-overridable](#pipeline-overridable) constants used to configure the shader. The interface includes:

*   [Shader stage inputs](#shader-stage-input)

*   [Shader stage outputs](#shader-stage-output)

*   [Override-declarations](#override-declaration)

*   [Immediate data](#immediate-data)

*   Attached [resources](#resource), which include:

    *   [Uniform buffers](#uniform-buffer)

    *   [Storage buffers](#storage-buffer)

    *   [Texture resources](#texture-resource)

    *   [Sampler resources](#sampler-resource)

A declaration _D_ is statically accessed by a shader when:

*   An identifier [resolving](#resolves) to _D_ appears in the [declaration](#function-declaration) of any of the [functions in the shader stage](#functions-in-a-shader-stage).

*   An identifier [resolving](#resolves) to _D_ is used to define a type for a [statically accessed](#statically-accessed) declaration.

*   An identifier [resolving](#resolves) to _D_ is used in the initializer for a [statically accessed](#statically-accessed) declaration.

*   An identifier [resolving](#resolves) to _D_ is used by an attribute used by a [statically accessed](#statically-accessed) declaration.

Note:Static access is recursively defined, taking into account the following:

*   All the parts of a [function declaration](#function-declaration) including attributes, formal parameters, return type, and function body.

*   Any type needed to define the above, including following [type aliases](#type-alias).

*   As a particular case of helping to define a type, any [override-declaration](#override-declaration) used in an [override-expression](#override-expressions) that is the [element count](#element-count) of an [array](#array) type for a variable in the [workgroup](#address-spaces-workgroup) address space, when that variable itself is statically accessed.

*   Any override declarations used to support the evaluation of override-expressions in any of the above.

*   Any attributes on any of the above.

We can now precisely define the interface of a shader as consisting of:

*   The [formal parameters](#formal-parameter) of the [entry point](#entry-point). These denote the shader stage inputs.

*   The [return value](#return-value) of the entry point. This denotes the shader stage outputs.

*   The [uniform buffer](#uniform-buffer), [storage buffer](#storage-buffer), [texture resource](#texture-resource), and [sampler resource](#sampler-resource) variables [statically accessed](#statically-accessed) by the shader.

*   The [override-declarations](#override-declaration)[statically accessed](#statically-accessed) by the shader.

*   The [immediate data](#immediate-data) variables [statically accessed](#statically-accessed) by the shader.

#### 13.3.1. Inter-stage Input and Output Interface[](#stage-inputs-outputs)

A shader stage input is a datum provided to the shader stage from upstream in the pipeline. Each datum is either a [built-in input value](#built-in-input-value), or a [user-defined input](#user-defined-input-datum).

A shader stage output is a datum the shader provides for further processing downstream in the pipeline. Each datum is either a [built-in output value](#built-in-output-value), or a [user-defined output](#user-defined-output-datum).

[IO attributes](#io-attributes) are used to establish an object as a [shader stage input](#shader-stage-input) or a [shader stage output](#shader-stage-output), or to further describe the properties of an input or output. The IO attributes are:

*   [builtin](#attribute-builtin)

*   [location](#attribute-location)

*   [blend_src](#attribute-blend_src)

*   [interpolate](#attribute-interpolate)

*   [invariant](#attribute-invariant)

##### 13.3.1.1. Built-in Inputs and Outputs[](#builtin-inputs-outputs)

A built-in input value provides access to system-generated control information. An entry point [must](#shader-creation-error) not have two built-in inputs with the same [built-in value name](#built-in-value-name-token).

A built-in input for stage _S_ with name _X_ and type _T_ _X_ is accessed via a [formal parameter](#formal-parameter) to an [entry point](#entry-point) for [shader stage](#shader-stages)_S_, in one of two ways:

1.   The parameter has attribute `builtin(`_X_`)` and is of type _T_ _X_.

2.   The parameter has structure type, where one of the structure members has attribute `builtin(`_X_`)` and is of type _T_ _X_.

Conversely, when a parameter or member of a parameter for an entry point has a [builtin](#attribute-builtin) attribute, the corresponding builtin [must](#shader-creation-error) be an input for the entry point’s shader stage.

A built-in output value is used by the shader to convey control information to later processing steps in the pipeline. An entry point [must](#shader-creation-error) not have two built-in outputs with the same [built-in value name](#built-in-value-name-token).

A built-in output for stage _S_ with name _Y_ and type _T_ _Y_ is set via the [return value](#return-value) for an [entry point](#entry-point) for [shader stage](#shader-stages)_S_, in one of two ways:

1.   The entry point [return type](#return-type) has attribute `builtin(`_Y_`)` and is of type _T_ _Y_.

2.   The entry point [return type](#return-type) has structure type, where one of the structure members has attribute `builtin(`_Y_`)` and is of type _T_ _Y_.

Conversely, when the return type or member of a return type for an entry point has a [builtin](#attribute-builtin) attribute, the corresponding builtin [must](#shader-creation-error) be an output for the entry point’s shader stage.

Note: The [position](#built-in-values-position) built-in is both an output of a vertex shader, and an input to the fragment shader.

Collectively, built-in input and built-in output values are known as built-in values.

The following table summarizes the available built-in values. Each is a [built-in value name](#built-in-value-name-token)[token](#token) for a [built-in value](#built-in-values). Each is described in detail in subsequent sections.

Built-in input and output values
| Name | Stage | Direction | Type | [Extension](#extension)| [vertex_index](#built-in-values-vertex_index) | vertex | input | u32 | | | [instance_index](#built-in-values-instance_index) | vertex | input | u32 | | [clip_distances](#built-in-values-clip_distances) | vertex | output | array<f32, N> (`N` ≤ `8`) | [clip_distances](#extension-clip_distances) | | [position](#built-in-values-position) | vertex | output | vec4<f32> | | | fragment | input | vec4<f32> | | [front_facing](#built-in-values-front_facing) | fragment | input | bool | | [frag_depth](#built-in-values-frag_depth) | fragment | output | f32 | | [primitive_index](#built-in-values-primitive_index) | fragment | input | u32 | [primitive_index](#extension-primitive_index) | | [sample_index](#built-in-values-sample_index) | fragment | input | u32 | | | [sample_mask](#built-in-values-sample_mask) | fragment | input | u32 | | fragment | output | u32 | | [local_invocation_id](#built-in-values-local_invocation_id) | compute | input | vec3<u32> | | [local_invocation_index](#built-in-values-local_invocation_index) | compute | input | u32 | | [global_invocation_id](#built-in-values-global_invocation_id) | compute | input | vec3<u32> | | [global_invocation_index](#built-in-values-global_invocation_index) | compute | input | u32 | [linear_indexing](#language_extension-linear_indexing) | | [workgroup_id](#built-in-values-workgroup_id) | compute | input | vec3<u32> | | | [workgroup_index](#built-in-values-workgroup_index) | compute | input | u32 | [linear_indexing](#language_extension-linear_indexing) | | [num_workgroups](#built-in-values-num_workgroups) | compute | input | vec3<u32> | | | [subgroup_invocation_id](#built-in-values-subgroup_invocation_id) | compute | input | u32 | [subgroups](#extension-subgroups) | | fragment | | [subgroup_size](#built-in-values-subgroup_size) | compute | input | u32 | [subgroups](#extension-subgroups) | | fragment | | [subgroup_id](#built-in-values-subgroup_id) | compute | input | u32 | [subgroups](#extension-subgroups) and [subgroup_id](#language_extension-subgroup_id) | | [num_subgroups](#built-in-values-num_subgroups) | compute | input | u32 | [subgroups](#extension-subgroups) and [subgroup_id](#language_extension-subgroup_id) | |
| --- | --- | --- | --- | --- |

EXAMPLE: Declaring built-in values

 struct VertexOutput {
   @builtin(position) my_pos: vec4<f32>,
   @builtin(clip_distances) my_clip_distances: array<f32, 8>,
 }

 @vertex
 fn vs_main(
   @builtin(vertex_index) my_index: u32,
   @builtin(instance_index) my_inst_index: u32,
 ) -> VertexOutput {}

 struct FragmentOutput {
   @builtin(frag_depth) depth: f32,
   @builtin(sample_mask) mask_out: u32
 }

 @fragment
 fn fs_main(
   @builtin(front_facing) is_front: bool,
   @builtin(position) coord: vec4<f32>,
   @builtin(sample_index) my_sample_index: u32,
   @builtin(sample_mask) mask_in: u32,
 ) -> FragmentOutput {}

 @compute @workgroup_size(64)
 fn cs_main(
   @builtin(local_invocation_id) local_id: vec3<u32>,
   @builtin(local_invocation_index) local_index: u32,
   @builtin(global_invocation_id) global_id: vec3<u32>,
) {}

###### 13.3.1.1.1. `clip_distances`[](#clip-distances-builtin-value)

Name clip_distances
Stage[vertex](#vertex-shader-stage)
Type array<f32, N>
Direction Output
Description Each value in the array represents a distance to a user-defined clip plane. A clip distance of `0` means the vertex is on the plane, a positive distance means the vertex is inside the clip half-space, and a negative distance means the vertex is outside the clip half-space. The array size of [clip_distances](#built-in-values-clip_distances)[must](#shader-creation-error) be ≤ `8`. See [WebGPU § 23.2.4 Primitive Clipping](../webgpu_spec/webgpu-5f71975aec.md#primitive-clipping).

###### 13.3.1.1.2. `frag_depth`[](#frag-depth-builtin-value)

Name frag_depth
Stage[fragment](#fragment-shader-stage)
Type f32
Direction Output
Description Updated depth of the fragment, in the viewport depth range. 
See [WebGPU § 3.3 Coordinate Systems](../webgpu_spec/webgpu-5f71975aec.md#coordinate-systems).

If the [fragment_depth](#language_extension-fragment_depth) feature is supported, then the [builtin](#attribute-builtin) attribute can have an optional second parameter to specify a [depth mode](#depth-mode-name-token):

*   Specifying the [depth_mode](#depth-mode-name-token)`less` is a promise that if the [fragment](#fragment) shader returns [frag_depth](#built-in-values-frag_depth) (i.e. doesn’t `discard`), then the returned value will be less than or equal to the original depth of the [fragment](#fragment).

*   Specifying the [depth_mode](#depth-mode-name-token)`greater` is a promise that if the [fragment](#fragment) shader returns [frag_depth](#built-in-values-frag_depth) (i.e. doesn’t `discard`), then the returned value will be greater than or equal to the original depth of the [fragment](#fragment).

The original depth of the [fragment](#fragment) is the depth property of the fragment’s [RasterizationPoint](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint).

If the shader returns a depth value that violates the depth mode promise, then an indeterminate depth value may be used instead.

@fragment
fn main() -> @builtin(frag_depth, greater) f32 {
    return 1.0f;
}

###### 13.3.1.1.3. `front_facing`[](#front-facing-builtin-value)

Name front_facing
Stage[fragment](#fragment-shader-stage)
Type bool
Direction Input
Description True when the current fragment is on a [front-facing](../WGPU/gpuweb-spec/gpuweb-spec.md#front-facing) primitive. False otherwise.

###### 13.3.1.1.4. `global_invocation_id`[](#global-invocation-id-builtin-value)

Name global_invocation_id
Stage[compute](#compute-shader-stage)
Type vec3<u32>
Direction Input
Description The current invocation’s [global invocation ID](#global-invocation-id), i.e. its position in the [compute shader grid](#compute-shader-grid). The value of [global_invocation_id](#built-in-values-global_invocation_id) is equal to [workgroup_id](#built-in-values-workgroup_id) * [workgroup_size](#attribute-workgroup_size) + [local_invocation_id](#built-in-values-local_invocation_id).

###### 13.3.1.1.5. `global_invocation_index`[](#global-invocation-index-builtin-value)

Name global_invocation_index
Stage[compute](#compute-shader-stage)
Type u32;
Direction Input
Description The current invocation’s [global invocation index](#global-invocation-index), i.e. its linear position in the [compute shader grid](#compute-shader-grid). The value of [global_invocation_index](#built-in-values-global_invocation_index) is equal to: 
[global_invocation_id](#built-in-values-global_invocation_id).x +  
 ([global_invocation_id](#built-in-values-global_invocation_id).y * [workgroup_size](#attribute-workgroup_size).x * [num_workgroups](#built-in-values-num_workgroups).x) +  
 ([global_invocation_id](#built-in-values-global_invocation_id).z * [workgroup_size](#attribute-workgroup_size).x * [num_workgroups](#built-in-values-num_workgroups).x * [workgroup_size](#attribute-workgroup_size).y * [num_workgroups](#built-in-values-num_workgroups).y)

Note: If the number of dispatched workgroups would cause this value to exceed the range of the [u32](#u32) type, then the dispatch will fail:

*   For `dispatchWorkgroups`, the `GPUComputePassEncoder` will be invalidated.

*   For `dispatchWorkgroupsIndirect`, the dispatch will not execute.

###### 13.3.1.1.6. `instance_index`[](#instance-index-builtin-value)

Name instance_index
Stage[vertex](#vertex-shader-stage)
Type u32
Direction Input
Description Instance index of the current vertex within the current API-level draw command. 
The first instance has an index equal to the `firstInstance` argument of the draw, whether provided directly or indirectly. The index is incremented by one for each additional instance in the draw.

###### 13.3.1.1.7. `local_invocation_id`[](#local-invocation-id-builtin-value)

Name local_invocation_id
Stage[compute](#compute-shader-stage)
Type vec3<u32>
Direction Input
Description The current invocation’s [local invocation ID](#local-invocation-id), i.e. its position in the [workgroup grid](#workgroup-grid).

###### 13.3.1.1.8. `local_invocation_index`[](#local-invocation-index-builtin-value)

Name local_invocation_index
Stage[compute](#compute-shader-stage)
Type u32
Direction Input
Description The current invocation’s [local invocation index](#local-invocation-index), a linearized index of the invocation’s position within the [workgroup grid](#workgroup-grid).

###### 13.3.1.1.9. `num_workgroups`[](#num-workgroups-index-builtin-value)

Name num_workgroups
Stage[compute](#compute-shader-stage)
Type vec3<u32>
Direction Input
Description The [dispatch size](#dispatch-size), `vec3<u32>(group_count_x, group_count_y,       group_count_z)`, of the compute shader [dispatched](../webgpu_spec/webgpu-5f71975aec.md#compute-pass-encoder-dispatch) by the API.

###### 13.3.1.1.10. `position`[](#position-builtin-value)

Name position
Stage[fragment](#fragment-shader-stage)
Type vec4<f32>
Direction Input
Description Input position of the current fragment rasterization point.

Let rp be the [RasterizationPoint](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint) for the fragment.  
 Let vp be the `[[viewport]]` in effect for the draw command.  
 Then fp is the computed input position of the fragment rasterization point.

Then schematically:

> fp.xy = rp.[destination](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint-destination).[position](../WGPU/gpuweb-spec/gpuweb-spec.md#fragmentdestination-position) 
> fp.z = rp.[depth](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint-depth) 
> fp.w = rp.[perspectiveDivisor](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint-perspectivedivisor)

In more detail:

*   fp.x and fp.y are the interpolated x and y coordinates of the position the current fragment rasterization point in the [framebuffer](../WGPU/gpuweb-spec/gpuweb-spec.md#framebuffer).

The framebuffer is a two-dimensional grid of pixels with the top-left at (0.0,0.0) and the bottom right at (vp.width, vp.height). Each pixel has an extent of 1.0 unit in each of the x and y dimensions, and pixel centers are at (0.5,0.5) offset from integer coordinates.

*   fp.z is the interpolated depth of the current fragment rasterization point. For example:

    *   depth 0 in [normalized device coordinates](../WGPU/gpuweb-spec/gpuweb-spec.md#ndc) maps to fp.z = vp.minDepth,

    *   depth 1 in normalized device coordinates maps to fp.z = vp.maxDepth.

*   fp.w is the perspective divisor for the fragment rasterization point, which is the interpolation of 1.0 ÷ vertex_w, where vertex_w is the w component of the [position](#built-in-values-position) output of the vertex shader.

See [WebGPU § 3.3 Coordinate Systems](../webgpu_spec/webgpu-5f71975aec.md#coordinate-systems) and [WebGPU § 23.2.5 Rasterization](../webgpu_spec/webgpu-5f71975aec.md#rasterization).

###### 13.3.1.1.11. `primitive_index`[](#primitive-index-builtin-value)

Name primitive_index
Stage[fragment](#fragment-shader-stage)
Type u32
Direction Input
Description Per-primitive index based on the number of primitives processed for the current instance since the beginning of the current draw operation. Begins at 0 and increments by 1 after every point, line, or triangle primitive is processed. Resets to 0 between each instance drawn. Restarting a strip primitive with the [primitive restart value](../WGPU/gpuweb-spec/gpuweb-spec.md#primitive-restart-value) has no effect on the primitive index. The index is uniform across all fragments of the primitive.

###### 13.3.1.1.12. `sample_index`[](#sample-index-builtin-value)

Name sample_index
Stage[fragment](#fragment-shader-stage)
Type u32
Direction Input
Description Sample index for the current fragment rasterization point. The value is least 0 and at most `sampleCount`-1, where `sampleCount` is the sample `count` specified for the GPU render pipeline. When this attribute is applied, if the effects of the fragment shader would vary based on the value of [sample_index](#built-in-values-sample_index), the [fragment](#fragment) shader will be invoked once per sample. 
See [WebGPU § 10.3 GPURenderPipeline](../webgpu_spec/webgpu-5f71975aec.md#gpurenderpipeline).

###### 13.3.1.1.13. `sample_mask`[](#sample-mask-builtin-value)

Name sample_mask
Stage[fragment](#fragment-shader-stage)
Type u32
Direction Input
Description Sample coverage bitmask for the current fragment. 
Bits are indexed by a sample index in the half-open interval [0, `sampleCount`), where `sampleCount` is the sample `count` specified for the GPU render pipeline.

A bit will be set to 1 _only if_ the sample is covered by the primitive being rendered. Bits with index `sampleCount` and above are always set to zero.

There are two possible values for the bitmask:

*   The bitmask has a 1 bit set for every sample covered by the fragment. In this case the bitmask equals the fragment’s [RasterizationPoint](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint)[coverageMask](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint-coveragemask).

*   The bitmask has only 1 bit set, corresponding to the sample being processed by the current fragment shader invocation. That is, the bitmask is (1 `<<`[sample_index](#built-in-values-sample_index)), as if using the `sample_index` built-in input.

Note: These two cases are the same when `sampleCount` = 1.

Note: This is a known portability hazard when `sampleCount`> 1. Some devices yield the full coverage mask. Other devices yield the single-bit mask.

See [WebGPU § 23.2.10 Per-Sample Shading](../webgpu_spec/webgpu-5f71975aec.md#per-sample-shading) and [WebGPU § 23.2.11 Sample Masking](../webgpu_spec/webgpu-5f71975aec.md#sample-masking).

Name sample_mask
Stage[fragment](#fragment-shader-stage)
Type u32
Direction Output
Description Sample coverage mask control for the current fragment. The last value written to this variable becomes the [shader-output mask](../WGPU/gpuweb-spec/gpuweb-spec.md#shader-output-mask). Zero bits in the written value will cause corresponding samples in the color attachments to be discarded. 
See [WebGPU § 23.2.11 Sample Masking](../webgpu_spec/webgpu-5f71975aec.md#sample-masking).

###### 13.3.1.1.14. `vertex_index`[](#vertex-index-builtin-value)

Name vertex_index
Stage[vertex](#vertex-shader-stage)
Type u32
Direction Input
Description Index of the current vertex within the current API-level draw command, independent of draw instancing. 
For a non-indexed draw, the first vertex has an index equal to the `firstVertex` argument of the draw, whether provided directly or indirectly. The index is incremented by one for each additional vertex in the draw instance.

For an indexed draw, the index is equal to the index buffer entry for the vertex, plus the `baseVertex` argument of the draw, whether provided directly or indirectly.

###### 13.3.1.1.15. `workgroup_id`[](#workgroup-id-builtin-value)

Name workgroup_id
Stage[compute](#compute-shader-stage)
Type vec3<u32>
Direction Input
Description The current invocation’s [workgroup ID](#workgroup-id), i.e. the position of the workgroup in overall [compute shader grid](#compute-shader-grid). 
All invocations in the same workgroup have the same workgroup ID.

Workgroup IDs span from (0,0,0) to ([group_count_x](#group_count_x) - 1, [group_count_y](#group_count_y) - 1, [group_count_z](#group_count_z) - 1).

###### 13.3.1.1.16. `workgroup_index`[](#workgroup-index-builtin-value)

Name workgroup_index
Stage[compute](#compute-shader-stage)
Type u32
Direction Input
Description The current invocation’s [workgroup index](#workgroup-index), i.e. the linear position of the workgroup in overall [compute shader grid](#compute-shader-grid). 
All invocations in the same workgroup have the same workgroup index.

Note: If the number of dispatched workgroups would cause this value to exceed the range of the [u32](#u32) type, then the dispatch will fail:

*   For `dispatchWorkgroups`, the `GPUComputePassEncoder` will be invalidated.

*   For `dispatchWorkgroupsIndirect`, the dispatch will not execute.

###### 13.3.1.1.17. `subgroup_invocation_id`[](#subgroup-invocation-id-builtin-value)

Name subgroup_invocation_id
Stage[compute](#compute-shader-stage) or [fragment](#fragment-shader-stage)
Type u32
Direction Input
Description The current invocation’s [subgroup invocation ID](#subgroup-invocation-id). 
The ID is within the range [0, [subgroup_size](#built-in-values-subgroup_size) - 1].

In a [compute](#compute-shader-stage) shader, IDs begin at zero and are dense. That is, when the compute shader begins execution, then within each subgroup:

*   One invocation will have `subgroup_invocation_id` = 0, and

*   If the subgroup has an invocation with `subgroup_invocation_id` = k, then the subgroup has an invocation with `subgroup_invocation_id` = j, for all 0 ≤ j<k.

Note: Subgroup invocation indexing in fragment shaders may not be dense. The implementation may assign some lower-numbered IDs to [helper invocations](#helper-invocation).

###### 13.3.1.1.18. `subgroup_size`[](#subgroup-size-builtin-value)

Name subgroup_size
Stage[compute](#compute-shader-stage) or [fragment](#fragment-shader-stage)
Type u32
Direction Input
Description The [subgroup size](#subgroup-size) of current invocation’s subgroup. 
For compute shaders with a [subgroup_size](#attribute-subgroup_size) attribute, this value is equal to the specified attribute value.

###### 13.3.1.1.19. `subgroup_id`[](#subgroup-id-builtin-value)

Name subgroup_id
Stage[compute](#compute-shader-stage)
Type u32
Direction Input
Description The [subgroup ID](#subgroup-id) of current invocation’s [subgroup](#subgroup) within the [workgroup](#compute-shader-stage-workgroup). 
The ID is in the range [0, [num_subgroups](#built-in-values-num_subgroups) - 1].

###### 13.3.1.1.20. `num_subgroups`[](#num-subgroups-builtin-value)

Name num_subgroups
Stage[compute](#compute-shader-stage)
Type u32
Direction Input
Description The number of [subgroups](#subgroup) in the current invocation’s [workgroup](#compute-shader-stage-workgroup).

##### 13.3.1.2. User-defined Inputs and Outputs[](#user-defined-inputs-outputs)

User-defined data can be passed as input to the start of a pipeline, passed between stages of a pipeline or output from the end of a pipeline.

Each user-defined input datum and user-defined output datum[must](#shader-creation-error):

*   be of [numeric scalar](#numeric-scalar) type or [numeric vector](#numeric-vector) type.

*   be assigned an IO location. See [§ 13.3.1.3 Input-output Locations](#input-output-locations).

A [compute](#compute) shader [must not](#shader-creation-error) have user-defined inputs or outputs.

##### 13.3.1.3. Input-output Locations[](#input-output-locations)

Each input-output location can store a value up to 16 bytes in size. The byte size of a type is defined using the _SizeOf_ column in [§ 14.4.1 Alignment and Size](#alignment-and-size). For example, a four-component vector of floating-point values occupies a single location.

IO locations are specified via the [location](#attribute-location) attribute.

Each user-defined [input](#user-defined-input-datum) and [output](#user-defined-output-datum)[must](#shader-creation-error) have an explicitly specified IO location. Each structure member in the entry point IO [must](#shader-creation-error) be one of either a built-in value (see [§ 13.3.1.1 Built-in Inputs and Outputs](#builtin-inputs-outputs)), or assigned a location.

For each entry point defined in a WGSL module, let inputs be its set of shader stage inputs (i.e. locations for its formal parameters, or for the members of its formal parameters of structure type).

*   inputs[must not](#shader-creation-error) contain two entries with the same [location](#attribute-location) value.

For each structure type S defined in a WGSL module (not just those used in shader stage inputs or outputs), let members be the set of members of S that have [location](#attribute-location) attributes.

*   If any entry in members specifies a [blend_src](#attribute-blend_src) attribute, members must  use dual source blending, which means:

    *   members[must](#shader-creation-error) contain exactly `2` entries, one with `@location(0) @blend_src(0)` and one with `@location(0) @blend_src(1)`.

    *   All the members[must](#shader-creation-error) have same data type.

*   Otherwise, members[must not](#shader-creation-error) contain two entries with the same [location](#attribute-location) value.

Note: Location numbering is distinct between inputs and outputs: Location numbers for an entry point’s shader stage inputs do not conflict with location numbers for the entry point’s shader stage outputs.

Note: No additional rule is required to prevent location overlap within an entry point’s outputs. When the output is a structure, the first rule above prevents overlap. Otherwise, the output is a scalar or a vector, and can have only a single location assigned to it.

Note: The number of available locations for an entry point is defined by the WebGPU API.

EXAMPLE: Applying location attributes

struct A {
  @location(0) x: f32,
  // Despite locations being 16-bytes, x and y cannot share a location
  @location(1) y: f32
}

// in1 occupies locations 0 and 1.
// in2 occupies location 2.
// The return value occupies location 0.
@fragment
fn fragShader(in1: A, @location(2) in2: f32) -> @location(0) vec4<f32> {
 // ...
}

User-defined IO can be mixed with built-in values in the same structure. For example,

EXAMPLE: Mixing builtins and user-defined IO

// Mixed builtins and user-defined inputs.
struct MyInputs {
  @location(0) x: vec4<f32>,
  @builtin(front_facing) y: bool,
  @location(1) @interpolate(flat) z: u32
}

struct MyOutputs {
  @builtin(frag_depth) x: f32,
  @location(0) y: vec4<f32>
}

@fragment
fn fragShader(in1: MyInputs) -> MyOutputs {
  // ...
}

EXAMPLE: Invalid location assignments

struct A {
  @location(0) x: f32,
  // Invalid, x and y cannot share a location.
  @location(0) y: f32
}

struct B {
  @location(0) x: f32
}

struct C {
  // Invalid, structures with user-defined IO cannot be nested.
  b: B
}

struct D {
  x: vec4<f32>
}

@fragment
// Invalid, location cannot be applied to a structure type.
fn fragShader1(@location(0) in1: D) {
  // ...
}

@fragment
// Invalid, in1 and in2 cannot share a location.
fn fragShader2(@location(0) in1: f32, @location(0) in2: f32) {
  // ...
}

@fragment
// Invalid, location cannot be applied to a structure.
fn fragShader3(@location(0) in1: vec4<f32>) -> @location(0) D {
  // ...
}

##### 13.3.1.4. Interpolation[](#interpolation)

Authors can control how user-defined IO data is interpolated through the use of the [interpolate](#attribute-interpolate) attribute. WGSL offers two aspects of interpolation to control: the type of interpolation, and the sampling of the interpolation.

The interpolation type[must](#shader-creation-error) be one of the following [interpolation type name](#interpolation-type-name-token)[tokens](#token):

perspective
Values are interpolated in a perspective correct manner.

linear
Values are interpolated in a linear, non-perspective correct manner.

flat
Values are not interpolated.

The interpolation sampling[must](#shader-creation-error) be one of the following [interpolation sampling name](#interpolation-sampling-name-token)[tokens](#token):

center
Interpolation is performed at the center of the pixel.

centroid
Interpolation is performed at a point that lies within all the samples covered by the fragment within the current primitive. This value is the same for all samples in the primitive.

sample
Interpolation is performed per sample. The [fragment](#fragment) shader is invoked once per sample when this attribute is applied.

first
The value is provided by the first vertex of the primitive.

either
The value is provided by the first vertex or last vertex of the primitive. Whether the value comes from the first or last vertex is implementation dependent.

For user-defined IO of scalar or vector floating-point type:

*   If the interpolation attribute is not specified, then `@interpolate(perspective, center)` is assumed.

*   If the interpolation attribute is specified with an interpolation type:

    *   If the interpolation type is `flat`, then:

        *   If interpolation sampling is specified, it [must](#shader-creation-error) be `first` or `either`.

        *   Otherwise, `first` is assumed.

    *   If the interpolation type is `perspective` or `linear`, then:

        *   If interpolation sampling is specified, it [must](#shader-creation-error) be `center`, `centroid`, or `sample`.

        *   Otherwise, `center` is assumed.

User-defined [vertex](#vertex) outputs and [fragment](#fragment) inputs of scalar or vector integer type [must](#shader-creation-error) always be specified with interpolation type `flat`.

[Interstage interface validation](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-validating-inter-stage-interfaces) checks that, within a [render pipeline](#gpurenderpipeline), the interpolation properties of each user-defined [fragment](#fragment) input match the interpolation properties of a vertex output with the same [location](#attribute-location) assignment. If not, a [pipeline-creation error](#pipeline-creation-error)[will](#behavioral-requirements) result.

#### 13.3.2. Resource Interface[](#resource-interface)

A resource is an object which provides access to data external to a [shader stage](#shader-stages), and which is not an [override-declaration](#override-declaration), not an [immediate data](#immediate-data) variable, and not a [shader stage input or output](#stage-inputs-outputs). Resources are shared by all invocations of the shader.

There are four kinds of resources:

*   [Uniform buffers](#uniform-buffer)

*   [Storage buffers](#storage-buffer)

*   [Texture resources](#texture-resource)

*   [Sampler resources](#sampler-resource)

The resource interface of a shader is the set of module-scope resource variables [statically accessed](#statically-accessed) by [functions in the shader stage](#functions-in-a-shader-stage).

Each resource variable [must](#shader-creation-error) be declared with both [group](#attribute-group) and [binding](#attribute-binding) attributes. Together with the shader’s stage, these identify the binding address of the resource on the shader’s pipeline. See [WebGPU § 8.3 GPUPipelineLayout](../webgpu_spec/webgpu-5f71975aec.md#gpupipelinelayout).

[Immediate data](#immediate-data) variables do not use [group](#attribute-group) or [binding](#attribute-binding) attributes.

Two different resource variables in a [shader](#shader)[must not](#shader-creation-error) have the same [group](#attribute-group) and [binding](#attribute-binding) values, when considered as a pair.

#### 13.3.3. Resource Layout Compatibility[](#resource-layout-compatibility)

WebGPU requires that a shader’s resource interface match the [layout of the pipeline](../webgpu_spec/webgpu-5f71975aec.md#gpupipelinelayout) using the shader.

It is a [pipeline-creation error](#pipeline-creation-error) if a WGSL variable in a resource interface is bound to an incompatible WebGPU [binding member](../WGPU/gpuweb-spec/gpuweb-spec.md#binding-member) or [binding type](../WGPU/gpuweb-spec/gpuweb-spec.md#binding-type), where compatibility is defined by the following table.

WebGPU binding type compatibility
| WGSL resource | WebGPU [binding member](../WGPU/gpuweb-spec/gpuweb-spec.md#binding-member) | WebGPU [binding type](../WGPU/gpuweb-spec/gpuweb-spec.md#binding-type)| [uniform buffer](#uniform-buffer) | `buffer` | `GPUBufferBindingType` | `"uniform"` | | [storage buffer](#storage-buffer) with [read_write](#access-read_write) access | `"storage"` | | [storage buffer](#storage-buffer) with [read](#access-read) access | `"read-only-storage"` | | [sampler](#type-sampler) | `sampler` | `GPUSamplerBindingType` | `"filtering"` | | `"non-filtering"` | | [sampler_comparison](#type-sampler_comparison) | `"comparison"` | | [sampled texture](#type-sampled-texture), [depth texture](#type-depth-texture), or [multisampled texture](#type-multisampled-texture) | `texture` | `GPUTextureSampleType` | `"float"` | | `"unfilterable-float"` | | `"sint"` | | `"uint"` | | `"depth"` | | [write-only storage texture](#type-write-only-storage-texture) | `storageTexture` | `GPUStorageTextureAccess` | `"write-only"` | | [read-write storage texture](#type-read-write-storage-texture) | `"read-write"` | | [read-only storage texture](#type-read-only-storage-texture) | `"read-only"` | | [external texture](#type-external-texture) | `externalTexture` | (not applicable) | |
| --- | --- | --- |

See the [WebGPU API](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-validating-gpuprogrammablestage) specification for interface validation requirements.

#### 13.3.4. Buffer Binding Determines Runtime-Sized Array Element Count[](#buffer-binding-determines-runtime-sized-array-element-count)

When a [storage buffer](#storage-buffer) variable contains a [runtime-sized](#runtime-sized) array, then the number of elements in that array is determined from the size of the corresponding `resource`:

> *   Let T be the [store type](#store-type) for a [storage buffer](#storage-buffer) variable, where T is a [runtime-sized](#runtime-sized) array type or contains a runtime-sized array type.
> 
> *   Let bufferBinding be [get as buffer binding](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-get-as-buffer-binding)(`resource`).
> 
> *   Let EBS be the [effective buffer binding size](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-effective-buffer-binding-size) for the bufferBinding bound to the pipeline binding address corresponding to the storage buffer variable.
> 
> *   Then NRuntime, i.e. the number of elements in the runtime-sized array, is the largest integer such that [SizeOf](#sizeof)(T) ≤ EBS.

In more detail, the [NRuntime](#nruntime) for a runtime-size array of type _RAT_ is:

> [truncate](#truncate)((EBBS − _array\_offset_) ÷ _array\_stride_), where: 
> *   EBBS is the [effective buffer binding size](../WGPU/gpuweb-spec/gpuweb-spec.md#abstract-opdef-effective-buffer-binding-size) associated with the variable,
> 
> *   _array\_offset_ is the byte offset of the runtime-sized array within the store type of the variable.
> 
> 
>     *   It is zero if the store type is RAT, the runtime-sized array type itself.
> 
>     *   Otherwise the store type is a structure, and its last member is the runtime-sized array. In this case _array\_offset_ is the [byte offset of that member](#offsetofmember) within the structure.
> 
> 
> *   _array\_stride_ is the stride of the array type, i.e. [StrideOf](#strideof)(RAT).

A shader can compute [NRuntime](#nruntime) via the [arrayLength](#arrayLength-builtin) builtin function.

Note: This algorithm is unambiguous: When a runtime-sized array is part of a larger type, it may only appear as the last element of a structure, which itself cannot be part of an enclosing array or structure.

[NRuntime](#nruntime) is determined by the size of the corresponding buffer binding, and that can be different for each [draw](#draw-command) or [dispatch command](#dispatch-command).

WebGPU validation rules ensure that 1 ≤ [NRuntime](#nruntime).

In the following code sample:

*   The `weights` variable is a [storage buffer](#storage-buffer).

*   Its store type is the runtime-sized array type `array<f32>`.

*   The array offset is 0.

*   The array stride is [StrideOf](#strideof)(array<f32>), which is 4.

EXAMPLE: number of elements in a simple runtime sized array

@group(0) @binding(1) var<storage> weights: array<f32>;

The following table shows examples of [NRuntime](#nruntime) for the `weights` variable, based on the corresponding effective buffer binding size.

Example number of elements for simple runtime-sized array
| Effective buffer binding size | NRuntime for `weights` variable | Calculation | 1024 | 256 | [truncate](#truncate)( 1024 ÷ 4 ) | | 1025 | 256 | [truncate](#truncate)( 1025 ÷ 4 ) | | 1026 | 256 | [truncate](#truncate)( 1026 ÷ 4 ) | | 1027 | 256 | [truncate](#truncate)( 1027 ÷ 4 ) | | 1028 | 257 | [truncate](#truncate)( 1028 ÷ 4 ) | |
| --- | --- |

In the following code sample:

*   The `lights` variable is a [storage buffer](#storage-buffer).

*   Its store type is `LightStorage`.

*   The `point` member of `LightStorage` is a runtime-sized array of type `array<PointLight>`.

    *   The member is at byte offset 16 in the variable’s storage.

    *   The array stride is [StrideOf](#strideof)(array<`PointLight`>) = [roundUp](#roundup)([AlignOf](#alignof)(`PointLight`),[SizeOf](#sizeof)(`PointLight`)) = [roundUp](#roundup)(16,32) = 32

EXAMPLE: number of elements in a complex runtime sized array

struct PointLight {                          // align(16) size(32)
  position : vec3f,                          // offset(0) align(16) size(12)
  // -- implicit member alignment padding -- // offset(12) size(4)
  color : vec3f,                             // offset(16) align(16) size(12)
  // -- implicit struct size padding -- // offset(28) size(4)
}

struct LightStorage {                        // align(16)
  pointCount : u32,                          // offset(0) align(4) size(4)
  // -- implicit member alignment padding -- // offset(4) size(12)
  point : array<PointLight>,                 // offset(16) align(16) elementsize(32)
}

@group(0) @binding(1) var<storage> lights : LightStorage;

The following table shows examples of [NRuntime](#nruntime) for the `point` member of the `lights` variable.

Example number of elements for complex runtime-sized array
| Effective buffer binding size | NRuntime for `point` member of `lights` variable | Calculation | 1024 | 31 | [truncate](#truncate)( ( 1024 - 16 ) ÷ 32) ) | | 1025 | 31 | [truncate](#truncate)( ( 1025 - 16 ) ÷ 32) ) | | 1039 | 31 | [truncate](#truncate)( ( 1039 - 16 ) ÷ 32) ) | | 1040 | 32 | [truncate](#truncate)( ( 1040 - 16 ) ÷ 32) ) | |
| --- | --- |

## 14. Memory[](#memory)

In WGSL, a value of [storable](#storable) type may be stored in memory, for later retrieval. This section describes the structure of memory, and the semantics of operations accessing memory. See [§ 6.5 Memory Views](#memory-views) for the types of values that can be placed in memory, and the types used to perform memory accesses.

### 14.1. Memory Locations[](#memory-locations-section)

Memory consists of a set of distinct memory locations. Each memory location is 8-bits in size. An operation affecting memory interacts with a set of one or more memory locations. Memory operations on [composites](#composite)[will not](#behavioral-requirements) access padding memory locations. Therefore, the set of memory locations accessed by an operation may not be contiguous.

Two sets of memory locations overlap if the intersection of their sets of memory locations is non-empty.

### 14.2. Memory Access Mode[](#memory-access-mode)

A memory access is an operation that acts on [memory locations](#memory-locations).

*   A read access observes the contents of memory locations.

*   A write access sets the contents of memory locations.

A single operation can read, write, or both read and write.

Particular memory locations may support only certain kinds of accesses, expressed as the memory’s access mode.

Access Modes
| Access mode | Supported accesses | read | Supports read accesses, but not writes. | | write | Supports write accesses, but not reads. | | read_write | Supports both read and write accesses. | |
| --- | --- |

WGSL [predeclares](#predeclared) the [enumerants](#enumerant)`read`, `write`, and `read_write`.

### 14.3. Address Spaces[](#address-space)

Memory locations are partitioned into address spaces. Each address space has unique properties determining mutability, visibility, the values it may contain, and how to use variables with it. See [§ 7 Variable and Value Declarations](#var-and-value) for more details.

The access mode of a given [memory view](#memory-view) is often determined by context:

The [storage](#address-spaces-storage) address space supports both [read](#access-read) and [read_write](#access-read_write) access modes. Each other address space supports only one access mode. The default access mode for each address space is described in the following table.

Address Spaces
| Address space | Sharing among invocations | Default access mode | Notes | function | Same invocation only | [read_write](#access-read_write) | | | private | Same invocation only | [read_write](#access-read_write) | | | workgroup | Invocations in the same [compute shader](#compute-shader-stage)[workgroup](#compute-shader-stage-workgroup) | [read_write](#access-read_write) | The [element count](#element-count) of an outermost array may be a [pipeline-overridable](#pipeline-overridable) constant. | | uniform | Invocations in the same [shader stage](#shader-stages) | [read](#access-read) | For [uniform buffer](#uniform-buffer) variables | | storage | Invocations in the same [shader stage](#shader-stages) | [read](#access-read) | For [storage buffer](#storage-buffer) variables | | immediate | Invocations in the same [shader stage](#shader-stages) | [read](#access-read) | For [immediate data](#immediate-data) variables. Each [entry point](#entry-point) can [statically access](#statically-accessed) at most one immediate variable. | | handle | Invocations in the same shader stage | [read](#access-read) | For [sampler](#sampler-resource) and [texture](#texture-resource) variables. | |
| --- | --- | --- | --- |

WGSL [predeclares](#predeclared) an [enumerant](#enumerant) for each address space, except for the `handle` address space.

[Variables](#variable) in the [workgroup](#address-spaces-workgroup) address space [must](#shader-creation-error) only be [statically accessed](#statically-accessed) in a [compute shader stage](#compute-shader-stage).

[Variables](#variable) in the [storage](#address-spaces-storage) address space ([storage buffers](#storage-buffer)) can only be [statically accessed](#statically-accessed) by a [vertex shader stage](#vertex-shader-stage) if the access mode is [read](#access-read). Variables whose [store type](#store-type) is a [storage texture](#type-storage-texture) with a [write](#access-write) or [read_write](#access-read_write)[access mode](#access-mode) cannot be [statically accessed](#statically-accessed) by a [vertex shader stage](#vertex-shader-stage). See WebGPU `createBindGroupLayout()`.

Note: Each address space may have different performance characteristics.

When writing a [variable declaration](#variable-declaration) or a [pointer type](#pointer-type) in WGSL source:

*   For the [storage](#address-spaces-storage) address space, the access mode is optional, and defaults to [read](#access-read).

*   For other address spaces, the access mode [must not](#shader-creation-error) be written.

### 14.4. Memory Layout[](#memory-layouts)

The layout of types in WGSL is independent of [address space](#address-spaces). Strictly speaking, however, that layout can only be observed by [host-shareable](#host-shareable) buffers. [Uniform buffer](#uniform-buffer) and [storage buffer](#storage-buffer) variables are used to share bulk data organized as a sequence of bytes in memory. Buffers are shared between the CPU and the GPU, or between different shader stages in a pipeline, or between different pipelines.

Because buffer data are shared without reformatting or translation, it is a [dynamic error](#dynamic-error) if buffer producers and consumers do not agree on the memory layout, which is the description of how the bytes in a buffer are organized into typed WGSL values. These bytes are [memory locations](#memory-locations) of a value relative to a common base location.

The [store type](#store-type) of a buffer variable [must](#shader-creation-error) be [host-shareable](#host-shareable), with fully elaborated memory layout, as described below.

Each buffer variable [must](#shader-creation-error) be declared in either the [uniform](#address-spaces-uniform) or [storage](#address-spaces-storage) address spaces.

The memory layout of a type is significant only when evaluating an expression with:

*   a variable in the [uniform](#address-spaces-uniform) or [storage](#address-spaces-storage) address space, or

*   a pointer into the [uniform](#address-spaces-uniform) or [storage](#address-spaces-storage) address space.

An 8-bit byte is the most basic unit of [host-shareable](#host-shareable) memory. The terms defined in this section express counts of 8-bit bytes.

We will use the following notation, where T is a [host-shareable](#host-shareable) or [fixed footprint](#fixed-footprint) type, S is a host-shareable or fixed footprint structure type, and A is a host-shareable or fixed footprint array or runtime-sized array:

*   AlignOf(T) is the [alignment](#alignment) of T, when T is a not a [buffer](#buffer).

*   AlignOfMember(S, i) is the alignment of the i’th member of S.

*   SizeOf(T) is the [byte-size](#byte-size) of T.

*   SizeOfMember(S, i) is the size of the i’th member of S.

*   OffsetOfMember(S, i) is the offset of the i’th member from the start of S.

*   StrideOf(A) is the element stride of A, defined as the number of bytes from the start of one array element to the start of the next element. It equals the size of the array’s element type, rounded up to the alignment of the element type:

[StrideOf](#strideof)(array<E, N>) = [roundUp](#roundup)([AlignOf](#alignof)(E), [SizeOf](#sizeof)(E))  
[StrideOf](#strideof)(array<E>) = [roundUp](#roundup)([AlignOf](#alignof)(E), [SizeOf](#sizeof)(E))

*   AccessibleBytes(T) is the set of byte offsets within an instance of type T that contain data.

    *   If T is a scalar or vector, then [AccessibleBytes](#accessible-bytes)(T) is the set of integers `k` such that `0 <= k <`[SizeOf](#sizeof)(T).

    *   If T is a matrix with C columns and R rows, then [AccessibleBytes](#accessible-bytes)(T) is the set calculated as:

        *   Let `Stride` be [roundUp](#roundup)([AlignOf](#alignof)(vec R), [SizeOf](#sizeof)(vec R)).

        *   For each `i` in `0..C-1`:

            *   For each `k` in [AccessibleBytes](#accessible-bytes)(vec R):

                *   The set contains `k + i * Stride`.

    *   If T is a structure S, then [AccessibleBytes](#accessible-bytes)(T) is the set calculated as:

        *   For each member `M_i` at byte offset `Offset` = [OffsetOfMember](#offsetofmember)(S, `i`):

            *   For each `k` in [AccessibleBytes](#accessible-bytes)(`M_i`):

                *   The set contains `k + Offset`.

*   AccessibleSlots(T) is the set of integers `i` such that the intersection of the interval `[4*i, 4*i+4)` and [AccessibleBytes](#accessible-bytes)(T) is not empty.

#### 14.4.1. Alignment and Size[](#alignment-and-size)

Each [host-shareable](#host-shareable) or [fixed footprint](#fixed-footprint) data type T has a size. Except for [buffer](#buffer) types, each host-shareable or fixed footprint type has an alignment.

The alignment of a type is a constraint on where values of that type may be placed in memory, expressed as an integer: a type’s alignment [must](#shader-creation-error) evenly divide the byte address of the starting [memory location](#memory-locations) of a value of that type. Alignments enable use of more efficient hardware instructions for accessing the values, or satisfy more restrictive hardware requirements on certain address spaces. (See [address space layout constraints](#address-space-layout-constraints)).

Note: Each alignment value is always a power of two, by construction.

The byte-size of a type or structure member is the number of contiguous bytes reserved in host-shareable memory for the purpose of storing a value of the type or structure member. The size may include non-addressable padding at the end of the type. Consequently, loads and stores of a value might access fewer memory locations than the value’s size.

Alignment and size of [host-shareable](#host-shareable) and [fixed footprint](#fixed-footprint) types are defined recursively in the following table:

 Alignment and size for host-shareable and fixed footprint types  

| Host-shareable or fixed footprint type T | [AlignOf](#alignof)(T) | [SizeOf](#sizeof)(T) | [bool](#bool) See [Note](#why-is-bool-4-bytes). | 4 | 4 | | [i32](#i32), [u32](#u32), or [f32](#f32) | 4 | 4 | | [f16](#f16) | 2 | 2 | | [atomic<T>](#atomic-type) | 4 | 4 | | [vec](#vector)2<T>, T is [bool](#bool), [i32](#i32), [u32](#u32), or [f32](#f32) | 8 | 8 | | vec2<f16> | 4 | 4 | | vec3<T>, T is [bool](#bool), [i32](#i32), [u32](#u32), or [f32](#f32) | 16 | 12 | | vec3<f16> | 8 | 6 | | vec4<T>, T is [bool](#bool), [i32](#i32), [u32](#u32), or [f32](#f32) | 16 | 16 | | vec4<f16> | 8 | 8 | | [mat](#matrix)C x R (col-major) (General form) | [AlignOf](#alignof)(vec R) | [SizeOf](#sizeof)(array<vec R, C>) | | mat2x2<f32> | 8 | 16 | | mat2x2<f16> | 4 | 8 | | mat3x2<f32> | 8 | 24 | | mat3x2<f16> | 4 | 12 | | mat4x2<f32> | 8 | 32 | | mat4x2<f16> | 4 | 16 | | mat2x3<f32> | 16 | 32 | | mat2x3<f16> | 8 | 16 | | mat3x3<f32> | 16 | 48 | | mat3x3<f16> | 8 | 24 | | mat4x3<f32> | 16 | 64 | | mat4x3<f16> | 8 | 32 | | mat2x4<f32> | 16 | 32 | | mat2x4<f16> | 8 | 16 | | mat3x4<f32> | 16 | 48 | | mat3x4<f16> | 8 | 24 | | mat4x4<f32> | 16 | 64 | | mat4x4<f16> | 8 | 32 | | [struct](#structure)S with members M 1...M N | max([AlignOfMember](#alignofmember)(S,1), ... , [AlignOfMember](#alignofmember)(S,N)) | [roundUp](#roundup)([AlignOf](#alignof)(S), justPastLastMember) where justPastLastMember = [OffsetOfMember](#offsetofmember)(S,N) + [SizeOfMember](#sizeofmember)(S,N) | | [array](#array)<E, N> | [AlignOf](#alignof)(E) | N × [roundUp](#roundup)([AlignOf](#alignof)(E), [SizeOf](#sizeof)(E)) | | array<E> | [AlignOf](#alignof)(E) | [NRuntime](#nruntime) × [roundUp](#roundup)([AlignOf](#alignof)(E),[SizeOf](#sizeof)(E)) where NRuntime is the runtime-determined number of elements of T | | [buffer](#buffer)<N> | _N/A_ | N | | buffer | _N/A_ | The size of the attached WebGPU `GPUBuffer` | |
| --- | --- | --- |

Note: The alignment of [buffer](#buffer) types is irrelevant since they cannot be contained in any other type.

[](#why-is-bool-4-bytes)Note: Many GPUs cannot implement single-byte writes without introducing potential data races. By specifying that a `bool` value occupies 4 bytes with 4 byte alignment, implementations can support adjacent boolean values in memory without introducing data races.

#### 14.4.2. Structure Member Layout[](#structure-member-layout)

The internal layout of a [structure](#structure) is computed from the sizes and alignments of its members. By default, the members are arranged tightly, in order, without overlap, while satisfying member alignment requirements.

This default internal layout can be overriden by using layout attributes, which are:

*   [size](#attribute-size)

*   [align](#attribute-align)

The i’th member of structure type S has a size and alignment, denoted by [SizeOfMember](#sizeofmember)(S, i) and [AlignOfMember](#alignofmember)(S, i), respectively. The member sizes and alignments are used to calculate each member’s byte offset from the start of the structure, as described in [§ 14.4.4 Internal Layout of Values](#internal-value-layout).

> [SizeOfMember](#sizeofmember)(S, i) is kif the i’th member of Shas attribute [size](#attribute-size)(k). Otherwise, it is [SizeOf](#sizeof)(T) where Tis the type of the member.

> [AlignOfMember](#alignofmember)(S, i) is kif the i’th member of Shas attribute [align](#attribute-align)(k). Otherwise, it is [AlignOf](#alignof)(T) where Tis the type of the member.

If a structure member has the [size](#attribute-size) attribute applied, the value [must](#shader-creation-error) be at least as large as the size of the member’s type:

> [SizeOfMember](#sizeofmember)(S, i) ≥ [SizeOf](#sizeof)(T) 
> Where Tis the type of the i’th member of S.

The first structure member always has a zero byte offset from the start of the structure:

> [OffsetOfMember](#offsetofmember)(S, 1) = 0

Each subsequent member is placed at the lowest offset that satisfies the member type alignment, and which avoids overlap with the previous member. For each member index i> 1:

> [OffsetOfMember](#offsetofmember)(S, i) = [roundUp](#roundup)([AlignOfMember](#alignofmember)(S, i), [OffsetOfMember](#offsetofmember)(S, i-1) + [SizeOfMember](#sizeofmember)(S, i-1))

EXAMPLE: Layout of structures using implicit member sizes and alignments

struct A {                                     // align(8) size(24)
    u: f32,                                    // offset(0) align(4) size(4)
    v: f32,                                    // offset(4) align(4) size(4)
    w: vec2<f32>,                              // offset(8) align(8) size(8)
    x: f32                                     // offset(16) align(4) size(4)
    // -- implicit struct size padding -- // offset(20) size(4)
}

struct B {                                     // align(16) size(160)
    a: vec2<f32>,                              // offset(0) align(8) size(8)
    // -- implicit member alignment padding -- // offset(8) size(8)
    b: vec3<f32>,                              // offset(16) align(16) size(12)
    c: f32,                                    // offset(28) align(4) size(4)
    d: f32,                                    // offset(32) align(4) size(4)
    // -- implicit member alignment padding -- // offset(36) size(4)
    e: A,                                      // offset(40) align(8) size(24)
    f: vec3<f32>,                              // offset(64) align(16) size(12)
    // -- implicit member alignment padding -- // offset(76) size(4)
    g: array<A, 3>,    // element stride 24 offset(80) align(8) size(72)
    h: i32                                     // offset(152) align(4) size(4)
    // -- implicit struct size padding -- // offset(156) size(4)
}

@group(0) @binding(0)
var<storage,read_write> storage_buffer: B;

EXAMPLE: Layout of structures with explicit member sizes and alignments

struct A {                                     // align(8) size(32)
    u: f32,                                    // offset(0) align(4) size(4)
    v: f32,                                    // offset(4) align(4) size(4)
    w: vec2<f32>,                              // offset(8) align(8) size(8)
    @size(16) x: f32                           // offset(16) align(4) size(16)
}

struct B {                                     // align(16) size(208)
    a: vec2<f32>,                              // offset(0) align(8) size(8)
    // -- implicit member alignment padding -- // offset(8) size(8)
    b: vec3<f32>,                              // offset(16) align(16) size(12)
    c: f32,                                    // offset(28) align(4) size(4)
    d: f32,                                    // offset(32) align(4) size(4)
    // -- implicit member alignment padding -- // offset(36) size(12)
    @align(16) e: A,                           // offset(48) align(16) size(32)
    f: vec3<f32>,                              // offset(80) align(16) size(12)
    // -- implicit member alignment padding -- // offset(92) size(4)
    g: array<A, 3>,    // element stride 32 offset(96) align(8) size(96)
    h: i32                                     // offset(192) align(4) size(4)
    // -- implicit struct size padding -- // offset(196) size(12)
}

@group(0) @binding(0)
var<uniform> uniform_buffer: B;

#### 14.4.3. Array Layout Examples[](#array-layout-examples)

EXAMPLE: Fixed-size array layout examples

// Array where:
// - alignment is 4 = AlignOf(f32)
// - element stride is 4 = roundUp(AlignOf(f32),SizeOf(f32)) = roundUp(4,4)
// - size is 32 = stride * number_of_elements = 4 * 8
var small_stride: array<f32, 8>;

// Array where:
// - alignment is 16 = AlignOf(vec3<f32>) = 16
// - element stride is 16 = roundUp(AlignOf(vec3<f32>), SizeOf(vec3<f32>))
// = roundUp(16,12)
// - size is 128 = stride * number_of_elements = 16 * 8
var bigger_stride: array<vec3<f32>, 8>;

EXAMPLE: Runtime-sized array layout examples

// Array where:
// - alignment is 4 = AlignOf(f32)
// - element stride is 4 = roundUp(AlignOf(f32),SizeOf(f32)) = 4
// If B is the effective buffer binding size for the binding on the
// draw or dispatch command, the number of elements is:
// N_runtime = floor(B / element stride) = floor(B / 4)
@group(0) @binding(0)
var<storage> weights: array<f32>;

// Array where:
// - alignment is 16 = AlignOf(vec3<f32>) = 16
// - element stride is 16 = roundUp(AlignOf(vec3<f32>), SizeOf(vec3<f32>))
// = roundUp(16,12)
// If B is the effective buffer binding size for the binding on the
// draw or dispatch command, the number of elements is:
// N_runtime = floor(B / element stride) = floor(B / 16)
var<storage> directions: array<vec3<f32>>;

#### 14.4.4. Internal Layout of Values[](#internal-value-layout)

This section describes how the internals of a [host-shareable](#host-shareable) value are placed in the byte locations of a buffer, given an assumed placement of the overall value. These layouts depend on the value’s type, and the [align](#attribute-align) and [size](#attribute-size) attributes on structure members. These rules apply to [non-opaque](#opaque) types as described below; values of [buffer](#buffer) type do not have an internal structure, and are not constrained by these rules.

The buffer byte offset at which a value is placed [must](#shader-creation-error) satisfy the type alignment requirement: If a value of type T is placed at buffer offset k, then k = c × [AlignOf](#alignof)(T), for some non-negative integer c.

The data [will](#behavioral-requirements) appear identically regardless of the address space.

Note: The [bool](#bool) type is not [host-shareable](#host-shareable). WGSL specifies that a [bool](#bool) value has a size and alignment of 4 bytes, but does not specify the internal layout of a bool value.

When a value V of type [u32](#u32) or [i32](#i32) is placed at byte offset k of a host-shared buffer, then:

*   Byte k contains bits 0 through 7 of V

*   Byte k+1 contains bits 8 through 15 of V

*   Byte k+2 contains bits 16 through 23 of V

*   Byte k+3 contains bits 24 through 31 of V

Note: Recall that [i32](#i32) uses twos-complement representation, so the sign bit is in bit position 31.

64-bit integer layout: Some features of the WebGPU API write 64-bit unsigned integer values into buffers. When such a value V appears at byte offset k of a host-shared buffer, then:

*   Byte k contains bits 0 through 7 of V

*   Byte k+1 contains bits 8 through 15 of V

*   Byte k+2 contains bits 16 through 23 of V

*   Byte k+3 contains bits 24 through 31 of V

*   Byte k+4 contains bits 32 through 39 of V

*   Byte k+5 contains bits 40 through 47 of V

*   Byte k+6 contains bits 48 through 55 of V

*   Byte k+7 contains bits 56 through 63 of V

Note: WGSL does not have a [concrete](#type-concrete)[64-bit integer](#64-bit-integer) type.

A value V of type [f32](#f32) is represented in [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary32](#ieee754-binary32) format. It has one sign bit, 8 exponent bits, and 23 fraction bits. When V is placed at byte offset k of host-shared buffer, then:

*   Byte k contains bits 0 through 7 of the fraction.

*   Byte k+1 contains bits 8 through 15 of the fraction.

*   Bits 0 through 6 of byte k+2 contain bits 16 through 22 of the fraction.

*   Bit 7 of byte k+2 contains bit 0 of the exponent.

*   Bits 0 through 6 of byte k+3 contain bits 1 through 7 of the exponent.

*   Bit 7 of byte k+3 contains the sign bit.

A value V of type [f16](#f16) is represented in [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary16](#ieee754-binary16) format. It has one sign bit, 5 exponent bits, and 10 fraction bits. When V is placed at byte offset k of host-shared buffer, then:

*   Byte k contains bits 0 through 7 of the fraction.

*   Bits 0 through 1 of byte k+1 contain bits 8 through 9 of the fraction.

*   Bits 2 through 6 of byte k+1 contain bits 0 through 4 of the exponent.

*   Bit 7 of byte k+1 contains the sign bit.

Note: The above rules imply that numeric values in host-shared buffers are stored in little-endian format.

When a value V of [atomic type](#atomic-type)`atomic`<T> is placed in a host-shared buffer, it has the same internal layout as a value of the underlying type T.

When a value V of [vector type](#vector) vec N<T> is placed at byte offset k of a host-shared buffer, then:

*   V.x is placed at byte offset k

*   V.y is placed at byte offset k + [SizeOf](#sizeof)(T)

*   If N ≥ 3, then V.z is placed at byte offset k + 2 × [SizeOf](#sizeof)(T)

*   If N ≥ 4, then V.w is placed at byte offset k + 3 × [SizeOf](#sizeof)(T)

When a value V of [matrix type](#matrix) mat C x R<T> is placed at byte offset k of a host-shared buffer, then:

*   Column vector i of V is placed at byte offset k + i × [AlignOf](#alignof)(vec R<T>)

When a value of [array type](#array)A is placed at byte offset k of a host-shared memory buffer, then:

*   Element i of the array is placed at byte offset k + i × [StrideOf](#strideof)(A)

When a value of [structure type](#structure)S is placed at byte offset k of a host-shared memory buffer, then:

*   The i'th member of the structure value is placed at byte offset k + [OffsetOfMember](#offsetofmember)(S,i). See [§ 14.4.2 Structure Member Layout](#structure-member-layout).

#### 14.4.5. Address Space Layout Constraints[](#address-space-layout-constraints)

The [storage](#address-spaces-storage) and [uniform](#address-spaces-uniform) address spaces have different layout constraints which are described in this section.

All [address spaces](#address-spaces) except [uniform](#address-spaces-uniform) have the same constraints as the [storage](#address-spaces-storage) address space.

All structure and array types directly or indirectly referenced by a variable [must](#shader-creation-error) obey the constraints of the variable’s address space. Violations of an address space constraint results in a [shader-creation error](#shader-creation-error).

In this section we define RequiredAlignOf(S, C) as the byte offset [alignment](#alignment) requirement of values of host-shareable or fixed-footprint type S when used in address space C.

 Alignment requirements of host-shareable or fixed footprint types in address space C
| Host-shareable or fixed footprint type S, assuming S can appear in C | [RequiredAlignOf](#requiredalignof)(S, C), [uniform_buffer_standard_layout](#language_extension-uniform_buffer_standard_layout) is supported or C is not [uniform](#address-spaces-uniform) | [RequiredAlignOf](#requiredalignof)(S, C), [uniform_buffer_standard_layout](#language_extension-uniform_buffer_standard_layout) is **not** supported and C is [uniform](#address-spaces-uniform)| [bool](#bool), [i32](#i32), [u32](#u32), [f32](#f32), or [f16](#f16) | [AlignOf](#alignof)(S) | [AlignOf](#alignof)(S) | | [atomic](#atomic-type)<T> | [AlignOf](#alignof)(S) | [AlignOf](#alignof)(S) | | [vec](#vector)N<T> | [AlignOf](#alignof)(S) | [AlignOf](#alignof)(S) | | [mat](#matrix)CxR<T> | [AlignOf](#alignof)(S) | [AlignOf](#alignof)(S) | | [array](#array)<T, N> | [AlignOf](#alignof)(S) | [roundUp](#roundup)(16, [AlignOf](#alignof)(S)) | | [array](#array)<T> | [AlignOf](#alignof)(S) Disallowed if C is [uniform](#address-spaces-uniform) except as the result of a [buffer_view built-in function](#buffer-view-builtin-functions) | [roundUp](#roundup)(16, [AlignOf](#alignof)(S)) Disallowed except as the result of a [buffer_view built-in function](#buffer-view-builtin-functions) | | [struct](#structure)S | [AlignOf](#alignof)(S) | [roundUp](#roundup)(16, [AlignOf](#alignof)(S)) | |
| --- | --- | --- |

Structure members of type T[must](#shader-creation-error) have a byte offset from the start of the structure that is a multiple of the [RequiredAlignOf](#requiredalignof)(T, C) for the address space C:

> [OffsetOfMember](#offsetofmember)(S, i) = k× [RequiredAlignOf](#requiredalignof)(T, C) 
> Where kis a non-negative integer and the i’th member of structure Shas type T

Arrays of element type T[must](#shader-creation-error) have an [element stride](#element-stride) that is a multiple of the [RequiredAlignOf](#requiredalignof)(T, C) for the address space C:

> [StrideOf](#strideof)(array<T, N>) = k× [RequiredAlignOf](#requiredalignof)(T, C) 
> [StrideOf](#strideof)(array<T>) = k× [RequiredAlignOf](#requiredalignof)(T, C) 
> Where kis a positive integer

When [uniform_buffer_standard_layout](#language_extension-uniform_buffer_standard_layout) is **not** supported, the [uniform](#address-spaces-uniform) address space requires that:

*   Array elements are aligned to 16 byte boundaries. That is, [StrideOf](#strideof)(array<T,N>) = 16 × k’ for some positive integer k'.

*   If a structure member itself has a structure type `S`, then the number of bytes between the start of that member and the start of any following member [must](#shader-creation-error) be at least [roundUp](#roundup)(16, [SizeOf](#sizeof)(S)).

Note: The following examples show how to use [align](#attribute-align) and [size](#attribute-size) attributes on structure members to satisfy layout requirements for uniform buffers. In particular, these techniques can be used mechanically transform a GLSL buffer with std140 layout to WGSL.

EXAMPLE: Satisfying offset requirements for uniform address space

struct S {
  x: f32
}
struct Invalid {
  a: S,
  b: f32 // invalid: offset between a and b is 4 bytes, but must be at least 16
}
@group(0) @binding(0) var<uniform> invalid: Invalid;

struct Valid {
  a: S,
  @align(16) b: f32 // valid: offset between a and b is 16 bytes
}
@group(0) @binding(1) var<uniform> valid: Valid;

EXAMPLE: Satisfying stride requirements for uniform address space

struct small_stride {
  a: array<f32,8> // stride 4
}
// Invalid, stride must be a multiple of 16
@group(0) @binding(0) var<uniform> invalid: small_stride;

struct wrapped_f32 {
  @size(16) elem: f32
}
struct big_stride {
  a: array<wrapped_f32,8> // stride 16
}
@group(0) @binding(1) var<uniform> valid: big_stride;     // Valid

### 14.5. Memory Model[](#memory-model)

In general, WGSL follows the [Vulkan Memory Model](#biblio-vulkanmemorymodel "Vulkan Memory Model"). The remainder of this section describes how WGSL programs map to the Vulkan Memory Model.

Note: The Vulkan Memory Model is a textual version of a [formal Alloy model](https://github.com/KhronosGroup/Vulkan-MemoryModel/blob/master/alloy/spirv.als).

#### 14.5.1. Memory Operation[](#memory-operation)

In WGSL, a [read access](#read-access) is equivalent to a memory read operation in the Vulkan Memory Model. In WGSL, a [write access](#write-access) is equivalent to a memory write operation in the Vulkan Memory Model.

A [read access](#read-access) occurs when an invocation executes one of the following:

*   An evaluation of the [Load Rule](#load-rule)

*   An evaluation of the [Swizzle View Load Rule](#swizzle-view-load-rule)

*   Any [texture builtin function](#texture-builtin-functions) except:

    *   [textureDimensions](#texturedimensions)

    *   [textureStore](#texturestore)

    *   [textureNumLayers](#texturenumlayers)

    *   [textureNumLevels](#texturenumlevels)

    *   [textureNumSamples](#texturenumsamples)

*   Any atomic built-in function except [atomicStore](#atomic-store)

*   A [workgroupUniformLoad](#workgroupUniformLoad-builtin) built-in function

*   A [swizzle assignment](#swizzle-assignment) statement (for the [left-hand side](#left-hand-side) expression)

*   A [compound assignment](#compound-assignment) statement (for the [left-hand side](#left-hand-side) expression)

A [write access](#write-access) occurs when an invocation executes one of the following:

*   A [simple assignment](#simple-assignment), [swizzle assignment](#swizzle-assignment), or a [compound assignment](#compound-assignment) (for the [left-hand side](#left-hand-side) expression)

*   A [textureStore](#texturestore) built-in function

*   Any atomic built-in function except [atomicLoad](#atomic-load)

    *   [atomicCompareExchangeWeak](#atomic-rmw) only performs a write if the `exchanged` member of the returned result is `true`

[Atomic read-modify-write](#atomic-rmw) built-in functions perform a single memory operation that is both a [read access](#read-access) and a [write access](#write-access).

Read and write accesses do not occur under any other circumstances. Read and write accesses are collectively known as [memory operations](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-memory-operation) in the Vulkan Memory Model.

A memory operation via a [memory view](#memory-view) generally accesses exactly the set of [locations](#memory-locations) associated with that [memory view](#memory-view). The exception is that a write access to a component of a vector **may** access all memory locations associated with that vector.

*   For example, a memory read that accesses a [u32](#u32) from a struct containing multiple members, only reads the memory locations associated with that u32 member.

*   For example, a memory write to the second component of a three element vector will write the locations for that second component, and may read and may write all three elements of the vector.

A memory operation via a [swizzle view](#swizzle-view) will access all memory locations associated with the underlying vector. See [swizzle view read](#swizzle-view-read) and [swizzle view write](#swizzle-view-write) for details.

EXAMPLE: Accessing memory locations

struct S {
  a : f32,
  b : u32,
  c : f32
}

@group(0) @binding(0)
var<storage> v : S;

fn foo() {
  let x = v.b; // Does not access memory locations for v.a or v.c.
}

#### 14.5.2. Memory Model Reference[](#memory-model-reference)

Each module-scope [resource](#resource) variable forms a [memory model reference](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-references) for the unique [group](#attribute-group) and [binding](#attribute-binding) pair. Each other variable (i.e. variables in the [function](#address-spaces-function), [private](#address-spaces-private), and [workgroup](#address-spaces-workgroup) address spaces) forms a unique [memory model reference](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-references) for the lifetime of the variable.

#### 14.5.3. Scoped Operations[](#scoped-operations)

When an invocation performs a scoped operation, it will affect one or two sets of invocations. These sets are the memory scope and the execution scope. The memory scope specifies the set of invocations that will see any updates to memory contents affected by the operation. For [synchronization built-in functions](#sync-builtin-functions), this also means that all affected memory operations program ordered before the function are visible to affected operations program ordered after the function. The execution scope specifies the set of invocations which may participate in an operation (see [§ 15.6 Collective Operations](#collective-operations)).

[Atomic built-in functions](#atomic-builtin-functions) map to [atomic operations](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-atomic-operation) whose memory [scope](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-scope) is:

*   `Workgroup` if the atomic pointer is in the [workgroup](#address-spaces-workgroup) address space

*   `QueueFamily` if the atomic pointer is in the [storage](#address-spaces-storage) address space

[Synchronization built-in functions](#sync-builtin-functions) map to control barriers whose execution and memory [scopes](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-scope) are `Workgroup`.

Implicit and explicit [derivatives](#derivatives) have an implicit [quad](#quad) execution scope.

Note: If the Vulkan memory model is not enabled in generated shaders, `Device` scope should be used instead of `QueueFamily`.

#### 14.5.4. Memory Semantics[](#memory-semantics)

All [Atomic built-in functions](#atomic-builtin-functions) use `Relaxed`[memory semantics](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-memory-semantics) and, thus, no storage class semantics.

Note: Address space in WGSL is equivalent to storage class in SPIR-V.

[workgroupBarrier](#sync-builtin-functions) uses `AcquireRelease`[memory semantics](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-memory-semantics) and `WorkgroupMemory` semantics. [storageBarrier](#sync-builtin-functions) uses `AcquireRelease`[memory semantics](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-memory-semantics) and `UniformMemory` semantics. [textureBarrier](#sync-builtin-functions) uses `AcquireRelease`[memory semantics](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-memory-semantics) and `ImageMemory` semantics.

Note: A combined `workgroupBarrier` and `storageBarrier` uses `AcquireRelease` ordering semantics and both `WorkgroupMemory` and `UniformMemory` memory semantics.

Note: No atomic or synchronization built-in functions use `MakeAvailable` or `MakeVisible` semantics.

#### 14.5.5. Private vs Non-private[](#private-vs-non-private)

All non-atomic [read accesses](#read-access) in the [storage](#address-spaces-storage) or [workgroup](#address-spaces-workgroup) address spaces are considered [non-private](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-non-private) and correspond to read operations with `NonPrivatePointer | MakePointerVisible` memory operands with the `Workgroup` scope.

All non-atomic [write accesses](#write-access) in the [storage](#address-spaces-storage) or [workgroup](#address-spaces-workgroup) address spaces are considered [non-private](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-non-private) and correspond to write operations with `NonPrivatePointer | MakePointerAvailable` memory operands with the `Workgroup` scope.

All non-atomic [read accesses](#read-access) in the the [handle](#address-spaces-handle) address space are considered [non-private](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-non-private) and correspond to read operations with `NonPrivateTexel | MakeTexelVisible` memory operands with the `Workgroup` scope.

All non-atomic [write accesses](#write-access) in the [handle](#address-spaces-handle) address space are considered [non-private](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/vkspec.html#memory-model-non-private) and correspond to write operations with `NonPrivateTexel | MakeTexelAvailable` memory operands with the `Workgroup` scope.

## 15. Execution[](#execution)

[§ 1.1 Overview](#overview) describes how a shader is invoked and partitioned into [invocations](#invocations). This section describes further constraints on how invocations execute, individually and collectively.

### 15.1. Program Order Within an Invocation[](#program-order)

Each statement in a WGSL module may be executed zero or more times during execution. For a given invocation, each execution of a given statement represents a unique dynamic statement instance.

When a statement includes an expression, the statement’s semantics determines:

*   Whether the expression is evaluated as part of statement execution.

*   The relative ordering of evaluation between independent expressions in the statement.

Expression nesting defines data dependencies which must be satisfied to complete evaluation. That is, a nested expression must be evaluated before the enclosing expression can be evaluated. The order of evaluation for operands of an expression is left-to-right in WGSL. For example, `foo() + bar()` must evaluate `foo()` before `bar()`. See [§ 8 Expressions](#expressions).

Statements in a WGSL module are executed in control flow order. See [§ 9 Statements](#statements) and [§ 11.2 Function Calls](#function-calls).

### 15.2. Uniformity[](#uniformity)

A [collective operation](#collective-operations) (e.g. barrier, derivative, or a texture operation relying on an implicitly computed derivative) requires coordination among different invocations running concurrently on the GPU. The operation executes correctly and portably when all invocations execute it concurrently, i.e. in [uniform control flow](#uniform-control-flow).

Conversely, incorrect or non-portable behavior occurs when a strict subset of invocations execute the operation, i.e. in non-uniform control flow. Informally, some invocations reach the collective operation, but others do not, or not at the same time, as a result of non-uniform control dependencies. Non-uniform control dependencies arise from [control flow](#control-flow) statements whose behavior depends on [non-uniform values](#uniform-value).

> For example, a non-uniform control dependency arises when different invocations compute different values for the condition of an [if](#statement-if), [break-if](#statement-break-if), [while](#statement-while), or [for](#statement-for), different values for the selector of a [switch](#statement-switch), or the left-hand operand of a short-circuiting binary operator (`&&`or `||`).

These non-uniform values can often be traced back to certain sources that are not statically proven to be uniform. These sources include, but are not limited to:

*   Mutable [module-scope](#module-scope)[variables](#variable)

*   Most [built-in values](#built-in-values)

*   [User-defined inputs](#user-defined-input-datum)

*   Certain [built-in functions](#built-in-functions) (see [§ 15.2.7 Uniformity Rules for Function Calls](#uniformity-function-calls))

To ensure correct and portable behavior, a WGSL implementation [will](#behavioral-requirements) perform a static uniformity analysis, attempting to prove that each collective operation executes in [uniform control flow](#uniform-control-flow). Subsequent subsections describe the analysis.

A uniformity failure[will](#behavioral-requirements) be triggered when [uniformity analysis](#uniformity-analysis) cannot prove that a particular [collective operation](#collective-operations) executes in [uniform control flow](#uniform-control-flow).

*   If a uniformity failure is triggered for a [builtin function that computes a derivative](#builtin-functions-that-compute-a-derivative), then a [derivative_uniformity](#trigger-derivative_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered).

    *   The diagnostic’s [triggering location](#diagnostic-triggering-location) is the location of the [call site](#call-site) of that builtin.

    *   The diagnostic’s [severity](#diagnostic-severity) defaults to an [error](#severity-error) but can be controlled with a [diagnostic filter](#diagnostic-filter).

*   If a uniformity failure is triggered for a [synchronization builtin](#sync-builtin-functions), an [error](#severity-error)[diagnostic](#diagnostic) is [triggered](#triggered), which results in a [shader-creation error](#shader-creation-error).

*   If a uniformity failure is triggered for a [subgroup](#subgroup-builtin-functions) or [quad](#quad-builtin-functions) builtin, then a [subgroup_uniformity](#trigger-subgroup_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered)

    *   The diagnostic’s [triggering location](#diagnostic-triggering-location) is the location of the [call site](#call-site) of that builtin or the location of the parameter required to be uniform in the case of [subgroupShuffleUp](#subgroupshuffleup-builtin), [subgroupShuffleDown](#subgroupshuffledown-builtin), or [subgroupShuffleXor](#subgroupshufflexor-builtin)

    *   The diagnostic’s [severity](#diagnostic-severity) defaults to an [error](#severity-error), but can be controlled with a [diagnostic filter](#diagnostic-filter).

#### 15.2.1. Terminology and Concepts[](#uniformity-concepts)

The following definitions are merely informative, trying to give an intuition for what the analysis in the next subsection is computing. The analysis is what actually defines these concepts, and when a program is valid or breaks the uniformity rules.

For a given group of invocations:

*   If all invocations in a given scope execute as if they are executing in lockstep at a given point in the program, that point is said to have uniform control flow for the given uniformity scope.

    *   Workgroup uniformity scope: For a [compute shader stage](#compute-shader-stage), the uniformity scope is all invocations in the same [workgroup](#compute-shader-stage-workgroup).

    *   Draw uniformity scope: For other shader stages, the uniformity scope is all invocations for that [entry point](#entry-point) in the same [draw command](#draw-command).

    *   Subgroup uniformity scope: If the [subgroup_uniformity](#language_extension-subgroup_uniformity) feature is supported, the uniformity scope for [subgroup](#subgroup-builtin-functions) and [quad](#quad-builtin-functions) built-in functions instead is all invocations in the same [subgroup](#subgroup).

*   If an expression is executed in uniform control flow, and all invocations compute the same value, it is said to be a uniform value.

*   If invocations hold the same value for a local variable at every point where it is live, it is said to be a uniform variable.

#### 15.2.2. Uniformity Analysis Overview[](#uniformity-overview)

The remaining subsections specify a static analysis that verifies that [collective operations](#collective-operations) are only executed in [uniform control flow](#uniform-control-flow). If the [subgroup_uniformity](#language_extension-subgroup_uniformity) feature is supported then there are multiple [uniformity scopes](#uniformity-scope). This analysis is performed once for each scope.

Note: The analysis is described as being executed once per scope, but implementations may perform a single analysis that includes each scope. [Workgroup](#workgroup-uniformity-scope) and [draw](#draw-uniformity-scope) uniformity scopes are effectively equivalent since they operate on different shader stages and represent the largest uniformity scope in a shader stage.

The analysis assumes [dynamic errors](#dynamic-error) do not occur. A shader stage with a [dynamic error](#dynamic-error) is already non-portable, no matter the outcome of uniformity analysis.

Note:This analysis has the following desirable properties:

*   Sound, meaning that a [uniformity failure](#uniformity-failure)[will](#behavioral-requirements) be triggered for a program that would break the uniformity requirements of builtins.

*   Refactoring a piece of code into a function, or inlining a function, cannot make a shader invalid if it was valid before the transformation.

*   If the analysis refuses a program, it provides a straightforward chain of implications that can be used by the user agent to craft a good error message.

Each function is analyzed, trying to ensure two things:

*   Uniformity requirements are satisfied when it calls other functions, and

*   Uniformity requirements are satisfied whenever it is called.

 A [uniformity failure](#uniformity-failure) is triggered if either of these two checks fail. 
As part of this work, the analysis computes metadata about the function to help analyze its callers in turn. This means that the call graph must first be built, and functions must be analyzed from the leaves upwards, i.e. from functions that call no function outside the standard library toward the entry point. This way, whenever a function is analyzed, the metadata for all of its callees has already been computed. There is no risk of being trapped in a cycle, as recurrence is forbidden in the language.

Note: Another way of saying the same thing is that we do a topological sort of functions ordered by the "is a (possibly indirect) callee of" partial order, and analyze them in that order.

Additionally, for each function call, the analysis computes and propagates the set of [triggering rules](#diagnostic-triggering-rule), if any, that would be triggered if that call cannot be proven to be in uniform control flow. We call this the potential-trigger-set for the call. The elements of this set are drawn from the following possibilites:

*   [derivative_uniformity](#trigger-derivative_uniformity), for functions relying on computing a derivative,

*   [subgroup_uniformity](#trigger-subgroup_uniformity), for functions in [§ 17.12 Subgroup Built-in Functions](#subgroup-builtin-functions) or [§ 17.13 Quad Operations](#quad-builtin-functions), or

*   an unnamed triggering rule, for the uniformity requirements that cannot be filtered.

    *   This is used for compute shader functions relying on [synchronization functions](#sync-builtin-functions).

#### 15.2.3. Analyzing the Uniformity Requirements of a Function[](#uniformity-function)

Each function is analyzed in two phases.

The first phase walks over the syntax of the function, building a directed graph along the way based on the rules in the following subsections. The second phase explores that graph, computing the constraints on calling this function, and potentially triggering a [uniformity failure](#uniformity-failure).

Note:Apart from four special nodes [RequiredToBeUniform.error](#requiredtobeuniformerror), [RequiredToBeUniform.warning](#requiredtobeuniformwarning), [RequiredToBeUniform.info](#requiredtobeuniforminfo), and [MayBeNonUniform](#maybenonuniform), each node can be understood as capturing the truth-value one of the following statements:

*   A specific point of the program must be executed in [uniform control flow](#uniform-control-flow).

*   An expression must be a [uniform value](#uniform-value).

*   A variable must be a [uniform variable](#uniform-variable).

*   A value stored in memory, that could be loaded via a pointer, must be a [uniform value](#uniform-value).

An edge can be understood as an implication from the statement corresponding to its source node to the statement corresponding to its target node.

For example, one uniformity requirement is that the `workgroupBarrier` builtin function must only be called within uniform control flow. To express this, we add an edge from [RequiredToBeUniform.error](#requiredtobeuniformerror) to the node corresponding to the `workgroupBarrier`[call site](#call-site). One way to understand this is that [RequiredToBeUniform.error](#requiredtobeuniformerror) corresponds to the proposition True, so that [RequiredToBeUniform.error](#requiredtobeuniformerror) -> X is the same as saying that X is true.

Reciprocally, to express that we cannot ensure the uniformity of something (e.g. a variable which holds the thread id), we add an edge from the corresponding node to [MayBeNonUniform](#maybenonuniform). One way to understand this, is that [MayBeNonUniform](#maybenonuniform) corresponds to the proposition False, so that X ->[MayBeNonUniform](#maybenonuniform) is the same as saying that X is false.

A consequence of this interpretation is that every node reachable from [RequiredToBeUniform.error](#requiredtobeuniformerror) corresponds to something which is required to be uniform for the program to be valid, and every node from which [MayBeNonUniform](#maybenonuniform) is reachable corresponds to something whose uniformity we cannot guarantee. It follows that we have a uniformity violation, triggering a [uniformity failure](#uniformity-failure), if there is any path from [RequiredToBeUniform.error](#requiredtobeuniformerror) to [MayBeNonUniform](#maybenonuniform).

The nodes [RequiredToBeUniform.warning](#requiredtobeuniformwarning) and [RequiredToBeUniform.info](#requiredtobeuniforminfo) are used in a similar way, but instead help determine when [warning](#severity-warning) or [info](#severity-info)[diagnostics](#diagnostic) should be triggered:

*   If there is a path from [RequiredToBeUniform.warning](#requiredtobeuniformwarning) to [MayBeNonUniform](#maybenonuniform), then a [warning](#severity-warning)[diagnostic](#diagnostic) will be triggered.

*   If there is a path from [RequiredToBeUniform.info](#requiredtobeuniforminfo) to [MayBeNonUniform](#maybenonuniform), then an [info](#severity-info)[diagnostic](#diagnostic) will be triggered.

As described in [§ 2.3 Diagnostics](#diagnostics), lower severity diagnostics may be discarded if higher severity diagnostics have also been generated.

For each function, two tags are computed:

*   A call site tag describing the control flow uniformity requirements on the [call sites](#call-site) of the function, and

*   A function tag describing the function’s effects on uniformity.

For each [formal parameter](#formal-parameter) of a function, one or two tags are computed:

*   A parameter tag describes the uniformity requirement of the parameter value.

*   A parameter return tag describes how the uniformity of the parameter influences that of the function’s [return value](#return-value).

*   A pointer parameter tag, when the parameter type is a pointer into the [function](#address-spaces-function) address space. The tag describes whether the value in the memory pointed to by the parameter may become [non-uniform](#uniform-value) during the execution of the function call.

[Call site tag](#call-site-tag) values
| Call Site Tag | Description | CallSiteRequiredToBeUniform.S, where S is one of the severities: [error](#severity-error), [warning](#severity-warning), or [info](#severity-info). | The function must only be called from [uniform control flow](#uniform-control-flow). Otherwise a diagnostic with severity S will be triggered. Associated with a [potential-trigger-set](#potential-trigger-set). | | CallSiteNoRestriction | The function may be called from [non-uniform control flow](#uniform-control-flow). | |
| --- | --- |

[Function tag](#function-tag) values
| Function Tag | Description | ReturnValueMayBeNonUniform | The [return value](#return-value) of the function may be non-uniform. | | NoRestriction | The function does not introduce non-uniformity. | |
| --- | --- |

[Parameter tag](#parameter-tag) values
| Parameter Tag | Description | ParameterRequiredToBeUniform.S, where S is one of the severities: [error](#severity-error), [warning](#severity-warning), or [info](#severity-info). | The parameter must be a [uniform value](#uniform-value). If the parameter type is a pointer, the memory view, but not necessarily its contents, must be uniform. Otherwise a diagnostic with severity S will be triggered. Associated with a [potential-trigger-set](#potential-trigger-set). | | ParameterContentsRequiredToBeUniform.S, where S is one of the severities: [error](#severity-error), [warning](#severity-warning), or [info](#severity-info). | The value stored in the memory pointed to by the pointer parameter must be a [uniform value](#uniform-value). Otherwise a diagnostic with severity S will be triggered. Associated with a [potential-trigger-set](#potential-trigger-set). | | ParameterNoRestriction | The parameter value has no uniformity requirement. | |
| --- | --- |

[Parameter return tag](#parameter-return-tag) values
| Parameter Return Tag | Description | ParameterReturnContentsRequiredToBeUniform | The parameter [must](#shader-creation-error) be a [uniform value](#uniform-value) in order for the [return value](#return-value) to be a uniform value. If the parameter is a pointer, then the values stored in the memory pointed to by the pointer must also be [uniform](#uniform-value). | | ParameterReturnNoRestriction | The parameter value has no uniformity requirement. | |
| --- | --- |

[Pointer parameter tag](#pointer-parameter-tag) values
| Pointer Parameter Tag | Description | PointerParameterMayBeNonUniform | The value stored in the memory pointed to by the pointer parameter may be [non-uniform](#uniform-value) after the function call. | | PointerParameterNoRestriction | The uniformity of the value stored in the memory pointed to by the pointer parameter is unaffected by the function call. | |
| --- | --- |

The following algorithm describes how to compute these tags for a given function:

*   Create the following nodes:

    *   RequiredToBeUniform.error, RequiredToBeUniform.warning, and RequiredToBeUniform.info. Collectively these are called the RequiredToBeUniform.S nodes.

        *   Each such node is associated with a [potential-trigger-set](#potential-trigger-set), which is initially empty.

    *   MayBeNonUniform

    *   CF_start, representing the uniformity requirement for control flow when the function begins executing.

    *   param_i, where _i_ ranges over the function’s [formal parameters](#formal-parameter).

    *   If the function has a [return type](#return-type), create a node called Value_return.

*   Desugar pointers as described in [§ 15.2.4 Pointer Desugaring](#pointer-desugar).

    *   For each formal parameter that is a pointer in the [function](#address-spaces-function) address space, create the following nodes:

        *   param_i_contents: this represents the uniformity of the contents of the memory view.

        *   Value_return_i_contents: this represents the function’s effects on the uniformity of the contents of the memory view.

*   Walk over the syntax of the function, adding nodes and edges to the graph following the rules of the next sections ([§ 15.2.5 Function-scope Variable Value Analysis](#func-var-value-analysis), [§ 15.2.6 Uniformity Rules for Statements](#uniformity-statements), [§ 15.2.7 Uniformity Rules for Function Calls](#uniformity-function-calls), [§ 15.2.8 Uniformity Rules for Expressions](#uniformity-expressions)), using [CF_start](#cf_start) as the starting control-flow for the function’s body.

    *   The nodes added in this step are called interior nodes.

*   Initialize as follows:

    *   The [function tag](#function-tag) is initialized to [NoRestriction](#norestriction).

    *   The [call site tag](#call-site-tag) is initialized to [CallSiteNoRestriction](#callsitenorestriction).

    *   The [parameter tag](#parameter-tag) for each [param_i](#param_i) is initialized to [ParameterNoRestriction](#parameternorestriction).

    *   The [parameter return tag](#parameter-return-tag) for each [param_i](#param_i) is initialized to [ParameterReturnNoRestriction](#parameterreturnnorestriction).

    *   The [pointer parameter tag](#pointer-parameter-tag) for each [param_i](#param_i), if it exists, is initialized to [PointerParameterNoRestriction](#pointerparameternorestriction).

*   For each severity _S_ in the order {[error](#severity-error), [warning](#severity-warning), [info](#severity-info)}, perform the following:

    *   Let _R.S_ be the set of unvisited nodes reachable from [RequiredToBeUniform.S](#requiredtobeuniforms).

    *   Mark the [interior nodes](#interior-nodes) in _R.S_ as visited.

    *   Let _PTS_ be the [potential-trigger-set](#potential-trigger-set) associated with [RequiredToBeUniform.S](#requiredtobeuniforms).

    *   If _R.S_ includes the node [MayBeNonUniform](#maybenonuniform), then trigger a [uniformity failure](#uniformity-failure):

        *   [Trigger](#triggered) a diagnostic with severity _S_ and triggering rule _t_, for each _t_ in _PTS_.

    *   Otherwise:

        *   If _R.S_ includes [CF_start](#cf_start), and the [call site tag](#call-site-tag) has not been updated since initialization, then set the [call site tag](#call-site-tag) to [CallSiteRequiredToBeUniform.S](#callsiterequiredtobeuniforms), and set its [potential-trigger-set](#potential-trigger-set) to _PTS_.

        *   For each [param_i](#param_i) in _R.S_, if its corresponding [parameter tag](#parameter-tag) has not been updated since initialization, then set that tag to [ParameterRequiredToBeUniform.S](#parameterrequiredtobeuniforms), and set its [potential-trigger-set](#potential-trigger-set) to _PTS_.

        *   For each [param_i_contents](#param_i_contents) in _R.S_, if its corresponding [parameter tag](#parameter-tag) has not been updated since initialization, then set that tag to [ParameterContentsRequiredToBeUniform.S](#parametercontentsrequiredtobeuniforms), and set its [potential-trigger-set](#potential-trigger-set) to _PTS_.

*   Mark all the [interior nodes](#interior-nodes) as unvisited.

*   If [Value_return](#value_return) exists, let _VR_ be the set of nodes reachable from [Value_return](#value_return).

    *   If _VR_ includes [MayBeNonUniform](#maybenonuniform), then set the [function tag](#function-tag) to [ReturnValueMayBeNonUniform](#returnvaluemaybenonuniform).

    *   For each [param_i](#param_i) in _VR_, set the corresponding [parameter return tag](#parameter-return-tag) to [ParameterReturnContentsRequiredToBeUniform](#parameterreturncontentsrequiredtobeuniform).

*   For each [Value_return_i_contents](#value_return_i_contents) node, let _VRi_ be the set of nodes reachable from [Value_return_i_contents](#value_return_i_contents).

    *   If _VRi_ includes [MayBeNonUniform](#maybenonuniform), set the corresponding [pointer parameter tag](#pointer-parameter-tag) to [PointerParameterMayBeNonUniform](#pointerparametermaybenonuniform).

Note: The entire graph can be destroyed at this point. The tags described above are all that we need to remember to analyze callers of this function. However, the graph contains information that can be used to provide more informative diagnostics. For example a value in a one function may not be provably [uniform](#uniform-value), which then contributes to triggering a uniformity failure in another function. An informative diagnostic would describe the non-uniform value, as well as the function call at the diagnostic’s [triggered location](#diagnostic-triggering-location).

#### 15.2.4. Pointer Desugaring[](#pointer-desugar)

Each [parameter](#formal-parameter) of [pointer type](#pointer-type) in the [function](#address-spaces-function) address space is desugared as a local variable declaration whose initial value is equivalent to dereferencing the parameter. That is, function address space pointers are viewed as aliases to a local variable declaration. The initial value assignment produces an edge to [param_i_contents](#param_i_contents) for _i_ th parameter (i.e. _V(e)_ is [param_i_contents](#param_i_contents)).

Each [let-declaration](#let-declaration), _L_, with an [effective-value-type](#effective-value-type) that is a [pointer type](#pointer-type) is desugared as follows:

*   Visit each subexpression, _SE_, of the initializer expression of _L_ in a postorder depth-first traversal:

    *   If _SE_ invokes the [load rule](#load-rule) or the [swizzle view load rule](#swizzle-view-load-rule) during [type checking](#type-checking), and the [root identifier](#root-identifier) for the [memory view](#memory-view) or [swizzle view](#swizzle-view) is a mutable variable then:

        *   Create a new let-declaration, _LSE_, immediately prior to _L_ initialized with _SE_.

        *   Replace _SE_ in _L_ with a [value identifier expression](#value-identifier-expr) composed of _LSE_.

*   Record the, possibly updated, initializer expression of _L_.

*   Substitute each [identifier](#identifier) that [resolves](#resolves) to _L_ with the recorded initializer expression (wrapped in a [parenthesized expression](#parenthesized-expressions)).

This desugaring simplifies the subsequent analyses by exposing the [root identifier](#root-identifier) of the pointer directly at each of its uses.

Note: For the purposes of uniformity analysis [type checking](#type-checking) is described to occur both before and after this desugaring has occurred.

EXAMPLE: pointers in the uniformity analysis

fn foo(p : ptr<function, array<f32, 4>>, i : i32) -> f32 {
  let p1 = p;
  var x = i;
  let p2 = &((*p1)[x]);
  x = 0;
  *p2 = 5;
  return (*p1)[x];
}

// This is the equivalent version of foo for the analysis.
fn foo_for_analysis(p : ptr<function, array<f32, 4>>, i : i32) -> f32 {
  var p_var = *p;            // Introduce variable for p.
  let p1 = &p_var;           // Use the variable for p1
  var x = i;
  let x_tmp1 = x;            // Capture value of x
  let p2 = &(p_var[x_tmp1]); // Substitute p1's initializer
  x = 0;
  *(&(p_var[x_tmp1])) = 5;   // Substitute p2's initializer
  return (*(&p_var))[x];     // Substitute p1's initializer
}

#### 15.2.5. Function-scope Variable Value Analysis[](#func-var-value-analysis)

The value of each [function-scope](#function-scope)[variable](#variable) at a particular statement can be analyzed in terms of the assignments that reach it and, potentially, its initial value.

An assignment is a full assignment if:

*   The variable’s [effective-value-type](#effective-value-type) is a [scalar](#scalar) type, or

*   The variable’s [effective-value-type](#effective-value-type) is a [composite](#composite) type and each [component](#components) of the composite is assigned a value.

Otherwise, an assignment is a partial assignment.

A full reference is an expression of [reference type](#reference-type) that is one of:

*   an identifier _x_ that [resolves](#resolves) to a variable, or

*   `(`_r_`)` where _r_ is a [full reference](#full-reference), or

*   `*`_p_ where _p_ is a [full pointer](#full-pointer).

A full pointer is an expression of [pointer type](#pointer-type) that is one of:

*   `&`_r_ where _r_ is a [full reference](#full-reference), or

*   an identifier _p_ that [resolves](#resolves) to a [let-declaration](#let-declaration) initialized to a [full pointer](#full-pointer), or

*   `(`_p_`)` where _p_ is a [full pointer](#full-pointer).

Note: For the purposes of this analysis, we don’t need the case where a formal parameter of pointer type may be a full pointer.

A [full reference](#full-reference), and similarly a [full pointer](#full-pointer), is a [memory view](#memory-view) for _all_ the memory locations for the corresponding [originating variable](#originating-variable)_x_.

A reference that is not a [full reference](#full-reference) is a partial reference. As such, a partial reference is either:

*   a memory view for a strict subset of the memory locations for the corresponding [originating variable](#originating-variable), or

*   a memory view the with same set of locations as the corresponding originating variable, but with a different [store type](#store-type).

Note: A [partial reference](#partial-reference) can still cover all the same memory locations as a full reference, i.e. all the locations used by a variable declaration. This can occur when the store type is a structure type having only one member, or when the store type is an array type with one element.

Consider a structure type with a single member, and a variable storing that type:

struct S { member: i32; }
fn foo () {
   var v: S;
}

Then `v` is a full reference and `v.member` is a partial reference. Their memory views cover the same memory locations, but the store type for `v` is `S` and the store type of `v.s` is `i32`.

A similar situation occurs with arrays having a single element:

fn foo () {
   var arr: array<i32,1>;
}

Then `arr` is a full reference and `arr[0]` is a partial reference. Their memory views cover the same memory locations, but the store type for `arr` is `array<i32,1>` and the store type of `arr[0]` is `i32`.

To simplify analysis, an assignment via _any_ kind of [partial reference](#partial-reference) is treated as if it does _not_ modify every memory location in the associated [originating variable](#originating-variable). This causes the analysis to be conservative, potentially triggering a [uniformity failure](#uniformity-failure) for more programs than strictly necessary.

A full swizzle view is an expression evaluating to a [swizzle view](#swizzle-view)sv = (p, IndexList) where:

*   p is a [full pointer](#full-pointer) to a vector of N elements.

*   IndexList is a permutation of {0, ..., N-1}.

Note: Assigning via a full swizzle view will overwrite all the elements of the underlying vector in memory.

A partial swizzle view is an expression of [swizzle view type](#swizzle-view-type) that is not a [full swizzle view](#full-swizzle-view).

Note: Full swizzle views can be determined at shader-creation time, since it only depends on the fullness of the underlying pointer expression and IndexList, both of which are known at shader-creation time. This holds even when chaining swizzle view expressions.

An assignment through a [full reference](#full-reference) or a [full swizzle view](#full-swizzle-view) is a [full assignment](#full-assignment).

An assignment through a [partial reference](#partial-reference) or a [partial swizzle view](#partial-swizzle-view) is a [partial assignment](#partial-assignment).

When the uniformity rules in subsequent sections refer to the value for a function-scope variable used as an [RHSValue](#rhsvalue), it means the value of the variable prior to evaluation of the RHSValue expression. When the uniformity rules in subsequent sections refer to the value for a function-scope variable used as an [LHSValue](#lhsvalue), it means the value of the variable after execution of the statement the expression appears in.

Multiple assignments to a variable might reach a use of that variable due to [control-flow statements](#control-flow) or partial assignments. The analysis joins multiple assignments reaching out of control-flow statements by unioning the set of assignments that reach each control-flow exit.

The following table describes the rules for joining assignments. In the uniformity graph, each join is an edge from the result node to node representing the source of the value. It is written in terms of an arbitrary variable `x`. It uses the following notations:

*   _Vin_(_S_) is the value of `x` prior the execution of the statement _S_.

*   _Vout_(_S_) is the value of `x` after the execution of the statement _S_.

*   _Vout_(_prev_) is the value of `x` prior to the execution of the current statement.

*   _Vin_(_next_) is the value of `x` prior to the execution of the next statement.

*   _V_(_e_) is a value node for an expression as in the subsequent sections.

*   _V_(_0_) is the zero value of `x`’s [effective-value-type](#effective-value-type).

Rules for joining multiple assignments to a function-scope variable. 
| Statement | Result | Edges from the Result | var _x_; | _Vin_(_next_) | _V_(_0_) | | var _x_ = _e_; | _Vin_(_next_) | _V_(_e_) Note: This is a [full assignment](#full-assignment) to _x_. | | _x_ = _e_; | | _r_ = _e_; where _r_ is a [full reference](#full-reference) to variable _x_ | | _sv_ = _e_; where _sv_ is a [full swizzle view](#full-swizzle-view) with originating variable _x_ | | _r_ = _e_; where _r_ is a [partial reference](#partial-reference) to variable _x_ | _Vout_(_S_) | _V_(_e_), _Vout_(_prev_) Note: This is a [partial assignment](#partial-assignment) to _x_. Note: Partial assignments include the previous value. The assignment either writes only a subset of the stored components, or the type of the written value differs from the [store type](#store-type) of the [originating variable](#originating-variable). | | _sv_ = _e_; where _sv_ is a [partial swizzle view](#partial-swizzle-view) with originating variable _x_ | | _s1_ _s2_ where _Next_ is in behavior of _s1_. Note:_s1_ often ends in a semicolon. | _Vin_(_s2_) | _Vout_(_s1_) | | if _e_ _s1_ else _s2_ where _Next_ is in the behaviors of both _s1_ and _s2_ | _Vin_(_next_) | _Vout_(_s1_), _Vout_(_s2_) | | if _e_ _s1_ else _s2_ where _Next_ is in the behavior of _s1_, but not _s2_ | _Vin_(_next_) | _Vout_(_s1_) | | if _e_ _s1_ else _s2_ where _Next_ is in the behavior of _s2_, but not _s1_ | _Vin_(_next_) | _Vout_(_s2_) | | loop { _s1_ continuing { _s2_ } } | _Vin_(_s1_) | _Vout_(_prev_), _Vout_(_s2_) if the behavior of _s1_ intersects {Next,Continue} | | loop { _s1_ continuing { _s2_ } } | _Vin_(_s2_) | _Vout_(_s1_) if Next is in the behavior of _s1_, _Vout_(_s_ i) for all _s_ i in _s1_ whose behavior is {_Continue_} and transfer control to _s2_ | | loop { _s1_ continuing { _s2_ } } | _Vin_(_next_) | _Vout_(_s2_) if Break is in the behavior of _s1_, _Vout_(_s_ i) for all _s_ i in _s1_ whose behavior is {_Break_} and transfer control to _next_ | | switch _e_ { case _: _s1_ case _: _s2_ ... case _: _s3_ } | _Vin_(_s_ i) | _Vout_(_prev_) | | switch _e_ { case _: _s1_ case _: _s2_ ... case _: _s3_ } | _Vin_(_next_) | _Vout_(_s_ i), for all _s_ i whose behavior includes _Next_ or _Break_, and _Vout_(_s_ j) for all statements inside _s_ j whose behavior is {_Break_} and trasfer control to _next_ | |
| --- | --- | --- |

For all other statements (except function calls), _Vin_(_next_) is equivalent to _Vout_(_prev_).

Note: The same desugarings apply as in [statement behavior analysis](#behaviors).

#### 15.2.6. Uniformity Rules for Statements[](#uniformity-statements)

The rules for analyzing statements take as argument both the statement itself and the node corresponding to control flow at the beginning of it (which we’ll note "CF" below) and return both of the following:

*   A node corresponding to control flow at the exit of it

*   A set of new nodes and edges to add to the graph

In the table below, `(CF1, S) => CF2` means "run the analysis on S starting with control flow CF1, apply the required changes to the graph, and name the resulting control flow node CF2". Similarly, `(CF1, E) => V` means "run the analysis on expression E, starting with control flow CF1, apply the required changes to the graph, and name the resulting value node V" (see next section for the analysis of expressions). This evaluation of expressions is used for any expression that is not part of the [left-hand side](#left-hand-side) of an [assignment](#statement-assignment) and is called an RHSValue.

There is a similar set of rules for expressions that are part of the [left-hand side](#left-hand-side) of an [assignment](#statement-assignment), the LHSValue, that we denote by `LHSValue: (CF, E) => L`. Instead of computing the node which corresponds to the uniformity of the value, it computes the node which corresponds to the uniformity of the variable being assigned to.

Note:[LHSValues](#lhsvalue) include expressions in [increment](#increment-statement) and [decrement](#decrement-statement) statements.

Note:[RHSValues](#rhsvalue) include expression that are part of the [right-hand side](#right-hand-side) of an [assignment](#statement-assignment) statement or expressions that are not part of an assignment, [increment](#increment-statement), or [decrement](#decrement-statement) statement.

When several edges have to be created we use `X -> {Y, Z}` as a short-hand for `X -> Y, X -> Z`.

In analyzing loops, we use the following patterns:

*   Node _CF'_ models control flow uniformity at the start of each [iteration](#iteration).

*   Node _CF1_ models control flow uniformity at the end of the loop body _s1_.

*   Node _CF2_ models control flow uniformity at the end of the continuing block statements _s2_.

*   The edges _CF'_ ->_CF1_ and _CF'_ ->_CF2_ model the fact control flow uniformity at the end of a loop affects the uniformity at the start of the next iteration. They are absent when loop body statements _s1_ only break or return, i.e. the behavior of _s1_ is a subset of {Break, Return}.

*   The _CF'_ ->_CF_ edge models the fact that uniformity at the start of at least some iterations depends on the uniformity when control flow reaches the whole loop statement.

*   When the whole loop has behavior {Next}, we assume any control flow divergence is resolved by the time the loop ends. The loop’s result control flow node is therefore set to _CF_, to model the fact that uniformity upon leaving the loop matches uniformity when first arriving at the loop.

*   Note:[Statement behavior analysis](#behaviors) implies that the behavior of a loop is one of {Next}, {Return}, or {Next,Return}.

Uniformity rules for statements
| Statement | New nodes | Recursive analyses | Resulting control flow node | New edges | _empty statement_ | | | _CF_ | | | {_s_} | | (_CF_, _s_) =>_CF'_ | _CF'_ | | | _s1_ _s2_, with Next in behavior of _s1_ Note:_s1_ often ends in a semicolon. | | (_CF_, _s1_) =>_CF1_ (_CF1_, _s2_) =>_CF2_ | _CF2_ | | | _s1_ _s2_, without Next in behavior of _s1_ Note:_s1_ often ends in a semicolon. | | (_CF_, _s1_) =>_CF1_ Note:_s2_ is statically unreachable and not recursively analyzed. _s2_ does not contribute to the uniformity analysis. | _CF1_ | | | if _e_ _s1_ else _s2_ with behavior {Next} | | (_CF_, _e_) =>_V_ (_V_, _s1_) =>_CF1_ (_V_, _s2_) =>_CF2_ | _CF_ | | | if _e_ _s1_ else _s2_ with another behavior | _CFend_ | _CFend_ | _CFend_ -> {_CF1_, _CF2_} | | loop {_s1_} Return not in behavior of _s1_ | _CF'_ | (_CF'_, _s1_) =>_CF1_ | _CF_ | _CF'_ -> {_CF1_, _CF_}, if behavior of _s1_ intersects {Next,Continue} | | _CF'_ ->_CF_, if behavior of _s1_ does not intersect {Next,Continue} | | loop {_s1_} Return in behavior of _s1_ | _CF'_ | (_CF'_, _s1_) =>_CF1_ | _CF1_ | _CF'_ -> {_CF1_, _CF_} if behavior of _s1_ intersects {Next,Continue} | | _CF'_ ->_CF_ if behavior of _s1_ does not intersect {Next,Continue} | | loop {_s1_ continuing {_s2_}} _s1_ has behavior {Break} | | (_CF_, _s1_) =>_CF1_ | _CF_ | Note: The loop executes only a single iteration, so no additional edges are required. | | loop {_s1_ continuing {_s2_}} _s1_ has behavior {Return} or {Break,Return} | | (_CF_, _s1_) =>_CF1_ | _CF1_ | | loop {_s1_ continuing {_s2_}} _s1_'s behaviour intersects {Next,Continue} | _CF'_ | (_CF'_, _s1_) =>_CF1_ (_CF1_, _s2_) =>_CF2_ | _CF_ if Return not in behavior of _s1_ | _CF'_ -> {_CF2_, _CF_} | | _CF'_ if Return in behavior of _s1_ | | switch _e_ case _: _s\_1_ .. case _: _s\_n_ with behavior {Next} | | (_CF_, _e_) =>_V_ (_V_, _s\_1_) =>_CF\_1_ ... (_V_, _s\_n_) =>_CF\_n_ | _CF_ | | | switch _e_ case _: _s\_1_ .. case _: _s\_n_ with another behavior | _CFend_ | _CFend_ | _CFend_ -> {_CF\_1_, ..., _CF\_n_} | | var x: T; | | | _CF_ | Note: If x is a [function](#address-spaces-function) address space variable, _CF_ is used as the zero value initializer in the [value analysis](#func-var-value-analysis). | | break; | | continue; | | break if _e_; | _CFend_ | (_CF_, _e_) =>_V_ | _CFend_ | _CFend_ ->_V_ Note: The edge from _CFend_ to _V_ captures the fact that when the condition value is non-uniform, then control flow resulting from this `break if` statement is also non-uniform. | | return; | | | _CF_ | For each [function](#address-spaces-function) address space pointer parameter _i_, [Value_return_i_contents](#value_return_i_contents) ->_Vin_(_prev_) (see [§ 15.2.5 Function-scope Variable Value Analysis](#func-var-value-analysis)) | | return _e_; | | (_CF_, _e_) =>_V_ | _CF_ | [Value_return](#value_return) ->_V_ For each [function](#address-spaces-function) address space pointer parameter _i_, [Value_return_i_contents](#value_return_i_contents) ->_Vin_(_prev_) (see [§ 15.2.5 Function-scope Variable Value Analysis](#func-var-value-analysis)) | | _e1_ = _e2_; | | [LHSValue](#lhsvalue): (_CF_, _e1_) =>_LV_ (_CF_, _e2_) =>_RV_ | _CF_ | _LV_ ->_RV_ Note:_LV_ is the result value from the [value analysis](#func-var-value-analysis). | | _ = _e_ | | (_CF_, _e_) =>_V_ | _CF_ | | | let x = _e_; | | (_CF_, _e_) =>_V_ | _CF_ | | | var x = _e_; | | (_CF_, _e_) =>_V_ | _CF_ | Note: If x is a [function](#address-spaces-function) address space variable, _V_ is used as the result value in the [value analysis](#func-var-value-analysis). | | _f_`()` Function call statement without arguments | | Invoke [function call analysis](#uniformity-function-calls): (_CF_, _f_()) =>[Result](#result) | _CF_ | | | _f_`(`_e1_,...,_eN_`)` Function call statement with arguments | | Invoke [function call analysis](#uniformity-function-calls): (_CF_, _f_(_e1_,...,_eN_)) =>[Result](#result) | _CF_ | | |
| --- | --- | --- | --- | --- |

For the purpose of this analysis:

*   `for` loops get desugared (see [§ 9.4.4 For Statement](#for-statement))

*   `while` loops get desugared (see [§ 9.4.5 While Statement](#while-statement))

*   `loop {s}` is treated as `loop {s continuing {}}`

*   `if` statements without an `else` branch are treated as if they had an empty else branch, i.e. ended in `else {}`

*   `if` statements with `else if` branches are treated as if they were nested simple `if/else` statements

*   a [switch_clause](#syntax-switch_clause) starting with `default` behaves just like a [switch_clause](#syntax-switch_clause) starting with `case _:`

To maximize performance, implementations often try to minimize the amount of [non-uniform control flow](#uniform-control-flow). However, the points at which invocations can be said to be uniform varies depending on a number of factors. WGSL’s static analysis conservatively assumes a return to uniform control flow occuring at the end of [if](#statement-if), [switch](#statement-switch), and [loop](#statement-loop) statements if the [behavior](#behaviors) for the statement is {Next}. This is modeled in the preceding table as the resulting control flow node being the same as input control flow node.

#### 15.2.7. Uniformity Rules for Function Calls[](#uniformity-function-calls)

The most complex rule is for function calls:

*   Let _CF_ be the control flow at the beginning of the function call expression.

*   For each argument, apply the corresponding expression rule with _CF_. Name the corresponding value nodes arg_i

*   Create a new node named Result

    *   Add an edge from [Result](#result) to _CF_

*   If the [call site tag](#call-site-tag) of the function is [CallSiteRequiredToBeUniform.S](#callsiterequiredtobeuniforms), then:

    *   Add an edge from [RequiredToBeUniform.S](#requiredtobeuniforms) to _CF_

    *   Add the members of the [potential-trigger-set](#potential-trigger-set) of the [call site tag](#call-site-tag) to the potential-trigger-set associated with [RequiredToBeUniform.S](#requiredtobeuniforms).

*   If the [function tag](#function-tag) is [ReturnValueMayBeNonUniform](#returnvaluemaybenonuniform), then add an edge from [Result](#result) to [MayBeNonUniform](#maybenonuniform)

*   For each argument _i_:

    *   If the corresponding [parameter tag](#parameter-tag) is [ParameterRequiredToBeUniform.S](#parameterrequiredtobeuniforms), then:

        *   Add an edge from [RequiredToBeUniform.S](#requiredtobeuniforms) to [arg_i](#arg_i).

        *   Add the members of the [potential-trigger-set](#potential-trigger-set) of the [parameter tag](#parameter-tag) to the potential-trigger-set associated with [RequiredToBeUniform.S](#requiredtobeuniforms).

    *   If the [parameter return tag](#parameter-return-tag) is [ParameterReturnContentsRequiredToBeUniform](#parameterreturncontentsrequiredtobeuniform), then add an edge from [Result](#result) to [arg_i](#arg_i)

    *   If the corresponding parameter has a [pointer parameter tag](#pointer-parameter-tag) of [PointerParameterMayBeNonUniform](#pointerparametermaybenonuniform), then add an edge from _Vout_(_call_) to [MayBeNonUniform](#maybenonuniform)

    *   If the parameter is a pointer in the [function](#address-spaces-function) address space, add an edge from _Vout_(_call_) to each corresponding [arg_i](#arg_i) for the reachable parameters recorded previously

        *   If the [parameter tag](#parameter-tag) is [ParameterContentsRequiredToBeUniform.S](#parametercontentsrequiredtobeuniforms), add an edge from [RequiredToBeUniform.S](#requiredtobeuniforms) to _Vout_(_call_)

Note: Refer to [§ 15.2.5 Function-scope Variable Value Analysis](#func-var-value-analysis) for the definition of _Vout_(_call_).

Most built-in functions have tags of:

*   A [call site tag](#call-site-tag) of [CallSiteNoRestriction](#callsitenorestriction).

*   A [function tag](#function-tag) of [NoRestriction](#norestriction).

*   For each parameter:

    *   a [parameter tag](#parameter-tag) of [ParameterNoRestriction](#parameternorestriction).

    *   a [parameter return tag](#parameter-return-tag) of [ParameterReturnContentsRequiredToBeUniform](#parameterreturncontentsrequiredtobeuniform).

Here is the list of exceptions:

*   A call to a function in [§ 17.11 Synchronization Built-in Functions](#sync-builtin-functions):

    *   Has a [function tag](#function-tag) of [NoRestriction](#norestriction).

    *   Has a [call site tag](#call-site-tag) of:

        *   [CallSiteRequiredToBeUniform.error](#callsiterequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of an unnamed [triggering rule](#diagnostic-triggering-rule) if [subgroup_uniformity](#language_extension-subgroup_uniformity) is not supported or the [uniformity scope](#uniformity-scope) is not subgroup.

            *   Note: The triggering rule has no name, and so it cannot be filtered.

        *   [CallSiteNoRestriction](#callsitenorestriction) otherwise.

    *   Additionally if [subgroup_uniformity](#language_extension-subgroup_uniformity) is not supported or the [uniformity scope](#uniformity-scope) is not subgroup, for a call to [workgroupUniformLoad](#workgroupUniformLoad-builtin), the parameter `p` has a [parameter tag](#parameter-tag) of [ParameterRequiredToBeUniform.error](#parameterrequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of an unnamed [triggering rule](#diagnostic-triggering-rule).

*   A call to a function in [§ 17.6 Derivative Built-in Functions](#derivative-builtin-functions), [§ 17.7.8 textureSample](#texturesample), [§ 17.7.9 textureSampleBias](#texturesamplebias), and [§ 17.7.10 textureSampleCompare](#texturesamplecompare):

    *   Has a [function tag](#function-tag) of [ReturnValueMayBeNonUniform](#returnvaluemaybenonuniform).

    *   Has a [call site tag](#call-site-tag) as follows:

        *   If [subgroup_uniformity](#language_extension-subgroup_uniformity) is not supported or the [uniformity scope](#uniformity-scope) is not subgroup

            *   Let _DF_ be the [nearest enclosing diagnostic filter](#nearest-enclosing-diagnostic-filter) for the call site location and triggering rule [derivative_uniformity](#trigger-derivative_uniformity)

            *   If _DF_ exists, then let _S_ be the _DF_'s new severity parameter.

                *   If _S_ is the severity [off](#severity-off), the call site tag is [CallSiteNoRestriction](#callsitenorestriction).

                *   Otherwise the call site tag is [CallSiteRequiredToBeUniform.S](#callsiterequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of a [derivative_uniformity](#trigger-derivative_uniformity) element.

            *   If there is no such _DF_, the call site tag is [CallSiteRequiredToBeUniform.error](#callsiterequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of a [derivative_uniformity](#trigger-derivative_uniformity) element.

        *   [CallSiteNoRestriction](#callsitenorestriction) otherwise.

*   A call to [§ 17.7.4 textureLoad](#textureload):

    *   Has a [call site tag](#call-site-tag) of [CallSiteNoRestriction](#callsitenorestriction)

    *   Has a [function tag](#function-tag) as follows:

        *   [ReturnValueMayBeNonUniform](#returnvaluemaybenonuniform) if the argument corresponding to the `t` parameter is a [read-write storage texture](#type-read-write-storage-texture)

        *   [NoRestriction](#norestriction) otherwise

*   A call to a function in [§ 17.12 Subgroup Built-in Functions](#subgroup-builtin-functions) or [§ 17.13 Quad Operations](#quad-builtin-functions):

    *   Has a [function tag](#function-tag) of:

        *   [NoRestriction](#norestriction) if the [uniformity scope](#uniformity-scope) is subgroup and the function is one of the following:

            *   [subgroupAdd](#subgroupadd-builtin)

            *   [subgroupAll](#subgroupall-builtin)

            *   [subgroupAnd](#subgroupand-builtin)

            *   [subgroupAny](#subgroupany-builtin)

            *   [subgroupBallot](#subgroupballot-builtin)

            *   [subgroupBroadcast](#subgroupbroadcast-builtin)

            *   [subgroupBroadcastFirst](#subgroupbroadcastfirst-builtin)

            *   [subgroupMax](#subgroupmax-builtin)

            *   [subgroupMin](#subgroupmin-builtin)

            *   [subgroupMul](#subgroupmul-builtin)

            *   [subgroupOr](#subgroupor-builtin)

            *   [subgroupXor](#subgroupxor-builtin)

        *   [ReturnValueMayBeNonUniform](#returnvaluemaybenonuniform) otherwise

    *   Let _DF_ be the [nearest enclosing diagnostic filter](#nearest-enclosing-diagnostic-filter) for the call site location and triggering rule [subgroup_uniformity](#trigger-subgroup_uniformity)

    *   Has a [call site tag](#call-site-tag) as follows:

        *   If [subgroup_uniformity](#language_extension-subgroup_uniformity) is not supported or the [uniformity scope](#uniformity-scope) is subgroup then:

            *   If _DF_ exists, then let _S_ be the _DF_'s new severity parameter.

                *   If _S_ is the severity [off](#severity-off), the call site tag is [CallSiteNoRestriction](#callsitenorestriction).

                *   Otherwise, the call site tag is [CallSiteRequiredToBeUniform.S](#callsiterequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of a [subgroup_uniformity](#trigger-subgroup_uniformity) element.

            *   If there is no such _DF_, the call site tag is [CallSiteRequiredToBeUniform.error](#callsiterequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of a [subgroup_uniformity](#trigger-subgroup_uniformity) element.

        *   [CallSiteNoRestriction](#callsitenorestriction) otherwise.

    *   Additionally for the case of a call to [subgroupShuffleUp](#subgroupshuffleup-builtin) or [subgroupShuffleDown](#subgroupshuffledown-builtin), the parameter `delta` has a [parameter tag](#parameter-tag) of:

        *   If [subgroup_uniformity](#language_extension-subgroup_uniformity) is not supported or the [uniformity scope](#uniformity-scope) is subgroup then:

            *   If _DF_ exists, then let _S_ be _DF_'s new severity parameter.

                *   If _S_ is the severity [off](#severity-off), the parameter tag is [NoRestriction](#norestriction).

                *   Otherwise, the parameter tag is [ParameterRequiredToBeUniform.S](#parameterrequiredtobeuniforms) with [potential-trigger-set](#potential-trigger-set) consisting of a [subgroup_uniformity](#trigger-subgroup_uniformity) element.

            *   If there is no such _DF_, the parameter tag is [ParameterRequiredToBeUniform.error](#parameterrequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of a [subgroup_uniformity](#trigger-subgroup_uniformity) element.

        *   [NoRestriction](#norestriction) otherwise.

    *   Additionally for the case of a call to [subgroupShuffleXor](#subgroupshufflexor-builtin), the parameter `mask` has a [parameter tag](#parameter-tag) of:

        *   If [subgroup_uniformity](#language_extension-subgroup_uniformity) is not supported or the [uniformity scope](#uniformity-scope) is subgroup then:

            *   If _DF_ exists, then let _S_ be _DF_'s new severity parameter.

                *   If _S_ is the severity [off](#severity-off), the parameter tag is [NoRestriction](#norestriction).

                *   Otherwise, the parameter tag is [ParameterRequiredToBeUniform.S](#parameterrequiredtobeuniforms) with [potential-trigger-set](#potential-trigger-set) consisting of a [subgroup_uniformity](#trigger-subgroup_uniformity) element.

            *   If there is no such _DF_, the parameter tag is [ParameterRequiredToBeUniform.error](#parameterrequiredtobeuniforms), with [potential-trigger-set](#potential-trigger-set) consisting of a [subgroup_uniformity](#trigger-subgroup_uniformity) element.

        *   [NoRestriction](#norestriction) otherwise.

Note: A WGSL implementation will ensure that if control flow prior to a function call is [uniform](#uniform-control-flow) for a particular scope, it will also be uniform after the function call.

#### 15.2.8. Uniformity Rules for Expressions[](#uniformity-expressions)

The rules for analyzing expressions take as argument both the expression itself and the node corresponding to control flow at the beginning of it (which we’ll note "CF" below) and return the following:

*   A node corresponding to its value

*   A set of new nodes and edges to add to the graph

Uniformity rules for [RHSValue](#rhsvalue) expressions
| Expression | New nodes | Recursive analyses | Resulting value node | New edges | _e1_ || _e2_ | | (_CF_, _e1_) =>_V1_ (_V1_, _e2_) =>_V2_ | _V2_ | | | _e1_&&_e2_ | | Literal | | | _CF_ | | | identifier [resolving](#resolves) to function-scope variable "x", where the identifier appears as the [root identifier](#root-identifier) of a [memory view](#memory-view) expression, _MVE_, and the [load rule](#load-rule) is invoked on _MVE_ during [type checking](#type-checking) | _Result_ | _X_ is the node corresponding to the value of "x" at the input to the statement containing this expression | _Result_ | _Result_ -> {_CF_, _X_} Note:_X_ is equivalent to _Vout_(_prev_) for "x" (see [§ 15.2.5 Function-scope Variable Value Analysis](#func-var-value-analysis)) | | identifier [resolving](#resolves) to function-scope variable "x", where the identifier appears as the [root identifier](#root-identifier) of a [swizzle view expression](#swizzle-view-expr), _SVE_, and the [swizzle view load rule](#swizzle-view-load-rule) is invoked on _SVE_ during [type checking](#type-checking) | | identifier [resolving](#resolves) to function-scope variable "x", where "x" is the desugared pointer parameter _i_, and where the identifier appears as the [root identifier](#root-identifier) of a [memory view](#memory-view) expression, _MVE_, and the [load rule](#load-rule) is not invoked on _MVE_ during [type checking](#type-checking) | | | [param_i](#param_i) | | | identifier [resolving](#resolves) to function-scope variable "x", where "x" is the desugared pointer parameter _i_, and where the identifier appears as the [root identifier](#root-identifier) of a [swizzle view expression](#swizzle-view-expr), _SVE_, and the [swizzle view load rule](#swizzle-view-load-rule) is invoked on _SVE_ during [type checking](#type-checking) | | identifier [resolving](#resolves) to function-scope variable "x", where the identifier appears as the [root identifier](#root-identifier) of a [memory view](#memory-view) expression, _MVE_, and the [load rule](#load-rule) is not invoked on _MVE_ during [type checking](#type-checking) | | | _CF_ | | | identifier [resolving](#resolves) to function-scope variable "x", where the identifier appears as the [root identifier](#root-identifier) of a [swizzle view expression](#swizzle-view-expr), _SVE_, and the [swizzle view load rule](#swizzle-view-load-rule) is not invoked on _SVE_ during [type checking](#type-checking) | | identifier [resolving](#resolves) to [const-declaration](#const-declaration), [override-declaration](#override-declaration), [let-declaration](#let-declaration), or non-built-in [formal parameter](#formal-parameter) of [non-pointer type](#pointer-type) "x" | _Result_ | _X_ is the node corresponding to "x" | _Result_ | _Result_ -> {_CF_, _X_} | | identifier [resolving](#resolves) to a [formal parameter](#formal-parameter) of [pointer type](#pointer-type) in the [storage](#address-spaces-storage), [workgroup](#address-spaces-workgroup), or [private](#address-spaces-private)[address spaces](#address-spaces) with a non-read-only [access mode](#access-mode) where the identifier appears as the [root identifier](#root-identifier) of a [memory view](#memory-view) expression, _MVE_, and the [load rule](#load-rule) is invoked on _MVE_ during [type checking](#type-checking) | | | [MayBeNonUniform](#maybenonuniform) | | | identifier [resolving](#resolves) to a [formal parameter](#formal-parameter) of [pointer type](#pointer-type) in the [storage](#address-spaces-storage), [workgroup](#address-spaces-workgroup), or [private](#address-spaces-private)[address spaces](#address-spaces) with a non-read-only [access mode](#access-mode) where the identifier appears as the [root identifier](#root-identifier) of a [swizzle view expression](#swizzle-view-expr), _SVE_, and the [swizzle view load rule](#swizzle-view-load-rule) is invoked on _SVE_ during [type checking](#type-checking) | | identifier [resolving](#resolves) to a [formal parameter](#formal-parameter) of [pointer type](#pointer-type) in the [storage](#address-spaces-storage), [workgroup](#address-spaces-workgroup), or [private](#address-spaces-private)[address spaces](#address-spaces) with a non-read-only [access mode](#access-mode) where the identifier appears as the [root identifier](#root-identifier) of a [memory view](#memory-view) expression, _MVE_, and the [load rule](#load-rule) is not invoked on _MVE_ during [type checking](#type-checking) | | | _CF_ | | | identifier [resolving](#resolves) to a [formal parameter](#formal-parameter) of [pointer type](#pointer-type) in the [storage](#address-spaces-storage), [workgroup](#address-spaces-workgroup), or [private](#address-spaces-private)[address spaces](#address-spaces) with a non-read-only [access mode](#access-mode) where the identifier appears as the [root identifier](#root-identifier) of a [swizzle view expression](#swizzle-view-expr), _SVE_, and the [swizzle view load rule](#swizzle-view-load-rule) is not invoked on _SVE_ during [type checking](#type-checking) | | identifier [resolving](#resolves) to a [formal parameter](#formal-parameter) of [pointer type](#pointer-type) in an [address space](#address-spaces) other than [function](#address-spaces-function) with a read-only [access mode](#access-mode) | | | _CF_ | | | identifier [resolving](#resolves) to uniform built-in value "x" | | | _CF_ | | | identifier [resolving](#resolves) to non-uniform built-in value "x" | | | [MayBeNonUniform](#maybenonuniform) | | | identifier [resolving](#resolves) to read-only module-scope variable "x" | | | _CF_ | | | identifier [resolving](#resolves) to non-read-only module-scope variable "x" where the identifier appears as the [root identifier](#root-identifier) of a [memory view](#memory-view) expression, _MVE_, and the [load rule](#load-rule) is invoked on _MVE_ during [type checking](#type-checking) | | | [MayBeNonUniform](#maybenonuniform) | | | identifier [resolving](#resolves) to non-read-only module-scope variable "x" where the identifier appears as the [root identifier](#root-identifier) of a [swizzle view expression](#swizzle-view-expr), _SVE_, and the [swizzle view load rule](#swizzle-view-load-rule) is invoked on _SVE_ during [type checking](#type-checking) | | identifier [resolving](#resolves) to non-read-only module-scope variable "x" where the identifier appears as the [root identifier](#root-identifier) of a [memory view](#memory-view) expression, _MVE_, and the [load rule](#load-rule) is not invoked on _MVE_ during [type checking](#type-checking) | | | _CF_ | | | identifier [resolving](#resolves) to non-read-only module-scope variable "x" where the identifier appears as the [root identifier](#root-identifier) of a [swizzle view expression](#swizzle-view-expr), _SVE_, and the [swizzle view load rule](#swizzle-view-load-rule) is not invoked on _SVE_ during [type checking](#type-checking) | | ( _e_ ) | | (_CF_, _e_) =>_V_ | _V_ | | | _op_ _e_, where _op_ is a unary operator | | _e_._field_, where _field_ is a structure member name | | _e_._swiz_, where _swiz_ is a [swizzle](#swizzle) name | | _e1_ _op_ _e2_, where _op_ is a non-short-circuiting binary operator | _Result_ | (_CF_, _e1_) =>_V1_ (_CF_, _e2_) =>_V2_ | _Result_ | _Result_ -> {_V1_, _V2_} | | e2[e1] | | _f_`()` Function call expression without arguments | | Invoke [function call analysis](#uniformity-function-calls): (_CF_, _f_()) =>[Result](#result) | _Result_ | | | _f_`(`_e1_,...,_eN_`)` Function call expression with arguments | | Invoke [function call analysis](#uniformity-function-calls): (_CF_, _f_(_e1_,...,_eN_)) =>[Result](#result) | _Result_ | | |
| --- | --- | --- | --- | --- |

The following built-in input variables are considered uniform:

*   [workgroup_id](#built-in-values-workgroup_id)

*   [num_workgroups](#built-in-values-num_workgroups)

*   [subgroup_size](#built-in-values-subgroup_size) when used in a [compute shader stage](#compute-shader-stage)

*   [num_subgroups](#built-in-values-num_subgroups)

At [subgroup uniformity scope](#subgroup-uniformity-scope), the following built-in input variables are also considered uniform:

*   [subgroup_id](#built-in-values-subgroup_id)

All other ones (see [built-in values](#built-in-values)) are considered non-uniform.

Note: An author should avoid grouping the uniform built-in values together with other non-uniform inputs because the analysis does not analyze the [components](#components) of a [composite](#composite) type separately.

Uniformity rules for [LHSValue](#lhsvalue) expressions
| Expression | New nodes | Recursive analyses | Resulting variable node | New edges | identifier [resolving](#resolves) to function-scope variable "x" | _Result_ | _X_ is the node corresponding to the value of "x" at the output of the statement containing this expression. | _Result_ | _Result_ -> {_CF_, _X_} Note:_X_ is equivalent to _Vin_(_next_) for "x" (see [§ 15.2.5 Function-scope Variable Value Analysis](#func-var-value-analysis)) | | identifier [resolving](#resolves) to [const-declaration](#const-declaration), [override-declaration](#override-declaration), [let-declaration](#let-declaration), or [formal parameter](#formal-parameter) "x" | | _X_ is the node corresponding to "x" | _X_ | | | identifier [resolving](#resolves) to module-scope variable "x" | | | [MayBeNonUniform](#maybenonuniform) | | | _e_._field_, where _field_ is a structure member name | | [LHSValue](#lhsvalue): (_CF_, _e_) =>_L1_ | _L1_ | | | _e_._swiz_, where _swiz_ is a [swizzle](#swizzle) name | | *_e_ | | &_e_ | | _e2_[_e1_] | | (_CF_, _e1_) =>_V1_ [LHSValue](#lhsvalue): (_CF_, _e2_) =>_L2_ | _L2_ | _L2_ ->_V1_ | | _f_`()` Function call expression without arguments | | Invoke [function call analysis](#uniformity-function-calls): [LHSValue](#lhsvalue): (_CF_, _f_()) =>[Result](#result) | _Result_ | | | _f_`(`_e1_,...,_eN_`)` Function call expression with arguments | | Invoke [function call analysis](#uniformity-function-calls): [LHSValue](#lhsvalue): (_CF_, _f_(_e1_,...,_eN_)) =>[Result](#result) | _Result_ | | |
| --- | --- | --- | --- | --- |

#### 15.2.9. Annotating the Uniformity of Every Point in the Control-flow[](#uniformity-optional-diagnosis-mode)

This entire subsection is non-normative.

If implementers want to provide developers with a diagnostic mode that shows for each point in the control-flow of the entire shader whether it is uniform or not (and thus whether it would be valid to call a function that requires uniformity there), we suggest the following:

*   Run the (mandatory, normative) analysis described in the previous subsections, keeping the graph for every function.

*   Reverse all edges in all of those graphs

*   Go through each function, starting with the entry point and never visiting a function before having visited all of its callers:

    *   Add an edge from [MayBeNonUniform](#maybenonuniform) to every argument that was non-uniform in at least one caller.

    *   Add an edge from [MayBeNonUniform](#maybenonuniform) to [CF_start](#cf_start) if the function was called in non-uniform control-flow in at least one caller.

    *   Look at which nodes are reachable from [MayBeNonUniform](#maybenonuniform). Every node visited is an expression or point in the control-flow whose uniformity cannot be proven by the analysis.

Any node which is not visited by these reachability analyses can be proven to be uniform by the analysis (and so it would be safe to call a derivative or similar function there).

Note: The bottom-up analysis is still required, as it lets us know what edges to add to the graphs when encountering calls.

#### 15.2.10. Examples[](#uniformity-examples)

The graphs in the subsequent example use the following conventions for nodes:

*   Rectangles represent value nodes.

*   Rounded rectangles represent control flow nodes.

##### 15.2.10.1. Invalid `textureSample` Function Call[](#uniformity-example1)

This example shows an invalid use of a [textureSample](#texturesample) built-in function call. The function call is made within an if statement whose condition depends on a non-uniform value (i.e. the built-in value `position`). The invalid dependency chain is highlighted in red.

EXAMPLE: WGSL invalid textureSample

@group(0) @binding(0) var t : texture_2d<f32>;
@group(0) @binding(1) var s : sampler;

@fragment
fn main(@builtin(position) pos : vec4<f32>) {
  if (pos.x < 0.5) {
    // Invalid textureSample function call.
    _ = textureSample(t, s, pos.xy);
  }
}

Uniformity graph

The example also shows that uniformity of the control flow after the if statement is the same as the uniformity prior to the if statement (CF_return being connected to [CF_start](#cf_start)). That is, the control flow is once again uniform after the if statement (because it is guaranteed to start as uniform control flow at the beginning of the entry point). If the `textureSample` function call had been moved outside the if statement the program would have been valid. Likewise, if the condition of the if statement were a uniform value (e.g. each invocation read the same value from a [uniform buffer](#uniform-buffer)), the program would also have been valid.

##### 15.2.10.2. Function-scope Variable Uniformity[](#uniformity-example2)

This example shows both a valid and an invalid [barrier](#sync-builtin-functions) function call that depend on the value of a function-scope variable. The `workgroupBarrier` is invalid because the value of `x` is derived from the mutable module-scope variable `a`. The `storageBarrier` is valid because the value of `x` is derived from the immutable module-scope variable `b`. This example highlights the [value analysis'](#func-var-value-analysis) ability to separate different periods of uniformity in a function-scope variable’s lifetime. This example also clearly shows that control flow becomes uniform again after the end of the first [if](#statement-if) statement. We know this because that section of the graph is independent from the second if statement.

EXAMPLE: WGSL using function variable

@group(0) @binding(0) var<storage, read_write> a : i32;
@group(0) @binding(1) var<uniform> b : i32;

@compute @workgroup_size(16,1,1)
fn main() {
  var x : i32;
  x = a;
  if x > 0 {
    // Invalid barrier function call.
    workgroupBarrier();
  }
  x = b;
  if x < 0 {
    // Valid barrier function call.
    storageBarrier();
  }
}

Uniformity graph

Note: The subgraphs are only included in the example for ease of understanding.

##### 15.2.10.3. Composite Value Analysis Limitations[](#uniformity-example3)

One limitation of the uniformity analysis is that it does not track the [components](#components) of a [composite](#composite) value independently. That is, any non-uniform component value [will](#behavioral-requirements) cause the analysis to treat the entire composite value as non-uniform. This example illustrates this issue and a potential workaround that shader authors can employ to avoid this limitation.

EXAMPLE: Invalid composite value WGSL

struct Inputs {
  // workgroup_id is a uniform built-in value.
  @builtin(workgroup_id) wgid : vec3<u32>,
  // local_invocation_index is a non-uniform built-in value.
  @builtin(local_invocation_index) lid : u32
}

@compute @workgroup_size(16,1,1)
fn main(inputs : Inputs) {
  // This comparison is always uniform,
  // but the analysis cannot determine that.
  if inputs.wgid.x == 1 {
    workgroupBarrier();
  }
}

Invalid uniformity graph

The easiest way to work around this limitation of the analysis is to split the composite up so that values that are known to be uniform are separate from value that are known to be non-uniform. In the alternative WGSL below, splitting the two built-in values into separate parameters satisfies the uniformity analysis. This can be seen by the lack of a path from [RequiredToBeUniform.S](#requiredtobeuniforms) to [MayBeNonUniform](#maybenonuniform) in the graph.

EXAMPLE: Valid alternative WGSL

@compute @workgroup_size(16,1,1)
fn main(@builtin(workgroup_id) wgid : vec3<u32>,
        @builtin(local_invocation_index) lid : u32) {
  // The uniformity analysis can now correctly determine this comparison is
  // always uniform.
  if wgid.x == 1 {
    // Valid barrier function call.
    workgroupBarrier();
  }
}

Valid alternative uniformity graph

##### 15.2.10.4. Uniformity in a Loop[](#uniformity-example4)

In this example, there is an invalid `workgroupBarrier` function call in a loop. The non-uniform built-in value `local_invocation_index` is the ultimate cause despite the fact that it appears after the barrier in the loop. This occurs, because on later iterations some of the invocations in the workgroup will have exited the loop prematurely while others attempt to execute the barrier. The analysis models the inter-iteration dependencies as an edge, where the control at the start of the loop body (CF_loop_body) depends on the control flow at the end of the loop body (CF_after_if).

EXAMPLE: Loop uniformity WGSL

@compute @workgroup_size(16,1,1)
fn main(@builtin(local_invocation_index) lid : u32) {
  for (var i = 0u; i < 10; i++) {
    workgroupBarrier();
    if (lid + i) > 7 {
      break;
    }
  }
}

Uniformity graph

##### 15.2.10.5. User-defined Function Calls[](#uniformity-example5)

This example is modification of the [first example](#uniformity-example1), but uses a user-defined function call. The analysis sets the [parameter return tag](#parameter-return-tag) of both parameters of `scale` as [ParameterReturnContentsRequiredToBeUniform](#parameterreturncontentsrequiredtobeuniform). This leads to the path in `main` between the return value of the `scale` function call and the `position` built-in value. That path is a subpath of the overall invalid path from [RequiredToBeUniform.S](#requiredtobeuniforms) to [MayBeNonUniform](#maybenonuniform).

EXAMPLE: User-defined function call uniformity WGSL

fn scale(in1 : f32, in2 : f32) -> f32 {
  let v = in1 / in2;
  return v;
}

@group(0) @binding(0) var t : texture_2d<f32>;
@group(0) @binding(1) var s : sampler;

@fragment
fn main(@builtin(position) pos : vec4<f32>) {
  let tmp = scale(pos.x, 0.5);
  if tmp > 1.0 {
    _ = textureSample(t, s, pos.xy);
  }
}

Uniformity graph for scale

Uniformity graph for main

Note: The subgraphs are only included in the example for ease of understanding.

### 15.3. Compute Shaders and Workgroups[](#compute-shader-workgroups)

A workgroup is a set of invocations which concurrently execute a [compute shader stage](#compute-shader-stage)[entry point](#entry-point), and share access to shader variables in the [workgroup](#address-spaces-workgroup) address space.

The workgroup grid for a compute shader is the set of points with integer coordinates _(i,j,k)_ with:

*   0 ≤ i < workgroup_size_x

*   0 ≤ j < workgroup_size_y

*   0 ≤ k < workgroup_size_z

where _(workgroup\_size\_x, workgroup\_size\_y, workgroup\_size\_z)_ is the value specified for the [workgroup_size](#attribute-workgroup_size) attribute of the entry point.

There is exactly one invocation in a workgroup for each point in the workgroup grid.

An invocation’s local invocation ID is the coordinate triple (i,j,k) for the invocation’s corresponding workgroup grid point.

When an invocation has [local invocation ID](#local-invocation-id), then its local invocation index is:

i + (j × workgroup_size_x) + (k × workgroup_size_x × workgroup_size_y)

Note that if a workgroup has W invocations, then each invocation I the workgroup has a unique local invocation index L(I) such that 0 ≤ L(I) <W, and that entire range is covered.

A compute shader begins execution when a WebGPU implementation removes a dispatch command from a queue and begins the specified work on the GPU. The dispatch command specifies a dispatch size, which is an integer triple (group_count_x, group_count_y, group_count_z) indicating the number of workgroups to be executed, as described in the following.

The compute shader grid for a particular dispatch is the set of points with integer coordinates _(CSi,CSj,CSk)_ with:

*   0 ≤ CSi < workgroup_size_x × group_count_x

*   0 ≤ CSj < workgroup_size_y × group_count_y

*   0 ≤ CSk < workgroup_size_z × group_count_z

where _workgroup\_size\_x_, _workgroup\_size\_y_, and _workgroup\_size\_z_ are as above for the compute shader entry point.

The work to be performed by a compute shader dispatch is to execute exactly one invocation of the entry point for each point in the compute shader grid.

An invocation’s global invocation ID is the coordinate triple for the invocation’s corresponding compute shader grid point.

The invocations are organized into workgroups, so that each invocation’s [global invocation ID](#global-invocation-id)_(CSi, CSj, CSk)_ maps to a single workgroup, identified by workgroup ID:

( ⌊ _CSi_ ÷ workgroup_size_x ⌋, ⌊ _CSj_ ÷ workgroup_size_y ⌋, ⌊ _CSk_ ÷ workgroup_size_z ⌋)

and a single invocation within that workgroup, identified by [local invocation ID](#local-invocation-id):

( _CSi_ mod workgroup_size_x , _CSj_ mod workgroup_size_y , _CSk_ mod workgroup_size_z ).

Note: Workgroup IDs span from (0,0,0) to ([group_count_x](#group_count_x) - 1, [group_count_y](#group_count_y) - 1, [group_count_z](#group_count_z) - 1).

If the [linear_indexing](#language_extension-linear_indexing) feature is supported, then when a workgroup has a [workgroup ID](#workgroup-id)_(WGi, WGj, WGk)_, then its workgroup index is:

_WGi_ + ( _WGj_ × group_count_x ) + ( _WGk_ × group_count_x × group_count_y )

If the [linear_indexing](#language_extension-linear_indexing) feature is supported, then when an invocation has [global invocation ID](#global-invocation-id)_(CSi, CSj, CSk)_, then its global invocation index is:

_CSi_ + ( _CSj_ × workgroup_size_x × group_count_x ) + ( _CSk_ × workgroup_size_x × group_count_x × workgroup_size_y × group_count_y )

WebGPU provides no guarantees about:

*   Whether invocations from different workgroups execute concurrently. That is, you cannot assume more than one workgroup executes at a time.

*   Whether, once invocations from a workgroup begin executing, that other workgroups are blocked from execution. That is, you cannot assume that only one workgroup executes at a time. While a workgroup is executing, the implementation may choose to concurrently execute other workgroups as well, or other queued but unblocked work.

*   Whether invocations from one particular workgroup begin executing before the invocations of another workgroup. That is, you cannot assume that workgroups are launched in a particular order.

### 15.4. Fragment Shaders and Helper Invocations[](#fragment-shaders-helper-invocations)

Invocations in the [fragment shader stage](#fragment-shader-stage) are divided into 2x2 grids of invocations with neighbouring [positions](#built-in-values-position) in the X and Y dimensions. Each of these grids is referred to as a quad. Quads can collaborate in some collective operations (see [§ 15.6.2 Derivatives](#derivatives)). An invocation’s quad invocation ID is the unique ID within the quad, where:

*   ID 0 is the upper-left invocation.

*   ID 1 is the upper-right invocation.

*   ID 2 is the lower-left invocation.

*   ID 3 is the lower-right invocation.

Note: There is no built-in value accessor for the quad ID.

Ordinarily, [fragment processing](../webgpu_spec/webgpu-5f71975aec.md#fragment-processing) creates one invocation of a fragment shader for each [RasterizationPoint](../WGPU/gpuweb-spec/gpuweb-spec.md#rasterizationpoint) produced by [rasterization](../webgpu_spec/webgpu-5f71975aec.md#rasterization). Sometimes there may be insufficient RasterizationPoints to fully populate a quad, for example at the edge of a graphics primitive. When a quad has only 1, 2, or 3 invocations corresponding to RasterizationPoints, fragment processing [will](#behavioral-requirements) create a helper invocation for each unpopulated position in the quad.

Helper invocations have limited observable effects. They help compute [derivatives](#derivatives) and may participate in [subgroup operations](#subgroup-ops). As such, helper invocations are subject to the following restrictions:

*   No [write accesses](#write-access) (see also [§ 14.5.1 Memory Operation](#memory-operation)) [will](#behavioral-requirements) be performed on the [storage](#address-spaces-storage) or [handle](#address-spaces-handle) address spaces.

*   [Atomic built-in functions](#atomic-builtin-functions)[will](#behavioral-requirements) return [indeterminate](#indeterminate-value) results.

*   The [Entry point](#entry-point)[return value](#return-value)[will](#behavioral-requirements) not be further processed downstream in the [GPURenderPipeline](#gpurenderpipeline).

If all of the invocations in a quad become helper invocations (e.g. due to executing a [discard](#statement-discard) statement), execution of the quad may be terminated; however, such termination is not considered to produce [non-uniform control flow](#uniform-control-flow).

### 15.5. Subgroups[](#subgroups)

A subgroup is a set of invocations which concurrently execute a [compute](#compute-shader-stage) or [fragment](#fragment-shader-stage) shader stage [entry point](#entry-point), and which can efficiently share data and [collectively](#subgroup-ops) compute results. Each invocation in a compute or fragment shader belongs to exactly one subgroup. In a compute shader, each subgroup is a subset of a particular [workgroup](#compute-shader-stage-workgroup). In a fragment shader, a subgroup might contain invocations from multiple [draw commands](#draw-command). Each [quad](#quad) will be contained in a single subgroup.

The subgroup size is the maximum number of invocations in a subgroup. Within a shader, the value is accessible via the [subgroup_size](#built-in-values-subgroup_size) built-in value. The subgroup size is a [uniform value](#uniform-value) within a [dispatch command](#dispatch-command) and hence within a [workgroup](#compute-shader-stage-workgroup), but it may not be a uniform value within a [draw command](#draw-command). All subgroup sizes are powers of two within the range [4, 128], and the value for a shader compiled for a specific device will be within the range [[subgroupMinSize](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-gpuadapterinfo-subgroupminsize), [subgroupMaxSize](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-gpuadapterinfo-subgroupmaxsize)] for the [WebGPU § 4.3 GPUAdapter](../webgpu_spec/webgpu-5f71975aec.md#gpuadapter). The actual size depends on the shader, device properties, and the device compiler. Each device supports a subset of the possible range of subgroup sizes (possibly a single value). The device compiler selects a size from the supported sizes using a variety of heuristics. Each subgroup may contain fewer invocations than the reported subgroup size (e.g. if fewer invocations than the subgroup size are launched).

An invocation’s subgroup invocation ID is a unique ID within the subgroup. This ID is accessible via the [subgroup_invocation_id](#built-in-values-subgroup_invocation_id) built-in value and is in the range [0, `subgroup_size` - 1].

If the [subgroup_id](#language_extension-subgroup_id) feature is supported, within a compute shader the subgroup ID is the unique ID for the subgroup within the workgroup. This ID is accessible via the [subgroup_id](#built-in-values-subgroup_id) built-in value and is in the range [0, [num_subgroups](#built-in-values-num_subgroups) - 1].

There is no defined relationship between subgroup values (i.e. `subgroup_invocation_id` and `subgroup_id`) and [local_invocation_index](#built-in-values-local_invocation_index). To avoid non-portable code, shader authors should not assume a particular mapping between these two values.

When invocations in the same subgroup execute different control flow paths, we say subgroup execution has diverged. This is a special case of [non-uniform control flow](#uniform-control-flow). Divergence affects the semantics of subgroup operations. The invocations in a subgroup that concurrently execute a subgroup operation are active for that operation. Other invocations in the subgroup are inactive for that operation. When the subgroup size exceeds the number of invocations in a subgroup, the extra hypothetical invocations are considered inactive. [Helper invocations](#helper-invocation) may be active or inactive in an operation. That is, on some devices helper invocations may participate in subgroup operations, while on other devices they may not.

Note: There is considerable non-portability among underlying devices when operating in non-uniform control flow, and device compilers often aggressively optimize such code. The result is that the subgroup may contain a different set of active invocations than the shader author expects.

### 15.6. Collective Operations[](#collective-operations)

#### 15.6.1. Barriers[](#barrier)

A barrier is a [synchronization built-in function](#sync-builtin-functions) that orders memory operations in a program. A control barrier is executed by all invocations in the same [workgroup](#compute-shader-stage-workgroup) as if it were executed concurrently. As such, control barriers [must](#shader-creation-error) only be executed in [uniform control flow](#uniform-control-flow) in a [compute](#compute-shader-stage) shader.

#### 15.6.2. Derivatives[](#derivatives)

A partial derivative is the rate of change of a value along an axis. Fragment shader invocations within the same [quad](#quad) collaborate to compute approximate partial derivatives.

The builtin functions that compute a derivative are:

*   [textureSample](#texturesample), [textureSampleBias](#texturesamplebias), and [textureSampleCompare](#texturesamplecompare)

*   [dpdx](#dpdx-builtin), [dpdxCoarse](#dpdxCoarse-builtin), and [dpdxFine](#dpdxFine-builtin)

*   [dpdy](#dpdy-builtin), [dpdyCoarse](#dpdyCoarse-builtin), and [dpdyFine](#dpdyFine-builtin)

*   [fwidth](#fwidth-builtin), [fwidthCoarse](#fwidthCoarse-builtin), and [fwidthFine](#fwidthFine-builtin)

Partial derivatives of the _fragment coordinate_ are computed implicitly as part of operation of the following built-in functions:

*   [textureSample](#texturesample),

*   [textureSampleBias](#texturesamplebias), and

*   [textureSampleCompare](#texturesamplecompare).

For these, the derivatives help determine the mip levels of texels to be sampled, or in the case of `textureSampleCompare`, sampled and compared against a reference value.

Partial derivatives of _invocation-specified_ values are computed by the built-in functions described in [§ 17.6 Derivative Built-in Functions](#derivative-builtin-functions):

*   [dpdx](#dpdx-builtin), [dpdxCoarse](#dpdxCoarse-builtin), and [dpdxFine](#dpdxFine-builtin) compute partial derivatives along the x axis.

*   [dpdy](#dpdy-builtin), [dpdyCoarse](#dpdyCoarse-builtin), and [dpdyFine](#dpdyFine-builtin) compute partial derivatives along the y axis.

*   [fwidth](#fwidth-builtin), [fwidthCoarse](#fwidthCoarse-builtin), and [fwidthFine](#fwidthFine-builtin) compute the Manhattan metric over the associated x and y partial derivatives.

Because neighbouring invocations collaborate to compute derivatives, these functions should only be invoked in [uniform control flow](#uniform-control-flow) in a fragment shader. For each call to one of these functions, a [derivative_uniformity](#trigger-derivative_uniformity)[diagnostic](#diagnostic) is triggered if [uniformity analysis](#uniformity) cannot prove the call occurs in uniform control flow.

If one of these functions is called in non-uniform control flow, then the result is an [indeterminate value](#indeterminate-value).

Note: Derivatives are an implicit type of [quad operation](#quad-ops). Their use does not require the [subgroups](#extension-subgroups) extension.

#### 15.6.3. Subgroup Operations[](#subgroup-ops)

The [subgroup built-in functions](#subgroup-builtin-functions) allow efficient communication and computation between the invocations in a [subgroup](#subgroup). Subgroup operations are single-instruction multiple-thread (SIMT) operations.

The [active](#subgroups-active) invocations in a subgroup communicate to determine results. Therefore, portability is maximized when these functions are invoked when all invocations are active (i.e. in [uniform control flow](#uniform-control-flow) at the subgroup level).

#### 15.6.4. Quad Operations[](#quad-ops)

The [quad built-in functions](#quad-builtin-functions) operate on a [quad](#quad) of invocations. They are useful for data communication among the [quad](#quad).

The [active](#subgroups-active) invocations in a quad communicate to determine results. Therefore, portability is maximized when these functions are invoked when all invocations are active (i.e. in [uniform control flow](#uniform-control-flow) at the quad level).

### 15.7. Floating Point Evaluation[](#floating-point-evaluation)

WGSL floating point features are based on the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") standard for floating point, but with reduced functionality reflecting the compromises made by GPUs, and with some additional guardrails for portability.

#### 15.7.1. Overview of IEEE-754[](#overview-of-ieee-754)

WGSL floating point types are based on [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") binary floating point types.

An [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") binary floating point type approximates the [extended real](#extended-real) number line as follows:

*   The type has a finite set of values, including distinct categories for:

    *   Positive and negative rational numbers.

        *   Each of these is finite, and is either [normal](#ieee754-normal) or [subnormal](#ieee754-subnormal) as defined below.

    *   [Positive infinity](#positive-infinity) and [negative infinity](#negative-infinity).

    *   NaN values. A NaN, short for "Not a Number", represents the result of an [invalid operation](#ieee754-invalid-operation). IEEE-754 requires both signalling and quiet NaNs, for distinguishing cases related to error reporting. WGSL does not require such error reporting, and may yield [indeterminate values](#indeterminate-value) instead of NaNs. See [§ 15.7.2 Differences from IEEE-754](#differences-from-ieee754).

*   The type supports operations including:

    *   Basic arithmetic such as: addition (`+`), subtraction (`-`), mutiplication (`*`), and division (`/`).

    *   [Scalar conversion](#scalar-conversion) to and from other numeric types.

    *   Built-in functions such as: [max](#max-float-builtin), [sqrt](#sqrt-builtin), [cos](#cos-builtin)

    *   Note: Infinities are ordinary participants in most operations. For example adding +∞ to 5 produces +∞.

*   The type has a bit representation characterized by:

    *   A fixed bit width, where each value’s bit representation has three contiguous bit fields, ordered from most significant bit to least:

        *   A 1-bit sign field.

        *   A fixed-width exponent field.

        *   A fixed-width trailing significand field.

    *   An integer-valued exponent bias related to interpretation of the [exponent field](#ieee754-exponent-field).

The finite range of a floating point type is the [interval](#interval) [low, high], where low is the lowest finite value in the type, and high is the highest finite value in the type.

The IEEE-754 floating point types of interest are:

*   binary16:

    *   [exponent field](#ieee754-exponent-field) width 5

    *   [trailing significand field](#ieee754-trailing-significand-field) width 10

    *   [exponent bias](#ieee754-exponent-bias) 15

    *   [finite range](#finite-range): [−65504, 65504]

*   binary32:

    *   [exponent field](#ieee754-exponent-field) width 8

    *   [trailing significand field](#ieee754-trailing-significand-field) width 23

    *   [exponent bias](#ieee754-exponent-bias) 127

    *   [finite range](#finite-range): [ − (2 − 2−23) × 2 127, (2 − 2−23) × 2 127 ], or approximately [ − 3.4028235 × 10 38, 3.4028235 × 10 38 ].

*   binary64:

    *   [exponent field](#ieee754-exponent-field) width 11

    *   [trailing significand field](#ieee754-trailing-significand-field) width 52

    *   [exponent bias](#ieee754-exponent-bias) 1023

    *   [finite range](#finite-range): [ − (2 − 2−52) × 2 1023, (2 − 2−52) × 2 1023 ], or approximately [ − 1.798 × 10 308, 1.798 × 10 308 ].

The following algorithm maps a bit representation of a floating point value to its corresponding [extended real](#extended-real) value, or NaN:

> **Algorithm:**Floating point interpretation of bits
> **Input**: Bits, a bit representation for a value in a binary floating point type.
> 
> 
> **Output:**F, the floating point value represented by Bits.
> 
> 
> **Procedure:**
> 
> 
> *   Let bias be the [exponent bias](#ieee754-exponent-bias) for the type.
> 
> *   Let tsw be the bit width of the [trailing significand field](#ieee754-trailing-significand-field) for the type.
> 
> *   Partition Bits into the [sign field](#ieee754-sign-field), [exponent field](#ieee754-exponent-field), and the [trailing significand field](#ieee754-trailing-significand-field).
> 
> *   Let Sign, E, and T be the interpretations of those respective fields as unsigned integers.
> 
> *   If the [exponent field](#ieee754-exponent-field) is all 1 bits, then:
> 
> 
>     *   The result F = +∞ when Sign = 0 and T = 0.
> 
>     *   The result F = −∞ when Sign = 1 and T = 0.
> 
>     *   The result F is a [NaN](#nan) when T ≠ 0.
> 
> 
> *   Otherwise, if the [exponent field](#ieee754-exponent-field) is all 0 bits, then:
> 
> 
>     *   The result F = (− 1)Sign × 2−bias × T × 2−tsw+1.
> 
>     *   If T = 0, then the value is a zero.
> 
> 
>         *   Each floating point type has both a positive zero and a negative zero. A negative zero is a zero value with `1` for its [sign](#ieee754-sign-field) bit. Negative zero and positive zero compare as equal. IEEE-754 uses negative zero to indicate certain edge cases unimportant to WGSL.
> 
> 
>     *   If T ≠ 0, then the value F is subnormal. (Denormalized is a synonym for subnormal.)
> 
> 
> *   Otherwise, the [exponent field](#ieee754-exponent-field) is neither all 1 bits, nor all 0 bits:
> 
> 
>     *   The result F = (− 1)Sign × 2(E−bias) × ( 1 + T × 2−tsw).
> 
>     *   The value F is normal.

The domain of a floating point operation is the set of [extended real](#extended-real) number inputs for which the operation is well defined.

*   For example, the domain of the mathematical function √ is the interval [0,+∞]: √ is not well defined for inputs less than zero.

*   When evaluated _inside_ its [domain](#domain), an operation is defined in terms of an infinitely precise [extended real](#extended-real)intermediate result, which is then converted to a floating point result, via [rounding](#rounding).

*   When evaluated _outside_ its [domain](#domain), the default exception handling rules of IEEE-754 require an implementation to generate an [exception](#ieee754-exceptions) and yield a [NaN](#nan) value. In contrast, WGSL does not mandate floating point exceptions, and may instead yield an [indeterminate value](#indeterminate-value). See [§ 15.7.2 Differences from IEEE-754](#differences-from-ieee754).

Rounding maps an [extended real](#extended-real) value x to a value x' in the floating point type. When x is in the floating point type, then rounding maps x to itself: x = x'. Rounding may [overflow](#ieee754-overflow) when x is outside the [finite range](#finite-range) of the type. Otherwise x' is the either the lowest floating point value above x, or the highest floating point value below x; a rounding mode determines which one is chosen.

Generally, an operation with a [NaN](#nan) input will yield a [NaN](#nan) output. Exceptions include:

*   A NaN is never equal to, less than, or greater than any other floating point value. Such comparisons yield false.

IEEE-754 defines five kinds of exceptions:

*   Invalid operation. This occurs when an operation is evaluated on [extended real](#extended-real) inputs outside its [domain](#domain). Such operations yield a NaN. Examples of invalid operations are 0 × +∞, and `sqrt`(−1).

*   Division by zero. This occurs when an operation on finite operands is defined as having an exact infinite result. Examples are 1 ÷ 0, and log(0).

*   Overflow. This occurs when an [intermediate result](#intermediate-result) exceeds the [finite range](#finite-range) of the type. See [§ 15.7.3 Floating Point Rounding and Overflow](#floating-point-rounding-and-overflow).

*   Underflow. This occurs when the [intermediate result](#intermediate-result) or the rounded result is [subnormal](#ieee754-subnormal).

*   Inexact. This occurs when the rounded result is different from the [intermediate result](#intermediate-result), or when overflow occurs.

#### 15.7.2. Differences from IEEE-754[](#differences-from-ieee754)

WGSL follows the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") standard, but with the following differences:

*   No [rounding mode](#ieee754-rounding-mode) is specified. An implementation may round an [intermediate result](#intermediate-result) up or down.

*   When [converting](#scalar-conversion) a floating point value x to an integer type, x is first clamped to the value range of the target type. See [§ 15.7.6 Floating Point Conversion](#floating-point-conversion).

*   No floating point [exceptions](#ieee754-exceptions) are generated.

    *   A floating point operation in WGSL [will](#behavioral-requirements) produce an [intermediate result](#intermediate-result) according to IEEE-754 rules, but exceptions mandated by IEEE-754 will map to different behaviors depending on whether the expression is a [const-expression](#const-expressions), an [override-expression](#override-expressions), or a [runtime expression](#runtime-expression).

    *   Consider an operation on finite operands. The [intermediate result](#intermediate-result) for an operation produces overflow, infinity, or a NaN if and only if IEEE-754 would require the operation to signal an [overflow](#ieee754-overflow), [invalid operation](#ieee754-invalid-operation), or [division by zero](#ieee754-division-by-zero) exception. Behavior is further modified by the [Finite Math Assumption](#finite-math-assumption).

*   Signaling NaNs may not be generated. In an intermediate calculation, any signaling NaN may be converted to a quiet NaN.

*   Finite Math Assumption:

    *   [Overflow](#ieee754-overflow), infinities, and NaNs generated before [shader execution](#shader-execution-start)[will](#behavioral-requirements) generate errors.

        *   [Const-expressions](#const-expressions) and [override-expressions](#override-expressions) over finite values [will](#behavioral-requirements) generate overflow, infinities, and NaNs as [intermediate result](#intermediate-result) values, following IEEE-754 rules.

            *   Note: This rule requires implementations to reliably detect overflow, infinities, and NaNs to within accuracy limits for these kinds of expressions, so that errors can be generated consistently.

        *   A [shader-creation error](#shader-creation-error) results if any [const-expression](#const-expressions) of floating-point type overflows or evaluates to NaN or infinity.

        *   A [pipeline-creation error](#pipeline-creation-error) results if any [override-expression](#override-expressions) of floating-point type overflows or evaluates to NaN or infinity.

    *   Implementations may assume that overflow, infinities, and NaNs are not present during [shader execution](#shader-execution-start).

        *   In such an implementation, if the [intermediate result](#intermediate-result) of evaluating a [runtime expression](#runtime-expression) overflows, or yields an infinity or a NaN, the final result [will](#behavioral-requirements) be an [indeterminate value](#indeterminate-value) of the target type.

        *   Note: This means some functions (e.g. `min` and `max`) may not return the expected result due to optimizations about the presence of NaNs and infinities.

*   Implementations may ignore the [sign field](#ieee754-sign-field) of a floating point zero value. That is, a zero with a positive sign may behave like a zero a with a negative sign, and vice versa.

*   To flush to zero is to replace a [subnormal](#ieee754-subnormal) value for a floating point type with a zero value of that type.

    *   Any inputs or outputs of operations listed in [§ 15.7.4 Floating Point Accuracy](#floating-point-accuracy) may be flushed to zero.

    *   Additionally, [intermediate result](#intermediate-result) values of operations listed in [§ 17.2 Bit Reinterpretation Built-in Functions](#bit-reinterp-builtin-functions), [§ 17.9 Data Packing Built-in Functions](#pack-builtin-functions), or [§ 17.10 Data Unpacking Built-in Functions](#unpack-builtin-functions) may be flushed to zero.

    *   Other operations are required to preserve [subnormal](#ieee754-subnormal) numbers.

*   The accuracy of operations is given in [§ 15.7.4 Floating Point Accuracy](#floating-point-accuracy).

*   Some built-in functions in WGSL have different semantics from the corresponding IEEE-754 operation. Such cases are listed as needed at the definition of the WGSL built-in function.

For example the WGSL [§ 17.5.32 fma](#fma-builtin) function may expand to an ordinary multiply (including a rounding step) and an add (and another rounding step), while the IEEE-754 `fusedMultiplyAdd` operation requires that only final rounding step occurs.

#### 15.7.3. Floating Point Rounding and Overflow[](#floating-point-rounding-and-overflow)

Overflowing computations can round to infinity or to the nearest finite value. The outcome depends on the magnitude of the overflowing [intermediate result](#intermediate-result) value and on whether evaluation occurs during [shader module creation](#shader-module-creation), [pipeline creation](#pipeline-creation), or during [shader execution](#shader-execution-start).

For a floating point type _T_, define _MAX(T)_ as the largest positive finite value of _T_, and 2 _EMAX(T)_ as the largest power of 2 representable by _T_. In particular, EMAX([f32](#f32)) = 127, and EMAX([f16](#f16)) = 15.

Let _X_ be an infinitely precise [intermediate result](#intermediate-result) from a floating point computation. The final value of the expression is determined in two stages, via [intermediate result](#intermediate-result) values _X'_ and _X''_ as follows:

From _X_, compute _X'_ in _T_ by rounding:

*   If _X_ is in the [finite range](#finite-range) of _T_ then _X'_ is the result of rounding _X_ up or down.

*   If _X_ is NaN, then _X'_ is NaN.

*   If _MAX(T)_<_X_< 2 _EMAX(T)+1_, then either rounding direction is used: _X'_ is _MAX(T)_ or +∞.

*   If 2 _EMAX(T)+1_ ≤ _X_, then _X'_ = +∞.

    *   Note: This clause matches the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") rule.

*   If −_MAX(T)_>_X_> −2 _EMAX(T)+1_, then either rounding direction is used: _X'_ is −_MAX(T)_ or −∞.

*   If −2 _EMAX(T)+1_ ≥ _X_, then _X'_ = −∞.

    *   Note: This clause matches the IEEE-754 rule.

From _X'_, compute the final value of the expression, _X''_, or detect a program error:

*   If _X'_ is an infinity or NaN, then by the [Finite Math Assumption](#finite-math-assumption):

    *   If the expression is a [const-expression](#const-expressions), generate a [shader-creation error](#shader-creation-error).

    *   If the expression is a [override-expression](#override-expressions), generate a [pipeline-creation error](#pipeline-creation-error).

    *   Otherwise the expression is a [runtime expression](#runtime-expression) and _X''_ is an [indeterminate value](#indeterminate-value).

*   Otherwise _X''_ = _X'_.

#### 15.7.4. Floating Point Accuracy[](#floating-point-accuracy)

Let x be the exact real-valued or infinite result of an operation when computed with unbounded precision. The correctly rounded result of the operation for floating point type T is:

*   x, when x is in T,

*   Otherwise:

    *   the smallest value in T greater than x, or

    *   the largest value in T less than x.

That is, the result may be [rounded](#rounding) up or down: WGSL does not specify a [rounding mode](#ieee754-rounding-mode).

Note: Floating point types include positive and negative infinity, so the correctly rounded result may be finite or infinite.

Note: The result of an operation when computed with unbounded precision may require precision which exceeds that of a double. An example of such a case is in `x - y` where `x=1.0`and `y=1.17e-38` (the smallest positive normal single precision float). These numbers have exponents are that are `126` units apart. The [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary64](#ieee754-binary64)(double precision) format only has 52 bits in its significand, so in doing the subtraction, all the significant bits of `y` are lost. Depending on rounding modes, for this and many other cases where `y` is small but non-zero, the WGSL expression `x - y` may yield the same value as `x`. Note that [[ECMASCRIPT]](https://www.w3.org/TR/WGSL/#biblio-ecmascript "ECMAScript Language Specification") uses the equivalent of the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") roundTiesToEven rounding mode.

The units in the last place, ULP, for a floating point number `x` is defined as follows [[Muller2005]](https://www.w3.org/TR/WGSL/#biblio-muller2005 "On the definition of ulp(x)"):

*   If `x` is in the [finite range](#finite-range) of the floating point type, then ULP(x) is the minimum distance between two non-equal, finite floating point numbers `a` and `b` such that `a` ≤ `x` ≤ `b` (i.e. `ulp(x) =     min``a,b``|b - a|`).

*   Otherwise, ULP(x) is `|b - a|` where `b` and `a` are the largest and second-largest representable finite floating point values.

The accuracy of an operation is provided among five possibilities:

*   Correct result (for non-floating point result values).

*   [Correctly rounded](#correctly-rounded).

*   An absolute error bound.

*   A relative error bound expressed as [ULP](#ulp).

*   An expression that the accuracy is inherited from. That is, the accuracy of the operation is defined as the accuracy of evaluating the given WGSL expression. The given expression is only one valid implementation of the function.

When evaluating the inherited-from expression, subexpression evaluations are subject to other rules for floating-point evaluation, including those regarding [rounding](#rounding), [overflow](#ieee754-overflow), [reassociation](#reassociation), [fusion](#reassociation-and-fusion), and [flush-to-zero](#flush-to-zero).

A WebGPU implementation may implement the operation differently, with better accuracy or with greater tolerance for extreme inputs.

When the accuracy for an operation is specified over an input range, the accuracy is undefined for input values outside that range.

If an allowed result is outside the [finite range](#finite-range) of the result type, then the rules in [§ 15.7.3 Floating Point Rounding and Overflow](#floating-point-rounding-and-overflow) apply.

##### 15.7.4.1. Accuracy of Concrete Floating Point Expressions[](#concrete-float-accuracy)

Accuracy of concrete floating point operations
| Expression | Accuracy for f32 | Accuracy for f16 | `x + y` | Correctly rounded | | `x - y` | Correctly rounded | | `x * y` | Correctly rounded | | `x / y` | 2.5 ULP for `|y|` in the range [2-126, 2 126] | 2.5 ULP for `|y|` in the range [2-14, 2 14] | | `x % y` | Inherited from `x - y * trunc(x/y)` | | `-x` | Correctly rounded | | `x == y` | Correct result | | `x != y` | Correct result | | `x < y` | Correct result | | `x <= y` | Correct result | | `x > y` | Correct result | | `x >= y` | Correct result | |
| --- | --- | --- |

Accuracy of concrete floating point built-in functions
| Built-in Function | Accuracy for f32 | Accuracy for f16 | `abs(x)` | Correctly rounded | | `acos(x)` | The worse of: * Absolute error 6.77×10-5 * Inherited from `atan2(sqrt(1.0 - x * x), x)` | The worse of: * Absolute error 3.91×10-3 * Inherited from `atan2(sqrt(1.0 - x * x), x)` | | `acosh(x)` | Inherited from `log(x + sqrt(x * x - 1.0))` | | `asin(x)` | The worse of: * Absolute error 6.81×10-5 * Inherited from `atan2(x, sqrt(1.0 - x * x))` | The worse of: * Absolute error 3.91×10-3 * Inherited from `atan2(x, sqrt(1.0 - x * x))` | | `asinh(x)` | Inherited from `log(x + sqrt(x * x + 1.0))` | | `atan(x)` | 4096 ULP | 5 ULP | | `atan2(y, x)` | 4096 ULP for `|x|` in the range [2-126, 2 126], and `y` is finite and normal | 5 ULP for `|x|` in the range [2-14, 2 14], and `y` is finite and normal | | `atanh(x)` | Inherited from `log( (1.0 + x) / (1.0 - x) ) * 0.5` | | `ceil(x)` | Correctly rounded | | `clamp(x,low,high)` | Correctly rounded. The infinitely precise result is computed as either `min(max(x,low),high)`, or with a median-of-3-values formulation. These may differ when `low > high`. If `x` and either `low` or `high` are [subnormal](#ieee754-subnormal), the result may be any of the [subnormal](#ieee754-subnormal) values. This follows from the possible results from the `min` and `max` functions on [subnormal](#ieee754-subnormal) inputs. | | `cos(x)` | Absolute error at most 2-11 when `x` is in the interval [-π, π] | Absolute error at most 2-7 when `x` is in the interval [-π, π] | | `cosh(x)` | Inherited from `(exp(x) + exp(-x)) * 0.5` | | `cross(x, x)` | Inherited from `(x[i] * y[j] - x[j] * y[i])` where `i` ≠ `j` | | `degrees(x)` | Inherited from `x * 57.295779513082322865` | | `determinant(m:mat2x2<T>)` `determinant(m:mat3x3<T>)` `determinant(m:mat4x4<T>)` | Infinite ULP. Note:WebGPU implementations should provide a pragmatically useful determinant function. In ideal math, determinants are computed with add, subtract, and multiply operations. However, GPUs use floating point math, and GPU implementations of determinant favour speed and simplicity over robustness against overflow and error. For example, the naive computation of even a 2x2 determinant (`m[0][0] * m[1][1] - m[1][0] * m[0][1]`) fails to guard against catastrophic cancellation. Providing tighter error bounds for 2x2 determinants is the subject of relatively recent research [[Jeannerod2013]](https://www.w3.org/TR/WGSL/#biblio-jeannerod2013 "Further Analysis of Kahan's Algorithm for the Accurate Computation of 2x2 Determinants"). The challenges compound quickly as matrix sizes increase. The lack of a finite error bound for determinants in WGSL reflects the same lack in underlying implementations. | | `distance(x, y)` | Inherited from `length(x - y)` | | `dot(x, y)` | Inherited from sum of `x[i] * y[i]` | | `dpdx(x)` `dpdxCoarse(x)` `dpdxFine(x)` `dpdy(x)` `dpdyCoarse(x)` `dpdyFine(x)` `fwidth(x)` `fwidthCoarse(x)` `fwidthFine(x)` | Infinite ULP. Note:WebGPU implementations should provide a pragmatically useful derivative functions. Derivatives are implemented as differences (or difference of absolutes in the case of `fwidth`) between values in different invocations on GPUs. The lack of a finite error bound for derivatives in WGSL reflects the same lack in underlying implementations. | | `exp(x)` | `3 + 2 * |x|` ULP | `1 + 2 * |x|` ULP | | `exp2(x)` | `3 + 2 * |x|` ULP | `1 + 2 * |x|` ULP | | `faceForward(x, y, z)` | Inherited from `select(-x, x, dot(z, y) < 0.0)` | | `floor(x)` | Correctly rounded | | `fma(x, y, z)` | Inherited from `x * y + z` | | `fract(x)` | Inherited from `x - floor(x)` | | `frexp(x)` | Correctly rounded, when `x` is zero or normal. | | `inverseSqrt(x)` | 2 ULP | | `ldexp(x, y)` | Correctly rounded | | `length(x)` | Inherited from `sqrt(dot(x, x))` in the vector case, and `sqrt(x*x)` in the scalar case. | | `log(x)` | Absolute error at most 2-21 when `x` is in the interval [0.5, 2.0]. 3 ULP when `x` is outside the interval [0.5, 2.0]. | Absolute error at most 2-7 when `x` is in the interval [0.5, 2.0]. 3 ULP when `x` is outside the interval [0.5, 2.0]. | | `log2(x)` | Absolute error at most 2-21 when `x` is in the interval [0.5, 2.0]. 3 ULP when `x` is outside the interval [0.5, 2.0]. | Absolute error at most 2-7 when `x` is in the interval [0.5, 2.0]. 3 ULP when `x` is outside the interval [0.5, 2.0]. | | `max(x, y)` | Correctly rounded If both `x` and `y` are [subnormal](#ieee754-subnormal), the result may be either input. | | `min(x, y)` | Correctly rounded. If both `x` and `y` are [subnormal](#ieee754-subnormal), the result may be either input. | | `mix(x, y, z)` | Inherited from `x * (1.0 - z) + y * z` | | `modf(x)` | Correctly rounded | | `normalize(x)` | Inherited from `x / length(x)` | | `pack4x8snorm(x)` | Correctly rounded [intermediate result](#intermediate-result) value. Correct result. | | `pack4x8unorm(x)` | Correctly rounded [intermediate result](#intermediate-result) value. Correct result. | | `pack2x16snorm(x)` | Correctly rounded [intermediate result](#intermediate-result) value. Correct result. | | `pack2x16unorm(x)` | Correctly rounded [intermediate result](#intermediate-result) value. Correct result. | | `pack2x16float(x)` | Correctly rounded [intermediate result](#intermediate-result) value. Correct result. | | `pow(x, y)` | Inherited from `exp2(y * log2(x))` | | `quantizeToF16(x)` | Correctly rounded | | `radians(x)` | Inherited from `x * 0.017453292519943295474` | | `reflect(x, y)` | Inherited from `x - 2.0 * dot(x, y) * y` | | `refract(x, y, z)` | Inherited from `z * x - (z * dot(y, x) + sqrt(k)) * y`, where `k = 1.0 - z * z * (1.0 - dot(y, x) * dot(y, x))` If `k < 0.0` the result is precisely 0.0 | | `round(x)` | Correctly rounded | | `sign(x)` | Correctly rounded | | `sin(x)` | Absolute error at most 2-11 when `x` is in the interval [-π, π] | Absolute error at most 2-7 when `x` is in the interval [-π, π] | | `sinh(x)` | Inherited from `(exp(x) - exp(-x)) * 0.5` | | `saturate(x)` | Correctly rounded | | `smoothstep(edge0, edge1, x)` | Inherited from `t * t * (3.0 - 2.0 * t)`, where `t = clamp((x - edge0) / (edge1 - edge0), 0.0, 1.0)` | | `sqrt(x)` | Inherited from `1.0 / inverseSqrt(x)` | | `step(edge, x)` | Correctly rounded | | `tan(x)` | Inherited from `sin(x) / cos(x)` | | `tanh(x)` | The worse of: * Absolute error 1.0×10-5 * Inherited from `sinh(x) / cosh(x)` | | `transpose(x)` | Correctly rounded | | `trunc(x)` | Correctly rounded | | `unpack4x8snorm(x)` | 3 ULP | N/A | | `unpack4x8unorm(x)` | 3 ULP | N/A | | `unpack2x16snorm(x)` | 3 ULP | N/A | | `unpack2x16unorm(x)` | 3 ULP | N/A | | `unpack2x16float(x)` | Correctly rounded | N/A | | `subgroupBroadcast(x, i)` | Correctly rounded | | `subgroupBroadcastFirst(x)` | Correctly rounded | | `subgroupAdd(x)` | Inherited from sum of x for all [active](#subgroups-active) invocations in the subgroup | | `subgroupExclusiveAdd(x)` | Inherited from the sum of x for all [active](#subgroups-active) invocations in the subgroup whose [subgroup invocation ID](#subgroup-invocation-id)s are less than the current invocation’s ID. | | `subgroupInclusiveAdd(x)` | Inherited from the sum of x for all [active](#subgroups-active) invocations in the subgroup whose [subgroup invocation ID](#subgroup-invocation-id)s are less than or equal to current invocation’s ID. | | `subgroupMul(x)` | Inherited from the product of x for all [active](#subgroups-active) invocations in the subgroup | | `subgroupExclusiveMul(x)` | Inherited from the product of x i for all [active](#subgroups-active) invocations in the subgroup whose [subgroup invocation ID](#subgroup-invocation-id) is less than ID of the i’th invocation | | `subgroupInclusiveMul(x)` | Inherited from the product of x i for all [active](#subgroups-active) invocations in the subgroup whose [subgroup invocation ID](#subgroup-invocation-id) is less than or equal to ID of the i’th invocation | | `subgroupMax(x)` | Inherited from max(x) for all [active](#subgroups-active) invocations in the subgroup | | `subgroupMin(x)` | Inherited from min(x) for all [active](#subgroups-active) invocations in the subgroup | | `subgroupShuffle(x, id)` | Correctly rounded | | `subgroupShuffleDown(x, delta)` | Correctly rounded | | `subgroupShuffleUp(x, delta)` | Correctly rounded | | `subgroupShuffleXor(x, mask)` | Correctly rounded | | `quadBroadcast(x, id)` | Correctly rounded | | `quadSwapDiagonal(x)` | Correctly rounded | | `quadSwapX(x)` | Correctly rounded | | `quadSwapY(x)` | Correctly rounded | |
| --- | --- | --- |

##### 15.7.4.2. Accuracy of AbstractFloat Expressions[](#abstract-float-accuracy)

The accuracy of an [AbstractFloat](#abstractfloat) operation is as follows:

*   A correct result is required when the corresponding [f32](#f32) operation requires a correct result.

*   A [correctly rounded](#correctly-rounded) result is required when the corresponding [f32](#f32) operation requires a correctly rounded result.

*   `fract(x)`’s error is inherited from `x - floor(x)`, where the intermediate calculations are performed as [AbstractFloat](#abstractfloat) operations.

*   Otherwise, the error of the corresponding [f32](#f32) operation is an absolute error, a relative error, an error inherited from a potential implementation, or a combination of these. In this case the error of the [AbstractFloat](#abstractfloat) is unbounded.

    *   However, the error of the [AbstractFloat](#abstractfloat) operation _should_ be at most the error of the corresponding operation in [f32](#f32), in absolute terms.

    *   This recommendation is meant to avoid surprises: the accuracy of an expression should not be _reduced_ when changing its type from f32 to AbstractFloat.

    *   The operation may be evaluated in a WebAssembly [[WASM-CORE-2]](https://www.w3.org/TR/WGSL/#biblio-wasm-core-2 "WebAssembly Core Specification") or an ECMAScript [[ECMASCRIPT]](https://www.w3.org/TR/WGSL/#biblio-ecmascript "ECMAScript Language Specification") environment, and those specifications do not specify error bounds on many of the corresponding numeric computations. For example, ECMAScript specifies many floating point operations as being [implementation-approximated](https://tc39.es/ecma262/multipage/overview.html#sec-terms-and-definitions-implementation-approximated). Implementations are encouraged to strive to approximate the ideal, but no strict requirement is specified.

Note:A given absolute error bound, when quantified as ULP, depends critically on the underlying floating point type.

The [ULP](#ulp) for an [AbstractFloat](#abstractfloat) value assumes AbstractFloat is identical to the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary64](#ieee754-binary64) type.

One [ULP](#ulp) for an f32 value is 2 29 times larger than 1 ULP for an IEEE-754 binary64 value, since the significand in the binary64 format is 29 bits longer than the significand in the f32 type.

For example, suppose the true result value of an operation is x, but it is computed as x'. If its error x-x' is 3 ULP in f32, then the same absolute error, x-x', is 3·2 29 ULP in AbstractFloat.

#### 15.7.5. Reassociation and Fusion[](#reassociation-and-fusion)

Reassociation is the reordering of operations in an expression such that the answer is the same if computed exactly. For example:

*   `(a + b) + c` reassociates to `a + (b + c)`

*   `(a - b) + c` reassociates to `(a + c) - b`

*   `(a * b) / c` reassociates to `(a / c) * b`

However, the result may not be the same when computed in floating point. The reassociated result may be inaccurate due to approximation, or may trigger an overflow or NaN when computing [intermediate results](#intermediate-result).

An implementation may reassociate operations.

An implementation may fuse operations if the transformed expression is at least as accurate as the original formulation. For example, some fused multiply-add implementations can be more accurate than performing a multiply followed by an addition.

#### 15.7.6. Floating Point Conversion[](#floating-point-conversion)

This section describes the details of a [scalar conversion](#scalar-conversion) where either the source or destination is a floating point type.

In this section, a floating point type may be any of:

*   The [f32](#f32), [f16](#f16), and [AbstractFloat](#abstractfloat) types in WGSL.

*   A hypothetical type corresponding to a binary format defined by the [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") floating point standard.

Note: Recall that the [f32](#f32) WGSL type corresponds to the IEEE-754 [binary32](#ieee754-binary32) format, and the [f16](#f16) WGSL type corresponds to the IEEE-754 [binary16](#ieee754-binary16) format.

The scalar floating point to integral conversion algorithm is:

> To convert a floating point scalar value Xto an [integer scalar](#integer-scalar)type T: 
> *   If X is a [NaN](#nan), the result is an [indeterminate value](#indeterminate-value) in T.
> 
> *   If X is exactly representable in the target type T, then the result is that value.
> 
> *   Otherwise, the result is the value in T closest to [truncate](#truncate)(X) and also exactly representable in the original floating point type.

Note: In other words, for non-NaN cases, floating point to integer conversion clamps the value to be within the range of the target type, then rounds toward zero. This clamping requirement is one place where WGSL mandates a meaningful result, but which would yield undefined behavior in C and C++, and where [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic") mandates an invalid operation exception and a NaN result.

Note: For example:

*   3.9f converted to [u32](#u32) is 3u

*   -1f converted to [u32](#u32) is 0u

*   1e20f converted to [u32](#u32) is the largest float value representable in u32, 4294967040u

*   Note this is smaller than the maximum u32 value 4294967295u

*   -3.9f converted to [i32](#i32) is -3i

*   1e20f converted to [i32](#i32) is the maximum i32 value, 2147483520i

*   Note this is smaller than the maximum i32 value 2147483647i

*   -1e20f converted to [i32](#i32) is the minimum i32 value, i32(-2147483648)

The numeric scalar conversion to floating point algorithm is:

> **Algorithm:**Numeric [scalar conversion](#scalar-conversion)to floating point 
> **Inputs:**
> 
> 
> *   X, a [numeric scalar](#numeric-scalar) value of type S
> 
> *   T, a destination floating point type.
> 
> 
> 
> **Output:**XOut, the result of converting X to type T, or generate an error.
> 
> 
> **Procedure:**
> 
> 
> *   If X is a NaN for the source type S, then XOut is a NaN in type T.
> 
> *   If X is exactly representable in the destination type T, then XOut is the value in T equal to X.
> 
> 
>     *   Additionally, if X is zero and of [integer scalar](#integer-scalar) type, then XOut has a zero [sign bit](#ieee754-sign-field).
> 
> 
> *   Otherwise, X is not exactly representable in T:
> 
> 
>     *   If X lies between two adjacent finite values in T, then XOut is one of those two values. WGSL does not specify whether the higher or lower representable value is chosen, and different instances of such a conversion may choose differently.
> 
>     *   Otherwise, X lies outside the [finite range](#finite-range) of the destination type:
> 
> 
>         *   A [shader-creation error](#shader-creation-error) results if the expression for X is a [const-expression](#const-expressions).
> 
>         *   A [pipeline-creation error](#pipeline-creation-error) results if the expression for X is an [override-expression](#override-expressions).
> 
>         *   Otherwise the conversion proceeds as follows:
> 
> 
>             1.   Set X' to the original value X.
> 
>             2.   If source type S is a floating point type with more significand bits than the destination type T, the extra significand bits of the source value X _may_ be discarded (i.e. treated as if they are 0). Update X' accordingly.
> 
>             3.   If X' is the most-positive or most-negative finite value of the destination type T, then set XOut = X'.
> 
>             4.   Otherwise, set XOut to the infinity value of destination type T, with the same sign as X'.

NOTE: An integer value may lie between two adjacent representable floating point values. In particular, the [f32](#f32) type uses 23 explicit fractional bits. Additionally, when the floating point value is in the normal range (the exponent is neither extreme value), then the significand is the set of fractional bits together with an extra 1-bit at the most significant position at bit position 23. Then, for example, integers 2 28 and 1+2 28 both map to the same floating point value: the difference in the least significant 1 bit is not representable by the floating point format. This kind of collision occurs for pairs of adjacent integers with a magnitude of at least 2 25.

Note: The original value is always within range of the destination type when the original type is one of [i32](#i32) or [u32](#u32) and the destination type is [f32](#f32).

Note: The original value is always within range of the destination type when the source type is a floating point type with fewer exponent and significand bits than the target floating point type.

#### 15.7.7. Domains of Floating Point Expressions and Built-in Functions[](#domains-of-floating-point-expressions-and-builtins)

Previous sections describe the expected behavior when a floating point expression is evaluated outside its [domain](#domain).

Sections [§ 8.8 Arithmetic Expressions](#arithmetic-expr) and [§ 17.5 Numeric Built-in Functions](#numeric-builtin-functions) define the [domains](#domain) for floating point expressions and built-in functions, respectively. If no restriction is listed for a given operation, then the domain is total: the domain includes all finite and infinite inputs. Otherwise an explicit domain is listed.

In many cases where a WGSL operation corresponds to an operation defined by [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic"), they will have the same domain. For example the both the WGSL and IEEE-754 `acos` operations have a domain of [−1,1].

For a [component-wise](#component-wise) WGSL operation with an explicitly listed domain, only the scalar case is described. The vector case is inferred from the component-wise semantics.

Some WGSL operations may be implemented in terms of other WGSL expressions. Section [§ 15.7.4 Floating Point Accuracy](#floating-point-accuracy) lists these as having [inherited from](#inherited-from) accuracy. When listing the domain for one of these operations, either:

*   The domain is explicitly described, or

*   The domain is stated as implied from linear terms, meaning the domain is derived by:

    *   Assuming the original operation was replaced by the "inherited from" expression, which is a combination of floating point addition, subtraction, and mulitiplication operations.

    *   Applying and combining the domain restrictions for those remaining operations over the given parameters.

For example: The `dot(a,b)` function over 2-element vectors a and b has its accuracy [inherited from](#inherited-from) the expression a[0] * b[0] + a[1] * b[1]. This uses two floating point multiplications, and one floating point addition.

*   Floating point multiplication is well defined over the extended reals except when one operand is zero and the other is infinite.

*   Floating point addition is well defined except when the two operands are infinites of opposite sign.

*   Therefore, the domain is all pairs of extended real two-element vectors a and b except:

    *   Implied from the multiplications:

        *   a[i] is zero and b[i] is infinite.

        *   a[i] is infinite and b[i] is zero.

    *   Implied from the addition:

        *   a[0] × b[0] is +∞ and a[1] × b[1] is +∞

        *   a[0] × b[0] is −∞ and a[1] × b[1] is −∞

## 16. Keyword and Token Summary[](#grammar)

### 16.1. Keyword Summary[](#keyword-summary)

*   `alias`

*   `break`

*   `case`

*   `const`

*   `const_assert`

*   `continue`

*   `continuing`

*   `default`

*   `diagnostic`

*   `discard`

*   `else`

*   `enable`

*   `false`

*   `fn`

*   `for`

*   `if`

*   `let`

*   `loop`

*   `override`

*   `requires`

*   `return`

*   `struct`

*   `switch`

*   `true`

*   `var`

*   `while`

### 16.2. Reserved Words[](#reserved-words)

A reserved word is a [token](#token) which is reserved for future use. A WGSL module [must not](#shader-creation-error) contain a reserved word.

The following are reserved words:

_reserved :

| `'NULL'`

| `'Self'`

| `'abstract'`

| `'active'`

| `'alignas'`

| `'alignof'`

| `'as'`

| `'asm'`

| `'asm_fragment'`

| `'async'`

| `'attribute'`

| `'auto'`

| `'await'`

| `'become'`

| `'cast'`

| `'catch'`

| `'class'`

| `'co_await'`

| `'co_return'`

| `'co_yield'`

| `'coherent'`

| `'column_major'`

| `'common'`

| `'compile'`

| `'compile_fragment'`

| `'concept'`

| `'const_cast'`

| `'consteval'`

| `'constexpr'`

| `'constinit'`

| `'crate'`

| `'debugger'`

| `'decltype'`

| `'delete'`

| `'demote'`

| `'demote_to_helper'`

| `'do'`

| `'dynamic_cast'`

| `'enum'`

| `'explicit'`

| `'export'`

| `'extends'`

| `'extern'`

| `'external'`

| `'fallthrough'`

| `'filter'`

| `'final'`

| `'finally'`

| `'friend'`

| `'from'`

| `'fxgroup'`

| `'get'`

| `'goto'`

| `'groupshared'`

| `'highp'`

| `'impl'`

| `'implements'`

| `'import'`

| `'inline'`

| `'instanceof'`

| `'interface'`

| `'layout'`

| `'lowp'`

| `'macro'`

| `'macro_rules'`

| `'match'`

| `'mediump'`

| `'meta'`

| `'mod'`

| `'module'`

| `'move'`

| `'mut'`

| `'mutable'`

| `'namespace'`

| `'new'`

| `'nil'`

| `'noexcept'`

| `'noinline'`

| `'nointerpolation'`

| `'non_coherent'`

| `'noncoherent'`

| `'noperspective'`

| `'null'`

| `'nullptr'`

| `'of'`

| `'operator'`

| `'package'`

| `'packoffset'`

| `'partition'`

| `'pass'`

| `'patch'`

| `'pixelfragment'`

| `'precise'`

| `'precision'`

| `'premerge'`

| `'priv'`

| `'protected'`

| `'pub'`

| `'public'`

| `'readonly'`

| `'ref'`

| `'regardless'`

| `'register'`

| `'reinterpret_cast'`

| `'require'`

| `'resource'`

| `'restrict'`

| `'self'`

| `'set'`

| `'shared'`

| `'sizeof'`

| `'smooth'`

| `'snorm'`

| `'static'`

| `'static_assert'`

| `'static_cast'`

| `'std'`

| `'subroutine'`

| `'super'`

| `'target'`

| `'template'`

| `'this'`

| `'thread_local'`

| `'throw'`

| `'trait'`

| `'try'`

| `'type'`

| `'typedef'`

| `'typeid'`

| `'typename'`

| `'typeof'`

| `'union'`

| `'unless'`

| `'unorm'`

| `'unsafe'`

| `'unsized'`

| `'use'`

| `'using'`

| `'varying'`

| `'virtual'`

| `'volatile'`

| `'wgsl'`

| `'where'`

| `'with'`

| `'writeonly'`

| `'yield'`

### 16.3. Syntactic Tokens[](#syntactic-tokens)

A syntactic token is a sequence of special code points, used:

*   to spell an expression operator, or

*   as punctuation: to group, sequence, or separate other grammar elements.

The [syntactic tokens](#syntactic-token) are:

*   `'&'` (Code point: `U+0026`)

*   `'&&'` (Code points: `U+0026``U+0026`)

*   `'->'` (Code points: `U+002D``U+003E`)

*   `'@'` (Code point: `U+0040`)

*   `'/'` (Code point: `U+002F`)

*   `'!'` (Code point: `U+0021`)

*   `'['` (Code point: `U+005B`)

*   `']'` (Code point: `U+005D`)

*   `'{'` (Code point: `U+007B`)

*   `'}'` (Code point: `U+007D`)

*   `':'` (Code point: `U+003A`)

*   `','` (Code point: `U+002C`)

*   `'='` (Code point: `U+003D`)

*   `'=='` (Code points: `U+003D``U+003D`)

*   `'!='` (Code points: `U+0021``U+003D`)

*   `'>'` (Code point: `U+003E`) (also `_greater_than` for template disambiguation)

*   `'>='` (Code points: `U+003E``U+003D`) (also `_greater_than_equal` for template disambiguation)

*   `'>>'` (Code point: `U+003E``U+003E`) (also `_shift_right` for template disambiguation)

*   `'<'` (Code point: `U+003C`) (also `_less_than` for template disambiguation)

*   `'<='` (Code points: `U+003C``U+003D`) (also `_less_than_equal` for template disambiguation)

*   `'<<'` (Code points: `U+003C``U+003C`) (also `_shift_left` for template disambiguation)

*   `'%'` (Code point: `U+0025`)

*   `'-'` (Code point: `U+002D`)

*   `'--'` (Code points: `U+002D``U+002D`)

*   `'.'` (Code point: `U+002E`)

*   `'+'` (Code point: `U+002B`)

*   `'++'` (Code points: `U+002B``U+002B`)

*   `'|'` (Code point: `U+007C`)

*   `'||'` (Code points: `U+007C``U+007C`)

*   `'('` (Code point: `U+0028`)

*   `')'` (Code point: `U+0029`)

*   `';'` (Code point: `U+003B`)

*   `'*'` (Code point: `U+002A`)

*   `'~'` (Code point: `U+007E`)

*   `'_'` (Code point: `U+005F`)

*   `'^'` (Code point: `U+005E`)

*   `'+='` (Code points: `U+002B``U+003D`)

*   `'-='` (Code points: `U+002D``U+003D`)

*   `'*='` (Code points: `U+002A``U+003D`)

*   `'/='` (Code points: `U+002F``U+003D`)

*   `'%='` (Code points: `U+0025``U+003D`)

*   `'&='` (Code points: `U+0026``U+003D`)

*   `'|='` (Code points: `U+007C``U+003D`)

*   `'^='` (Code points: `U+005E``U+003D`)

*   `'>>='` (Code point: `U+003E``U+003E``U+003D`) (also `_shift_right_assign` for template disambiguation)

*   `'<<='` (Code points: `U+003C``U+003C``U+003D`) (also `_shift_left_assign` for template disambiguation)

*   `_template_args_end`

    *   Text: `'>'` (Code point: `U+003E`)

    *   This token is textually the same as the [greater_than](#syntax_sym-greater_than) syntactic token.

    *   It is generated by template list disambiguation, and is used as the last token in a template list.

*   `_template_args_start`

    *   Text: `'<'` (Code point: `U+003C`)

    *   This token is textually the same as the [less_than](#syntax_sym-less_than) syntactic token.

    *   It is generated by template list disambiguation, and is used as the first token in a template list.

*   `_disambiguate_template`

    *   Text: None

    *   In the standard parser formulation given in [§ 3.1 Parsing](#parsing), this token serves no purpose, and is effectively ignored. To ignore it, the scanner always succeeds in matching it to an empty string.

    *   In the alternative parsing formulation given in [§ 3.1 Parsing](#parsing), this token triggers the scanner to perform template list discovery in an on-demand fashion, as described in that section.

## 17. Built-in Functions[](#builtin-functions)

Certain functions are [predeclared](#predeclared), provided by the implementation, and therefore always available for use in a WGSL module. These are called built-in functions.

A built-in function is a family of functions, all with the same name, but distinguished by the number, order, and types of their [formal parameters](#formal-parameter). Each of these distinct function variations is an [overload](#overload).

Note: Each [user-defined function](#user-defined-function) only has one [overload](#overload).

Each [overload](#overload) is described below via:

*   Type parameterizations, if any.

*   The built-in function name, a parenthesized list of [formal parameters](#formal-parameter), and optionally a [return type](#return-type).

*   The behavior of this overload of the function.

When calling a built-in function, all arguments to the function are evaluated before function evaluation begins. See [§ 11.2 Function Calls](#function-calls).

### 17.1. Constructor Built-in Functions[](#constructor-builtin-function)

A value constructor built-in function explicitly creates a value of a given type.

WGSL provides value constructors for all [predeclared](#predeclared) types and all [constructible](#constructible)[structure](#structure) types. Such a constructor built-in function has the same spelling as the type, or a [type alias](#type-alias) for the type. Wherever such a built-in function is used, the [identifier](#identifier)[must](#shader-creation-error) be [in scope](#in-scope) of the type or the type alias, and the [identifier](#identifier)[must not](#shader-creation-error)[resolve](#resolves) to another declaration.

Note: The structure types returned by [frexp](#frexp-builtin), [modf](#modf-builtin), and [atomicCompareExchangeWeak](#atomic-rmw) cannot be written in WGSL modules.

Note: A value declaration of the type needs to be valid at that statement of the WGSL text.

WGSL provides two kinds of value constructors:

*   [zero value constructors](#zero-value-builtin-function)

*   [value constructors](#value-constructor-builtin-function) (which also provide conversion)

#### 17.1.1. Zero Value Built-in Functions[](#zero-value-builtin-function)

Each [concrete](#type-concrete), [constructible](#constructible)_T_ has a unique zero value, and a corresponding built-in function written in WGSL as the type followed by an empty pair of parentheses: _T_`()`. [Abstract numeric types](#abstract-numeric-types) also have zero values, but there are no built-in functions to access them.

The zero values are as follows:

*   `bool()` is `false`

*   `i32()` is 0i

*   `u32()` is 0u

*   `f32()` is 0.0f

*   `f16()` is 0.0h

*   The zero value for an _N_-component vector of type _T_ is the _N_-component vector of the zero value for _T_.

*   The zero value for an _C_-column _R_-row matrix of type _T_ is the matrix of those dimensions filled with the zero value for _T_.

*   The zero value for a [constructible](#constructible)_N_-element array with element type _E_ is an array of _N_ elements of the zero value for _E_.

*   The zero value for a [constructible](#constructible) structure type _S_ is the structure value _S_ with zero-valued members.

*   The zero value of an [AbstractInt](#abstractint) is 0.

*   The zero value of an [AbstractFloat](#abstractfloat) is 0.0.

Note: WGSL does not have zero built-in functions for [atomic types](#atomic-type), [runtime-sized](#runtime-sized) arrays, buffers, or other types that are not [constructible](#constructible).

Overload@const @must_use fn T() -> T
Parameterization`T` is a [concrete](#type-concrete)[constructible](#constructible) type.
Description Construct [zero value](#zero-value) of the type `T`.

Note: Zero-filled vectors of AbstractInt can be written as `vec2()`, `vec3()`, and `vec4()`.

EXAMPLE: Zero-valued vectors

vec2<f32>()                 // The zero-valued vector of two f32 components.
vec2<f32>(0.0, 0.0)         // The same value, written explicitly.

vec3<i32>()                 // The zero-valued vector of three i32 components.
vec3<i32>(0, 0, 0)          // The same value, written explicitly.

EXAMPLE: Zero-valued arrays

array<bool, 2>()               // The zero-valued array of two booleans.
array<bool, 2>(false, false)   // The same value, written explicitly.

EXAMPLE: Zero-valued structures

struct Student {
  grade: i32,
  GPA: f32,
  attendance: array<bool,4>
}

fn func() {
  var s: Student;

  // The zero value for Student
  s = Student();

  // The same value, written explicitly.
  s = Student(0, 0.0, array<bool,4>(false, false, false, false));

  // The same value, written with zero-valued members.
  s = Student(i32(), f32(), array<bool,4>());
}

#### 17.1.2. Value Constructor Built-in Functions[](#value-constructor-builtin-function)

The built-in functions defined in following subsections create a [constructible](#constructible) value by:

*   Copying an existing value of the same type (i.e. the identity function), or

*   Creating a composite value from an explicit list of components.

*   Converting from another value type.

The vector and matrix forms construct vector and matrix values from various combinations of components and subvectors with matching component types. There are [overloads](#overload) for constructing vectors and matrices that specify the dimensions of the target type without having to specify the component type; the component type is inferred from the constructor arguments.

##### 17.1.2.1. `array`[](#array-builtin)

Overload@const @must_use fn array<T, N>(e1 : T, ..., eN : T) -> array<T, N>
Parameterization`T` is [concrete](#type-concrete) and [constructible](#constructible)
Description Construction of an [array](#array) from elements. 
Note: array<T,N> is [constructible](#constructible) because its [element count](#element-count) is equal to the number of arguments to the constructor, and hence fully determined at [shader-creation](#shader-module-creation) time.

Overload@const @must_use fn array(e1 : T, ..., eN : T) -> array<T, N>
Parameterization`T` is [constructible](#constructible)
Description Construction of an [array](#array) from elements. 
The component type is inferred from the elements' type. The size of the array is determined by the number of elements.

##### 17.1.2.2. `bool`[](#bool-builtin)

Overload@const @must_use fn bool(e : T) -> bool
Parameterization`T` is a [scalar](#scalar) type.
Description Construct a [bool](#bool) value. 
If `T` is [bool](#bool), this is an identity operation.  
 Otherwise this is a boolean coercion. The result is `false` if `e` is a [zero value](#zero-value) (or -0.0 for floating point types) and `true` otherwise.

##### 17.1.2.3. `f16`[](#f16-builtin)

Overload@const @must_use fn f16(e : T) -> f16
Parameterization`T` is a [scalar](#scalar) type
Description Construct an [f16](#f16) value. 
If `T` is [f16](#f16), this is an identity operation.  
 If `T` is a [numeric scalar](#numeric-scalar) (other than [f16](#f16)), `e` is converted to [f16](#f16) (including invalid conversions).  
 If `T` is [bool](#bool), the result is `1.0h` if `e` is `true` and `0.0h` otherwise.

##### 17.1.2.4. `f32`[](#f32-builtin)

Overload@const @must_use fn f32(e : T) -> f32
Parameterization`T` is a [concrete](#type-concrete)[scalar](#scalar) type
Description Construct an [f32](#f32) value. 
If `T` is [f32](#f32), this is an identity operation.  
 If `T` is a [numeric scalar](#numeric-scalar) (other than [f32](#f32)), `e` is converted to [f32](#f32) (including invalid conversions).  
 If `T` is [bool](#bool), the result is `1.0f` if `e` is `true` and `0.0f` otherwise.

##### 17.1.2.5. `i32`[](#i32-builtin)

Overload@const @must_use fn i32(e : T) -> i32
Parameterization`T` is a [scalar](#scalar) type
Description Construct an [i32](#i32) value. 
If `T` is [i32](#i32), this is an identity operation.  
 If `T` is [u32](#u32), this is a reinterpretation of bits (i.e. the result is the unique value in [i32](#i32) that has the same bit pattern as `e`).  
 If `T` is a [floating point type](#floating-point-types), `e` is [converted](#scalar-floating-point-to-integral-conversion) to [i32](#i32), [rounding](#rounding) towards zero.  
 If `T` is [bool](#bool), the result is `1i` if `e` is `true` and `0i` otherwise.  
 If `T` is an [AbstractInt](#abstractint), this is an identity operation if `e` can be represented in [i32](#i32), otherwise it produces a [shader-creation error](#shader-creation-error).

##### 17.1.2.6. `mat2x2`[](#mat2x2-builtin)

Overload@const @must_use fn mat2x2<T>(e : mat2x2<S>) -> mat2x2<T>
@const @must_use fn mat2x2(e : mat2x2<S>) -> mat2x2<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 2x2 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat2x2<T>(v1 : vec2<T>, v2 : vec2<T>) -> mat2x2<T>
@const @must_use fn mat2x2(v1 : vec2<T>, v2 : vec2<T>) -> mat2x2<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 2x2 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat2x2<T>(e1 : T, e2 : T, e3 : T, e4 : T) -> mat2x2<T>
@const @must_use fn mat2x2(e1 : T, e2 : T, e3 : T, e4 : T) -> mat2x2<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 2x2 column-major [matrix](#matrix) from elements. 
Same as mat2x2(vec2(e1,e2), vec2(e3,e4)).

##### 17.1.2.7. `mat2x3`[](#mat2x3-builtin)

Overload@const @must_use fn mat2x3<T>(e : mat2x3<S>) -> mat2x3<T>
@const @must_use fn mat2x3(e : mat2x3<S>) -> mat2x3<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 2x3 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat2x3<T>(v1 : vec3<T>, v2 : vec3<T>) -> mat2x3<T>
@const @must_use fn mat2x3(v1 : vec3<T>, v2 : vec3<T>) -> mat2x3<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 2x3 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat2x3<T>(e1 : T, ..., e6 : T) -> mat2x3<T>
@const @must_use fn mat2x3(e1 : T, ..., e6 : T) -> mat2x3<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 2x3 column-major [matrix](#matrix) from elements. 
Same as mat2x3(vec3(e1,e2,e3), vec3(e4,e5,e6)).

##### 17.1.2.8. `mat2x4`[](#mat2x4-builtin)

Overload@const @must_use fn mat2x4<T>(e : mat2x4<S>) -> mat2x4<T>
@const @must_use fn mat2x4(e : mat2x4<S>) -> mat2x4<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 2x4 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat2x4<T>(v1 : vec4<T>, v2 : vec4<T>) -> mat2x4<T>
@const @must_use fn mat2x4(v1 : vec4<T>, v2 : vec4<T>) -> mat2x4<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 2x4 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat2x4<T>(e1 : T, ..., e8 : T) -> mat2x4<T>
@const @must_use fn mat2x4(e1 : T, ..., e8 : T) -> mat2x4<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 2x4 column-major [matrix](#matrix) from elements. 
Same as mat2x4(vec4(e1,e2,e3,e4), vec4(e5,e6,e7,e8)).

##### 17.1.2.9. `mat3x2`[](#mat3x2-builtin)

Overload@const @must_use fn mat3x2<T>(e : mat3x2<S>) -> mat3x2<T>
@const @must_use fn mat3x2(e : mat3x2<S>) -> mat3x2<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 3x2 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat3x2<T>(v1 : vec2<T>,
                              v2 : vec2<T>,
                              v3 : vec2<T>) -> mat3x2<T>
@const @must_use fn mat3x2(v1 : vec2<T>,
                           v2 : vec2<T>,
                           v3 : vec2<T>) -> mat3x2<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 3x2 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat3x2<T>(e1 : T, ..., e6 : T) -> mat3x2<T>
@const @must_use fn mat3x2(e1 : T, ..., e6 : T) -> mat3x2<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 3x2 column-major [matrix](#matrix) from elements. 
Same as mat3x2(vec2(e1,e2), vec2(e3,e4), vec2(e5,e6)).

##### 17.1.2.10. `mat3x3`[](#mat3x3-builtin)

Overload@const @must_use fn mat3x3<T>(e : mat3x3<S>) -> mat3x3<T>
@const @must_use fn mat3x3(e : mat3x3<S>) -> mat3x3<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 3x3 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat3x3<T>(v1 : vec3<T>,
                              v2 : vec3<T>,
                              v3 : vec3<T>) -> mat3x3<T>
@const @must_use fn mat3x3(v1 : vec3<T>,
                           v2 : vec3<T>,
                           v3 : vec3<T>) -> mat3x3<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 3x3 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat3x3<T>(e1 : T, ..., e9 : T) -> mat3x3<T>
@const @must_use fn mat3x3(e1 : T, ..., e9 : T) -> mat3x3<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 3x3 column-major [matrix](#matrix) from elements. 
Same as mat3x3(vec3(e1,e2,e3), vec3(e4,e5,e6), vec3(e7,e8,e9)).

##### 17.1.2.11. `mat3x4`[](#mat3x4-builtin)

Overload@const @must_use fn mat3x4<T>(e : mat3x4<S>) -> mat3x4<T>
@const @must_use fn mat3x4(e : mat3x4<S>) -> mat3x4<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 3x4 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat3x4<T>(v1 : vec4<T>,
                              v2 : vec4<T>,
                              v3 : vec4<T>) -> mat3x4<T>
@const @must_use fn mat3x4(v1 : vec4<T>,
                           v2 : vec4<T>,
                           v3 : vec4<T>) -> mat3x4<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 3x4 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat3x4<T>(e1 : T, ..., e12 : T) -> mat3x4<T>
@const @must_use fn mat3x4(e1 : T, ..., e12 : T) -> mat3x4<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 3x4 column-major [matrix](#matrix) from elements. 
Same as mat3x4(vec4(e1,e2,e3,e4), vec4(e5,e6,e7,e8), vec4(e9,e10,e11,e12)).

##### 17.1.2.12. `mat4x2`[](#mat4x2-builtin)

Overload@const @must_use fn mat4x2<T>(e : mat4x2<S>) -> mat4x2<T>
@const @must_use fn mat4x2(e : mat4x2<S>) -> mat4x2<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 4x2 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat4x2<T>(v1 : vec2<T>,
                              v2 : vec2<T>,
                              v3 : vec2<T>,
                              v4: vec2<T>) -> mat4x2<T>
@const @must_use fn mat4x2(v1 : vec2<T>,
                           v2 : vec2<T>,
                           v3 : vec2<T>,
                           v4: vec2<T>) -> mat4x2<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 4x2 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat4x2<T>(e1 : T, ..., e8 : T) -> mat4x2<T>
@const @must_use fn mat4x2(e1 : T, ..., e8 : T) -> mat4x2<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 4x2 column-major [matrix](#matrix) from elements. 
Same as mat4x2(vec2(e1,e2), vec2(e3,e4), vec2(e5,e6), vec2(e7,e8)).

##### 17.1.2.13. `mat4x3`[](#mat4x3-builtin)

Overload@const @must_use fn mat4x3<T>(e : mat4x3<S>) -> mat4x3<T>
@const @must_use fn mat4x3(e : mat4x3<S>) -> mat4x3<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 4x3 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat4x3<T>(v1 : vec3<T>,
                              v2 : vec3<T>,
                              v3 : vec3<T>,
                              v4 : vec3<T>) -> mat4x3<T>
@const @must_use fn mat4x3(v1 : vec3<T>,
                           v2 : vec3<T>,
                           v3 : vec3<T>,
                           v4 : vec3<T>) -> mat4x3<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 4x3 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat4x3<T>(e1 : T, ..., e12 : T) -> mat4x3<T>
@const @must_use fn mat4x3(e1 : T, ..., e12 : T) -> mat4x3<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 4x3 column-major [matrix](#matrix) from elements. 
Same as mat4x3(vec3(e1,e2,e3), vec3(e4,e5,e6), vec3(e7,e8,e9), vec3(e10,e11,e12)).

##### 17.1.2.14. `mat4x4`[](#mat4x4-builtin)

Overload@const @must_use fn mat4x4<T>(e : mat4x4<S>) -> mat4x4<T>
@const @must_use fn mat4x4(e : mat4x4<S>) -> mat4x4<S>
Parameterization`T` is [f16](#f16) or [f32](#f32)  
`S` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Constructor for a 4x4 column-major [matrix](#matrix). 
If `T` does not match `S`, a [conversion](#floating-point-conversion) occurs.

Overload@const @must_use fn mat4x4<T>(v1 : vec4<T>,
                              v2 : vec4<T>,
                              v3 : vec4<T>,
                              v4 : vec4<T>) -> mat4x4<T>
@const @must_use fn mat4x4(v1 : vec4<T>,
                           v2 : vec4<T>,
                           v3 : vec4<T>,
                           v4 : vec4<T>) -> mat4x4<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 4x4 column-major [matrix](#matrix) from column vectors.

Overload@const @must_use fn mat4x4<T>(e1 : T, ..., e16 : T) -> mat4x4<T>
@const @must_use fn mat4x4(e1 : T, ..., e16 : T) -> mat4x4<T>
Parameterization`T` is [AbstractFloat](#abstractfloat), [f16](#f16), or [f32](#f32)
Description Construct a 4x4 column-major [matrix](#matrix) from elements. 
Same as mat4x4(vec4(e1,e2,e3,e4), vec4(e5,e6,e7,e8), vec4(e9,e10,e11,e12), vec4(e13,e14,e15,e16)).

##### 17.1.2.15. Structures[](#structures-builtin)

Overload@const @must_use fn S(e1 : T1, ..., eN : TN) -> S
Parameterization`S` is a [constructible](#constructible) structure type with members having types `T1` ... `TN`.
Description Construct a [structure](#structure) of type `S` from members.

##### 17.1.2.16. `u32`[](#u32-builtin)

Overload@const @must_use fn u32(e : T) -> u32
Parameterization`T` is a [scalar](#scalar) type
Description Construct a [u32](#u32) value. 
If `T` is [u32](#u32), this is an identity operation.  
 If `T` is [i32](#i32), this is a reinterpretation of bits (i.e. the result is the unique value in [u32](#u32) that has the same bit pattern as `e`).  
 If `T` is a [floating point type](#floating-point-types), `e` is [converted](#scalar-floating-point-to-integral-conversion) to [u32](#u32), [rounding](#rounding) towards zero.  
 If `T` is [bool](#bool), the result is `1u` if `e` is `true` and `0u` otherwise.  
 If `T` is [AbstractInt](#abstractint), this is an identity operation if the `e` can be represented in [u32](#u32), otherwise it produces a [shader-creation error](#shader-creation-error).
Note: The overload from [AbstractInt](#abstractint) exists so expressions such as `u32(4*1000*1000*1000)` can create a u32 value that would otherwise overflow the i32 type. If this overload did not exist, [overload resolution](#overload-resolution) would select the `u32(i32)` overload, the AbstractInt expression would automatically convert to i32, and this would cause a shader-creation error due to overflow.

##### 17.1.2.17. `vec2`[](#vec2-builtin)

Overload@const @must_use fn vec2<T>(e : T) -> vec2<T>
@const @must_use fn vec2(e : S) -> vec2<S>
Parameterization`T` is a [concrete](#type-concrete)[scalar](#scalar)  
`S` is [scalar](#scalar)
Description Construction of a two-component [vector](#vector) with `e` as both components.

Overload@const @must_use fn vec2<T>(e : vec2<S>) -> vec2<T>
@const @must_use fn vec2(e : vec2<S>) -> vec2<S>
Parameterization`T` is a [concrete](#type-concrete)[scalar](#scalar)  
`S` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a two-component [vector](#vector) with `e.x` and `e.y` as components. 
If `T` does not match `S` a conversion is used and the components are `T(e.x)` and `T(e.y)`.

Overload@const @must_use fn vec2<T>(e1 : T, e2 : T) -> vec2<T>
@const @must_use fn vec2(e1 : T, e2 : T) -> vec2<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a two-component [vector](#vector) with `e1` and `e2` as components.

Overload@const @must_use fn vec2() -> vec2<T>
Parameterization`T` is AbstractInt
Description Returns the value `vec2(0,0)`.

##### 17.1.2.18. `vec3`[](#vec3-builtin)

Overload@const @must_use fn vec3<T>(e : T) -> vec3<T>
@const @must_use fn vec3(e : S) -> vec3<S>
Parameterization`T` is a [concrete](#type-concrete)[scalar](#scalar)  
`S` is [scalar](#scalar)
Description Construction of a three-component [vector](#vector) with `e` as all components.

Overload@const @must_use fn vec3<T>(e : vec3<S>) -> vec3<T>
@const @must_use fn vec3(e : vec3<S>) -> vec3<S>
Parameterization`T` is a [concrete](#type-concrete)[scalar](#scalar)  
`S` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a three-component [vector](#vector) with `e.x`, `e.y`, and `e.z` as components. 
If `T` does not match `S` a conversion is used and the components are `T(e.x)`, `T(e.y)`, and `T(e.z)`.

Overload@const @must_use fn vec3<T>(e1 : T, e2 : T, e3 : T) -> vec3<T>
@const @must_use fn vec3(e1 : T, e2 : T, e3 : T) -> vec3<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a three-component [vector](#vector) with `e1`, `e2`, and `e3` as components.

Overload@const @must_use fn vec3<T>(v1 : vec2<T>, e1 : T) -> vec3<T>
@const @must_use fn vec3(v1 : vec2<T>, e1 : T) -> vec3<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a three-component [vector](#vector) with `v1.x`, `v1.y`, and `e1` as components.

Overload@const @must_use fn vec3<T>(e1 : T, v1 : vec2<T>) -> vec3<T>
@const @must_use fn vec3(e1 : T, v1 : vec2<T>) -> vec3<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a three-component [vector](#vector) with `e1`, `v1.x`, and `v1.y` as components.

Overload@const @must_use fn vec3() -> vec3<T>
Parameterization`T` is AbstractInt
Description Returns the value `vec3(0,0,0)`.

##### 17.1.2.19. `vec4`[](#vec4-builtin)

Overload@const @must_use fn vec4<T>(e : T) -> vec4<T>
@const @must_use fn vec4(e : S) -> vec4<S>
Parameterization`T` is a [concrete](#type-concrete)[scalar](#scalar)  
`S` is [scalar](#scalar)
Description Construction of a four-component [vector](#vector) with `e` as all components.

Overload@const @must_use fn vec4<T>(e : vec4<S>) -> vec4<T>
@const @must_use fn vec4(e : vec4<S>) -> vec4<S>
Parameterization`T` is a [concrete](#type-concrete)[scalar](#scalar)  
`S` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `e.x`, `e.y`, `e.z`, and `e.w` as components. 
If `T` does not match `S` a conversion is used and the components are `T(e.x)`, `T(e.y)`, `T(e.z)` and `T(e.w)`.

Overload@const @must_use fn vec4<T>(e1 : T, e2 : T, e3 : T, e4 : T) -> vec4<T>
@const @must_use fn vec4(e1 : T, e2 : T, e3 : T, e4 : T) -> vec4<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `e1`, `e2`, `e3`, and `e4` as components.

Overload@const @must_use fn vec4<T>(e1 : T, v1 : vec2<T>, e2 : T) -> vec4<T>
@const @must_use fn vec4(e1 : T, v1 : vec2<T>, e2 : T) -> vec4<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `e1`, `v1.x`, `v1.y`, and `e2` as components.

Overload@const @must_use fn vec4<T>(e1 : T, e2 : T, v1 : vec2<T>) -> vec4<T>
@const @must_use fn vec4(e1 : T, e2 : T, v1 : vec2<T>) -> vec4<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `e1`, `e2`, `v1.x`, and `v1.y` as components.

Overload@const @must_use fn vec4<T>(v1 : vec2<T>, v2 : vec2<T>) -> vec4<T>
@const @must_use fn vec4(v1 : vec2<T>, v2 : vec2<T>) -> vec4<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `v1.x`, `v1.y`, `v2.x`, and `v2.y` as components.

Overload@const @must_use fn vec4<T>(v1 : vec2<T>, e1 : T, e2 : T) -> vec4<T>
@const @must_use fn vec4(v1 : vec2<T>, e1 : T, e2 : T) -> vec4<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `v1.x`, `v1.y`, `e1`, and `e2` as components.

Overload@const @must_use fn vec4<T>(v1 : vec3<T>, e1 : T) -> vec4<T>
@const @must_use fn vec4(v1 : vec3<T>, e1 : T) -> vec4<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `v1.x`, `v1.y`, `v1.z`, and `e1` as components.

Overload@const @must_use fn vec4<T>(e1 : T, v1 : vec3<T>) -> vec4<T>
@const @must_use fn vec4(e1 : T, v1 : vec3<T>) -> vec4<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) construction of a four-component [vector](#vector) with `e1`, `v1.x`, `v1.y`, and `v1.z` as components.

Overload@const @must_use fn vec4() -> vec4<T>
Parameterization`T` is AbstractInt
Description Returns the value `vec4(0,0,0,0)`.

### 17.2. Bit Reinterpretation Built-in Functions[](#bit-reinterp-builtin-functions)

#### 17.2.1. `bitcast`[](#bitcast-builtin)

A `bitcast` built-in function is used to reinterpret the bit representation of a value in one type as a value in another type.

The internal layout rules are described in [§ 14.4.4 Internal Layout of Values](#internal-value-layout).

Overload@const @must_use fn bitcast<T>(e : T) -> T
Parameterization`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Identity transform.  
[Component-wise](#component-wise) when `T` is a [vector](#vector).  
 The result is `e`.

Overload@const @must_use fn bitcast<T>(e : S) -> T
Parameterization`S` is i32, u32, or f32  
`T` is not `S` and is i32, u32, or f32
Description Reinterpretation of bits as `T`.  
 The result is the reintepretation of bits in `e` as a `T` value.

Overload@const @must_use fn bitcast<vecN<T>>(e : vecN<S>) -> vecN<T>
Parameterization`S` is i32, u32, or f32  
`T` is not `S` and is i32, u32, or f32
Description[Component-wise](#component-wise) reinterpretation of bits as `T`.  
 The result is the reintepretation of bits in `e` as a `vecN<T>` value.

Overload@const @must_use fn bitcast<u32>(e : AbstractInt) -> u32
@const @must_use fn bitcast<vecN<u32>>(e : vecN<AbstractInt>) -> vecN<u32>
Parameterization
Description The identity operation if `e` can be represented as [u32](#u32), otherwise it produces a [shader-creation error](#shader-creation-error). That is, produces the same result as `u32(e)`. 
[Component-wise](#component-wise) when `e` is a vector.

Overload@const @must_use fn bitcast<T>(e : vec2<f16>) -> T
Parameterization`T` is i32, u32, or f32
Description[Component-wise](#component-wise) reinterpretation of bits as `T`.  
 The result is the reintepretation of the 32 bits in `e` as a `T` value, following the internal layout rules.

Overload@const @must_use fn bitcast<vec2<T>>(e : vec4<f16>) -> vec2<T>
Parameterization`T` is i32, u32, or f32
Description[Component-wise](#component-wise) reinterpretation of bits as `T`.  
 The result is the reintepretation of the 64 bits in `e` as a `T` value, following the internal layout rules.

Overload@const @must_use fn bitcast<vec2<f16>>(e : T) -> vec2<f16>
Parameterization`T` is i32, u32, or f32
Description[Component-wise](#component-wise) reinterpretation of bits as f16.  
 The result is the reintepretation of the 32 bits in `e` as an f16 value, following the internal layout rules.

Overload@const @must_use fn bitcast<vec4<f16>>(e : vec2<T>) -> vec4<f16>
Parameterization`T` is i32, u32, or f32
Description[Component-wise](#component-wise) reinterpretation of bits as `vec2<f16>`.  
 The result is the reintepretation of the 64 bits in `e` as an f16 value, following the internal layout rules.

### 17.3. Logical Built-in Functions[](#logical-builtin-functions)

#### 17.3.1. `all`[](#all-builtin)

Overload@const @must_use fn all(e: vecN<bool>) -> bool
Description Returns true if each component of `e` is true.

Overload@const @must_use fn all(e: bool) -> bool
Description Returns `e`.

#### 17.3.2. `any`[](#any-builtin)

Overload@const @must_use fn any(e: vecN<bool>) -> bool
Description Returns true if any component of `e` is true.

Overload@const @must_use fn any(e: bool) -> bool
Description Returns `e`.

#### 17.3.3. `select`[](#select-builtin)

Overload@const @must_use fn select(f: T,
                           t: T,
                           cond: bool) -> T
Parameterization`T` is [scalar](#scalar) or [vector](#vector)
Description Returns `t` when `cond` is true, and `f` otherwise.

Overload@const @must_use fn select(f: vecN<T>,
                           t: vecN<T>,
                           cond: vecN<bool>) -> vecN<T>
Parameterization`T` is [scalar](#scalar)
Description[Component-wise](#component-wise) selection. Result component `i` is evaluated as `select(f[i], t[i], cond[i])`.

### 17.4. Array Built-in Functions[](#array-builtin-functions)

#### 17.4.1. `arrayLength`[](#arrayLength-builtin)

Overload@must_use fn arrayLength(p: ptr<AS, array<E>, AM>) -> u32
Parameterization`E` is an element type for a [runtime-sized](#runtime-sized) array.  
`AS` is one of [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), or [workgroup](#address-spaces-workgroup).  
[access mode](#access-mode)`AM` is [read](#access-read) or [read_write](#access-read_write) and [must](#shader-creation-error) be valid for `AS`. 
Note:`AS` can only be [uniform](#address-spaces-uniform) or [workgroup](#address-spaces-workgroup) when `p` is derived from the result of a [bufferView](#bufferview-builtin) or [bufferArrayView](#bufferarrayview-builtin) built-in function.
Description Returns [NRuntime](#nruntime), the number of elements in the [runtime-sized](#runtime-sized) array. 
See [§ 13.3.4 Buffer Binding Determines Runtime-Sized Array Element Count](#buffer-binding-determines-runtime-sized-array-element-count)

When `p` is derived from a [bufferView](#bufferview-builtin) or [bufferArrayView](#bufferarrayview-builtin) built-in function, [NRuntime](#nruntime) is based on the size of the [buffer](#buffer) as determined by the analysis in [§ 17.14 Buffer View Built-in Functions](#buffer-view-builtin-functions).

EXAMPLE: Getting the number of elements in a runtime-sized array

struct PointLight {
  position : vec3f,
  color : vec3f,
}

struct LightStorage {
  pointCount : u32,
  point : array<PointLight>,
}

@group(0) @binding(1) var<storage> lights : LightStorage;

fn num_point_lights() -> u32 {
  return arrayLength( &lights.point );
}

### 17.5. Numeric Built-in Functions[](#numeric-builtin-functions)

#### 17.5.1. `abs`[](#abs-float-builtin)

Overload@const @must_use fn abs(e: T ) -> T
Parameterization S is AbstractInt, AbstractFloat, i32, u32, f32, or f16  
T is S, or vecN<S>
Description The absolute value of `e`. [Component-wise](#component-wise) when `T` is a vector. 
If `e` is a floating-point type, then the result is `e` with a positive sign bit. If `e` is an unsigned [integer scalar](#integer-scalar) type, then the result is `e`. If `e` is a signed [integer scalar](#integer-scalar) type and evaluates to the largest negative value, then the result is `e`.

#### 17.5.2. `acos`[](#acos-builtin)

Overload@const @must_use fn acos(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the principal value, in radians, of the inverse cosine (cos-1) of `e`.  
 That is, approximates `x` with 0 ≤ `x` ≤ π, such that `cos`(`x`) = `e`. 
[Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [−1, 1]

#### 17.5.3. `acosh`[](#acosh-builtin)

Overload@const @must_use fn acosh(x: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the inverse hyperbolic cosine (cosh-1) of `x`, as a [hyperbolic angle](#hyperbolic-angle).  
 That is, approximates `a` with 0 ≤ a ≤ +∞, such that `cosh`(`a`) = `x`. 
[Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [1, +∞]

#### 17.5.4. `asin`[](#asin-builtin)

Overload@const @must_use fn asin(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the principal value, in radians, of the inverse sine (sin-1) of `e`.  
 That is, approximates `x` with -π/2 ≤ `x` ≤ π/2, such that `sin`(`x`) = `e`. 
[Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [−1, 1]

#### 17.5.5. `asinh`[](#asinh-builtin)

Overload@const @must_use fn asinh(y: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the inverse hyperbolic sine (sinh-1) of `y`, as a [hyperbolic angle](#hyperbolic-angle).  
 That is, approximates `a` such that `sinh`(`y`) = `a`. 
[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.6. `atan`[](#atan-builtin)

Overload@const @must_use fn atan(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the principal value, in radians, of the inverse tangent (tan-1) of `e`.  
 That is, approximates `x` with − π/2 ≤ `x` ≤ π/2, such that `tan`(`x`) = `e`. 
[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.7. `atanh`[](#atanh-builtin)

Overload@const @must_use fn atanh(t: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the inverse hyperbolic tangent (tanh-1) of `t`, as a [hyperbolic angle](#hyperbolic-angle).  
 That is, approximates `a` such that `tanh`(`a`) = `t`. 
[Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [−1, 1]

#### 17.5.8. `atan2`[](#atan2-builtin)

Overload@const @must_use fn atan2(y: T,
                          x: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns an [angle](#angles), in radians, in the interval [-π, π] whose tangent is `y`÷`x`. 
The quadrant selected by the result depends on the signs of `y` and `x`. For example, the function may be implemented as:

*   `atan(y/x)` when `x`> 0

*   `atan(y/x)` + π when (`x`< 0) and (`y`> 0)

*   `atan(y/x)` - π when (`x`< 0) and (`y`< 0)

Note: The error in the result is unbounded:

*   When `abs(x)` is very small, e.g. [subnormal](#ieee754-subnormal) for its type,

*   At the origin (`x`,`y`) = (0,0), or

*   When `y` is subnormal or infinite.

[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.9. `ceil`[](#ceil-builtin)

Overload@const @must_use fn ceil(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the [ceiling](#ceiling-expression) of `e`. [Component-wise](#component-wise) when `T` is a vector.

#### 17.5.10. `clamp`[](#clamp)

Overload@const @must_use fn clamp(e: T,
                          low: T,
                          high: T) -> T
Parameterization S is AbstractInt, AbstractFloat, i32, u32, f32, or f16  
T is S, or vecN<S>
Description Restricts the value of `e` within a range. 
If `T` is an integer type, then the result is `min(max(e, low), high)`.

If `T` is a floating-point type, then the result is either `min(max(e,     low), high)`, or the median of the three values `e`, `low`, `high`.

[Component-wise](#component-wise) when `T` is a vector.

If `low` is greater than `high`, then:

*   It is a [shader-creation error](#shader-creation-error) if `low` and `high` are [const-expressions](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `low` and `high` are [override-expressions](#override-expressions).

#### 17.5.11. `cos`[](#cos-builtin)

Overload@const @must_use fn cos(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the cosine of `e`, where `e` is in radians. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval (−∞, +∞)

#### 17.5.12. `cosh`[](#cosh-builtin)

Overload@const @must_use fn cosh(a: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the hyperbolic cosine of `a`, where `a` is a [hyperbolic angle](#hyperbolic-angle). Approximates the pure mathematical function (_e_ a + _e_−a)÷2, but not necessarily computed that way. 
[Component-wise](#component-wise) when `T` is a vector

#### 17.5.13. `countLeadingZeros`[](#countLeadingZeros-builtin)

Overload@const @must_use fn countLeadingZeros(e: T) -> T
Parameterization`T` is i32, u32, vecN<i32>, or vecN<u32>
Description The number of consecutive 0 bits starting from the most significant bit of `e`, when `T` is a scalar type.  
[Component-wise](#component-wise) when `T` is a vector.  
 Also known as "clz" in some languages.

#### 17.5.14. `countOneBits`[](#countOneBits-builtin)

Overload@const @must_use fn countOneBits(e: T) -> T
Parameterization`T` is i32, u32, vecN<i32>, or vecN<u32>
Description The number of 1 bits in the representation of `e`.  
 Also known as "population count".  
[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.15. `countTrailingZeros`[](#countTrailingZeros-builtin)

Overload@const @must_use fn countTrailingZeros(e: T) -> T
Parameterization`T` is i32, u32, vecN<i32>, or vecN<u32>
Description The number of consecutive 0 bits starting from the least significant bit of `e`, when `T` is a scalar type.  
[Component-wise](#component-wise) when `T` is a vector.  
 Also known as "ctz" in some languages.

#### 17.5.16. `cross`[](#cross-builtin)

Overload@const @must_use fn cross(a: vec3<T>,
                          b: vec3<T>) -> vec3<T>
Parameterization`T` is AbstractFloat, f32, or f16
Description Returns the cross product of `e1` and `e2`.
Domain[Implied from linear terms](#implied-from-linear-terms) given by a possible implementation: 
*   a[1] × b[2] − a[2] × b[1]

*   a[2] × b[0] − a[0] × b[2]

*   a[0] × b[1] − a[1] × b[0]

#### 17.5.17. `degrees`[](#degrees-builtin)

Overload@const @must_use fn degrees(e1: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Converts radians to degrees, approximating `e1`×180÷π. [Component-wise](#component-wise) when `T` is a vector

#### 17.5.18. `determinant`[](#determinant-builtin)

Overload@const @must_use fn determinant(e: matCxC<T>) -> T
Parameterization`T` is AbstractFloat, f32, or f16
Description Returns the determinant of `e`.
Domain[Implied from linear terms](#implied-from-linear-terms) in a standard mathematical definition of the determinant.

#### 17.5.19. `distance`[](#distance-builtin)

Overload@const @must_use fn distance(e1: T,
                             e2: T) -> S
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the distance between `e1` and `e2` (e.g. `length(e1 - e2)`). 
The [domain](#domain) is all vectors (e1,e2) where the subtraction e1−e2 is valid. That is, the set of all vectors except where `e1[i]` and `e2[i]` are the same infinite value, for some component `i`.

#### 17.5.20. `dot`[](#dot-builtin)

Overload@const @must_use fn dot(e1: vecN<T>,
                        e2: vecN<T>) -> T
Parameterization`T` is AbstractInt, AbstractFloat, i32, u32, f32, or f16
Description Returns the dot product of `e1` and `e2`.
Domain[Implied from linear terms](#implied-from-linear-terms) of the sum over terms e1[i] × e2[i].

#### 17.5.21. `dot4U8Packed`[](#dot4U8Packed-builtin)

Overload@const @must_use fn dot4U8Packed(e1: u32,
                                 e2: u32) -> u32
Description`e1` and `e2` are interpreted as vectors with four 8-bit unsigned integer components. Return the unsigned integer dot product of these two vectors.

#### 17.5.22. `dot4I8Packed`[](#dot4I8Packed-builtin)

Overload@const @must_use fn dot4I8Packed(e1: u32,
                                 e2: u32) -> i32
Description`e1` and `e2` are interpreted as vectors with four 8-bit signed integer components. Return the signed integer dot product of these two vectors. Each component is sign-extended to i32 before performing the multiply, and then the add operations are done in WGSL i32 (the addition cannot overflow since the result is mathematically guaranteed to be in the range from -65024 to 65536, which lies within the range of numbers that can be represented by i32).

#### 17.5.23. `exp`[](#exp-builtin)

Overload@const @must_use fn exp(e1: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the natural exponentiation of `e1` (e.g. `e``e1`). [Component-wise](#component-wise) when `T` is a vector.

#### 17.5.24. `exp2`[](#exp2-builtin)

Overload@const @must_use fn exp2(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns 2 raised to the power `e` (e.g. `2``e`). [Component-wise](#component-wise) when `T` is a vector.

Overload@const @must_use fn extractBits(e: T,
                                offset: u32,
                                count: u32) -> T
Parameterization`T` is i32 or vecN<i32>
Description Reads bits from an integer, with sign extension. 
When `T` is a scalar type, then:

*   `w` is the bit width of `T`
*   `o = min(offset, w)`
*   `c = min(count, w - o)`
*   The result is 0 if `c` is 0. 
*   Otherwise, bits `0..c - 1` of the result are copied from bits `o..o + c - 1` of `e`. Other bits of the result are the same as bit `c - 1` of the result. 

[Component-wise](#component-wise) when `T` is a vector. 
If `count` + `offset` is greater than `w`, then:

*   It is a [shader-creation error](#shader-creation-error) if `count` and `offset` are [const-expressions](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `count` and `offset` are [override-expressions](#override-expressions).

Overload@const @must_use fn extractBits(e: T,
                                offset: u32,
                                count: u32) -> T
Parameterization`T` is u32 or vecN<u32>
Description Reads bits from an integer, without sign extension. 
When `T` is a scalar type, then:

*   `w` is the bit width of `T`
*   `o = min(offset, w)`
*   `c = min(count, w - o)`
*   The result is 0 if `c` is 0. 
*   Otherwise, bits `0..c - 1` of the result are copied from bits `o..o + c - 1` of `e`. Other bits of the result are 0. 

[Component-wise](#component-wise) when `T` is a vector. 
If `count` + `offset` is greater than `w`, then:

*   It is a [shader-creation error](#shader-creation-error) if `count` and `offset` are [const-expressions](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `count` and `offset` are [override-expressions](#override-expressions).

#### 17.5.27. `faceForward`[](#faceForward-builtin)

Overload@const @must_use fn faceForward(e1: T,
                                e2: T,
                                e3: T) -> T
Parameterization`T` is vecN<AbstractFloat>, vecN<f32>, or vecN<f16>
Description Returns `e1` if `dot(e2, e3)` is negative, and `-e1` otherwise.
Domain The domain restrictions arise from the `dot(e2,e3)` operation: they are [implied from linear terms](#implied-from-linear-terms) of the sum over terms e2[i] × e3[i].

#### 17.5.28. `firstLeadingBit` (signed)[](#firstLeadingBit-signed-builtin)

Overload@const @must_use fn firstLeadingBit(e: T) -> T
Parameterization`T` is i32 or vecN<i32>
Description For scalar `T`, the result is: 
*   -1 if `e` is 0 or -1. 
*   Otherwise the position of the most significant bit in `e` that is different from `e`’s sign bit. 

[Component-wise](#component-wise) when `T` is a vector.
Note: Since signed integers use twos-complement representation, the sign bit appears in the most significant bit position.

#### 17.5.29. `firstLeadingBit` (unsigned)[](#firstLeadingBit-unsigned-builtin)

Overload@const @must_use fn firstLeadingBit(e: T) -> T
Parameterization`T` is u32 or vecN<u32>
Description For scalar `T`, the result is: 
*   `T(-1)` if `e` is zero. 
*   Otherwise the position of the most significant 1 bit in `e`. 

[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.30. `firstTrailingBit`[](#firstTrailingBit-builtin)

Overload@const @must_use fn firstTrailingBit(e: T) -> T
Parameterization`T` is i32, u32, vecN<i32>, or vecN<u32>
Description For scalar `T`, the result is: 
*   `T(-1)` if `e` is zero. 
*   Otherwise the position of the least significant 1 bit in `e`. 

[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.31. `floor`[](#floor-builtin)

Overload@const @must_use fn floor(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the [floor](#floor-expression) of `e`. [Component-wise](#component-wise) when `T` is a vector.

#### 17.5.32. `fma`[](#fma-builtin)

Overload@const @must_use fn fma(e1: T,
                        e2: T,
                        e3: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns `e1 * e2 + e3`. [Component-wise](#component-wise) when `T` is a vector. 
Note: The name `fma` is short for "fused multiply add".

Note: The [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")`fusedMultiplyAdd` operation computes the [intermediate results](#intermediate-result) as if with unbounded range and precision, and only the final result is [rounded](#rounding) to a value in the destination type. However, the [§ 15.7.4 Floating Point Accuracy](#floating-point-accuracy) rule for `fma` allows an implementation which performs an ordinary multiply to the target type followed by an ordinary addition. In this case the [intermediate result](#intermediate-result) values may overflow or lose accuracy, and the overall operation is not "fused" at all.
Domain[Implied from linear terms](#implied-from-linear-terms) of the expressions e2 × e2 + e3.

#### 17.5.33. `fract`[](#fract-builtin)

Overload@const @must_use fn fract(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the fractional part of `e`, computed as `e - floor(e)`.  
[Component-wise](#component-wise) when `T` is a vector.
Note: Valid results are in the closed interval [0, 1.0]. For example, if `e` is a very small negative number, then `fract(e)` may be 1.0.

#### 17.5.34. `frexp`[](#frexp-builtin)

Overload@const @must_use fn frexp(e: T) -> __frexp_result_f32
Parameterization`T` is f32
Description Splits `e` into a fraction and an exponent. 
*   When `e` is zero, the fraction is zero.

*   When `e` is non-zero and normal, `e` = `fraction * 2``exponent`, where the fraction is in the range [0.5, 1.0) or (-1.0, -0.5].

*   Otherwise, `e` is [subnormal](#ieee754-subnormal), NaN, or infinite. The result fraction and exponent are [indeterminate values](#indeterminate-value).

Returns the `__frexp_result_f32` built-in structure, defined as follows:

struct __frexp_result_f32 {
  fract : f32, // fraction part
  exp : i32    // exponent part
}

Note: A mnemonic for the name `frexp` is "**fr**action and **exp**onent".
EXAMPLE: frexp usage

// Infers result type
let fraction_and_exponent = frexp(1.5);
// Sets fraction_only to 0.75
let fraction_only = frexp(1.5).fract;
Note: A value cannot be explicitly declared with the type `__frexp_result_f32`, but a value may infer the type.

Overload@const @must_use fn frexp(e: T) -> __frexp_result_f16
Parameterization`T` is f16
Description Splits `e` into a fraction and an exponent. 
*   When `e` is zero, the fraction is zero.

*   When `e` is non-zero and normal, `e` = `fraction * 2``exponent`, where the fraction is in the range [0.5, 1.0) or (-1.0, -0.5].

*   Otherwise, `e` is [subnormal](#ieee754-subnormal), NaN, or infinite. The result fraction and exponent are [indeterminate values](#indeterminate-value).

Returns the `__frexp_result_f16` built-in structure, defined as if as follows:

struct __frexp_result_f16 {
  fract : f16, // fraction part
  exp : i32    // exponent part
}

Note: A mnemonic for the name `frexp` is "**fr**action and **exp**onent".
Note: A value cannot be explicitly declared with the type `__frexp_result_f16`, but a value may infer the type.

Overload@const @must_use fn frexp(e: T) -> __frexp_result_abstract
Parameterization`T` is AbstractFloat
Description Splits `e` into a fraction and an exponent. 
*   When `e` is zero, the fraction is zero.

*   When `e` is non-zero and normal, `e` = `fraction * 2``exponent`, where the fraction is in the range [0.5, 1.0) or (-1.0, -0.5].

*   When `e` is [subnormal](#ieee754-subnormal), the fraction and exponent are have unbounded error. The fraction may be any AbstractFloat value, and the exponent may be any AbstractInt value.

Note: AbstractFloat expressions resulting in infinity or NaN cause a [shader-creation error](#shader-creation-error).

Returns the `__frexp_result_abstract` built-in structure, defined as follows:

struct __frexp_result_abstract {
  fract : AbstractFloat, // fraction part
  exp : AbstractInt      // exponent part
}

Note: A mnemonic for the name `frexp` is "**fr**action and **exp**onent".
EXAMPLE: abstract frexp usage

// Infers result type
const fraction_and_exponent = frexp(1.5);
// Sets fraction_only to 0.75
const fraction_only = frexp(1.5).fract;
Note: A value cannot be explicitly declared with the type `__frexp_result_abstract`, but a value may infer the type.

Overload@const @must_use fn frexp(e: T) -> __frexp_result_vecN_f32
Parameterization`T` is vecN<f32>
Description Splits components `ei` of `e` into a fraction and an exponent. 
*   When `ei` is zero, the fraction is zero.

*   When `ei` is non-zero and normal, `ei` = `fraction * 2``exponent`, where the fraction is in the range [0.5, 1.0) or (-1.0, -0.5].

*   Otherwise, `ei` is NaN or infinite. The result fraction and exponent are [indeterminate values](#indeterminate-value).

Returns the `__frexp_result_vecN_f32` built-in structure, defined as follows:

struct __frexp_result_vecN_f32 {
  fract : vecN<f32>, // fraction part
  exp : vecN<i32>    // exponent part
}

Note: A mnemonic for the name `frexp` is "**fr**action and **exp**onent".
Note: A value cannot be explicitly declared with the type `__frexp_result_vecN_f32`, but a value may infer the type.

Overload@const @must_use fn frexp(e: T) -> __frexp_result_vecN_f16
Parameterization`T` is vecN<f16>
Description Splits components `ei` of `e` into a fraction and an exponent. 
*   When `ei` is zero, the fraction is zero.

*   When `ei` is non-zero and normal, `ei` = `fraction * 2``exponent`, where the fraction is in the range [0.5, 1.0) or (-1.0, -0.5].

*   Otherwise, `ei` is NaN or infinite. The result fraction and exponent are [indeterminate values](#indeterminate-value).

Returns the `__frexp_result_vecN_f16` built-in structure, defined as if as follows:

struct __frexp_result_vecN_f16 {
  fract : vecN<f16>, // fraction part
  exp : vecN<i32>    // exponent part
}

Note: A mnemonic for the name `frexp` is "**fr**action and **exp**onent".
Note: A value cannot be explicitly declared with the type `__frexp_result_vecN_f16`, but a value may infer the type.

Overload@const @must_use fn frexp(e: T) -> __frexp_result_vecN_abstract
Parameterization`T` is vecN<AbstractFloat>
Description Splits components `ei` of `e` into a fraction and an exponent. 
*   When `ei` is zero, the fraction is zero.

*   When `ei` is non-zero and normal, `ei` = `fraction * 2``exponent`, where the fraction is in the range [0.5, 1.0) or (-1.0, -0.5].

*   When `ei` is [subnormal](#ieee754-subnormal), the fraction and exponent are have unbounded error. The fraction may be any AbstractFloat value, and the exponent may be any AbstractInt value.

Note: AbstractFloat expressions resulting in infinity or NaN cause a [shader-creation error](#shader-creation-error).

Returns the `__frexp_result_vecN_abstract` built-in structure, defined as follows:

struct __frexp_result_vecN_abstract {
  fract : vecN<AbstractFloat>, // fraction part
  exp : vecN<AbstractInt>      // exponent part
}

Note: A mnemonic for the name `frexp` is "**fr**action and **exp**onent".
Note: A value cannot be explicitly declared with the type `__frexp_result_vecN_abstract`, but a value may infer the type.

#### 17.5.35. `insertBits`[](#insertBits-builtin)

Overload@const @must_use fn insertBits(e: T,
                              newbits: T,
                              offset: u32,
                              count: u32) -> T
Parameterization`T` is i32, u32, vecN<i32>, or vecN<u32>
Description Sets bits in an integer. 
When `T` is a scalar type, then:

*   `w` is the bit width of `T`
*   `o = min(offset, w)`
*   `c = min(count, w - o)`
*   The result is `e` if `c` is 0. 
*   Otherwise, bits `o..o + c - 1` of the result are copied from bits `0..c - 1` of `newbits`. Other bits of the result are copied from `e`. 

[Component-wise](#component-wise) when `T` is a vector. 
If `count` + `offset` is greater than `w`, then:

*   It is a [shader-creation error](#shader-creation-error) if `count` and `offset` are [const-expressions](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `count` and `offset` are [override-expressions](#override-expressions).

#### 17.5.36. `inverseSqrt`[](#inverseSqrt-builtin)

Overload@const @must_use fn inverseSqrt(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the reciprocal of `sqrt(e)`. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [0, +∞]

#### 17.5.37. `ldexp`[](#ldexp-builtin)

Overload@const @must_use fn ldexp(e1: T,
                          e2: I) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>  
`I` is AbstractInt, i32, vecN<AbstractInt>, or vecN<i32>  
`I` is a vector if and only if `T` is a vector  
`T` can only be [abstract](#type-abstract) if `I` is also [abstract](#type-abstract) and vice versa 
Note: If either parameter is [concrete](#type-concrete) then the other parameter will undergo [automatic conversion](#feasible-automatic-conversion) to a [concrete](#type-concrete) type (if applicable) and the result will be a [concrete](#type-concrete) type.
Description Returns `e1 * 2``e2`, except: 
*   The result may be zero if `e2` + _bias_ ≤ 0.

*   If `e2`>_bias_ + 1

    *   It is a [shader-creation error](#shader-creation-error) if `e2` is a [const-expression](#const-expressions).

    *   It is a [pipeline-creation error](#pipeline-creation-error) if `e2` is an [override-expression](#override-expressions).

    *   Otherwise the result is an [indeterminate value](#indeterminate-value) for `T`.

Here, _bias_ is the exponent bias of the floating point format:

*   15 for `f16`

*   127 for `f32`

*   1023 for AbstractFloat, when AbstractFloat is [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary64](#ieee754-binary64)

If `x` is zero or a finite normal value for its type, then:

> x = ldexp(frexp(x).fract, frexp(x).exp)

[Component-wise](#component-wise) when `T` is a vector.

Note: A mnemonic for the name `ldexp` is "load exponent". The name may have been taken from the corresponding instruction in the floating point unit of the PDP-11.

#### 17.5.38. `length`[](#length-builtin)

Overload@const @must_use fn length(e: T) -> S
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the length of `e`.  
 Evaluates to the absolute value of `e` if `T` is [scalar](#scalar).  
 Evaluates to `sqrt(e[0]``2``+ e[1]``2``+ ...)` if `T` is a vector type. 
Note: The scalar case may be evaluated as `sqrt(e * e)`, which may unnecessarily overflow or lose accuracy.

#### 17.5.39. `log`[](#log-builtin)

Overload@const @must_use fn log(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the natural logarithm of `e`. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [0, +∞]

#### 17.5.40. `log2`[](#log2-builtin)

Overload@const @must_use fn log2(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the base-2 logarithm of `e`. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [0, +∞]

#### 17.5.41. `max`[](#max-float-builtin)

Overload@const @must_use fn max(e1: T,
                        e2: T) -> T
Parameterization S is AbstractInt, AbstractFloat, i32, u32, f32, or f16  
T is S, or vecN<S>
Description Returns `e2` if `e1` is less than `e2`, and `e1` otherwise. [Component-wise](#component-wise) when `T` is a vector. 
If `e1` and `e2` are floating-point values, then:

*   If both `e1` and `e2` are [subnormal](#ieee754-subnormal), then the result may be _either_ value.

#### 17.5.42. `min`[](#min-float-builtin)

Overload@const @must_use fn min(e1: T,
                        e2: T) -> T
Parameterization S is AbstractInt, AbstractFloat, i32, u32, f32, or f16  
T is S, or vecN<S>
Description Returns `e2` if `e2` is less than `e1`, and `e1` otherwise. [Component-wise](#component-wise) when `T` is a vector. 
If `e1` and `e2` are floating-point values, then:

*   If both `e1` and `e2` are [subnormal](#ieee754-subnormal), then the result may be _either_ value.

#### 17.5.43. `mix`[](#mix-builtin)

Overload@const @must_use fn mix(e1: T,
                        e2: T,
                        e3: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the linear blend of `e1` and `e2` (e.g. `e1 * (T(1) - e3) + e2 * e3`). [Component-wise](#component-wise) when `T` is a vector.
Domain[Implied from linear terms](#implied-from-linear-terms) of the expressions: e1[i] × (1 − e3[i]) + e2[i] × e3[i]. e2[i] × e2[i] + e3[i].

Overload@const @must_use fn mix(e1: T2,
                        e2: T2,
                        e3: T) -> T2
Parameterization`T` is AbstractFloat, f32, or f16  
`T2` is vecN<T>
Description Returns the component-wise linear blend of `e1` and `e2`, using scalar blending factor `e3` for each component.  
 Same as `mix(e1, e2, T2(e3))`.
Domain[Implied from linear terms](#implied-from-linear-terms) of the expressions: e1[i] × (1 − e3) + e2[i] × e3.

#### 17.5.44. `modf`[](#modf-builtin)

Overload@const @must_use fn modf(e: T) -> __modf_result_f32
Parameterization`T` is f32
Description Splits `e` into fractional and whole number parts. 
The whole part is [trunc](#trunc-builtin)(`e`), and the fractional part is `e` - [trunc](#trunc-builtin)(`e`).

Returns the `__modf_result_f32` built-in structure, defined as follows:

struct __modf_result_f32 {
  fract : f32, // fractional part
  whole : f32  // whole part
}
EXAMPLE: modf usage

// Infers result type
let fract_and_whole = modf(1.5);
// Sets fract_only to 0.5
let fract_only = modf(1.5).fract;
// Sets whole_only to 1.0
let whole_only = modf(1.5).whole;
Note: A value cannot be explicitly declared with the type `__modf_result_f32`, but a value may infer the type.

Overload@const @must_use fn modf(e: T) -> __modf_result_f16
Parameterization`T` is f16
Description Splits `e` into fractional and whole number parts. 
The whole part is [trunc](#trunc-builtin)(`e`), and the fractional part is `e` - [trunc](#trunc-builtin)(`e`).

Returns the `__modf_result_f16` built-in structure, defined as if as follows:

struct __modf_result_f16 {
  fract : f16, // fractional part
  whole : f16  // whole part
}
Note: A value cannot be explicitly declared with the type `__modf_result_f16`, but a value may infer the type.

Overload@const @must_use fn modf(e: T) -> __modf_result_abstract
Parameterization`T` is AbstractFloat
Description Splits `e` into fractional and whole number parts. 
The whole part is [trunc](#trunc-builtin)(`e`), and the fractional part is `e` - [trunc](#trunc-builtin)(`e`).

Returns the `__modf_result_abstract` built-in structure, defined as follows:

struct __modf_result_abstract {
  fract : AbstractFloat, // fractional part
  whole : AbstractFloat  // whole part
}
EXAMPLE: modf abstract usage

// Infers result type
const fract_and_whole = modf(1.5);
// Sets fract_only to 0.5
const fract_only = modf(1.5).fract;
// Sets whole_only to 1.0
const whole_only = modf(1.5).whole;
Note: A value cannot be explicitly declared with the type `__modf_result_abstract`, but a value may infer the type.

Overload@const @must_use fn modf(e: T) -> __modf_result_vecN_f32
Parameterization`T` is vecN<f32>
Description Splits the components of `e` into fractional and whole number parts. 
The `i`’th component of the whole and fractional parts equal the whole and fractional parts of `modf(e[i])`.

Returns the `__modf_result_vecN_f32` built-in structure, defined as follows:

struct __modf_result_vecN_f32 {
  fract : vecN<f32>, // fractional part
  whole : vecN<f32>  // whole part
}
Note: A value cannot be explicitly declared with the type `__modf_result_vecN_f32`, but a value may infer the type.

Overload@const @must_use fn modf(e: T) -> __modf_result_vecN_f16
Parameterization`T` is vecN<f16>
Description Splits the components of `e` into fractional and whole number parts. 
The `i`’th component of the whole and fractional parts equal the whole and fractional parts of `modf(e[i])`.

Returns the `__modf_result_vecN_f16` built-in structure, defined as if as follows:

struct __modf_result_vecN_f16 {
  fract : vecN<f16>, // fractional part
  whole : vecN<f16>  // whole part
}
Note: A value cannot be explicitly declared with the type `__modf_result_vecN_f16`, but a value may infer the type.

Overload@const @must_use fn modf(e: T) -> __modf_result_vecN_abstract
Parameterization`T` is vecN<AbstractFloat>
Description Splits the components of `e` into fractional and whole number parts. 
The `i`’th component of the whole and fractional parts equal the whole and fractional parts of `modf(e[i])`.

Returns the `__modf_result_vecN_abstract` built-in structure, defined as follows:

struct __modf_result_vecN_abstract {
  fract : vecN<AbstractFloat>, // fractional part
  whole : vecN<AbstractFloat>  // whole part
}
Note: A value cannot be explicitly declared with the type `__modf_result_vecN_abstract`, but a value may infer the type.

#### 17.5.45. `normalize`[](#normalize-builtin)

Overload@const @must_use fn normalize(e: vecN<T> ) -> vecN<T>
Parameterization`T` is AbstractFloat, f32, or f16
Description Returns a unit vector in the same direction as `e`. 
The [domain](#domain) is all vectors except the zero vector.

#### 17.5.46. `pow`[](#pow-builtin)

Overload@const @must_use fn pow(e1: T,
                        e2: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns `e1` raised to the power `e2`. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)The set of all pairs of [extended reals](#extended-real) (x,y) except: 
*   x< 0.

*   x is 1 and y is infinite.

*   x is infinite and y is 0.

This rule arises from the fact the result may be computed as `exp2(y * log2(x))`.

#### 17.5.47. `quantizeToF16`[](#quantizeToF16-builtin)

Overload@const @must_use fn quantizeToF16(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Quantizes a 32-bit floating point value `e` as if `e` were converted to a [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary16](#ieee754-binary16) value, and then converted back to a IEEE-754 [binary32](#ieee754-binary32) value. 
If `e` is outside the [finite range](#finite-range) of binary16, then:

*   It is a [shader-creation error](#shader-creation-error) if `e` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `e` is an [override-expression](#override-expressions).

*   Otherwise the result is an [indeterminate value](#indeterminate-value) for `T`.

The intermediate binary16 value may be [flushed to zero](#flush-to-zero), i.e. the final result may be zero if the intermediate binary16 value is [subnormal](#ieee754-subnormal).

See [§ 15.7.6 Floating Point Conversion](#floating-point-conversion).

[Component-wise](#component-wise) when `T` is a vector.
Note: The vec2<f32> case is the same as `unpack2x16float(pack2x16float(e))`.

#### 17.5.48. `radians`[](#radians-builtin)

Overload@const @must_use fn radians(e1: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Converts degrees to radians, approximating `e1`×π÷180. [Component-wise](#component-wise) when `T` is a vector

#### 17.5.49. `reflect`[](#reflect-builtin)

Overload@const @must_use fn reflect(e1: T,
                            e2: T) -> T
Parameterization`T` is vecN<AbstractFloat>, vecN<f32>, or vecN<f16>
Description For the incident vector `e1` and surface orientation `e2`, returns the reflection direction `e1 - 2 * dot(e2, e1) * e2`.

#### 17.5.50. `refract`[](#refract-builtin)

Overload@const @must_use fn refract(e1: T,
                            e2: T,
                            e3: I) -> T
Parameterization`T` is vecN<I>  
`I` is AbstractFloat, f32, or f16
Description For the incident vector `e1` and surface normal `e2`, and the ratio of indices of refraction `e3`, let `k = 1.0 - e3 * e3 * (1.0 - dot(e2, e1) * dot(e2, e1))`. If `k < 0.0`, returns the refraction vector 0.0, otherwise return the refraction vector `e3 * e1 - (e3 * dot(e2, e1) + sqrt(k)) * e2`. The incident vector `e1` and the normal `e2` should be normalized for desired results according to Snell’s Law; otherwise, the results may not conform to expected physical behavior.

#### 17.5.51. `reverseBits`[](#reverseBits-builtin)

Overload@const @must_use fn reverseBits(e: T) -> T
Parameterization`T` is i32, u32, vecN<i32>, or vecN<u32>
Description Reverses the bits in `e`: The bit at position `k` of the result equals the bit at position `31 -k` of `e`.  
[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.52. `round`[](#round-builtin)

Overload@const @must_use fn round(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Result is the integer `k` nearest to `e`, as a floating point value.  
 When `e` lies halfway between integers `k` and `k + 1`, the result is `k` when `k` is even, and `k + 1` when `k` is odd.  
[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.53. `saturate`[](#saturate-float-builtin)

Overload@const @must_use fn saturate(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns `clamp(e, 0.0, 1.0)`. [Component-wise](#component-wise) when `T` is a vector.

#### 17.5.54. `sign`[](#sign-builtin)

Overload@const @must_use fn sign(e: T) -> T
Parameterization S is AbstractInt, AbstractFloat, i32, f32, or f16  
T is S, or vecN<S>
Description Result is: 
*    1 when `e`> 0 
*    0 when `e` = 0 
*    -1 when `e`< 0 

[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.55. `sin`[](#sin-builtin)

Overload@const @must_use fn sin(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the sine of `e`, where `e` is in radians. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval (−∞, +∞)

#### 17.5.56. `sinh`[](#sinh-builtin)

Overload@const @must_use fn sinh(a: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the hyperbolic sine of `a`, where `a` is a [hyperbolic angle](#hyperbolic-angle). Approximates the pure mathematical function (_e_ a − _e_−a)÷2, but not necessarily computed that way. 
[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.57. `smoothstep`[](#smoothstep-builtin)

Overload@const @must_use fn smoothstep(edge0: T,
                               edge1: T,
                               x: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the smooth Hermite interpolation between 0 and 1. [Component-wise](#component-wise) when `T` is a vector. 
For scalar `T`, the result is `t * t * (3.0 - 2.0 * t)`,  
 where `t = clamp((x - edge0) / (edge1 - edge0), 0.0, 1.0)`.

Qualitatively:

*   When `edge0`<`edge1`, the function is 0 for `x` below `edge0`, then smoothly rises until `x` reaches `edge1`, and remains at 1 afterward.

*   When `edge0`>`edge1`, the function is 1 for `x` below `edge1`, then smoothly descends until `x` reaches `edge0`, and remains at 0 afterward.

If `edge0` = `edge1`:

*   It is a [shader-creation error](#shader-creation-error) if `edge0` and `edge1` are [const-expressions](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `edge0` and `edge1` are [override-expressions](#override-expressions).

*   Otherwise, the result is an [indeterminate value](#indeterminate-value) for `T`. In this case the computation performs a floating point [division by zero](#ieee754-division-by-zero), and the [Finite Math Assumption](#finite-math-assumption) applies.

#### 17.5.58. `sqrt`[](#sqrt-builtin)

Overload@const @must_use fn sqrt(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the square root of `e`. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval [0, +∞]

#### 17.5.59. `step`[](#step-builtin)

Overload@const @must_use fn step(edge: T,
                         x: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns 1.0 if `edge` ≤ `x`, and 0.0 otherwise. [Component-wise](#component-wise) when `T` is a vector.

#### 17.5.60. `tan`[](#tan-builtin)

Overload@const @must_use fn tan(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the tangent of `e`, where `e` is in radians. [Component-wise](#component-wise) when `T` is a vector.
Scalar [domain](#domain)Interval (−∞, +∞)

#### 17.5.61. `tanh`[](#tanh-builtin)

Overload@const @must_use fn tanh(a: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns the hyperbolic tangent of `a`, where `a` is a [hyperbolic angle](#hyperbolic-angle). Approximates the pure mathematical function (_e_ a − _e_−a) ÷ (_e_ a + _e_−a) but not necessarily computed that way. 
[Component-wise](#component-wise) when `T` is a vector.

#### 17.5.62. `transpose`[](#transpose-builtin)

Overload@const @must_use fn transpose(e: matRxC<T>) -> matCxR<T>
Parameterization`T` is AbstractFloat, f32, or f16
Description Returns the transpose of `e`.

#### 17.5.63. `trunc`[](#trunc-builtin)

Overload@const @must_use fn trunc(e: T) -> T
Parameterization S is AbstractFloat, f32, or f16  
T is S or vecN<S>
Description Returns [truncate](#truncate)(`e`), the nearest whole number whose absolute value is less than or equal to the absolute value of `e`. [Component-wise](#component-wise) when `T` is a vector.

### 17.6. Derivative Built-in Functions[](#derivative-builtin-functions)

See [§ 15.6.2 Derivatives](#derivatives).

Calls to these functions:

*   [Must](#shader-creation-error) only be used in a [fragment](#fragment) shader stage.

*   [Trigger](#triggered) a [derivative_uniformity](#trigger-derivative_uniformity)[diagnostic](#diagnostic) if [uniformity analysis](#uniformity-analysis) cannot prove the call is in [uniform control flow](#uniform-control-flow).

#### 17.6.1. `dpdx`[](#dpdx-builtin)

Overload@must_use fn dpdx(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Partial derivative of `e` with respect to window x coordinates. The result is the same as either `dpdxFine(e)` or `dpdxCoarse(e)`. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.2. `dpdxCoarse`[](#dpdxCoarse-builtin)

Overload@must_use fn dpdxCoarse(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Returns the partial derivative of `e` with respect to window x coordinates using local differences. This may result in fewer unique positions than `dpdxFine(e)`. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.3. `dpdxFine`[](#dpdxFine-builtin)

Overload@must_use fn dpdxFine(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Returns the partial derivative of `e` with respect to window x coordinates. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.4. `dpdy`[](#dpdy-builtin)

Overload@must_use fn dpdy(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Partial derivative of `e` with respect to window y coordinates. The result is the same as either `dpdyFine(e)` or `dpdyCoarse(e)`. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.5. `dpdyCoarse`[](#dpdyCoarse-builtin)

Overload@must_use fn dpdyCoarse(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Returns the partial derivative of `e` with respect to window y coordinates using local differences. This may result in fewer unique positions than `dpdyFine(e)`. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.6. `dpdyFine`[](#dpdyFine-builtin)

Overload@must_use fn dpdyFine(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Returns the partial derivative of `e` with respect to window y coordinates. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.7. `fwidth`[](#fwidth-builtin)

Overload@must_use fn fwidth(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Returns `abs(dpdx(e)) + abs(dpdy(e))`. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.8. `fwidthCoarse`[](#fwidthCoarse-builtin)

Overload@must_use fn fwidthCoarse(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Returns `abs(dpdxCoarse(e)) + abs(dpdyCoarse(e))`. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

#### 17.6.9. `fwidthFine`[](#fwidthFine-builtin)

Overload@must_use fn fwidthFine(e: T) -> T
Parameterization`T` is f32 or vecN<f32>
Description Returns `abs(dpdxFine(e)) + abs(dpdyFine(e))`. 
Returns an [indeterminate value](#indeterminate-value) if called in [non-uniform control flow](#uniform-control-flow).

### 17.7. Texture Built-in Functions[](#texture-builtin-functions)

Parameter values [must](#shader-creation-error) be valid for the respective texture types.

#### 17.7.1. `textureDimensions`[](#texturedimensions)

Returns the dimensions of a texture, or texture’s mip level in texels.

Parameterization Overload ST is [i32](#i32), [u32](#u32), or [f32](#f32) F is a [texel format](#texel-format) A is an [access mode](#access-mode) T is `texture_1d<ST>` or `texture_storage_1d<F,A>`@must_use fn textureDimensions(t: T) -> u32 ST is [i32](#i32), [u32](#u32), or [f32](#f32) T is `texture_1d<ST>` L is [i32](#i32), or [u32](#u32)@must_use fn textureDimensions(t: T, level: L) -> u32 ST is [i32](#i32), [u32](#u32), or [f32](#f32) F is a [texel format](#texel-format) A is an [access mode](#access-mode) T is `texture_2d<ST>`, `texture_2d_array<ST>`, `texture_cube<ST>`, `texture_cube_array<ST>`, `texture_multisampled_2d<ST>`, `texture_depth_2d`, `texture_depth_2d_array`, `texture_depth_cube`, `texture_depth_cube_array`, `texture_depth_multisampled_2d`, `texture_storage_2d<F,A>`, `texture_storage_2d_array<F,A>`, or `texture_external`@must_use fn textureDimensions(t: T) -> vec2<u32> ST is [i32](#i32), [u32](#u32), or [f32](#f32) T is `texture_2d<ST>`, `texture_2d_array<ST>`, `texture_cube<ST>`, `texture_cube_array<ST>`, `texture_depth_2d`, `texture_depth_2d_array`, `texture_depth_cube`, or `texture_depth_cube_array` L is [i32](#i32), or [u32](#u32)@must_use fn textureDimensions(t: T, level: L) -> vec2<u32> ST is [i32](#i32), [u32](#u32), or [f32](#f32) F is a [texel format](#texel-format) A is an [access mode](#access-mode) T is `texture_3d<ST>` or `texture_storage_3d<F,A>`@must_use fn textureDimensions(t: T) -> vec3<u32> ST is [i32](#i32), [u32](#u32), or [f32](#f32) T is `texture_3d<ST>` L is [i32](#i32), or [u32](#u32)@must_use fn textureDimensions(t: T, level: L) -> vec3<u32>

**Parameters:**

`t`The [sampled](#sampled-texture-type), [multisampled](#multisampled-texture-type), [depth](#texture-depth), [storage](#texture-storage), or [external](#external-texture-type) texture.
`level`The [mip level](#mip-level), with level 0 containing a full size version of the texture.  
 If omitted, the dimensions of level 0 are returned.

**Returns:**

The coordinate dimensions of the texture.

That is, the result provides the integer bounds on the coordinates of the [logical texel address](#logical-texel-address), excluding the [mip level count](#texture-mip-level-count), [array size](#texture-array-size), and [sample count](#texture-sample-count).

For textures based on cubes, the results are the dimensions of each face of the cube. Cube faces are square, so the x and y components of the result are equal.

If `level` is outside the range `[0, textureNumLevels(t))` then an [indeterminate value](#indeterminate-value) for the return type may be returned.

#### 17.7.2. `textureGather`[](#texturegather)

A texture gather operation reads from a 2D, 2D array, cube, or cube array texture, computing a four-component vector as follows:

*   Find the four texels that would be used in a sampling operation with linear filtering, from [mip level](#mip-level) 0:

    *   Use the specified coordinate, array index (when present), and offset (when present).

    *   The texels are adjacent, forming a square, when considering their texture space coordinates (_u_,_v_).

    *   Selected texels at the texture edge, cube face edge, or cube corners are handled as in ordinary texture sampling.

*   For each texel, read one channel and convert it into a scalar value.

    *   For non-depth textures, a zero-based `component` parameter specifies the channel to use.

        *   If the texture format supports the specified channel, i.e. has more than `component` channels:

            *   Yield scalar value `v[component]` when the texel value is `v`.

        *   Otherwise:

            *   Yield 0.0 when `component` is 1 or 2.

            *   Yield 1.0 when `component` is 3 (the alpha channel).

    *   For [depth textures](#type-depth-texture), yield the texel value. (Depth textures only have one channel.)

*   Yield the four-component vector, arranging scalars produced by the previous step into components according to the relative coordinates of the texels, as follows:

    *   Result component Relative texel coordinate x(_u_ min,_v_ max) y(_u_ max,_v_ max) z(_u_ max,_v_ min) w(_u_ min,_v_ min)

The four texels form the sampled area as described in the [WebGPU sampler descriptor](../webgpu_spec/webgpu-5f71975aec.md#GPUSamplerDescriptor).

Parameterization Overload C is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureGather(component: C, t: texture_2d<ST>, s: sampler, coords: vec2<f32>) -> vec4<ST> C is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureGather(component: C, t: texture_2d<ST>, s: sampler, coords: vec2<f32>, offset: vec2<i32>) -> vec4<ST> C is [i32](#i32), or [u32](#u32) A is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureGather(component: C, t: texture_2d_array<ST>, s: sampler, coords: vec2<f32>, array_index: A) -> vec4<ST> C is [i32](#i32), or [u32](#u32) A is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureGather(component: C, t: texture_2d_array<ST>, s: sampler, coords: vec2<f32>, array_index: A, offset: vec2<i32>) -> vec4<ST> C is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureGather(component: C, t: texture_cube<ST>, s: sampler, coords: vec3<f32>) -> vec4<ST> C is [i32](#i32), or [u32](#u32) A is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureGather(component: C, t: texture_cube_array<ST>, s: sampler, coords: vec3<f32>, array_index: A) -> vec4<ST> @must_use fn textureGather(t: texture_depth_2d, s: sampler, coords: vec2<f32>) -> vec4<f32> @must_use fn textureGather(t: texture_depth_2d, s: sampler, coords: vec2<f32>, offset: vec2<i32>) -> vec4<f32> @must_use fn textureGather(t: texture_depth_cube, s: sampler, coords: vec3<f32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureGather(t: texture_depth_2d_array, s: sampler, coords: vec2<f32>, array_index: A) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureGather(t: texture_depth_2d_array, s: sampler, coords: vec2<f32>, array_index: A, offset: vec2<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureGather(t: texture_depth_cube_array, s: sampler, coords: vec3<f32>, array_index: A) -> vec4<f32>

**Parameters:**

`component`Only applies to non-depth textures.   
The index of the channel to read from the selected texels.   
When provided, the `component` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `1`).  
 Its value must be at least 0 and at most 3. Values outside of this range will result in a [shader-creation error](#shader-creation-error).
`t`The [sampled](#sampled-texture-type) or [depth](#texture-depth) texture to read from.
`s`The [sampler type](#sampler-type).
`coords`The texture coordinates.
`array_index`The 0-based texture array index.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

A four component vector with components extracted from the specified channel from the selected texels, as described above.

EXAMPLE: Gather components from texels in 2D texture

@group(0) @binding(0) var t: texture_2d<f32>;
@group(0) @binding(1) var dt: texture_depth_2d;
@group(0) @binding(2) var s: sampler;

fn gather_x_components(c: vec2<f32>) -> vec4<f32> {
  return textureGather(0,t,s,c);
}
fn gather_y_components(c: vec2<f32>) -> vec4<f32> {
  return textureGather(1,t,s,c);
}
fn gather_z_components(c: vec2<f32>) -> vec4<f32> {
  return textureGather(2,t,s,c);
}
fn gather_depth_components(c: vec2<f32>) -> vec4<f32> {
  return textureGather(dt,s,c);
}

#### 17.7.3. `textureGatherCompare`[](#texturegathercompare)

A texture gather compare operation performs a depth comparison on four texels in a depth texture and collects the results into a single vector, as follows:

*   Find the four texels that would be used in a depth sampling operation with linear filtering, from [mip level](#mip-level) 0:

    *   Use the specified coordinate, array index (when present), and offset (when present).

    *   The texels are adjacent, forming a square, when considering their texture space coordinates (_u_,_v_).

    *   Selected texels at the texture edge, cube face edge, or cube corners are handled as in ordinary texture sampling.

*   For each texel, perform a comparison against the depth reference value, yielding a 0.0 or 1.0 value, as controlled by the comparison sampler parameters.

*   Yield the four-component vector where the components are the comparison results with the texels with relative texel coordinates as follows:

    *   Result component Relative texel coordinate x(_u_ min,_v_ max) y(_u_ max,_v_ max) z(_u_ max,_v_ min) w(_u_ min,_v_ min)

Parameterization Overload @must_use fn textureGatherCompare(t: texture_depth_2d, s: sampler_comparison, coords: vec2<f32>, depth_ref: f32) -> vec4<f32> @must_use fn textureGatherCompare(t: texture_depth_2d, s: sampler_comparison, coords: vec2<f32>, depth_ref: f32, offset: vec2<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureGatherCompare(t: texture_depth_2d_array, s: sampler_comparison, coords: vec2<f32>, array_index: A, depth_ref: f32) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureGatherCompare(t: texture_depth_2d_array, s: sampler_comparison, coords: vec2<f32>, array_index: A, depth_ref: f32, offset: vec2<i32>) -> vec4<f32> @must_use fn textureGatherCompare(t: texture_depth_cube, s: sampler_comparison, coords: vec3<f32>, depth_ref: f32) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureGatherCompare(t: texture_depth_cube_array, s: sampler_comparison, coords: vec3<f32>, array_index: A, depth_ref: f32) -> vec4<f32>

**Parameters:**

`t`The [depth](#texture-depth) texture to read from.
`s`The [sampler comparison](#sampler-type).
`coords`The texture coordinates.
`array_index`The 0-based texture array index.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`depth_ref`The reference value to compare the sampled depth value against.
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

A four component vector with comparison result for the selected texels, as described above.

EXAMPLE: Gather depth comparison

@group(0) @binding(0) var dt: texture_depth_2d;
@group(0) @binding(1) var s: sampler;

fn gather_depth_compare(c: vec2<f32>, depth_ref: f32) -> vec4<f32> {
  return textureGatherCompare(dt,s,c,depth_ref);
}

#### 17.7.4. `textureLoad`[](#textureload)

Reads a single texel from a texture without sampling or filtering.

Parameterization Overload C is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureLoad(t: texture_1d<ST>, coords: C, level: L) -> vec4<ST> C is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureLoad(t: texture_2d<ST>, coords: vec2<C>, level: L) -> vec4<ST> C is [i32](#i32), or [u32](#u32) A is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureLoad(t: texture_2d_array<ST>, coords: vec2<C>, array_index: A, level: L) -> vec4<ST> C is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureLoad(t: texture_3d<ST>, coords: vec3<C>, level: L) -> vec4<ST> C is [i32](#i32), or [u32](#u32) S is [i32](#i32), or [u32](#u32) ST is [i32](#i32), [u32](#u32), or [f32](#f32)@must_use fn textureLoad(t: texture_multisampled_2d<ST>, coords: vec2<C>, sample_index: S)-> vec4<ST> C is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32)@must_use fn textureLoad(t: texture_depth_2d, coords: vec2<C>, level: L) -> f32 C is [i32](#i32), or [u32](#u32) A is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32)@must_use fn textureLoad(t: texture_depth_2d_array, coords: vec2<C>, array_index: A, level: L) -> f32 C is [i32](#i32), or [u32](#u32) S is [i32](#i32), or [u32](#u32)@must_use fn textureLoad(t: texture_depth_multisampled_2d, coords: vec2<C>, sample_index: S)-> f32 C is [i32](#i32), or [u32](#u32)@must_use fn textureLoad(t: texture_external, coords: vec2<C>) -> vec4<f32> C is [i32](#i32), or [u32](#u32) AM is [read](#access-read) or [read_write](#access-read_write) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.@must_use fn textureLoad(t : texture_storage_1d<F, AM>, coords : C) -> vec4<CF> C is [i32](#i32), or [u32](#u32) AM is [read](#access-read) or [read_write](#access-read_write) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.@must_use fn textureLoad(t : texture_storage_2d<F, AM>, coords : vec2<C>) -> vec4<CF> C is [i32](#i32), or [u32](#u32) AM is [read](#access-read) or [read_write](#access-read_write) A is [i32](#i32) or [u32](#u32) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.@must_use fn textureLoad(t : texture_storage_2d_array<F, AM>, coords : vec2<C>, array_index : A) -> vec4<CF> C is [i32](#i32), or [u32](#u32) AM is [read](#access-read) or [read_write](#access-read_write) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.@must_use fn textureLoad(t : texture_storage_3d<F, AM>, coords : vec3<C>) -> vec4<CF>

**Parameters:**

`t`The [sampled](#type-sampled-texture), [multisampled](#type-multisampled-texture), [depth](#type-depth-texture), [storage](#type-storage-texture), or [external](#type-external-texture) texture
`coords`The 0-based texel coordinate.
`array_index`The 0-based texture array index.
`level`The [mip level](#mip-level), with level 0 containing a full size version of the texture.
`sample_index`The 0-based sample index of the [multisampled texture](#type-multisampled-texture).

**Returns:**

The unfiltered texel data.

The [logical texel address](#logical-texel-address) is invalid if:

*   any element of `coords` is outside the range `[0, textureDimensions(t, level))` for the corresponding element, or

*   `array_index` is outside the range `[0, textureNumLayers(t))`, or

*   `level` is outside the range `[0, textureNumLevels(t))`, or

*   `sample_index` is outside the range `[0, textureNumSamples(s))`

If the logical texel address is invalid, the built-in function returns one of:

*   The data for some texel within bounds of the texture.

*   For non-depth textures, either:

    *   The vector (0,0,0,0) or (0,0,0,1) of the appropriate type, with the [texture view swizzle](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-gputextureviewdescriptor-swizzle) applied, or

    *   The vector (0,0,0,0) or (0,0,0,1) of the appropriate type, without the [texture view swizzle](../WGPU/gpuweb-spec/gpuweb-spec.md#dom-gputextureviewdescriptor-swizzle) applied.

*   0.0 for depth textures.

#### 17.7.5. `textureNumLayers`[](#texturenumlayers)

Returns the number of layers (elements) of an [arrayed](#texture-arrayed) texture.

Parameterization Overload F is a [texel format](#texel-format) A is an [access mode](#access-mode) ST is [i32](#i32), [u32](#u32), or [f32](#f32) T is `texture_2d_array<ST>`, `texture_cube_array<ST>`, `texture_depth_2d_array`, `texture_depth_cube_array`, or `texture_storage_2d_array<F,A>`@must_use fn textureNumLayers(t: T) -> u32

**Parameters:**

`t`The [sampled](#type-sampled-texture), [depth](#type-depth-texture), or [storage texture](#type-storage-texture) array texture.

**Returns:**

If the texture is based on cubes, returns the number of cubes in the cube arrayed texture.

Otherwise returns the number of layers (homogeneous grids of texels) in the arrayed texture.

#### 17.7.6. `textureNumLevels`[](#texturenumlevels)

Returns the number of mip levels of a texture.

Parameterization Overload ST is [i32](#i32), [u32](#u32), or [f32](#f32) T is `texture_1d<ST>`, `texture_2d<ST>`, `texture_2d_array<ST>`, `texture_3d<ST>`, `texture_cube<ST>`, `texture_cube_array<ST>`, `texture_depth_2d`, `texture_depth_2d_array`, `texture_depth_cube`, or `texture_depth_cube_array`@must_use fn textureNumLevels(t: T) -> u32

**Parameters:**

`t`The [sampled](#type-sampled-texture) or [depth](#type-depth-texture) texture.

**Returns:**

The [mip level count](#texture-mip-level-count) for the texture.

#### 17.7.7. `textureNumSamples`[](#texturenumsamples)

Returns the number samples per texel in a [multisampled texture](#type-multisampled-texture).

Parameterization Overload ST is [i32](#i32), [u32](#u32), or [f32](#f32) T is `texture_multisampled_2d<ST>` or `texture_depth_multisampled_2d`@must_use fn textureNumSamples(t: T) -> u32

**Parameters:**

**Returns:**

The [sample count](#texture-sample-count) for the [multisampled texture](#type-multisampled-texture).

#### 17.7.8. `textureSample`[](#texturesample)

Samples a texture.

[Must](#shader-creation-error) only be used in a [fragment](#fragment) shader stage.

If [uniformity analysis](#uniformity-analysis) cannot prove a call to this function is in [uniform control flow](#uniform-control-flow), then a [derivative_uniformity](#trigger-derivative_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered).

Parameterization Overload @must_use fn textureSample(t: texture_1d<f32>, s: sampler, coords: f32) -> vec4<f32> @must_use fn textureSample(t: texture_2d<f32>, s: sampler, coords: vec2<f32>) -> vec4<f32> @must_use fn textureSample(t: texture_2d<f32>, s: sampler, coords: vec2<f32>, offset: vec2<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSample(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSample(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A, offset: vec2<i32>) -> vec4<f32> T is `texture_3d<f32>`, or `texture_cube<f32>`@must_use fn textureSample(t: T, s: sampler, coords: vec3<f32>) -> vec4<f32> @must_use fn textureSample(t: texture_3d<f32>, s: sampler, coords: vec3<f32>, offset: vec3<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSample(t: texture_cube_array<f32>, s: sampler, coords: vec3<f32>, array_index: A) -> vec4<f32> @must_use fn textureSample(t: texture_depth_2d, s: sampler, coords: vec2<f32>) -> f32 @must_use fn textureSample(t: texture_depth_2d, s: sampler, coords: vec2<f32>, offset: vec2<i32>) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSample(t: texture_depth_2d_array, s: sampler, coords: vec2<f32>, array_index: A) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSample(t: texture_depth_2d_array, s: sampler, coords: vec2<f32>, array_index: A, offset: vec2<i32>) -> f32 @must_use fn textureSample(t: texture_depth_cube, s: sampler, coords: vec3<f32>) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSample(t: texture_depth_cube_array, s: sampler, coords: vec3<f32>, array_index: A) -> f32

**Parameters:**

`t`The [sampled](#type-sampled-texture) or [depth](#type-depth-texture) texture to sample.
`s`The [sampler](#sampler) type.
`coords`The texture coordinates used for sampling.
`array_index`The 0-based texture array index to sample.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

The sampled value.

An [indeterminate value](#indeterminate-value) results if called in [non-uniform control flow](#uniform-control-flow).

#### 17.7.9. `textureSampleBias`[](#texturesamplebias)

Samples a texture with a bias to the mip level.

[Must](#shader-creation-error) only be used in a [fragment](#fragment) shader stage.

If [uniformity analysis](#uniformity-analysis) cannot prove a call to this function is in [uniform control flow](#uniform-control-flow), then a [derivative_uniformity](#trigger-derivative_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered).

Parameterization Overload @must_use fn textureSampleBias(t: texture_2d<f32>, s: sampler, coords: vec2<f32>, bias: f32) -> vec4<f32> @must_use fn textureSampleBias(t: texture_2d<f32>, s: sampler, coords: vec2<f32>, bias: f32, offset: vec2<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleBias(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A, bias: f32) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleBias(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A, bias: f32, offset: vec2<i32>) -> vec4<f32> T is `texture_3d<f32>`, or `texture_cube<f32>`@must_use fn textureSampleBias(t: T, s: sampler, coords: vec3<f32>, bias: f32) -> vec4<f32> @must_use fn textureSampleBias(t: texture_3d<f32>, s: sampler, coords: vec3<f32>, bias: f32, offset: vec3<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleBias(t: texture_cube_array<f32>, s: sampler, coords: vec3<f32>, array_index: A, bias: f32) -> vec4<f32>

**Parameters:**

`t`The [sampled texture](#type-sampled-texture) to sample.
`s`The [sampler](#type-sampler) type.
`coords`The texture coordinates used for sampling.
`array_index`The 0-based texture array index to sample.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`bias`The bias to apply to the mip level before sampling.  
 This value [will](#behavioral-requirements) be clamped in the range `[-16.0, 15.99]`.
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

The sampled value.

#### 17.7.10. `textureSampleCompare`[](#texturesamplecompare)

Samples a [depth texture](#type-depth-texture) and compares the sampled depth values against a reference value.

[Must](#shader-creation-error) only be used in a [fragment](#fragment) shader stage.

If [uniformity analysis](#uniformity-analysis) cannot prove a call to this function is in [uniform control flow](#uniform-control-flow), then a [derivative_uniformity](#trigger-derivative_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered).

Parameterization Overload @must_use fn textureSampleCompare(t: texture_depth_2d, s: sampler_comparison, coords: vec2<f32>, depth_ref: f32) -> f32 @must_use fn textureSampleCompare(t: texture_depth_2d, s: sampler_comparison, coords: vec2<f32>, depth_ref: f32, offset: vec2<i32>) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleCompare(t: texture_depth_2d_array, s: sampler_comparison, coords: vec2<f32>, array_index: A, depth_ref: f32) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleCompare(t: texture_depth_2d_array, s: sampler_comparison, coords: vec2<f32>, array_index: A, depth_ref: f32, offset: vec2<i32>) -> f32 @must_use fn textureSampleCompare(t: texture_depth_cube, s: sampler_comparison, coords: vec3<f32>, depth_ref: f32) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleCompare(t: texture_depth_cube_array, s: sampler_comparison, coords: vec3<f32>, array_index: A, depth_ref: f32) -> f32

**Parameters:**

`t`The [depth texture](#type-depth-texture) to sample.
`s`The [sampler_comparison](#type-sampler_comparison) type.
`coords`The texture coordinates used for sampling.
`array_index`The 0-based texture array index to sample.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`depth_ref`The reference value to compare the sampled depth value against.
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

A value in the range `[0.0..1.0]`.

Each sampled texel is compared against the reference value using the comparison operator defined by the `sampler_comparison`, resulting in either a `0` or `1` value for each texel.

If the sampler uses bilinear filtering then the returned value is the filtered average of these values, otherwise the comparison result of a single texel is returned.

An [indeterminate value](#indeterminate-value) results if called in [non-uniform control flow](#uniform-control-flow).

#### 17.7.11. `textureSampleCompareLevel`[](#texturesamplecomparelevel)

Samples a [depth texture](#type-depth-texture) and compares the sampled depth values against a reference value.

Parameterization Overload @must_use fn textureSampleCompareLevel(t: texture_depth_2d, s: sampler_comparison, coords: vec2<f32>, depth_ref: f32) -> f32 @must_use fn textureSampleCompareLevel(t: texture_depth_2d, s: sampler_comparison, coords: vec2<f32>, depth_ref: f32, offset: vec2<i32>) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleCompareLevel(t: texture_depth_2d_array, s: sampler_comparison, coords: vec2<f32>, array_index: A, depth_ref: f32) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleCompareLevel(t: texture_depth_2d_array, s: sampler_comparison, coords: vec2<f32>, array_index: A, depth_ref: f32, offset: vec2<i32>) -> f32 @must_use fn textureSampleCompareLevel(t: texture_depth_cube, s: sampler_comparison, coords: vec3<f32>, depth_ref: f32) -> f32 A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleCompareLevel(t: texture_depth_cube_array, s: sampler_comparison, coords: vec3<f32>, array_index: A, depth_ref: f32) -> f32

**Parameters:**

`t`The [depth texture](#type-depth-texture) to sample.
`s`The [sampler_comparison](#type-sampler_comparison) type.
`coords`The texture coordinates used for sampling.
`array_index`The 0-based texture array index to sample.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`depth_ref`The reference value to compare the sampled depth value against.
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

A value in the range `[0.0..1.0]`.

The `textureSampleCompareLevel` function is the same as `textureSampleCompare`, except that:

*   `textureSampleCompareLevel` always samples texels from mip level 0.

    *   The function does not compute derivatives.

    *   There is no requirement for `textureSampleCompareLevel` to be invoked in [uniform control flow](#uniform-control-flow).

*   `textureSampleCompareLevel` may be invoked in any shader stage.

#### 17.7.12. `textureSampleGrad`[](#texturesamplegrad)

Samples a texture using explicit gradients.

Parameterization Overload @must_use fn textureSampleGrad(t: texture_2d<f32>, s: sampler, coords: vec2<f32>, ddx: vec2<f32>, ddy: vec2<f32>) -> vec4<f32> @must_use fn textureSampleGrad(t: texture_2d<f32>, s: sampler, coords: vec2<f32>, ddx: vec2<f32>, ddy: vec2<f32>, offset: vec2<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleGrad(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A, ddx: vec2<f32>, ddy: vec2<f32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleGrad(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A, ddx: vec2<f32>, ddy: vec2<f32>, offset: vec2<i32>) -> vec4<f32> T is `texture_3d<f32>`, or `texture_cube<f32>`@must_use fn textureSampleGrad(t: T, s: sampler, coords: vec3<f32>, ddx: vec3<f32>, ddy: vec3<f32>) -> vec4<f32> @must_use fn textureSampleGrad(t: texture_3d<f32>, s: sampler, coords: vec3<f32>, ddx: vec3<f32>, ddy: vec3<f32>, offset: vec3<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleGrad(t: texture_cube_array<f32>, s: sampler, coords: vec3<f32>, array_index: A, ddx: vec3<f32>, ddy: vec3<f32>) -> vec4<f32>

**Parameters:**

`t`The [sampled texture](#type-sampled-texture) to sample.
`s`The [sampler](#type-sampler).
`coords`The texture coordinates used for sampling.
`array_index`The 0-based texture array index to sample.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`ddx`The x direction derivative vector used to compute the sampling locations.
`ddy`The y direction derivative vector used to compute the sampling locations.
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

The sampled value.

#### 17.7.13. `textureSampleLevel`[](#texturesamplelevel)

Samples a texture using an explicit mip level.

Parameterization Overload @must_use fn textureSampleLevel(t: texture_1d<f32>, s: sampler, coords: f32, level: f32) -> vec4<f32> @must_use fn textureSampleLevel(t: texture_2d<f32>, s: sampler, coords: vec2<f32>, level: f32) -> vec4<f32> @must_use fn textureSampleLevel(t: texture_2d<f32>, s: sampler, coords: vec2<f32>, level: f32, offset: vec2<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A, level: f32) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_2d_array<f32>, s: sampler, coords: vec2<f32>, array_index: A, level: f32, offset: vec2<i32>) -> vec4<f32> T is `texture_3d<f32>`, or `texture_cube<f32>`@must_use fn textureSampleLevel(t: T, s: sampler, coords: vec3<f32>, level: f32) -> vec4<f32> @must_use fn textureSampleLevel(t: texture_3d<f32>, s: sampler, coords: vec3<f32>, level: f32, offset: vec3<i32>) -> vec4<f32> A is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_cube_array<f32>, s: sampler, coords: vec3<f32>, array_index: A, level: f32) -> vec4<f32> L is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_depth_2d, s: sampler, coords: vec2<f32>, level: L) -> f32 L is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_depth_2d, s: sampler, coords: vec2<f32>, level: L, offset: vec2<i32>) -> f32 A is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_depth_2d_array, s: sampler, coords: vec2<f32>, array_index: A, level: L) -> f32 A is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_depth_2d_array, s: sampler, coords: vec2<f32>, array_index: A, level: L, offset: vec2<i32>) -> f32 L is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_depth_cube, s: sampler, coords: vec3<f32>, level: L) -> f32 A is [i32](#i32), or [u32](#u32) L is [i32](#i32), or [u32](#u32)@must_use fn textureSampleLevel(t: texture_depth_cube_array, s: sampler, coords: vec3<f32>, array_index: A, level: L) -> f32

**Parameters:**

`t`The [sampled](#type-sampled-texture) or [depth](#type-depth-texture) texture to sample.
`s`The [sampler](#sampler) type.
`coords`The texture coordinates used for sampling.
`array_index`The 0-based texture array index to sample.  
 This value [will](#behavioral-requirements) be clamped to the range `[0, textureNumLayers(t) - 1]`.
`level`The mip level, with level 0 containing a full size version of the texture. For the functions where `level` is a `f32`, fractional values may interpolate between two levels if the format is filterable according to the [Texture Format Capabilities](../WGPU/gpuweb-spec/gpuweb-spec.md#texture-format-caps).
`offset`The optional texel offset applied to the unnormalized texture coordinate before sampling the texture. This offset is applied before applying any texture wrapping modes.  
 The `offset` expression [must](#shader-creation-error) be a [const-expression](#const-expressions) (e.g. `vec2<i32>(1, 2)`).  
 Each `offset` component [must](#shader-creation-error) be at least `-8` and at most `7`. Values outside of this range will result in a [shader-creation error](#shader-creation-error).

**Returns:**

The sampled value.

#### 17.7.14. `textureSampleBaseClampToEdge`[](#textureSampleBaseClampToEdge)

Samples a texture view at its base level, with texture coordinates clamped to the edge as described below.

Parameterization Overload T is `texture_2d<f32>` or `texture_external`@must_use fn textureSampleBaseClampToEdge(t: T, s: sampler, coords: vec2<f32>) -> vec4<f32>

**Parameters:**

`t`The [sampled](#type-sampled-texture) or [external](#type-external-texture) texture to sample.
`s`The [sampler](#type-sampler) type.
`coords`The texture coordinates used for sampling. 
Before sampling, the given coordinates [will](#behavioral-requirements) be clamped to the rectangle

> [ _half\_texel_, 1 - _half\_texel_]

where

> _half\_texel_= vec2(0.5) / vec2<f32>(textureDimensions(t))

Note: The half-texel adjustment ensures that, independent of the sampler’s `addressing` and `filter` modes, wrapping will not occur. That is, when sampling near an edge, the sampled texels will be at or adjacent to that edge, and not selected from the opposite edge.

**Returns:**

The sampled value.

#### 17.7.15. `textureStore`[](#texturestore)

Writes a single texel to a texture.

Parameterization Overload F is a [texel format](#texel-format) C is [i32](#i32), or [u32](#u32) AM is [write](#access-write) or [read_write](#access-read_write) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.fn textureStore(t: texture_storage_1d<F,AM>, coords: C, value: vec4<CF>) F is a [texel format](#texel-format) C is [i32](#i32), or [u32](#u32) AM is [write](#access-write) or [read_write](#access-read_write) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.fn textureStore(t: texture_storage_2d<F,AM>, coords: vec2<C>, value: vec4<CF>) F is a [texel format](#texel-format) C is [i32](#i32), or [u32](#u32) AM is [write](#access-write) or [read_write](#access-read_write) A is [i32](#i32), or [u32](#u32) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.fn textureStore(t: texture_storage_2d_array<F,AM>, coords: vec2<C>, array_index: A, value: vec4<CF>) F is a [texel format](#texel-format) C is [i32](#i32), or [u32](#u32) AM is [write](#access-write) or [read_write](#access-read_write) CF depends on the storage texel format F. [See the texel format table](#storage-texel-formats) for the mapping of texel format to channel format.fn textureStore(t: texture_storage_3d<F,AM>, coords: vec3<C>, value: vec4<CF>)

**Parameters:**

`t`The [write-only storage texture](#type-write-only-storage-texture) or [read-write storage texture](#type-read-write-storage-texture)
`coords`The 0-based texel coordinate.
`array_index`The 0-based texture array index.
`value`The new texel value. `value` is converted using the [inverse channel transfer function](#inverse-channel-transfer-function).

**Note:**

The [logical texel address](#logical-texel-address) is invalid if:

*   any element of `coords` is outside the range `[0, textureDimensions(t))` for the corresponding element, or

*   `array_index` is outside the range of `[0, textureNumLayers(t))`

If the logical texel address is invalid, the built-in function [will](#behavioral-requirements) not be executed.

### 17.8. Atomic Built-in Functions[](#atomic-builtin-functions)

Atomic built-in functions can be used to read/write/read-modify-write atomic objects. They are the only operations allowed on [§ 6.2.8 Atomic Types](#atomic-types).

All atomic built-in functions use a `relaxed`[memory ordering](#memory-semantics). This means synchronization and ordering guarantees only apply among atomic operations acting on the same [memory locations](#memory-locations). No synchronization or ordering guarantees apply between atomic and non-atomic memory accesses, or between atomic accesses acting on different memory locations.

Atomic built-in functions [must not](#shader-creation-error) be used in a [vertex](#vertex) shader stage.

The address space `AS` of the `atomic_ptr` parameter in all atomic built-in functions [must](#shader-creation-error) be either [storage](#address-spaces-storage) or [workgroup](#address-spaces-workgroup).

Unless otherwise specified, T[must](#shader-creation-error) be either [u32](#u32) or [i32](#i32).

#### 17.8.1. `atomicLoad`[](#atomic-load)

fn atomicLoad(atomic_ptr: ptr<AS, atomic<T>, read_write>) -> T

Returns the atomically loaded the value pointed to by `atomic_ptr`. It does not [modify](#atomic-modification) the object.

#### 17.8.2. `atomicStore`[](#atomic-store)

fn atomicStore(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T)

Atomically stores the value `v` in the atomic object pointed to by `atomic_ptr`.

#### 17.8.3. Atomic Read-modify-write Arithmetic and Logical Functions[](#atomic-rmw)

Each function performs the following steps atomically:

1.   Load the original value pointed to by `atomic_ptr`.

2.   Obtains a new value by performing the operation (e.g. max) from the function name with the value v.

3.   Store the new value using `atomic_ptr`.

Each function returns the original value stored in the atomic object before the operation.

##### 17.8.3.1. `atomicAdd`[](#atomic-add)

fn atomicAdd(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically performs an addition operation on the atomic object pointed to by `atomic_ptr` with the value `v`, and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic addition as a function

// All operations are performed atomically
fn atomicAdd(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = old + v;
  return old;
}

##### 17.8.3.2. `atomicSub`[](#atomic-sub)

fn atomicSub(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically performs a subtraction operation on the atomic object pointed to by `atomic_ptr` with the value `v`, and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic subtraction as a function

// All operations are performed atomically
fn atomicSub(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = old - v;
  return old;
}

##### 17.8.3.3. `atomicMax`[](#atomic-max)

fn atomicMax(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically performs a maximum operation on the atomic object pointed to by `atomic_ptr` with the value `v`, and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic maximum as a function

// All operations are performed atomically
fn atomicMax(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = max(old, v);
  return old;
}

##### 17.8.3.4. `atomicMin`[](#atomic-min)

fn atomicMin(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically performs a minimum operation on the atomic object pointed to by `atomic_ptr` with the value `v`, and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic minimum as a function

// All operations are performed atomically
fn atomicMin(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = min(old, v);
  return old;
}

##### 17.8.3.5. `atomicAnd`[](#atomic-and)

fn atomicAnd(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically performs a bitwise AND operation on the atomic object pointed to by `atomic_ptr` with the value `v`, and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic bitwise and as a function

// All operations are performed atomically
fn atomicAnd(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = old & v;
  return old;
}

##### 17.8.3.6. `atomicOr`[](#atomic-or)

fn atomicOr(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically performs a bitwise OR operation on the atomic object pointed to by `atomic_ptr` with the value `v`, and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic bitwise or as a function

// All operations are performed atomically
fn atomicOr(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = old | v;
  return old;
}

##### 17.8.3.7. `atomicXor`[](#atomic-xor)

fn atomicXor(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically performs a bitwise XOR operation on the atomic object pointed to by `atomic_ptr` with the value `v`, and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic bitwise xor as a function

// All operations are performed atomically
fn atomicXor(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = old ^ v;
  return old;
}

#### 17.8.4. `atomicExchange`[](#atomic-exchange)

fn atomicExchange(atomic_ptr: ptr<AS, atomic<T>, read_write>, v: T) -> T

Atomically stores the value `v` in the atomic object pointed to by `atomic_ptr` and returns the original value stored in the atomic object before the operation.

EXAMPLE: Operation of atomic exchange as a function

// All operations are performed atomically
fn atomicExchange(atomic_ptr: ptr<AS, atomic<T>, read_write>, v : T) -> T {
  let old = *atomic_ptr;
  *atomic_ptr = v;
  return old;
}

#### 17.8.5. `atomicCompareExchangeWeak`[](#atomic-compare-exchange-weak)

fn atomicCompareExchangeWeak(
      atomic_ptr: ptr<AS, atomic<T>, read_write>,
      cmp: T,
      v: T) -> __atomic_compare_exchange_result<T>

struct __atomic_compare_exchange_result<T> {
  old_value : T,   // old value stored in the atomic
  exchanged : bool // true if the exchange was done
}

Note: A value cannot be explicitly declared with the type `__atomic_compare_exchange_result`, but a value may infer the type.

Performs the following steps atomically:

1.   Load the original value pointed to by `atomic_ptr`.

2.   Compare the original value to the value `cmp` using an equality operation.

3.   Store the value `v``only if` the result of the equality comparison was `true`.

Returns a two member structure, where the first member, `old_value`, is the original value of the atomic object before the operation and the second member, `exchanged`, is whether or not the comparison succeeded.

EXAMPLE: Operation of atomic compare exchange as a function

// All operations are performed atomically
fn atomicCompareExchangeWeak(atomic_ptr: ptr<AS, atomic<T>, read_write>, cmp : T, v : T) ->
  _atomic_compare_exchange_result<T> {
  let old = *atomic_ptr;
  // This comparison may spuriously fail.
  let comparison = old == cmp;
  if comparison {
    *atomic_ptr = v;
  }
  return __atomic_compare_exchange_result<T>(old, comparison);
}

Note: The equality comparison may spuriously fail on some implementations. That is, the `exchanged` member of the result structure may be `false` even if the `old_value` member equals `cmp`.

#### 17.8.6. Atomic Store Min and Max Functions[](#atomic-store-min-max)

These functions all require the [atomic_vec2u_min_max](#language_extension-atomic_vec2u_min_max) language feature.

The functions do not return a value.

##### 17.8.6.1. `atomicStoreMin`[](#atomic-store-min)

fn atomicStoreMin(atomic_ptr: ptr<storage, atomic<vec2<u32>>, read_write>,
                  v: vec2<u32>)

Atomically performs a 64-bit unsigned integer minimum operation on the atomic object pointed to by `atomic_ptr` with the value `v`.

Performs the following steps atomically:

1.   Load the original [vec2u](#vec2u) value old from the memory referenced by atomic_ptr.

2.   Compute the 64-bit unsigned integer values:

    *   old64 = 2 32 × old[1] + old[0]

    *   v64 = 2 32 × v[1] + v[0]

3.   Compute value new64 as the minimum of old64 and v64.

4.   Compute value new of type vec2<u32>, where:

    *   new[0] contains the least significant 32 bits of new64, and

    *   new[1] contains the 32 most significant bits of new64.

5.   Store new into the memory referenced by atomic_ptr.

##### 17.8.6.2. `atomicStoreMax`[](#atomic-store-max)

fn atomicStoreMax(atomic_ptr: ptr<storage, atomic<vec2<u32>>, read_write>, v: vec2<u32>)

Atomically performs a 64-bit unsigned integer maximum operation on the atomic object pointed to by `atomic_ptr` with the value `v`.

Performs the following steps atomically:

1.   Load the original [vec2u](#vec2u) value old from the memory referenced by atomic_ptr.

2.   Compute the 64-bit unsigned integer values:

    *   old64 = 2 32 × old[1] + old[0]

    *   v64 = 2 32 × v[1] + v[0]

3.   Compute value new64 as the maximum of old64 and v64.

4.   Compute value new of type vec2<u32>, where:

    *   new[0] contains the least significant 32 bits of new64, and

    *   new[1] contains the 32 most significant bits of new64.

5.   Store new into the memory referenced by atomic_ptr.

### 17.9. Data Packing Built-in Functions[](#pack-builtin-functions)

Data packing builtin functions can be used to encode values using data formats that do not correspond directly to types in WGSL. This enables a program to write many densely packed values to memory, which can reduce a shader’s memory bandwidth demand.

Each builtin applies the _inverse_ of a [channel transfer function](#channel-transfer-function) to several input values, then combines their results into a single output value.

Note: For packing unorm values, the normalized floating point values are in the interval [0.0, 1.0].

Note: For packing snorm values, the normalized floating point values are in the interval [-1.0, 1.0].

#### 17.9.1. `pack4x8snorm`[](#pack4x8snorm-builtin)

Overload@const @must_use fn pack4x8snorm(e: vec4<f32>) -> u32
Description Converts four normalized floating point values to 8-bit signed integers, and then combines them into one `u32` value. 
Component `e[i]` of the input is converted to an 8-bit twos complement integer value ⌊ 0.5 + 127 × min(1, max(-1, e[i])) ⌋ which is then placed in bits 8 × `i` through 8 × `i` + 7 of the result.

#### 17.9.2. `pack4x8unorm`[](#pack4x8unorm-builtin)

Overload@const @must_use fn pack4x8unorm(e: vec4<f32>) -> u32
Description Converts four normalized floating point values to 8-bit unsigned integers, and then combines them into one `u32` value. 
Component `e[i]` of the input is converted to an 8-bit unsigned integer value ⌊ 0.5 + 255 × min(1, max(0, e[i])) ⌋ which is then placed in bits 8 × `i` through 8 × `i` + 7 of the result.

#### 17.9.3. `pack4xI8`[](#pack4xI8-builtin)

Overload@const @must_use fn pack4xI8(e: vec4<i32>) -> u32
Description Pack the lower 8 bits of each component of `e` into a [u32](#u32) value and drop all the unused bits. 
Component `e[i]` of the input is mapped to bits 8 × `i` through 8 × `i` + 7 of the result.

#### 17.9.4. `pack4xU8`[](#pack4xU8-builtin)

Overload@const @must_use fn pack4xU8(e: vec4<u32>) -> u32
Description Pack the lower 8 bits of each component of `e` into a [u32](#u32) value and drop all the unused bits. 
Component `e[i]` of the input is mapped to bits 8 × `i` through 8 × `i` + 7 of the result.

#### 17.9.5. `pack4xI8Clamp`[](#pack4xI8Clamp-builtin)

Overload@const @must_use fn pack4xI8Clamp(e: vec4<i32>) -> u32
Description Clamp each component of `e` in the range [-128, 127] and then pack the lower 8 bits of each component into a [u32](#u32) value. 
Component `e[i]` of the input is mapped to bits 8 × `i` through 8 × `i` + 7 of the result.

#### 17.9.6. `pack4xU8Clamp`[](#pack4xU8Clamp-builtin)

Overload@const @must_use fn pack4xU8Clamp(e: vec4<u32>) -> u32
Description Clamp each component of `e` in the range of [0, 255] and then pack the lower 8 bits of each component into a [u32](#u32) value. 
Component `e[i]` of the input is mapped to bits 8 × `i` through 8 × `i` + 7 of the result.

#### 17.9.7. `pack2x16snorm`[](#pack2x16snorm-builtin)

Overload@const @must_use fn pack2x16snorm(e: vec2<f32>) -> u32
Description Converts two normalized floating point values to 16-bit signed integers, and then combines them into one `u32` value.  
 Component `e[i]` of the input is converted to a 16-bit twos complement integer value ⌊ 0.5 + 32767 × min(1, max(-1, e[i])) ⌋ which is then placed in bits 16 × `i` through 16 × `i` + 15 of the result.

#### 17.9.8. `pack2x16unorm`[](#pack2x16unorm-builtin)

Overload@const @must_use fn pack2x16unorm(e: vec2<f32>) -> u32
Description Converts two normalized floating point values to 16-bit unsigned integers, and then combines them into one `u32` value.  
 Component `e[i]` of the input is converted to a 16-bit unsigned integer value ⌊ 0.5 + 65535 × min(1, max(0, e[i])) ⌋ which is then placed in bits 16 × `i` through 16 × `i` + 15 of the result.

#### 17.9.9. `pack2x16float`[](#pack2x16float-builtin)

Overload@const @must_use fn pack2x16float(e: vec2<f32>) -> u32
Description Converts two floating point values to half-precision floating point numbers, and then combines them into one `u32` value.  
 Component `e[i]` of the input is converted to a [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary16](#ieee754-binary16) value, which is then placed in bits 16 × `i` through 16 × `i` + 15 of the result. See [§ 15.7.6 Floating Point Conversion](#floating-point-conversion). 
If either `e[0]` or `e[1]` is outside the [finite range](#finite-range) of binary16 then:

*   It is a [shader-creation error](#shader-creation-error) if `e` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `e` is an [override-expression](#override-expressions).

*   Otherwise the result is an [indeterminate value](#indeterminate-value) for u32.

### 17.10. Data Unpacking Built-in Functions[](#unpack-builtin-functions)

Data unpacking builtin functions can be used to decode values in data formats that do not correspond directly to types in WGSL. This enables a program to read many densely packed values from memory, which can reduce a shader’s memory bandwidth demand.

Each builtin breaks up an input value into channels, then applies a [channel transfer function](#channel-transfer-function) to each.

Note: For unpacking unorm values, the normalized floating point result is in the interval [0.0, 1.0].

Note: For unpacking snorm values, the normalized floating point result is in the interval [-1.0, 1.0].

#### 17.10.1. `unpack4x8snorm`[](#unpack4x8snorm-builtin)

Overload@const @must_use fn unpack4x8snorm(e: u32) -> vec4<f32>
Description Decomposes a 32-bit value into four 8-bit chunks, then reinterprets each chunk as a signed normalized floating point value.  
 Component `i` of the result is max(v ÷ 127, -1), where `v` is the interpretation of bits 8×`i` through 8×`i + 7` of `e` as a twos-complement signed integer.

#### 17.10.2. `unpack4x8unorm`[](#unpack4x8unorm-builtin)

Overload@const @must_use fn unpack4x8unorm(e: u32) -> vec4<f32>
Description Decomposes a 32-bit value into four 8-bit chunks, then reinterprets each chunk as an unsigned normalized floating point value.  
 Component `i` of the result is `v` ÷ 255, where `v` is the interpretation of bits 8×`i` through 8×`i + 7` of `e` as an unsigned integer.

#### 17.10.3. `unpack4xI8`[](#unpack4xI8-builtin)

Overload@const @must_use fn unpack4xI8(e: u32) -> vec4<i32>
Description`e` is interpreted as a vector with four 8-bit signed integer components. Unpack `e` into a vec4<i32> with sign extension.

#### 17.10.4. `unpack4xU8`[](#unpack4xU8-builtin)

Overload@const @must_use fn unpack4xU8(e: u32) -> vec4<u32>
Description`e` is interpreted as a vector with four 8-bit unsigned integer components. Unpack `e` into a vec4<u32> with zero extension.

#### 17.10.5. `unpack2x16snorm`[](#unpack2x16snorm-builtin)

Overload@const @must_use fn unpack2x16snorm(e: u32) -> vec2<f32>
Description Decomposes a 32-bit value into two 16-bit chunks, then reinterprets each chunk as a signed normalized floating point value.  
 Component `i` of the result is max(v ÷ 32767, -1), where `v` is the interpretation of bits 16×`i` through 16×`i + 15` of `e` as a twos-complement signed integer.

#### 17.10.6. `unpack2x16unorm`[](#unpack2x16unorm-builtin)

Overload@const @must_use fn unpack2x16unorm(e: u32) -> vec2<f32>
Description Decomposes a 32-bit value into two 16-bit chunks, then reinterprets each chunk as an unsigned normalized floating point value.  
 Component `i` of the result is `v` ÷ 65535, where `v` is the interpretation of bits 16×`i` through 16×`i + 15` of `e` as an unsigned integer.

#### 17.10.7. `unpack2x16float`[](#unpack2x16float-builtin)

Overload@const @must_use fn unpack2x16float(e: u32) -> vec2<f32>
Description Decomposes a 32-bit value into two 16-bit chunks, and reinterpets each chunk as a floating point value.  
 Component `i` of the result is the f32 representation of `v`, where `v` is the interpretation of bits 16×`i` through 16×`i + 15` of `e` as an [IEEE-754](#biblio-ieee-754 "IEEE Standard for Floating-Point Arithmetic")[binary16](#ieee754-binary16) value. See [§ 15.7.6 Floating Point Conversion](#floating-point-conversion).

### 17.11. Synchronization Built-in Functions[](#sync-builtin-functions)

All synchronization functions execute a [control barrier](#control-barrier) with Acquire/Release [memory ordering](#memory-semantics). That is, all synchronization functions, and affected memory and atomic operations are ordered in [program order](#program-order) relative to the synchronization function. Additionally, the affected memory and atomic operations program-ordered before the synchronization function must be visible to all other threads in the workgroup before any affected memory or atomic operation program-ordered after the synchronization function is executed by a member of the workgroup.

All synchronization functions use the `Workgroup`[memory scope](#memory-scope).  
 All synchronization functions have a `Workgroup`[execution scope](#execution-scope).  
 All synchronization functions [must](#shader-creation-error) only be used in the [compute](#compute) shader stage. All synchronization functions [must](#shader-creation-error) only be invoked in [uniform control flow](#uniform-control-flow).

#### 17.11.1. `storageBarrier`[](#storageBarrier-builtin)

Overload fn storageBarrier()
Description Executes a [control barrier](#control-barrier) synchronization function that affects memory and atomic operations in the [storage](#address-spaces-storage) address space.

#### 17.11.2. `textureBarrier`[](#textureBarrier-builtin)

Overload fn textureBarrier()
Description Executes a [control barrier](#control-barrier) synchronization function that affects memory operations in the [handle](#address-spaces-handle) address space.

#### 17.11.3. `workgroupBarrier`[](#workgroupBarrier-builtin)

Overload fn workgroupBarrier()
Description Executes a [control barrier](#control-barrier) synchronization function that affects memory and atomic operations in the [workgroup](#address-spaces-workgroup) address space.

#### 17.11.4. `workgroupUniformLoad`[](#workgroupUniformLoad-builtin)

Overload@must_use fn workgroupUniformLoad(p : ptr<workgroup, T>) -> T
Parameterization`T` is a [concrete](#type-concrete)[constructible](#constructible) type.
Description Returns the value pointed to by `p` to all invocations in the workgroup. The return value is [uniform](#uniform-value). `p`[must](#shader-creation-error) be a [uniform value](#uniform-value). 
Executes a [control barrier](#control-barrier) synchronization function that affects memory and atomic operations in the [workgroup](#address-spaces-workgroup) address space.

Overload@must_use fn workgroupUniformLoad(p : ptr<workgroup, atomic<T>, read_write>) -> T
Description Atomically loads the value pointed to by `p` and returns it to all invocations in the workgroup. The return value is [uniform](#uniform-value). `p`[must](#shader-creation-error) be a [uniform value](#uniform-value). 
Executes a [control barrier](#control-barrier) synchronization function that affects memory and atomic operations in the [workgroup](#address-spaces-workgroup) address space.

### 17.12. Subgroup Built-in Functions[](#subgroup-builtin-functions)

See [§ 15.6.3 Subgroup Operations](#subgroup-ops).

Calls to these functions:

*   [Must](#shader-creation-error) only be used in a [fragment](#fragment) or [compute](#compute) shader stage.

*   [Trigger](#triggered) a [subgroup_uniformity](#trigger-subgroup_uniformity)[diagnostic](#diagnostic) if [uniformity analysis](#uniformity-analysis) cannot prove the call is in [uniform control flow](#uniform-control-flow).

Note: For the [compute shader stage](#compute-shader-stage), the scope of uniform control flow is the [workgroup](#compute-shader-stage-workgroup). For the [fragment shader stage](#fragment-shader-stage), the scope of uniform control flow is the [draw command](#draw-command). Both of these scopes are larger than [subgroup](#subgroup).

#### 17.12.1. `subgroupAdd`[](#subgroupadd-builtin)

Overload@must_use fn subgroupAdd(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Reduction operation. 
Returns the sum of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

##### 17.12.1.1. `subgroupExclusiveAdd`[](#subgroupexclusiveadd-builtin)

Overload@must_use fn subgroupExclusiveAdd(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Exclusive prefix scan operation. 
Returns the sum of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup) whose [subgroup invocation IDs](#subgroup-invocation-id) are less than the current invocation’s id.

The value returned for the invocation with the lowest id among active invocations is `T(0)`.

##### 17.12.1.2. `subgroupInclusiveAdd`[](#subgroupinclusiveadd-builtin)

Overload@must_use fn subgroupInclusiveAdd(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Inclusive prefix scan operation. 
Returns the sum of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup) whose [subgroup invocation IDs](#subgroup-invocation-id) are less than or equal to the current invocation’s id.

Note: equivalent to `subgroupExclusiveAdd(x) + x`.

#### 17.12.2. `subgroupAll`[](#subgroupall-builtin)

Overload@must_use fn subgroupAll(e : bool) -> bool
Description Returns `true` if `e` is `true` for all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

#### 17.12.3. `subgroupAnd`[](#subgroupand-builtin)

Overload@must_use fn subgroupAnd(e : T) -> T
Preconditions`T` is i32, u32, vecN<i32>, or vecN<u32>
Description Reduction operation. 
Returns the bitwise and (`&`) of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

#### 17.12.4. `subgroupAny`[](#subgroupany-builtin)

Overload@must_use fn subgroupAny(e : bool) -> bool
Description Returns `true` if `e` is `true` for any [active](#subgroups-active) invocations in the [subgroup](#subgroup).

#### 17.12.5. `subgroupBallot`[](#subgroupballot-builtin)

Overload@must_use fn subgroupBallot(pred : bool) -> vec4<u32>
Description Returns a bitmask of the [active](#subgroups-active) invocations in the [subgroup](#subgroup) for whom `pred` is `true`. 
The x component of the return value contains invocations 0 through 31.  
 The y component of the return value contains invocations 32 through 63.  
 The z component of the return value contains invocations 64 through 95.  
 The w component of the return value contains invocations 96 through 127.

Within each component, the IDs are in ascending order by bit position (e.g. ID 32 is at bit position 0 in the y component).

#### 17.12.6. `subgroupBroadcast`[](#subgroupbroadcast-builtin)

Overload@must_use fn subgroupBroadcast(e : T, id : I) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)  
`I` is [u32](#u32) or [i32](#i32)
Description Returns the value of `e` from the invocation whose [subgroup invocation ID](#subgroup-invocation-id) matches `id` in the subgroup to all [active](#subgroups-active) invocations in the [subgroup](#subgroup). 
`id`[must](#shader-creation-error) be a [const-expression](#const-expressions) in the range [0, 128).

It is a [dynamic error](#dynamic-error) if `id` does not select an [active](#subgroups-active) invocation.

Note: If a non-constant version of `id` is required, use [subgroupShuffle](#subgroupshuffle-builtin) instead.

##### 17.12.6.1. `subgroupBroadcastFirst`[](#subgroupbroadcastfirst-builtin)

Overload@must_use fn subgroupBroadcastFirst(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Returns the value of `e` from the invocation that has the lowest [subgroup invocation ID](#subgroup-invocation-id) among [active](#subgroups-active) invocations in the [subgroup](#subgroup) to all active invocations in the subgroup.

#### 17.12.7. `subgroupElect`[](#subgroupelect-builtin)

Overload@must_use fn subgroupElect() -> bool
Description Returns `true` if the current invocation has the lowest [subgroup invocation ID](#subgroup-invocation-id) among [active](#subgroups-active) invocations in the [subgroup](#subgroup).

#### 17.12.8. `subgroupMax`[](#subgroupmax-builtin)

Overload@must_use fn subgroupMax(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Reduction operation. 
Returns the maximum value of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

#### 17.12.9. `subgroupMin`[](#subgroupmin-builtin)

Overload@must_use fn subgroupMin(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Reduction operation. 
Returns the minimum value of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

#### 17.12.10. `subgroupMul`[](#subgroupmul-builtin)

Overload@must_use fn subgroupMul(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Reduction operation. 
Returns the product of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

##### 17.12.10.1. `subgroupExclusiveMul`[](#subgroupexclusivemul-builtin)

Overload@must_use fn subgroupExclusiveMul(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Exclusive prefix scan operation. 
Returns the product of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup) whose [subgroup invocation IDs](#subgroup-invocation-id) are less than the current invocation’s id.

The value returned for the invocation with the lowest id among active invocations is `T(1)`.

##### 17.12.10.2. `subgroupInclusiveMul`[](#subgroupinclusivemul-builtin)

Overload@must_use fn subgroupInclusiveMul(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Inclusive prefix scan operation. 
Returns the product of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup) whose [subgroup invocation IDs](#subgroup-invocation-id) are less than or equal to the current invocation’s id.

Note: equivalent to `subgroupExclusiveMul(x) * x`.

#### 17.12.11. `subgroupOr`[](#subgroupor-builtin)

Overload@must_use fn subgroupOr(e : T) -> T
Preconditions`T` is i32, u32, vecN<i32>, or vecN<u32>
Description Reduction operation. 
Returns the bitwise or (`|`) of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

#### 17.12.12. `subgroupShuffle`[](#subgroupshuffle-builtin)

Overload@must_use fn subgroupShuffle(e : T, id : I) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)  
`I` is [u32](#u32) or [i32](#i32)
Description Returns `e` from the invocation whose [subgroup invocation ID](#subgroup-invocation-id) matches `id`. 
If `id` is outside the range [0, 128), then:

*   It is a [shader-creation error](#shader-creation-error) if `id` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `id` is an [override-expression](#override-expressions).

An [indeterminate value](#indeterminate-value) is returned if `id` does not select an [active](#subgroups-active) invocation.

##### 17.12.12.1. `subgroupShuffleDown`[](#subgroupshuffledown-builtin)

Overload@must_use fn subgroupShuffleDown(e : T, delta : u32) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Returns `e` from the invocation whose [subgroup invocation ID](#subgroup-invocation-id) matches `subgroup_invocation_id + delta` for the current invocation. 
If `delta` is greater than 127, then:

*   It is a [shader-creation error](#shader-creation-error) if `delta` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `delta` is an [override-expression](#override-expressions).

A [subgroup_uniformity](#trigger-subgroup_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered) if `delta` is not a [uniform value](#uniform-value). An [indeterminate value](#indeterminate-value) is returned if `subgroup_invocation_id + delta` does not select an [active](#subgroups-active) invocation or if `delta` is a not a uniform value within the subgroup.

##### 17.12.12.2. `subgroupShuffleUp`[](#subgroupshuffleup-builtin)

Overload@must_use fn subgroupShuffleUp(e : T, delta : u32) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Returns `e` from the invocation whose [subgroup invocation ID](#subgroup-invocation-id) matches `subgroup_invocation_id - delta` for the current invocation. 
If `delta` is greater than 127, then:

*   It is a [shader-creation error](#shader-creation-error) if `delta` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `delta` is an [override-expression](#override-expressions).

A [subgroup_uniformity](#trigger-subgroup_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered) if `delta` is not a [uniform value](#uniform-value). An [indeterminate value](#indeterminate-value) is returned if `subgroup_invocation_id - delta` does not select an [active](#subgroups-active) invocation or if `delta` is not a uniform value within the subgroup.

##### 17.12.12.3. `subgroupShuffleXor`[](#subgroupshufflexor-builtin)

Overload@must_use fn subgroupShuffleXor(e : T,  mask : u32) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Returns `e` from the invocation whose [subgroup invocation ID](#subgroup-invocation-id) matches `subgroup_invocation_id ^ mask` for the current invocation. 
If `mask` is greater than 127, then:

*   It is a [shader-creation error](#shader-creation-error) if `mask` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `mask` is an [override-expression](#override-expressions).

A [subgroup_uniformity](#trigger-subgroup_uniformity)[diagnostic](#diagnostic) is [triggered](#triggered) if `mask` is not a [uniform value](#uniform-value). An [indeterminate value](#indeterminate-value) is returned if `mask` does not select an [active](#subgroups-active) invocation or if `mask` is not a uniform value within the subgroup.

#### 17.12.13. `subgroupXor`[](#subgroupxor-builtin)

Overload@must_use fn subgroupXor(e : T) -> T
Preconditions`T` is i32, u32, vecN<i32>, or vecN<u32>
Description Reduction operation. 
Returns the bitwise xor (`^`) of `e` among all [active](#subgroups-active) invocations in the [subgroup](#subgroup).

### 17.13. Quad Operations[](#quad-builtin-functions)

See [§ 15.6.4 Quad Operations](#quad-ops).

Calls to these functions:

*   [Must](#shader-creation-error) only be used in a [fragment](#fragment) or [compute](#compute) shader stage.

*   [Trigger](#triggered) a [subgroup_uniformity](#trigger-subgroup_uniformity)[diagnostic](#diagnostic) if [uniformity analysis](#uniformity-analysis) cannot prove the call is in [uniform control flow](#uniform-control-flow).

Note: For the [compute shader stage](#compute-shader-stage), the scope of uniform control flow is the [workgroup](#compute-shader-stage-workgroup). For the [fragment shader stage](#fragment-shader-stage), the scope of uniform control flow is the [draw command](#draw-command). Both of these scopes are larger than [quad](#quad).

#### 17.13.1. `quadBroadcast`[](#quadbroadcast-builtin)

Overload@must_use fn quadBroadcast(e : T, id : I) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)  
`I` is [u32](#u32) or [i32](#i32)
Description Returns the value of `e` from the invocation whose [quad invocation ID](#quad-invocation-id) matches `id` in the quad to all [active](#subgroups-active) invocations in the quad. 
`id`[must](#shader-creation-error) be a [const-expression](#const-expressions) in the range [0, 4).

An [indeterminate value](#indeterminate-value) is returned if `id` does not select an [active](#subgroups-active) invocation.

Note: Unlike [subgroupBroadcast](#subgroupbroadcast-builtin), there is currently no non-constant alternative.

#### 17.13.2. `quadSwapDiagonal`[](#quadswapdiagonal-builtin)

Overload@must_use fn quadSwapDiagonal(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Returns the value of `e` from the invocation in the [quad](#quad) with the opposite coordinates. That is: 
*   IDs 0 and 3 swap.

*   IDs 1 and 2 swap.

#### 17.13.3. `quadSwapX`[](#quadswapx-builtin)

Overload@must_use fn quadSwapX(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Returns the value of `e` from invocation in the [quad](#quad) sharing the same X dimension. That is: 
*   IDs 0 and 1 swap.

*   IDs 2 and 3 swap.

#### 17.13.4. `quadSwapY`[](#quadswapy-builtin)

Overload@must_use fn quadSwapY(e : T) -> T
Preconditions`T` is [concrete](#type-concrete)[numeric scalar](#numeric-scalar) or [concrete](#type-concrete)[numeric vector](#numeric-vector)
Description Returns the value of `e` from invocation in the [quad](#quad) sharing the same Y dimension. That is: 
*   IDs 0 and 2 swap.

*   IDs 1 and 3 swap.

### 17.14. Buffer View Built-in Functions[](#buffer-view-builtin-functions)

These functions all require the [buffer_view](#language_extension-buffer_view) language feature.

These functions operate on a pointer to a [buffer](#buffer). [bufferView](#bufferview-builtin) and [bufferArrayView](#bufferarrayview-builtin) reinterpret the opaque data in the buffer into another [host-shareable](#host-shareable) data type. The resulting pointer can then be used like other pointers.

Define ArrayOffset(T) as:

*   [OffsetOfMember](#offsetofmember)(T, lastMemberIndex), if T is a [structure](#structure) whose last member is a [runtime-sized array](#runtime-sized) (array<E>)

*   0, otherwise

Define MinTypeSize(T) as:

*   [SizeOf](#sizeof)(T), if T has a [fixed footprint](#fixed-footprint)

*   [StrideOf](#strideof)(T), if T is a [runtime-sized array](#runtime-sized)

*   [ArrayOffset](#arrayoffset)(T) + [StrideOf](#strideof)(array<E>) if T is a [structure](#structure) whose last member is a [runtime-sized array](#runtime-sized)

Since buffer pointer arguments to [function calls](#function-call) can undergo [automatic conversion](#feasible-automatic-conversion) to the [parameter’s](#formal-parameter) type, implementations [will](#behavioral-requirements) use interprocedural analysis to check for both [invalid memory references](#invalid-memory-reference) and ensure correct results. The buffer size used for any buffer view built-in function is the minimum buffer size encountered for the particular [originating variable](#originating-variable) used with the call. Because this is a dynamic concept, implementations [will](#behavioral-requirements) ensure that this value is correctly determined for a particular instance of the built-in function. The size will be the minimum of:

*   The size of the [originating variable](#originating-variable), or

*   The minimum [fixed-size buffer](#fixed-size-buffer) encountered as a [formal parameter](#formal-parameter) in the call stack.

Note: If the implementation does not support the [unrestricted_pointer_parameters](#language_extension-unrestricted_pointer_parameters) language feature then the [root identifier](#root-identifier) of the argument to the built-in function must be the [originating variable](#originating-variable).

Note: Buffer sizes cannot be made larger as they are passed to functions.

#### 17.14.1. `bufferView`[](#bufferview-builtin)

Overloads@must_use fn bufferView<T>(p : ptr<AS, buffer, AM>, offset: I) -> ptr<AS, T, AM>
Preconditions`AS` is one of [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), or [workgroup](#address-spaces-workgroup).  
`AM` is a valid [access mode](#access-mode) for `AS`. 
`T` is a [host-shareable](#host-shareable) type.  
`T`[must not](#shader-creation-error) be or contain an [atomic](#atomic-type) or [buffer](#buffer) type.  
`T`[must](#shader-creation-error) satisfy the [address space layout constraints](#address-space-layout-constraints) for `AS`.

`I` is [u32](#u32) or [i32](#i32).
Description Reinterpret the [memory view](#memory-view)`offset` bytes from the start of `p` as the type `T`. That is, if the [memory locations](#memory-locations) associated with `p` are in the range [0, `bufferLength(p)`), then the resulting [memory locations](#memory-locations) associated with the result are in the range [`offset`, `bufferLength(p)`) with the store type `T`. 
If `I` is [i32](#i32), then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions)< 0.

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions)< 0.

*   Otherwise, an [indeterminate value](#indeterminate-value) for `I` may be used.

An [invalid pointer](#invalid-pointer) is returned if [MinTypeSize](#mintypesize)(`T`) + `offset`>[bufferLength](#bufferlength-builtin)(`p`).

If `offset` % [RequiredAlignOf](#requiredalignof)(`T`, `AS`) != 0, then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions).

*   A value of `offset`& ~([RequiredAlignOf](#requiredalignof)(`T`, `AS`) - 1) [will](#behavioral-requirements) be used for `offset`.

Note: This interacts with the [uniform_buffer_standard_layout](#language_extension-uniform_buffer_standard_layout) language feature.

Overloads@must_use fn bufferView<T>(p : ptr<AS, buffer<N>, AM>, offset: I) -> ptr<AS, T, AM>
Preconditions`AS` is one of [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), or [workgroup](#address-spaces-workgroup).  
`AM` is a valid [access mode](#access-mode) for `AS`. 
`T` is a [host-shareable](#host-shareable) type.  
`T`[must not](#shader-creation-error) be or contain an [atomic](#atomic-type) or [buffer](#buffer) type.  
`T`[must](#shader-creation-error) satisfy the [address space layout constraints](#address-space-layout-constraints) for `AS`.

`I` is [u32](#u32) or [i32](#i32).
Description Reinterpret the [memory view](#memory-view)`offset` bytes from the start of `p` as the type `T`. That is, if the [memory locations](#memory-locations) associated with `p` are in the range [0, `bufferLength(p)`), then the resulting [memory locations](#memory-locations) associated with the result are in the range [`offset`, `bufferLength(p)`) with the store type `T`. 
If `I` is [i32](#i32), then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions)< 0.

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions)< 0.

*   Otherwise, an [indeterminate value](#indeterminate-value) for `I` may be used.

An [invalid memory reference](#invalid-memory-reference) is returned if [MinTypeSize](#mintypesize)(`T`) + `offset`>`N`.

*   It is a [shader-creation error](#shader-creation-error) if [MinTypeSize](#mintypesize)(`T`) >`N`.

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions).

If `offset` % [RequiredAlignOf](#requiredalignof)(`T`, `AS`) != 0, then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions).

*   A value of `offset`& ~([RequiredAlignOf](#requiredalignof)(`T`, `AS`) - 1) [will](#behavioral-requirements) be used for `offset`.

Note: This interacts with the [uniform_buffer_standard_layout](#language_extension-uniform_buffer_standard_layout) language feature.

EXAMPLE: WGSL bufferView usage

requires buffer_view;

@group(0) @binding(0) var<storage> in : buffer;
@group(0) @binding(1) var<storage, read_write> out : buffer;

struct S {
  a : mat3x3f,
  b : vec2f,
}

fn foo(offsets : array<u32, 4>) {
  // Read and write some of the data as vec4u.
  let p1 = bufferView<vec4u>(&in, offsets[0]);
  *bufferView<vec4u>(&out, offsets[1]) = *p1;

  // Read and write some of the other data via a structure.
  let p2 = bufferView<array<S, 2>>(&in, offsets[2]);
  let v = (*p2)[1].a;
  *bufferView<mat3x3f>(&out, offsets[3]) = v;
}

#### 17.14.2. `bufferArrayView`[](#bufferarrayview-builtin)

Overloads@must_use fn bufferArrayView<T>(p : ptr<AS, buffer, AM>,
                                offset: OI, size: SI) -> ptr<AS, T, AM>
Preconditions`AS` is one of [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), or [workgroup](#address-spaces-workgroup).  
`AM` is a valid [access mode](#access-mode) for `AS`. 
`T` is a [host-shareable](#host-shareable) type without a [fixed footprint](#fixed-footprint).  
`T`[must not](#shader-creation-error) be nor contain an [atomic](#atomic-type) or [buffer](#buffer) type.  
`T`[must](#shader-creation-error) satisfy the [address space layout constraints](#address-space-layout-constraints) for `AS`.

`OI` is [u32](#u32) or [i32](#i32).  
`SI` is [u32](#u32) or [i32](#i32).
Description Reinterpret the [memory view](#memory-view)`offset` bytes from the start of `p` for `size` bytes as the type `T`. That is, if the [memory locations](#memory-locations) associated with `p` are in the range [0, `bufferLength(p)`), then the resulting [memory locations](#memory-locations) associated with the result are in the range [`offset`, `offset + size`) with the store type `T`. 
If `OI` is [i32](#i32), then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions)< 0.

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions)< 0.

*   Otherwise, an [indeterminate value](#indeterminate-value) for `OI` may be used.

If `SI` is [i32](#i32), then:

*   It is a [shader-creation error](#shader-creation-error) if `size` is a [const-expression](#const-expressions)< 0.

*   It is a [pipeline-creation error](#pipeline-creation-error) if `size` is an [override-expression](#override-expressions)< 0.

*   Otherwise, an [indeterminate value](#indeterminate-value) for `SI` may be used.

An [invalid memory reference](#invalid-memory-reference) is returned if [MinTypeSize](#mintypesize)(`T`) >`size`.

*   It is a [shader-creation error](#shader-creation-error) if `size` is a [const-expression](#const-expressions) (using 0 for `offset` if it is not).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `size` is an [override-expression](#override-expressions) (using 0 for `offset` if it is not).

An [invalid memory reference](#invalid-memory-reference) is returned if `offset` + `size`>[bufferLength](#bufferlength-builtin)(`p`).

If `offset` % [RequiredAlignOf](#requiredalignof)(`T`, `AS`) != 0, then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions).

*   A value of `offset`& ~([RequiredAlignOf](#requiredalignof)(`T`, `AS`) - 1) [will](#behavioral-requirements) be used for `offset`.

Note: This interacts with the [uniform_buffer_standard_layout](#language_extension-uniform_buffer_standard_layout) language feature.

If (`size` - [ArrayOffset](#arrayoffset)(`T`)) % [StrideOf](#strideof)(`array<E>`) != 0, then:

*   It is a [shader-creation error](#shader-creation-error) if `size` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `size` is an [override-expression](#override-expressions).

*   A value of [roundDown](#rounddown)([StrideOf](#strideof)(`array<E>`), `size` - [ArrayOffset](#arrayoffset)(`T`)) + [ArrayOffset](#arrayoffset)(`T`) [will](#behavioral-requirements) be used for `size`.

Overloads@must_use fn bufferArrayView<T>(p : ptr<AS, buffer<N>, AM>,
                                offset: OI, size: SI) -> ptr<AS, T, AM>
Preconditions`AS` is one of [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), or [workgroup](#address-spaces-workgroup).  
`AM` is a valid [access mode](#access-mode) for `AS`. 
`T` is a [host-shareable](#host-shareable) type without a [fixed footprint](#fixed-footprint).  
`T`[must not](#shader-creation-error) be nor contain an [atomic](#atomic-type) or [buffer](#buffer) type.  
`T`[must](#shader-creation-error) satisfy the [address space layout constraints](#address-space-layout-constraints) for `AS`.

`OI` is [u32](#u32) or [i32](#i32).  
`SI` is [u32](#u32) or [i32](#i32).
Description Reinterpret the [memory view](#memory-view)`offset` bytes from the start of `p` for `size` bytes as the type `T`. That is, if the [memory locations](#memory-locations) associated with `p` are in the range [0, `bufferLength(p)`), then the resulting [memory locations](#memory-locations) associated with the result are in the range [`offset`, `offset + size`) with the store type `T`. 
If `OI` is [i32](#i32), then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions)< 0.

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions)< 0.

*   Otherwise, an [indeterminate value](#indeterminate-value) for `OI` may be used.

If `SI` is [i32](#i32), then:

*   It is a [shader-creation error](#shader-creation-error) if `size` is a [const-expression](#const-expressions)< 0.

*   It is a [pipeline-creation error](#pipeline-creation-error) if `size` is an [override-expression](#override-expressions)< 0.

*   Otherwise, an [indeterminate value](#indeterminate-value) for `SI` may be used.

An [invalid memory reference](#invalid-memory-reference) is returned if [MinTypeSize](#mintypesize)(`T`) >`size`.

*   It is a [shader-creation error](#shader-creation-error) if `size` is a [const-expression](#const-expressions) (using 0 for `offset` if it is not).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `size` is an [override-expression](#override-expressions) (using 0 for `offset` if it is not).

An [invalid memory reference](#invalid-memory-reference) is returned if `offset` + `size`>`N`.

*   It is a [shader-creation error](#shader-creation-error) if either `offset` or `size` is a [const-expression](#const-expressions) (using 0 if a parameter is not).

*   It is a [pipeline-creation error](#pipeline-creation-error) if either `offset` or `size` is an [override-expression](#override-expressions) (using 0 if a parameter is not).

If [MinTypeSize](#mintypesize)(`T`) >`N`, then:

*   It is a [shader-creation error](#shader-creation-error) if `N` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `N` is an [override-expression](#override-expressions).

If `offset` % [RequiredAlignOf](#requiredalignof)(`T`, `AS`) != 0, then:

*   It is a [shader-creation error](#shader-creation-error) if `offset` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `offset` is an [override-expression](#override-expressions).

*   A value of `offset`& ~([RequiredAlignOf](#requiredalignof)(`T`, `AS`) - 1) [will](#behavioral-requirements) be used for `offset`.

Note: This interacts with the [uniform_buffer_standard_layout](#language_extension-uniform_buffer_standard_layout) language feature.

If (`size` - [ArrayOffset](#arrayoffset)(`T`)) % [StrideOf](#strideof)(`array<E>`) != 0, then:

*   It is a [shader-creation error](#shader-creation-error) if `size` is a [const-expression](#const-expressions).

*   It is a [pipeline-creation error](#pipeline-creation-error) if `size` is an [override-expression](#override-expressions).

*   A value of [roundDown](#rounddown)([StrideOf](#strideof)(`array<E>`), `size` - [ArrayOffset](#arrayoffset)(`T`)) + [ArrayOffset](#arrayoffset)(`T`) [will](#behavioral-requirements) be used for `size`.

EXAMPLE: WGSL bufferArrayView usage

requires buffer_view;

const stride = 32;
const N = 4;
const size = 2048;
const_assert stride * N < size;

struct strided_u32 {
  @size(stride) a : u32,
}

@group(0) @binding(0) var<uniform> in : buffer<size>;
@group(0) @binding(1) var<storage, read_write> out: array<u32, N>;

fn foo(offsets : u32) {
  // Read a strided array from in and copy it unstrided to out.
  var tmp : array<u32, N>;
  let view = bufferArrayView<array<strided_u32>>(&in, offset, stride * N);
  for (var i = 0; i < N; i++) {
    tmp[i] = (*view)[i];
  }
  out = tmp;
}

#### 17.14.3. `bufferLength`[](#bufferlength-builtin)

Overloads@must_use fn bufferLength(p : ptr<AS, buffer,    AM>) -> u32
@must_use fn bufferLength(p : ptr<AS, buffer<N>, AM>) -> u32
Preconditions`AS` is one of [storage](#address-spaces-storage), [uniform](#address-spaces-uniform), or [workgroup](#address-spaces-workgroup).  
`AM` is a valid [access mode](#access-mode) for `AS`.
Description Returns the minimum size of the [buffer](#buffer) pointed to by `p` encountered during the interprocedural analysis, or the size of the WebGPU `GPUBuffer` if only [runtime-sized buffers](#runtime-sized-buffer) were encountered.

EXAMPLE: bufferLength values

requires buffer_view;
requires unrestricted_pointer_parameters;

@group(0) @binding(0) var<storage> b1 : buffer<2048>;
@group(0) @binding(0) var<storage> b2 : buffer<4096>;

fn foobar(p : ptr<storage, buffer>) -> u32 {
  return bufferLength(p);
}
fn bar(p : ptr<storage, buffer<1024>>) -> u32 {
  return foobar(p);
}
fn foo(p : ptr<storage, buffer<256>>) -> u32 {
  return bufferLength(p);
}

@compute @workgroup_size(1)
fn main() {
  let len1 = bufferLength(&b1); // 2048
  let len2 = bufferLength(&b2); // 4096

  let len3 = foo(&b1); // 256
  let len4 = foo(&b2); // 256

  let len5 = bar(&b1); // 1024
  let len6 = bar(&b2); // 1024

  let len7 = foobar(&b1); // 2048
  let len8 = foobar(&b2); // 4096
}

## 18. Grammar for Recursive Descent Parsing[](#grammar-recursive-descent)

This section is non-normative.

The WGSL grammar is specified in a form suitable for an LALR(1) parser. An implementation may want to use a recursive-descent parser instead.

The normative grammar cannot be used directly in a recursive-descent parser, because several of its rules are left-recursive. A grammar rule is directly left-recursive when the nonterminal being defined appears first in one of its productions.

The following is the WGSL grammar, but mechanically transformed to:

*   Eliminate direct and indirect left-recursion.

*   Avoid empty productions. (That is, avoid epsilon-rules.)

*   Bring together common prefixes among sibling productions.

However, it is not LL(1). For some nonterminals, several productions have common lookahead sets. For example, all productions for the `attribute` nonterminal start with the `attr` token. A more subtle example is `global_decl`, where three productions start with an `attribute *` phrase, but then are distinguished by tokens `fn`, `override`, and `var`.

For the sake of brevity, many token definitions are not repeated. Use token definitions from the main part of the specification.

additive_operator:

`'+'`

| `'-'`

argument_expression_list:

`'('` ( [expression](#recursive-descent-syntax-expression) ( `','`[expression](#recursive-descent-syntax-expression) )* `','` ? )? `')'`

assignment_statement/0.1:

[compound_assignment_operator](#recursive-descent-syntax-compound_assignment_operator)

| `'='`

attribute:

[compute_attr](#recursive-descent-syntax-compute_attr)

| [const_attr](#recursive-descent-syntax-const_attr)

| [fragment_attr](#recursive-descent-syntax-fragment_attr)

| [interpolate_attr](#recursive-descent-syntax-interpolate_attr)

| [invariant_attr](#recursive-descent-syntax-invariant_attr)

| [must_use_attr](#recursive-descent-syntax-must_use_attr)

| [vertex_attr](#recursive-descent-syntax-vertex_attr)

| [workgroup_size_attr](#recursive-descent-syntax-workgroup_size_attr)

| `'@'`[ident_pattern_token](#syntax-ident_pattern_token) ( `'('` ( [expression](#recursive-descent-syntax-expression) ( `','`[expression](#recursive-descent-syntax-expression) )* `','` ? )? `')'` )?

| `'@'``'align'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'binding'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'blend_src'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'builtin'``'('`[builtin_value_name](#recursive-descent-syntax-builtin_value_name)`','` ? `')'`

| `'@'``'diagnostic'`[diagnostic_control](#recursive-descent-syntax-diagnostic_control)

| `'@'``'group'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'id'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'location'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'size'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'subgroup_size'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

bitwise_expression.post.unary_expression:

`'&'`[unary_expression](#recursive-descent-syntax-unary_expression) ( `'&'`[unary_expression](#recursive-descent-syntax-unary_expression) )*

| `'^'`[unary_expression](#recursive-descent-syntax-unary_expression) ( `'^'`[unary_expression](#recursive-descent-syntax-unary_expression) )*

| `'|'`[unary_expression](#recursive-descent-syntax-unary_expression) ( `'|'`[unary_expression](#recursive-descent-syntax-unary_expression) )*

bool_literal:

`'false'`

| `'true'`

builtin_value_name: [ident_pattern_token](#syntax-ident_pattern_token)

call_expression.post.ident:

[template_elaborated_ident.post.ident](#recursive-descent-syntax-template_elaborated_identpostident)`'('` ( [expression](#recursive-descent-syntax-expression) ( `','`[expression](#recursive-descent-syntax-expression) )* `','` ? )? `')'`

case_selector:

[expression](#recursive-descent-syntax-expression)

| `'default'`

component_or_swizzle_specifier:

`'.'`[member_ident](#recursive-descent-syntax-member_ident)[component_or_swizzle_specifier](#recursive-descent-syntax-component_or_swizzle_specifier) ?

| `'.'`[swizzle_name](#recursive-descent-syntax-swizzle_name)[component_or_swizzle_specifier](#recursive-descent-syntax-component_or_swizzle_specifier) ?

| `'['`[expression](#recursive-descent-syntax-expression)`']'`[component_or_swizzle_specifier](#recursive-descent-syntax-component_or_swizzle_specifier) ?

compound_assignment_operator:

[shift_left_assign](#syntax_sym-shift_left_assign)

| [shift_right_assign](#syntax_sym-shift_right_assign)

| `'%='`

| `'&='`

| `'*='`

| `'+='`

| `'-='`

| `'/='`

| `'^='`

| `'|='`

compound_statement:

[attribute](#recursive-descent-syntax-attribute) * `'{'`[statement](#recursive-descent-syntax-statement) * `'}'`

compute_attr:

`'@'``'compute'`

const_attr:

`'@'``'const'`

core_lhs_expression:

[ident](#recursive-descent-syntax-ident)

| [ident](#recursive-descent-syntax-ident)[call_expression.post.ident](#recursive-descent-syntax-call_expressionpostident)

| `'('`[lhs_expression](#recursive-descent-syntax-lhs_expression)`')'`

decimal_int_literal:

`/0[iu]?/`

| `/[1-9][0-9]*[iu]?/`

diagnostic_control:

`'('`[ident_pattern_token](#syntax-ident_pattern_token)`','`[diagnostic_rule_name](#recursive-descent-syntax-diagnostic_rule_name)`','` ? `')'`

diagnostic_rule_name:

[ident_pattern_token](#syntax-ident_pattern_token)

| [ident_pattern_token](#syntax-ident_pattern_token)`'.'`[ident_pattern_token](#syntax-ident_pattern_token)

fragment_attr:

`'@'``'fragment'`

global_assert:

`'const_assert'``';'`

global_decl:

[attribute](#recursive-descent-syntax-attribute) * `'fn'`[ident](#recursive-descent-syntax-ident)`'('` ( [attribute](#recursive-descent-syntax-attribute) * [ident](#recursive-descent-syntax-ident)`':'`[type_specifier](#recursive-descent-syntax-type_specifier) ( `','`[param](#recursive-descent-syntax-param) )* `','` ? )? `')'` ( `'->'`[attribute](#recursive-descent-syntax-attribute) * [ident](#recursive-descent-syntax-ident)[template_elaborated_ident.post.ident](#recursive-descent-syntax-template_elaborated_identpostident) )? [attribute](#recursive-descent-syntax-attribute) * `'{'`[statement](#recursive-descent-syntax-statement) * `'}'`

| [attribute](#recursive-descent-syntax-attribute) * `'var'` ( [_template_args_start](#syntax_sym-_template_args_start)[expression](#recursive-descent-syntax-expression) ( `','`[expression](#recursive-descent-syntax-expression) )* `','` ? [_template_args_end](#syntax_sym-_template_args_end) )? [optionally_typed_ident](#recursive-descent-syntax-optionally_typed_ident) ( `'='`[expression](#recursive-descent-syntax-expression) )? `';'`

| [global_value_decl](#recursive-descent-syntax-global_value_decl)`';'`

| `'alias'`[ident](#recursive-descent-syntax-ident)`'='`[ident](#recursive-descent-syntax-ident)[template_elaborated_ident.post.ident](#recursive-descent-syntax-template_elaborated_identpostident)`';'`

| `'struct'`[ident](#recursive-descent-syntax-ident)`'{'`[attribute](#recursive-descent-syntax-attribute) * [member_ident](#recursive-descent-syntax-member_ident)`':'`[type_specifier](#recursive-descent-syntax-type_specifier) ( `','`[attribute](#recursive-descent-syntax-attribute) * [member_ident](#recursive-descent-syntax-member_ident)`':'`[type_specifier](#recursive-descent-syntax-type_specifier) )* `','` ? `'}'`

global_directive:

`'diagnostic'``'('`[ident_pattern_token](#syntax-ident_pattern_token)`','`[diagnostic_rule_name](#recursive-descent-syntax-diagnostic_rule_name)`','` ? `')'``';'`

| `'enable'`[ident_pattern_token](#syntax-ident_pattern_token) ( `','`[ident_pattern_token](#syntax-ident_pattern_token) )* `','` ? `';'`

| `'requires'`[ident_pattern_token](#syntax-ident_pattern_token) ( `','`[ident_pattern_token](#syntax-ident_pattern_token) )* `','` ? `';'`

global_value_decl:

[attribute](#recursive-descent-syntax-attribute) * `'override'`[optionally_typed_ident](#recursive-descent-syntax-optionally_typed_ident) ( `'='`[expression](#recursive-descent-syntax-expression) )?

| `'const'`[optionally_typed_ident](#recursive-descent-syntax-optionally_typed_ident)`'='`[expression](#recursive-descent-syntax-expression)

interpolate_attr:

`'@'``'interpolate'``'('`[ident_pattern_token](#syntax-ident_pattern_token)`','` ? `')'`

| `'@'``'interpolate'``'('`[ident_pattern_token](#syntax-ident_pattern_token)`','`[ident_pattern_token](#syntax-ident_pattern_token)`','` ? `')'`

invariant_attr:

`'@'``'invariant'`

member_ident: [ident_pattern_token](#syntax-ident_pattern_token)

multiplicative_operator:

`'%'`

| `'*'`

| `'/'`

must_use_attr:

`'@'``'must_use'`

optionally_typed_ident:

[ident](#recursive-descent-syntax-ident) ( `':'`[type_specifier](#recursive-descent-syntax-type_specifier) )?

param:

[attribute](#recursive-descent-syntax-attribute) * [ident](#recursive-descent-syntax-ident)`':'`[type_specifier](#recursive-descent-syntax-type_specifier)

statement:

[attribute](#recursive-descent-syntax-attribute) * `'for'``'('`[for_init](#recursive-descent-syntax-for_init) ? `';'`[expression](#recursive-descent-syntax-expression) ? `';'`[for_update](#recursive-descent-syntax-for_update) ? `')'`[compound_statement](#recursive-descent-syntax-compound_statement)

| [attribute](#recursive-descent-syntax-attribute) * `'if'`[expression](#recursive-descent-syntax-expression)[compound_statement](#recursive-descent-syntax-compound_statement) ( `'else'``'if'`[expression](#recursive-descent-syntax-expression)[compound_statement](#recursive-descent-syntax-compound_statement) )* ( `'else'`[compound_statement](#recursive-descent-syntax-compound_statement) )?

| [attribute](#recursive-descent-syntax-attribute) * `'loop'`[attribute](#recursive-descent-syntax-attribute) * `'{'`[statement](#recursive-descent-syntax-statement) * ( `'continuing'`[attribute](#recursive-descent-syntax-attribute) * `'{'`[statement](#recursive-descent-syntax-statement) * ( `'break'``'if'`[expression](#recursive-descent-syntax-expression)`';'` )? `'}'` )? `'}'`

| [attribute](#recursive-descent-syntax-attribute) * `'switch'`[expression](#recursive-descent-syntax-expression)[attribute](#recursive-descent-syntax-attribute) * `'{'`[switch_clause](#recursive-descent-syntax-switch_clause) * `'}'`

| [attribute](#recursive-descent-syntax-attribute) * `'while'`[expression](#recursive-descent-syntax-expression)[compound_statement](#recursive-descent-syntax-compound_statement)

| [compound_statement](#recursive-descent-syntax-compound_statement)

| [ident](#recursive-descent-syntax-ident)[template_elaborated_ident.post.ident](#recursive-descent-syntax-template_elaborated_identpostident)[argument_expression_list](#recursive-descent-syntax-argument_expression_list)`';'`

| [variable_or_value_statement](#recursive-descent-syntax-variable_or_value_statement)`';'`

| [variable_updating_statement](#recursive-descent-syntax-variable_updating_statement)`';'`

| [assert_statement](#syntax-assert_statement)`';'`

| [break_statement](#syntax-break_statement)`';'`

| [continue_statement](#syntax-continue_statement)`';'`

| `';'`

| `'discard'``';'`

| `'return'`[expression](#recursive-descent-syntax-expression) ? `';'`

switch_clause:

`'case'`[case_selector](#recursive-descent-syntax-case_selector) ( `','`[case_selector](#recursive-descent-syntax-case_selector) )* `','` ? `':'` ? [compound_statement](#recursive-descent-syntax-compound_statement)

| `'default'``':'` ? [compound_statement](#recursive-descent-syntax-compound_statement)

swizzle_name:

`/[rgba]/`

| `/[rgba][rgba]/`

| `/[rgba][rgba][rgba]/`

| `/[rgba][rgba][rgba][rgba]/`

| `/[xyzw]/`

| `/[xyzw][xyzw]/`

| `/[xyzw][xyzw][xyzw]/`

| `/[xyzw][xyzw][xyzw][xyzw]/`

template_arg_expression: [expression](#recursive-descent-syntax-expression)

template_elaborated_ident.post.ident:

( [_template_args_start](#syntax_sym-_template_args_start)[template_arg_expression](#recursive-descent-syntax-template_arg_expression) ( `','`[expression](#recursive-descent-syntax-expression) )* `','` ? [_template_args_end](#syntax_sym-_template_args_end) )?

translation_unit:

[global_directive](#recursive-descent-syntax-global_directive) * ( [global_decl](#recursive-descent-syntax-global_decl) | [global_assert](#recursive-descent-syntax-global_assert) | `';'` ) *

translation_unit/0.1/0/0.0:

[global_assert](#recursive-descent-syntax-global_assert)

| [global_decl](#recursive-descent-syntax-global_decl)

| `';'`

type_specifier:

[ident](#recursive-descent-syntax-ident) ( [_template_args_start](#syntax_sym-_template_args_start)[template_arg_expression](#recursive-descent-syntax-template_arg_expression) ( `','`[expression](#recursive-descent-syntax-expression) )* `','` ? [_template_args_end](#syntax_sym-_template_args_end) )?

variable_decl:

`'var'` ( [_template_args_start](#syntax_sym-_template_args_start)[expression](#recursive-descent-syntax-expression) ( `','`[expression](#recursive-descent-syntax-expression) )* `','` ? [_template_args_end](#syntax_sym-_template_args_end) )? [optionally_typed_ident](#recursive-descent-syntax-optionally_typed_ident)

variable_or_value_statement:

[variable_decl](#recursive-descent-syntax-variable_decl)

| [variable_decl](#recursive-descent-syntax-variable_decl)`'='`[expression](#recursive-descent-syntax-expression)

| `'const'`[optionally_typed_ident](#recursive-descent-syntax-optionally_typed_ident)`'='`[expression](#recursive-descent-syntax-expression)

| `'let'`[optionally_typed_ident](#recursive-descent-syntax-optionally_typed_ident)`'='`[expression](#recursive-descent-syntax-expression)

variable_updating_statement:

[lhs_expression](#recursive-descent-syntax-lhs_expression) ( `'='` | [compound_assignment_operator](#recursive-descent-syntax-compound_assignment_operator) ) [expression](#recursive-descent-syntax-expression)

| [lhs_expression](#recursive-descent-syntax-lhs_expression)`'++'`

| [lhs_expression](#recursive-descent-syntax-lhs_expression)`'--'`

| `'_'``'='`[expression](#recursive-descent-syntax-expression)

vertex_attr:

`'@'``'vertex'`

workgroup_size_attr:

`'@'``'workgroup_size'``'('`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'workgroup_size'``'('`[expression](#recursive-descent-syntax-expression)`','`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

| `'@'``'workgroup_size'``'('`[expression](#recursive-descent-syntax-expression)`','`[expression](#recursive-descent-syntax-expression)`','`[expression](#recursive-descent-syntax-expression)`','` ? `')'`

## Appendix A: The `text/wgsl` Media Type[](#text-wgsl-media-type)

The Internet Assigned Numbers Authority (IANA) maintains a registry of media types, at [[IANA-MEDIA-TYPES]](https://www.w3.org/TR/WGSL/#biblio-iana-media-types "Media Types").

The following is the definition of the `text/wgsl` media type for WGSL modules. It has been registered at IANA, appearing at [https://www.iana.org/assignments/media-types/text/wgsl](https://www.iana.org/assignments/media-types/text/wgsl).

Type name 
text

Subtype name 
wgsl

Required parameters 
N/A

Optional parameters 
None

Encoding considerations 
binary

WGSL is Unicode text using the UTF-8 encoding, with no byte order mark (BOM). See [§ 3 Textual Structure](#textual-structure).

Security considerations: 
WebGPU Shading Language (WGSL) is a programming language for GPU code to be executed in the context of the WebGPU API. For security considerations, see [[WebGPU]](https://www.w3.org/TR/WGSL/#biblio-webgpu "WebGPU") Section 2.1 Security Considerations. For privacy considerations, see [[WebGPU]](https://www.w3.org/TR/WGSL/#biblio-webgpu "WebGPU") Section 2.2 Privacy Considerations.

Interoperability considerations: 
Implementations of WebGPU may have different capabilities, and these differences may affect what features may be exercised by WGSL programs. See [[WebGPU]](https://www.w3.org/TR/WGSL/#biblio-webgpu "WebGPU") Section 3.6 Optional capabilities, and [§ 4.1.2 Language Extensions](#language-extensions-sec).

It is expected that implementations will behave as if this registration applies to later editions of WGSL, and its published specification references may be updated accordingly from time to time. Although this expectation is unusual among media type registrations, it matches widespread industry conventions.

Published specification: 
WebGPU Shading Language

Applications that use this media type: 
Implementations of WebGPU. This is expected to include web browsers.

Fragment identifier considerations 
None

Additional information: 
Magic number(s): None

File extension(s): `.wgsl`

Macintosh file type code(s): `TEXT`

Person & email address to contact for further information: 
David Neto, dneto@google.com, or the Editors listed in WGSL.

Intended usage 
COMMON

Author 
W3C. See the Editors listed in WGSL.

Change controller 
W3C

Normative References 
[[WebGPU]](https://www.w3.org/TR/WGSL/#biblio-webgpu "WebGPU") W3C, "WebGPU” W3C Working Draft, January 2023. https://w3.org/TR/webgpu

Webgpu Shading Language W3C, "WebGPU Shading Language" W3C Working Draft, January 2023. https://w3.org/TR/WGSL
