# Overview of Cangjie-ArkTS Interoperability

On the OpenHarmony system, to reuse the ArkTS ecosystem, Cangjie supports mutual calls with ArkTS, which is referred to as Cangjie-ArkTS interoperability. Cangjie-ArkTS interoperability is based on Cangjie CFFI (C Foreign Function Interface) and ArkTS runtime interfaces, providing users with library-level interoperability capabilities.

Cangjie-ArkTS interoperability can be divided into two usage scenarios: using ArkTS in Cangjie applications and using Cangjie in ArkTS applications. In terms of calling methods, it can be categorized into ArkTS calling Cangjie and Cangjie calling ArkTS. ArkTS calling Cangjie can be further divided into development using interoperability macros and development using interoperability libraries. Cangjie calling ArkTS includes two scenarios: calling ArkTS system libraries and calling third-party ArkTS libraries. Calling system libraries is developed through dynamic import, while calling third-party libraries is developed using the HLE tool. The distinctions are shown in the following table:

Before introducing all usage methods, let's first explain the interoperability library. The interoperability library is a standard library that assists in implementing interoperability functions, primarily containing some type representations corresponding to ArkTS in Cangjie and APIs within these types. Several core types (not exhaustive) of the interoperability library are:

1. **JSValue**: Represents a unified ArkTS data type, used for parameter passing in cross-language calls.
2. **JSContext**: Represents the ArkTS runtime context, assisting in converting JSValue to Cangjie data.
3. **JSCallInfo**: Represents the parameter collection of an ArkTS function call, including all input parameters and the `this` pointer.
4. **JSRuntime**: Represents the ArkTS runtime created by Cangjie.