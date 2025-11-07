# Event Error Codes

> **Note:**
>
> This document only covers error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 1500001 Empty Action in Want

**Error Message**  
The action field in the want parameter is null.

**Error Description**  
This error code occurs when the `Action` property in the `want` parameter of an event is empty.

**Possible Causes**  
The `Action` property in the `want` parameter of the event is empty.

**Resolution Steps**  
Check whether the `Action` property in the `want` parameter is empty.

## 1500002 Sandbox Application Cannot Send Common Events

**Error Message**  
A sandbox application cannot send common events.

**Error Description**  
Sandbox applications are unable to send common events.

**Possible Causes**  
The event sender is a sandbox application, and the event is intercepted.

**Resolution Steps**  
Sandbox applications cannot send common events. Verify whether the application is a sandbox application before sending common events.

## 1500003 Excessive Event Sending Frequency

**Error Message**  
Too many common events are sent in a short period of time.

**Error Description**  
The application is sending events too frequently.

**Possible Causes**  
The application has sent too many events within a short time.

**Resolution Steps**  
Check whether the application is sending events too frequently.

## 1500004 Unable to Send System Common Events

**Error Message**  
A third-party application cannot send system common events.

**Error Description**  
The current application cannot send system common events.

**Possible Causes**  
A non-system application or non-system service is attempting to send system common events.

**Resolution Steps**  
Verify whether the current application is a system application or the current service is a system service.

## 1500005 Subscriber Not Found

**Error Message**  
The subscriber is not found.

**Error Description**  
The subscriber cannot be found.

**Possible Causes**  
The subscriber has been deleted.

**Resolution Steps**  
Check whether there are duplicate unsubscribe operations.

## 1500006 Invalid UserId

**Error Message**  
Invalid userId.

**Error Description**  
The userId is invalid.

**Possible Causes**  
The userId does not match the system `userId`, or the application/service is not a system application or system service.

**Resolution Steps**  

1. Check whether the current `userId` matches the system `userId`.  
2. Verify whether the current application is a system application or system service.

## 1500007 IPC Request Sending Failed

**Error Message**  
Failed to send the message.

**Error Description**  
The IPC request failed to send.

**Possible Causes**  
The connection object was not successfully created.

**Resolution Steps**  
Avoid frequent connection establishment and retry later.

## 1500008 Failed to Read Data

**Error Message**  
Failed to read the data.

**Error Description**  
An error occurred on the server side.

**Possible Causes**  
The server encountered a business exception while processing data.

**Resolution Steps**  
Retry later.

## 1500009 System Error

**Error Message**  
System error.

**Error Description**  
A system exception occurred during business processing, such as failure to obtain the current system time.

**Possible Causes**  
System malfunction, such as an exception while retrieving the current system time.

**Resolution Steps**  
Retry later.