# Using ArkTS APIs in Cangjie Applications

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Overview

Cangjie supports cross-language interoperability with ArkTS. Therefore, developers can call application development APIs and standard libraries provided by ArkTS in applications developed with the Cangjie language.

> **Note:**
>
> The application development APIs and language libraries provided by Cangjie are continuously being improved. If Cangjie application developers encounter APIs that are not yet available in Cangjie, they can utilize ArkTS APIs to complete their application development.

## Usage Guide

This section explains how to use ArkTS APIs in applications developed with Cangjie.

### Creating an ArkTS Runtime

Developers can create a `JSRuntime` object in Cangjie applications, which represents an instance of the ArkTS runtime. Through the `JSRuntime` object, ArkTS modules can be loaded. The interoperability context `mainContext` within the `JSRuntime` object allows for the creation and access of ArkTS data objects, among other operations. Currently, the ArkTS runtime can only be created on the main thread.

The following example demonstrates creating a `JSRuntime` object and obtaining the interoperability context through its `mainContext`:

<!-- compile -->

```cangjie
import ohos.ark_interop.*

func tryLoadArkTSSo() {
    // Create a new ArkTS runtime
    let runtime = JSRuntime()
    // Obtain the interoperability context
    let context = runtime.mainContext
    ...
}
```

### Loading ArkTS Modules

After successfully creating a `JSRuntime` object, Cangjie can load and run precompiled ArkTS modules. Precompiled ArkTS modules mainly include two types:

- Dynamic library `.so` files compiled from NAPI modules (C/C++)
- `.abc` bytecode files compiled from ArkTS modules

> **Note:**
>
> Currently, Cangjie only supports loading and running a subset of ArkTS modules. Attempting to call unsupported ArkTS modules will cause the program to fail.

Assuming there is an ArkTS system module `someModule` (a `.so` file), it can be loaded in Cangjie using the `requireSystemNativeModule` method, as shown in the following example:

<!-- compile -->

```cangjie
// Obtain the interoperability context
let context = runtime.mainContext

let module = context.requireSystemNativeModule("someModule")
```

### Calling ArkTS Interfaces

After successfully loading and running an ArkTS module, developers can call the APIs provided by the module using the `call` method.

Assuming the ArkTS module `someModule` exports an ArkTS interface `someFunc` with no parameters, it can be called as follows:

<!-- compile -->

```cangjie
let jsFunc: JSFunction = module["someFunc"].asFunction(context)

let result = jsFunc.call()
```