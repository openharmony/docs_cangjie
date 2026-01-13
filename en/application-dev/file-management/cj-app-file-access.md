# Application File Access (Cangjie)

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Applications need to perform operations such as viewing, creating, reading, writing, deleting, moving, copying, and retrieving attributes on application files within the application file directory. The specific methods are described below.

## Interface Description

Developers can implement application file access capabilities through basic file operation interfaces ([ohos.file_fs](../reference/CoreFileKit/cj-apis-file_fs.md)). The main functionalities are listed in the following table.

| Interface Name | Functionality                     | Interface Type |
| -------------- | --------------------------------- | ------------- |
| access         | Check if a file exists            | Method        |
| close          | Close a file                      | Method        |
| copyFile       | Copy a file                       | Method        |
| createStream   | Open a file stream based on path  | Method        |
| listFile       | List all filenames in a directory | Method        |
| mkdir          | Create a directory                | Method        |
| moveFile       | Move a file                       | Method        |
| open           | Open a file                       | Method        |
| read           | Read data from a file             | Method        |
| rename         | Rename a file or directory        | Method        |
| rmdir          | Delete an entire directory        | Method        |
| stat           | Retrieve detailed file attributes | Method        |
| unlink         | Delete a single file              | Method        |
| write          | Write data to a file              | Method        |
| Stream.close   | Close a file stream               | Method        |
| Stream.flush   | Flush a file stream               | Method        |
| Stream.write   | Write data to a stream file       | Method        |
| Stream.read    | Read data from a stream file      | Method        |
| File.fd        | Get file descriptor               | Property      |
| OpenMode       | Set file opening flags            | Property      |
| Filter         | Configure file filtering options  | Type          |

## Development Examples

Before accessing application files, developers need to obtain the application file path. The example below demonstrates how to retrieve the HAP-level file path from AbilityContext. For details on obtaining AbilityContext, refer to [Obtaining UIAbility Context Information](../application-models/cj-uiability-usage.md#获取uiability的上下文信息).

Below are examples of common operations.

### Create and Read/Write a File

The following example demonstrates how to create a file and perform read/write operations.

<!-- compile -->

```cangjie
// xxx.cj
import kit.CoreFileKit.*
import kit.AbilityKit.*
import ohos.base.*

// Refer to the section on obtaining UIAbility context information
let context = getContext()
// Get application file path
let filesDir = context.filesDir

func createFile(): Unit {
    // Create and open the file if it doesn't exist; open it if it exists
    let file = FileIo.open(filesDir + '/test.txt', mode: OpenMode.READ_WRITE | OpenMode.CREATE)
    // Write content to the file
    let writeLen = FileIo.write(file.fd, "Try to write str.")
    Hilog.info(1, "info", "The length of str is: ${writeLen}")
    let bufSize = 4096
    var readSize = 0
    // Create an Array<Byte> object of size 1024 to store read data
    let array = Array<Byte>(1024, repeat: 0)
    // Set read offset and length
    let readOptions = ReadOptions(
        offset: readSize,
        length: UIntNative(bufSize)
    )
    // Read file content into ArrayBuffer and return the actual bytes read
    let readLen = FileIo.read(file.fd, array, options: readOptions)
    Hilog.info(1, "info", "the content of file: ${String.fromUtf8(array[..readLen])}")
    // Close the file
    FileIo.close(file)
}
```

### Read File Content and Write to Another File

The following example demonstrates how to read content from one file and write it to another.

<!-- compile -->

```cangjie
// xxx.cj
import kit.CoreFileKit.*
import kit.AbilityKit.*
import ohos.base.*

// Refer to the section on obtaining UIAbility context information
let context = getContext()
// Get application file path
let filesDir = context.filesDir

func readWriteFile() {
    // Open files
    let srcFile = FileIo.open(filesDir + '/test.txt', mode: OpenMode.READ_WRITE | OpenMode.CREATE)
    let destFile = FileIo.open(filesDir + '/destFile.txt', mode: OpenMode.READ_WRITE | OpenMode.CREATE)
    // Read source file content and write to destination file
    let bufSize = 4096
    var readSize = 0
    let buf = Array<Byte>(bufSize, repeat: 0)
    var readOptions = ReadOptions(
        offset: readSize,
        length: UIntNative(bufSize)
    )
    var readLen = FileIo.read(srcFile.fd, buf, options: readOptions)
    while (readLen > 0) {
        readSize += readLen
        let writeOptions = WriteOptions(
            length: UIntNative(readLen)
        )
        FileIo.write(destFile.fd, buf, options: writeOptions)
        readOptions.offset = readSize
        readLen = FileIo.read(srcFile.fd, buf, options: readOptions)
    }
    // Close files
    FileIo.close(srcFile)
    FileIo.close(destFile)
}
```

> **Note:**
>
> When using read/write interfaces, pay attention to the `offset` parameter setting. For existing files that have been read/written before, the file pointer defaults to the end position of the last operation.

### Read/Write Files Using Streams

The following example demonstrates how to use stream interfaces to read content from `test.txt` and write it to `destFile.txt`.

<!-- compile -->

```cangjie
// xxx.cj
import kit.CoreFileKit.*
import kit.AbilityKit.*
import ohos.base.*

// Refer to the section on obtaining UIAbility context information
let context = getContext()
// Get application file path
let filesDir = context.filesDir

func readWriteFileWithStream() {
    // Create and open input file stream
    let inputStream = FileIo.createStream(filesDir + '/test.txt', 'r+')
    // Create and open output file stream
    let outputStream = FileIo.createStream(filesDir + '/destFile.txt', "w+")

    let bufSize = 4096
    var readSize = 0
    let buf = Array<Byte>(bufSize, repeat: 0)
    var readOptions = ReadOptions(
        offset: readSize,
        length: UIntNative(bufSize)
    )
    // Read source file content via stream and write to target file
    var readLen = inputStream.read(buf, options: readOptions)
    readSize += readLen
    while (readLen > 0) {
        outputStream.write(buf[0..readLen])
        readOptions.offset = readSize
        readLen = inputStream.read(buf, options: readOptions)
        readSize += readLen
    }
    // Close file streams
    inputStream.close()
    outputStream.close()
}
```

> **Note:**
>
> When using stream interfaces, ensure timely closure of streams. Stream interfaces do not support concurrent read/write operations.

### List Files

The following example demonstrates how to list files.

<!-- compile -->

```cangjie
import kit.CoreFileKit.*
import kit.CoreFileKit.*
import kit.AbilityKit.*
import ohos.base.*

// Refer to the section on obtaining UIAbility context information
let context = getContext()
// Get application file path
let filesDir = context.filesDir

// List files
func getListFile() {
    let listFileOption = ListFileOptions(
        recursion: false,
        listNum: 0,
        filter: Filter(
            suffix: [".png", ".jpg", ".txt"],
            displayName: ["test*"],
            fileSizeOver: 0,
            lastModifiedAfter: 10000.0
        )
    )
    let files = FileIo.listFile(filesDir, options: listFileOption)
    for (item in files) {
        Hilog.info(1, "info", "The name of file: ${item}")
    }
}
```