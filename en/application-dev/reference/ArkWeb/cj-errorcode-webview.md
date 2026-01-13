# Webview Error Codes

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

> **Note:**
>
> The following only introduces error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 17100001 WebviewController Not Associated with a Specific Web Component

**Error Message**

Init error. The WebviewController must be associated with a Web component.

**Error Description**

The WebviewController has not been associated with a specific Web component, making corresponding operations impossible.

**Resolution Steps**

Please check whether the WebviewController object has been associated with a Web component.

## 17100002 Invalid URL Format

**Error Message**

Invalid url.

**Error Description**

The URL format is incorrect.

**Resolution Steps**

Please verify that the entered URL is correct.

## 17100003 Invalid Resource Path

**Error Message**

Invalid resource path or file type.

**Error Description**

The resource path is incorrect.

**Possible Causes**

The file does not exist or is inaccessible at the specified resource path.

**Resolution Steps**

Please verify that the entered resource path is correct.

## 17100004 Feature Switch Not Enabled

**Error Message**

Function not enable.

**Error Description**

The feature switch is not enabled.

**Resolution Steps**

Please check whether the relevant feature switch has been configured to be enabled, such as verifying if the corresponding XXXAccess is set to true.

## 17100005 Invalid Cookie Value Format

**Error Message**

Invalid cookie value.

**Error Description**

The cookie value format is incorrect.

**Possible Causes**

Unsupported cookie value type.

**Resolution Steps**

Please verify that the entered value is correct.

## 17100006 Failed to Register Message Port Callback

**Error Message**

Can not register message event using this port.

**Error Description**

Failed to register a message port callback.

**Possible Causes**

The port may already be closed.

**Resolution Steps**

Please check whether the port is closed.

## 17100007 Invalid Back or Forward Operation

**Error Message**

Invalid back or forward operation.

**Error Description**

Invalid back or forward operation.

**Possible Causes**

1. Browsing history has been cleared.
2. No corresponding browsing operation exists for forward or backward navigation.

**Resolution Steps**

1. Check whether clearHistory was called.
2. Verify whether there are corresponding webpage navigations in the actual operation.

## 17100008 Deleting a Non-existent JavaScriptProxy

**Error Message**

Cannot delete JavaScriptProxy.

**Error Description**

Attempted to delete a non-existent JavaScriptProxy.

**Possible Causes**

The provided JavaScriptProxy was not previously registered.

**Resolution Steps**

Check whether the provided JavaScriptProxy was successfully registered.

## 17100009 Previous Zoom In/Out Operation Failed

**Error Message**

Cannot zoom in or zoom out.

**Error Description**

The previous zoom in/out operation failed.

**Possible Causes**

The maximum or minimum zoom scale has already been reached.

**Resolution Steps**

Check whether the current page scale has reached the maximum or minimum zoom size.

## 17100010 Unable to Send Messages Using This Port

**Error Message**

Cannot post message using this port.

**Error Description**

Unable to send messages using this port.

**Possible Causes**

The port is closed, or the peer port is closed.

**Resolution Steps**

1. Verify whether the local port has called the close interface.
2. Verify whether the local port has set the onMessageEvent callback.

## 17100011 Invalid Origin Parameter

**Error Message**

Invalid origin.

**Error Description**

The input origin parameter is invalid.

**Possible Causes**

1. The origin parameter is empty.
2. The origin parameter is invalid.

**Resolution Steps**

Check the input parameters.

## 17100012 No Available WebStorage Origin

**Error Message**

Invalid web storage origin.

**Error Description**

No available web storage origin.

**Possible Causes**

No relevant JS database API has been used.

**Resolution Steps**

1. Check whether any JS database API has been used.
2. If already in use, check the cause of the failure, such as whether the databaseAccess switch is enabled.

## 17100013 Invalid Socket Count During Preconnect

**Error Message**

The number of preconnect sockets is invalid.

**Error Description**

The input socket count during preconnect is invalid.

**Possible Causes**

The input socket count is less than or equal to 0 or greater than 6.

**Resolution Steps**

Verify that the input socket count is greater than 0 and less than or equal to 6.

## 17100014 Type and Value Mismatch

**Error Message**

The type does not match with the value of the message.

**Error Description**

The message type and value do not match.

**Possible Causes**

The retrieved value does not match the message type.

**Resolution Steps**

Call the corresponding interface based on the message type to retrieve the value. For example, if the type is BOOLEAN, call the GetBoolean interface to retrieve the boolean value.

## 17100015 Memory Allocation Failure

**Error Message**

New failed, out of memory.

**Error Description**

Allocation failed due to insufficient memory.

**Possible Causes**

The data to be sent is too large, causing memory allocation to fail.

**Resolution Steps**

Check the length of the data to be sent.

## 17100016 Download Task Not Paused

**Error Message**

The download is not paused.

**Error Description**

The download task is not in a paused state.

**Possible Causes**

WebDownloadItem.resume was called while the download was not paused.

**Resolution Steps**

The download was not paused and does not need to be resumed.

## 17100017 Invalid WebviewController

**Error Message**

No valid WebviewController is associated.

**Error Description**

The current WebviewController is invalid.

**Possible Causes**

The current WebviewController is not associated with a valid Web component.

**Resolution Steps**

Use a WebviewController associated with a valid Web component.

## 17100018 No Delegate Class Set to Receive Download Status

**Error Message**

No WebDownloadDelegate has been set yet.

**Error Description**

No delegate class has been set to receive download status.

**Possible Causes**

WebDownloadManager.resumeDownload was called without setting a delegate class.

**Resolution Steps**

First, set a delegate class via WebDownloadManager.setDownloadDelegate.

## 17100019 Download Not Started

**Error Message**

The download has not been started yet.

**Error Description**

The download task has not started.

**Possible Causes**

The download task has not started, making pause/resume operations invalid.

**Resolution Steps**

Call start('xxx') in WebDownloadDelegate.onBeforeDownload and specify the download path.

## 17100020 Failed to Register Custom Schemes

**Error Message**

Failed to register custom schemes.

**Error Description**

Failed to register custom schemes.

**Possible Causes**

Custom schemes were set after the ArkWeb engine was initialized.

**Resolution Steps**

Custom schemes must be registered before the ArkWeb engine is initialized.

## 17100021 WebResourceHandler Invalid

**Error Message**

The resource handler is invalid.

**Error Description**

The WebResourceHandler is invalid.

**Possible Causes**

1. The corresponding request was not intercepted in WebSchemeHandler.
2. The request ended before constructing the response body due to certain reasons.
3. The WebResourceHandler has already called didFinish or didFail.

**Resolution Steps**

Do not call WebResourceHandler interfaces under the above-mentioned conditions.

## 17100022 WebHttpBodyStream Initialization Failed

**Error Message**

Failed to initialize the HTTP body stream.

**Error Description**

WebHttpBodyStream data initialization failed.

**Possible Causes**

The data carried in POST or similar requests is invalid. For example, if the data stream contains file-type data but the file path does not exist, the data stream initialization will fail.

**Resolution Steps**Verify whether the data carried in POST and other types of requests is valid.