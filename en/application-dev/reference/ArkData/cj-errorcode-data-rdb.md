# Relational Database Error Codes

> **Note:**
>
> This document only introduces error codes specific to this module. For general error codes, please refer to the [Universal Error Code Documentation](../cj-errorcode-universal.md).

## 14800000 Internal Error

**Error Message**

Inner error.

**Error Description**

Internal error.

**Possible Causes**

Check the error log first for detailed error information. Main causes include:

1. SQL execution exception.
2. Internal state exception.
3. Incorrect interface usage.
4. System errors such as null pointer, insufficient memory, abnormal restart of data service, I/O error, IPC exception, JS engine exception, etc.

**Resolution Steps**

1. Developers should check if SQL statements and predicates are used correctly.
2. Developers should check if objects are being used after being closed.
3. Developers should verify if interfaces are used correctly as per the documentation.
4. Try retrying. If the issue persists, prompt the user to restart the application, upgrade the application, or update the device version.

## 14800010 Invalid Database Path

**Error Message**

Invalid database path.

**Error Description**

Invalid database path.

**Possible Causes**

Invalid database path.

**Resolution Steps**

Check the provided database path.

## 14800011 Database File Corrupted

**Error Message**

Database corrupted.

**Error Description**

This error code indicates that the database is corrupted when calling interfaces for operations such as insertion, deletion, query, or data synchronization.

**Possible Causes**

The database file is corrupted during operations like insertion, deletion, query, or data synchronization.

**Resolution Steps**

1. If a backup exists, attempt to restore the database using the backup file.
2. If no backup exists, try deleting and recreating the database.

## 14800012 Result Set Empty or Invalid Position

**Error Message**

Row out of bounds.

**Error Description**

Result set is empty or the specified position is invalid.

**Possible Causes**

The result set is empty or the specified row number is out of the valid range [0, m - 1], where m = resultsetV9.rowCount.

**Resolution Steps**

Check if the current result set is empty or if the specified position is valid.

## 14800013 Column Value Null or Incompatible Column Type

**Error Message**

Column out of bounds.

**Error Description**

Column value is null or the column type is incompatible with the current interface call.

**Possible Causes**

1. Result set is empty.
2. Current row number is out of range [0, m - 1], where m = resultsetV9.rowCount.
3. Current column number is out of range [0, n - 1], where n = resultsetV9.columnCount.
4. Current column data type is not supported by the interface.

**Resolution Steps**

1. Check if the result set is empty.
2. Verify if the current row and column numbers are within valid ranges.
3. Ensure the current column data type is supported.

## 14800014 Database or Result Set Closed

**Error Message**

Already closed.

**Error Description**

Database or result set is closed.

**Possible Causes**

Objects with close interfaces (e.g., RdbStore or ResultSet) have either been closed or failed to open successfully.

**Resolution Steps**

Reopen the RdbStore or requery to obtain a new ResultSet.

## 14800015 Database Unresponsive

**Error Message**

The database does not respond.

**Error Description**

Database is unresponsive.

**Possible Causes**

Read, write, attach, or detach operations are in progress, preventing the current operation from executing within the specified time (default: 2s).

**Resolution Steps**

Retry the operation.

## 14800016 Database Alias Already in Use

**Error Message**

The database is already attached.

**Error Description**

The alias of the attached database is already in use.

**Possible Causes**

The alias of the attached database is already in use.

**Resolution Steps**

Either skip attaching the database or modify the alias of the attached database.

## 14800017 Critical Configuration Changed

**Error Message**

Config changed.

**Error Description**

Critical database configuration has been modified.

**Possible Causes**

Changes to critical configurations such as area, isEncrypt, or securityLevel.

**Resolution Steps**

Either revert to the original configuration or export data using the original configuration, delete the old database, create a new one with the new configuration, and import the data.

## 14800018 No Data Matches the Condition

**Error Message**

No data meets the condition.

**Error Description**

SQL statement is incorrect, and no data matching the condition was found.

**Possible Causes**

The SQL statement does not correctly query the result set.

**Resolution Steps**

Write a correct query statement or add data to the database before querying.

## 14800019 SQL Must Be a Query Statement

**Error Message**

The SQL must be a query statement.

**Error Description**

SQL must be a query statement.

**Possible Causes**

SQL statement does not comply with specifications, causing query failure.

**Resolution Steps**

Write an SQL statement that complies with the specifications.

## 14800021 SQLite: Generic Error

**Error Message**

SQLite: Generic error.

**Error Description**

SQLite: Generic error.

**Possible Causes**

Errors during SQL execution, such as:

1. Inserting or updating a non-existent table.
2. Inserting or updating a non-existent column.
3. Calling undefined functions. Refer to SQLITE_ERROR scenarios.

**Resolution Steps**

Analyze the SQL statement to identify the error.

## 14800022 SQLite: Callback Request Aborted

**Error Message**

SQLite: Callback routine requested an abort.

**Error Description**

SQLite: Callback request aborted.

**Possible Causes**

1. Typically occurs when using SQLite's custom function mechanism, where the callback is aborted.
2. Refer to SQLITE_ABORT scenarios.

**Resolution Steps**

Check the implementation of SQLite hook functions (callbacks) to ensure correctness.

## 14800023 SQLite: Access Permission Denied

**Error Message**

SQLite: Access permission denied.

**Error Description**

SQLite access permission denied.

**Possible Causes**

1. OS-level permission issues, where SQLite lacks sufficient permissions to access or modify a file.
2. Refer to SQLITE_PERM scenarios.

**Resolution Steps**

1. Ensure the file is not read-only; if so, remove the read-only attribute.
2. Verify file and folder permissions to ensure the current user has sufficient read/write permissions.
3. Check if the file system is read-only; if so, switch to writable mode.
4. Ensure no other processes are locking the database file; if so, terminate those processes.
5. Ensure sufficient permissions to modify file or folder permissions.

## 14800024 SQLite: Database File Locked

**Error Message**

SQLite: The database file is locked.

**Error Description**

SQLite database file is locked.

**Possible Causes**

1. Concurrent database operations by multiple processes (e.g., UIability and datashareability) or processes within the same group.
2. Refer to SQLITE_BUSY scenarios.

**Resolution Steps**

1. Avoid concurrent database operations by processes.
2. Retry after waiting.

## 14800025 SQLite: Table Locked

**Error Message**

SQLite: A table in the database is locked.

**Error Description**

SQLite: A table in the database is locked.

**Possible Causes**

1. Attempting to write to a SQLite database while the file is locked by another process, possibly due to an ongoing transaction or other locking mechanisms.
2. Refer to SQLITE_LOCKED scenarios.

**Resolution Steps**

1. Ensure no other processes or threads are writing to the database file.
2. If using transactions, avoid write operations before committing.
3. Check for other locking mechanisms (e.g., file locks) blocking writes.
4. Ensure database connections are properly closed after operations.
5. In multi-threaded environments, use locks to prevent race conditions.

## 14800026 SQLite: Out of Memory

**Error Message**

SQLite: The database is out of memory.

**Error Description**

SQLite: Database out of memory.

**Possible Causes**

Insufficient memory due to large data volume or inadequate memory allocation.

**Resolution Steps**

Reduce data volume or increase memory allocation.

## 14800027 SQLite: Attempt to Write Readonly Database

**Error Message**

SQLite: Attempt to write a readonly database.

**Error Description**

SQLite: Attempt to write a readonly database.

**Possible Causes**

1. Attempting to write to a SQLite database opened in read-only mode, possibly due to file permissions, read-only file system, or database marked as read-only.
2. Refer to SQLITE_READONLY scenarios.

**Resolution Steps**

1. Ensure sufficient permissions to write to the database file.
2. If the file system is read-only, switch to writable mode.
3. Verify that the database was not opened with read-only parameters.

## 14800028 SQLite: Disk I/O Error

**Error Message**

SQLite: Some kind of disk I/O error occurred.

**Error Description**

SQLite: A disk I/O error occurred.

**Possible Causes**

Possible reasons include:

1. File does not exist.
2. File is read-only.
3. Insufficient disk space.
4. File corruption.
5. Refer to SQLITE_IOERR scenarios.

**Resolution Steps**

1. Verify the file path and existence.
2. Ensure the file is not read-only.
3. Check disk space and free up space if necessary.
4. Verify file permissions to ensure the application has sufficient read/write access.

## 14800029 SQLite: Database Full

**Error Message**

SQLite: The database is full.

**Error Description**

SQLite database is full.

**Possible Causes**

Database is full due to excessive data volume or insufficient disk space.

**Resolution Steps**

Reduce data volume or increase disk space.## 14800030 SQLite: Unable to Open Database File

**Error Message**

SQLite: Unable to open the database file.

**Error Description**

SQLite: Unable to open the database file.

**Possible Causes**

1. The file does not exist, and creating a new database failed.
2. The file exists, but the database file is corrupted.
3. File permission issues prevent SQLite from reading or writing the file.
4. Insufficient disk space.
5. Refer to error scenarios related to SQLITE_CANTOPEN.

**Resolution Steps**

1. Verify the database file path is correct, check file permissions, and ensure the application has sufficient permissions to read/write the file.
2. Confirm there is adequate disk space.

## 14800031 SQLite: TEXT or BLOB Exceeds Size Limit

**Error Message**

SQLite: TEXT or BLOB exceeds size limit.

**Error Description**

SQLite: TEXT or BLOB exceeds size limit.

**Possible Causes**

1. The query result set exceeds the size limit that SQLite can handle.
2. Refer to error scenarios related to SQLITE_TOOBIG.

**Resolution Steps**

Break down large queries into smaller ones, processing data in batches.

## 14800032 SQLite: Abort Due to Constraint Violation

**Error Message**

SQLite: Abort due to constraint violation.

**Error Description**

SQLite: Abort due to constraint violation.

**Possible Causes**

1. Attempting to write to the SQLite database violated its integrity constraints.
2. Refer to error scenarios related to SQLITE_CONSTRAINT.

**Resolution Steps**

Check if the data being inserted or updated violates the specified constraints.

## 14800033 SQLite: Data Type Mismatch

**Error Message**

SQLite: Data type mismatch.

**Error Description**

SQLite: Data type mismatch.

**Possible Causes**

1. The data types involved in an SQL statement do not match those stored in the database.
2. Refer to error scenarios related to SQLITE_MISMATCH.

**Resolution Steps**

Verify the data types of columns in the SQL statement and ensure the inserted, updated, or queried data types match the column data types.

## 14800034 SQLite: Library Used Incorrectly

**Error Message**

SQLite: Library used incorrectly.

**Error Description**

SQLite: Library used incorrectly.

**Possible Causes**

1. Indicates incorrect database operations or usage context. This error typically occurs in the following scenarios:
    - Performing another operation before the current database operation completes.
    - Continuing operations on a database connection after it has been closed.
    - Using database objects that have been released or are invalid.
2. Refer to error scenarios related to SQLITE_MISUSE.

**Resolution Steps**

1. Ensure proper synchronization between database operations, such as using locks or other synchronization mechanisms.
2. Ensure the database connection is open before use and closed after operations are completed.
3. Ensure all database objects are properly released after use.

## 14800047 WAL File Size Exceeds Default Limit

**Error Message**

The WAL file size exceeds the default limit.

**Error Description**

The WAL file size exceeds the default limit (200M).

**Possible Causes**

Continuous insert, update, or delete operations while read transactions are open or result sets are not closed, causing the WAL file size to exceed the default limit.

**Resolution Steps**

Check if result sets or transactions are left unclosed.

Close all result sets or transactions.

## 14800050 Failed to Obtain Subscription Service

**Error Message**

Failed to obtain subscription service.

**Error Description**

Failed to obtain subscription service.

**Possible Causes**

The current platform does not support subscription services.

**Resolution Steps**

Deploy subscription services on the current platform.

## 14801001 Context Environment Not in Stage Model

**Error Message**

Only supported in stage mode.

**Error Description**

This operation is only supported in Stage model.

**Possible Causes**

The current context environment is not in Stage model.

**Resolution Steps**

Switch the current context environment to use Stage model.

## 14801002 Invalid dataGroupId Parameter in storeConfig

**Error Message**

The data group id is not valid.

**Error Description**

Invalid dataGroupId parameter used.

**Possible Causes**

The dataGroupId used was not properly obtained from the application market.

**Resolution Steps**

Apply for a dataGroupId from the application market and pass it correctly.

## 14800051 Distributed Table Type Mismatch

**Error Message**

The type of the distributed table does not match.

**Error Description**

Inconsistent distributed table types set for the same database table.

**Possible Causes**

Inconsistent distributed table types set for the same database table. For distributed table types, refer to [DistributedType](../ArkData/cj-apis-relational_store.md#enum-distributedtype).

**Resolution Steps**

Ensure consistent distributed table types for the same database table. A distributed table configured for device-device synchronization cannot be reconfigured for device-cloud synchronization.