# Interoperation Error Codes

> **Note:**
>
> The following only introduces error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 34300001 Illegal Index

**Error Message**

The index used exceeds the allowed range.

**Error Description**

This error code is reported when the specified index exceeds the permitted range.

**Possible Causes**

The specified index is less than 0 or exceeds the upper limit.

**Resolution Steps**

1. Ensure the specified index is greater than or equal to 0.
2. Ensure the specified index is less than the upper limit.

## 34300002 ArkTS Code Exception

**Error Message**

An exception occurred in the executed ArkTS code.

**Error Description**

ArkTS runtime exception or an exception occurred in the called ArkTS function.

**Possible Causes**

1. ArkTS runtime exceptions such as StackOverflow.
2. Incorrect parameters passed or logical errors in the ArkTS function implementation.

**Resolution Steps**

1. Verify the parameters passed to the ArkTS function are correct.
2. Check the logic of the called function for correctness.

## 34300003 Illegal Object Access

**Error Message**

The accessed object has exceeded its lifecycle.

**Error Description**

The accessed object has been released.

**Possible Causes**

- Accessing JSValue beyond its scope.
- The accessed JSPromiseCapability has already completed.
- Continuing to access JSContext after the ArkTS runtime has been released.

**Resolution Steps**

Use safe references to escape the current scope for access.

## 34300004 Thread Verification Failed

**Error Message**

Interoperation performed on a non-ArkTS runtime thread.

**Error Description**

This error code is reported when creating or accessing ArkTS objects on a non-ArkTS runtime thread.

**Possible Causes**

Creating or accessing ArkTS objects on a non-ArkTS runtime thread.

**Resolution Steps**

Before performing interoperation, use the interface `JSContext.isBindThread()` to verify if the current thread is an ArkTS runtime thread.

## 34300005 Type Verification Failed

**Error Message**

ArkTS data type mismatch.

**Error Description**

This error code is reported when incorrect type operations are performed on ArkTS data.

**Possible Causes**

Incorrect type conversion, such as converting a number to JSString.

**Resolution Steps**

Verify the data type before performing operations.

## 34300008 ArrayBuffer Memory Size Misaligned

**Error Message**

ArrayBuffer memory size is not aligned.

**Error Description**

This error code is reported when reading an array from an ArrayBuffer whose byte length is not aligned with the array element type.

**Possible Causes**

Reading a UInt16 array from an ArrayBuffer with byteLength of 1.

**Resolution Steps**

Ensure the ArrayBuffer's byteLength is aligned before performing operations.

## 34300009 Encoding Conversion Error

**Error Message**

Encoding conversion error.

**Error Description**

The Unicode range expressible by UTF-8 encoding is larger than that of UTF-16. This error code is reported when converting a UTF-8 string containing characters outside the UTF-16 range to a UTF-16 string.

**Possible Causes**

The UTF-8 string contains characters outside the UTF-16 encoding range.

**Resolution Steps**

Check if the UTF-8 string contains characters outside the UTF-16 encoding range.

## 34300010 Unknown Native Reference

**Error Message**

Unknown Native reference.

**Error Description**

Native references created via the napi interface are type-compatible with JSExternal. This error code is reported when attempting to retrieve an object from such a reference.

**Possible Causes**

The accessed Native reference was not created by Cangjie.

**Resolution Steps**

Ensure the input is a Native reference created by Cangjie.

## 34300011 Property Access Error

**Error Message**

Property access error.

**Error Description**

This error code is reported when the accessed property does not exist or the type is mismatched.

**Possible Causes**

The accessed property does not exist or the type is mismatched.

**Resolution Steps**

Ensure the property exists and the type is correct.

## 34300012 Integer Overflow Error

**Error Message**

Integer overflow error.

**Error Description**

This error code is reported when an integer overflow occurs during data conversion.

**Possible Causes**

1. The source value exceeds the target type's range.
2. Precision loss occurs during numerical conversion.

**Resolution Steps**

Ensure the source value is within the target type's range.

## 34300013 Dictionary Key Not Found

**Error Message**

Dictionary key not found.

**Error Description**

This error code is reported when a key expected to exist in a dictionary cannot be found.

**Possible Causes**

The searched key does not exist.

**Resolution Steps**

Verify the key's existence before accessing it.

## 34300014 Runtime Creation Failed

**Error Message**

Runtime creation failed.

**Error Description**

This error code is reported when runtime creation fails.

**Possible Causes**

1. Insufficient system memory.
2. Attempting to create runtime on a non-main thread.

**Resolution Steps**

Ensure runtime is created on the main thread and check for insufficient system memory.