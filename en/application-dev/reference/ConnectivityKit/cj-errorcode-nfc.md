# NFC Error Codes

> **Note:**
>
> The following describes only the module-specific error codes. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 3100101

**Error Message**

NFC state is abnormal in service.

**Error Description**

The NFC service encountered an exception while executing NFC activation or deactivation internally.

**Possible Causes**

1. Communication exception with the NFC service.
2. Communication exception with the NFC chip.

**Handling Steps**

1. Retry activating or deactivating NFC.
2. Retry activating or deactivating NFC, or restart the device.

## 3100201

**Error Message**

Tag running state is abnormal in service.

**Error Description**

The NFC service encountered an error while executing Tag business logic.

**Possible Causes**

1. The Tag parameter values do not match the requirements of the called function.
2. The NFC state was deactivated during Tag operations.
3. The Tag was already disconnected before the operation.
4. The Tag chip returned an error status or response timeout.
5. No binding relationship was established with the NFC service, making it impossible to call the interface.

**Handling Steps**

1. Verify that the NFC parameters match the called interface.
2. Activate the device's NFC.
3. Call the connection first before performing read/write operations.
4. Retry tapping to read the card.
5. Exit the application and retry reading the card.

## 3100202

**Error Message**

The element state is invalid.

**Error Description**

When calling the interface, the page state of the application reading the card was incorrect, as the page was not in the foreground.

**Possible Causes**

The page state of the application reading the card was incorrect, as the page was not in the foreground.

**Handling Steps**

1. Only allow the interface to be called from the application's foreground page.

## 3100203

**Error Message**

The off() can be called only when the on() has been called.

**Error Description**

The off() interface can only be called after the on() interface has been called.

**Possible Causes**

1. The application's foreground page directly called the off() interface without first calling the on() interface.

**Handling Steps**

1. The application's foreground page should first execute the on() interface and then call the off() interface upon page exit.

## 3100204

**Error Message**

Tag I/O operation failed.

**Error Description**

NFC Tag I/O operation failed.

**Possible Causes**

1. The NFC Tag does not support the executed read/write operation.

**Handling Steps**

1. The application should handle the exception or provide prompts based on the business scenario.

## 3100301

**Error Message**

Card emulation running state is abnormal in service.

**Error Description**

The NFC service encountered an error while executing card emulation business logic.

**Possible Causes**

1. The NFC state was deactivated during card emulation.
2. The NFC chip returned an error status or response timeout.

**Handling Steps**

1. If the NFC is deactivated, prompt the user to activate it.
2. Prompt the user to deactivate and reactivate NFC to reinitialize the hardware.

## 3200101

**Error Message**

Connected NFC tag running state is abnormal in service.

**Error Description**

An error occurred while executing active NFC Tag business logic.

**Possible Causes**

1. The active NFC Tag parameter values do not match the requirements of the called function.
2. The active NFC Tag chip returned an error status or response timeout.

**Handling Steps**

1. Verify that the active NFC Tag parameters match the called interface.
2. Retry tapping to read the card.