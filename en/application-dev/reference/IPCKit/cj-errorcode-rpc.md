# RPC Error Codes

## 1900001 System Call mmap Failed

**Error Message**

Failed to call mmap.

**Error Description**

The system call mmap execution failed.

**Possible Causes**

1. The mapping region is too large.
2. High system memory pressure with insufficient available memory for mapping.

**Resolution Steps**

1. Verify if an excessively large memory size was specified when calling Ashmem::create();
2. Check whether the system has sufficient available memory during mapping execution.

## 1900002 System Call ioctl Failed

**Error Message**

Failed to call ioctl.

**Error Description**

The system call ioctl execution on the shared memory file descriptor failed.

**Possible Causes**

1. Invalid kernel parameters were set;
2. The specified type exceeds the type defined during shared memory mapping.

**Resolution Steps**

1. Verify if the specified parameters originate from Ashmem class's PROT_EXEC, PROT_READ, and PROT_WRITE;
2. Check whether the specified parameters are subsets of the types defined during shared memory mapping.

## 1900003 Shared Memory Write Failure

**Error Message**

Failed to write data to the shared memory.

**Error Description**

Failed to write data to shared memory.

**Possible Causes**

1. The single or cumulative write size exceeds the mapped shared memory capacity;
2. PROT_WRITE mode was not set for the shared memory.

**Resolution Steps**

1. Verify if current write operations exceed the total mapped size;
2. Check whether PROT_WRITE protection permission was configured.

## 1900004 Shared Memory Read Failure

**Error Message**

Failed to read data from the shared memory.

**Error Description**

Failed to read data from shared memory.

**Possible Causes**

1. The single or cumulative read size exceeds the mapped shared memory capacity;
2. PROT_READ mode was not set for the shared memory.

**Resolution Steps**

1. Verify if current read operations exceed the total mapped size;
2. Check whether PROT_READ protection permission was configured.

## 1900005 IPC Object Permission Error

**Error Message**

Operation allowed only for the proxy object.

**Error Description**

This operation is permitted only for proxy objects.

**Possible Causes**

A method supported exclusively by RemoteProxy was invoked on a RemoteObject.

**Resolution Steps**

Verify if methods exclusive to RemoteProxy were called on a RemoteObject.

## 1900006 IPC Object Permission Error

**Error Message**

Operation allowed only for the remote object.

**Error Description**

This operation is permitted only for remote objects.

**Possible Causes**

A method supported exclusively by RemoteObject was invoked on a RemoteProxy.

**Resolution Steps**

Verify if methods exclusive to RemoteObject were called on a RemoteProxy.

## 1900007 Remote Object Communication Failure

**Error Message**

Communication failed.

**Error Description**

Inter-process communication with the remote object failed.

**Possible Causes**

1. The remote object has been destroyed;
2. The remote object was destroyed and recreated, rendering the local proxy object obsolete.

**Resolution Steps**

1. Verify if the remote object has been destroyed;
2. Check whether a death notification was registered and if the remote object underwent destruction and recreation.

## 1900008 Invalid IPC Object

**Error Message**

The proxy or remote object is invalid.

**Error Description**

Invalid proxy or remote object.

**Possible Causes**

1. The proxy object has expired;
2. The remote object has been destroyed.

**Resolution Steps**

1. Verify if any exceptions occurred during proxy object acquisition;
2. Check whether the remote object has been destroyed.

## 1900009 MessageSequence Write Failure

**Error Message**

Failed to write data to the message sequence.

**Error Description**

Failed to write data to MessageSequence.

**Possible Causes**

The default sequence capacity has been exhausted.

**Resolution Steps**

Use MessageSequence's buffer space query methods to confirm remaining capacity.

## 1900010 MessageSequence Read Failure

**Error Message**

Failed to read data from the message sequence.

**Error Description**

Failed to read data from MessageSequence.

**Possible Causes**

Read and write operations were performed in inconsistent order.

**Resolution Steps**

Ensure read operations strictly follow the write sequence.

## 1900011 Memory Allocation Failure

**Error Message**

Memory allocation failed.

**Error Description**

Memory allocation failed during serialization.

**Possible Causes**

Excessively large data was written.

**Resolution Steps**

Verify if the written data or configured parameters are too large.

## 1900012 JS Method Failure

**Error Message**

Failed to call the JS callback function.

**Error Description**

Execution of JS callback method failed.

**Possible Causes**

The business JS method returned a failure.

**Resolution Steps**

Verify whether the business JS method executed successfully.

## 1900013 System Call dup Failed

**Error Message**

Failed to call dup.

**Error Description**

The system call dup execution failed.

**Possible Causes**

1. The process has exhausted its file descriptor resources;
2. The input fd parameter has been closed.

**Resolution Steps**

1. Verify if the input fd remains valid;
2. Investigate whether the process has exhausted fd resources.