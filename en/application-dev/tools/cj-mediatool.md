# mediatool Tool

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

mediatool is a lightweight command-line toolset that allows developers to manipulate media library resources. The media library provides and manages data for the gallery, where images and videos from the media library are displayed in the gallery interface.

The mediatool comes pre-installed with the system and does not require additional installation. It is built into the `/bin` folder and can be directly invoked via hdc shell.

## Prerequisites

- Device must be properly connected.
- Developer mode must be enabled in system settings.
- Use `hdc shell` to enter command-line execution mode.

## Command Line Instructions

<!--Del-->

### mediatool send

```shell
mediatool send <path-to-local-media-file> [-ts] [-tas] [-rf] [-urf]
```

This command pushes image, video, or audio files from the device path `<path-to-local-media-file>` into the media library for storage. It supports saving images, videos, and audio files. Files retain their original names in the media library. `<path-to-local-media-file>` can also be a folder, in which case mediatool will place all files within the folder into the media library. Upon successful saving, the URI of the pushed resource is printed.

By default, media files are saved into the media library with synchronous thumbnail creation, and the files under `<path-to-local-media-file>` are deleted afterward.

| Option               | Description             |
| :---- | :--------------- |
| -ts | Synchronously creates thumbnails when saving images or videos. Ensures thumbnails are generated before the media is displayed, but may result in longer save times. (Default) |
| -tas | Asynchronously creates thumbnails when saving images or videos. Cannot be used with the -ts option. Media files are displayed immediately after saving without waiting for thumbnails to generate. Results in shorter save times. |
| -rf | Deletes the source file after pushing it into the media library. (Default) |
| -urf | Does not delete the source file after pushing it into the media library. Cannot be used with the -rf option. |

**Usage Example:**

```shell
> mediatool send /data/tmp/MyImage.jpg
file://media/Photo/3/IMG_1721381297_001/MyImage.jpg # Successfully pushed the image, prints the URI of the pushed resource
```

### mediatool list

```shell
mediatool list <resource-uri>
```

This command prints the information of the media library resource corresponding to the specified `<resource-uri>` in CSV format.

For example, if the URI of image resource A in the media library is `file://media/Photo/3/IMG_1721381297_001/MyImage.jpg`, both `mediatool list file://media/Photo/3` and `mediatool list file://media/Photo/3/IMG_1721381297_001/MyImage.jpg` will successfully print the resource information.

The printed information includes:

- uri: The URI of the media resource.
- display_name: The name of the media resource.
- data: The physical path of the media resource's source file on the device.

Alternatively, `<resource-uri>` can be specified as `all`. `mediatool list all` will print information for all resources in the media library.

**Usage Example:**

```shell
# Query using an existing URI
> mediatool list file://media/Photo/3
Table Name: Photos
uri, display_name, data
"file://media/Photo/3/IMG_1721381297_001/MyImage.jpg", "MyImage.jpg", "/storage/cloud/100/files/Photo/2/IMG_1721381297_001.jpg"

# Query using an invalid URI format
> mediatool list file://media/Photo/
[FAIL] uri invalid. uri:file://media/Photo/
```

<!--DelEnd-->

### mediatool recv

```shell
mediatool recv <resource-uri> <dest-path>
```

This command exports the source file content of the media library resource specified by `<resource-uri>` to the device path specified by `<dest-path>`.

`<dest-path>` can be specified as either a file path to be created or a folder path. If it is a folder path, the file will be exported to that folder, retaining its name from the media library.

When `<dest-path>` specifies a file path to be created, it must not point to an existing file.
<!--Del-->
`<dest-path>` must specify a path with accessible permissions.
<!--DelEnd-->

Upon successful export, the path of the exported file is printed.

For obtaining media library resource URIs, refer to [Media Library URI Introduction/Acquisition Methods](#media-library-uri-introductionacquisition-methods).

Specifying `<resource-uri>` as `all` will export the source files of all media library resources. When `<resource-uri>` is `all`, `<dest-path>` must be a folder path.

This command cannot export media assets from hidden albums.

<!--RP1--><!--RP1End-->

**Usage Example:**

```shell
> mediatool recv file://media/Photo/3 /data/local/tmp/out.jpg
Table Name: Photos
/data/local/tmp/out.jpg
```

### mediatool delete

```shell
mediatool delete <resource-uri>
```

This command permanently deletes the media library resource specified by `<resource-uri>`. Deleted resources cannot be recovered, so use this command with caution.

For obtaining media library resource URIs, refer to [Media Library URI Introduction/Acquisition Methods](#media-library-uri-introductionacquisition-methods).

Specifying `<resource-uri>` as `all` will delete all media library resources and reset all media library data.

**Usage Example:**

```shell
> mediatool delete file://media/Photo/3
[SUCCESS] delete success.

> mediatool delete all # No output is printed upon successful execution of "delete all"
```

### mediatool query

```shell
mediatool query <display-name> [-p] [-u]
```

This command queries all media library resources with the name `<display-name>` and returns either the physical path of the source file or the URI of the media resource. By default, it returns the physical path of the source file.

This command cannot query media assets from hidden albums.

| Option   | Description  |
| ---- |----- |
| -p | Returns the physical path of the media resource's source file on the device. (Default) |
| -u | Returns the URI of the media resource. Cannot be used with the -p option. |

**Usage Example:**

```shell
# Querying an existing media resource
> mediatool query MyImage.jpg
find 1 result:
path
/storage/cloud/100/files/Photo/2/IMG_1721381297_001.jpg

# Querying a non-existent media resource
> mediatool query non_exist.jpg
find 0 result

# Querying with an incorrect name format
> mediatool query IMG_001
find 0 result
The displayName format is not correct!

# Querying the physical path of a media resource
> mediatool query MyImage.jpg -p
find 1 result:
path
/storage/cloud/100/files/Photo/2/IMG_1721381297_001.jpg

# Querying the URI of a media resource
> mediatool query MyImage.jpg -u
find 1 result:
uri
"file://media/Photo/2/IMG_1721381297_001/MyImage.jpg"
```

## Usage Guidelines

The following guidelines illustrate common usage scenarios for mediatool.

### Exporting Specific Media Library Assets

Example: Exporting a JPG image named "MyImage" from the gallery.

```shell
> hdc shell mediatool query -u MyImage.jpg
find 1 result
uri
"file://media/Photo/1/IMG_1743078145_000/MyImage.jpg"

> hdc shell mediatool recv file://media/Photo/1 /data/local/tmp/out.jpg
Table Name: Photos
/data/local/tmp/out.jpg

> hdc file recv /data/local/tmp/out.jpg .
FileTransfer finish, Size:10015455, File count = 1, time:679ms rate:14750.30kB/s
```

### Exporting All Media Library Assets

```shell
> hdc shell mediatool recv all /data/local/tmp/media
Table Name: Photos
/data/local/tmp/media/MyImage.jpg

Table Name: Audios

> hdc shell tar -cvf /data/local/tmp/media.tar /data/local/tmp/media/*
removing leading '/' from member names
data/local/tmp/media/MyImage.jpg

> hdc file recv /data/local/tmp/media.tar .
FileTransfer finish, Size:10017280, File count = 1, time:664ms rate:15086.27kB/s
```

### Deleting Specific Media Library Assets

Example: Deleting a JPG image named "MyImage" from the gallery.

```shell
> hdc shell mediatool query -u MyImage.jpg
find 1 result
uri
"file://media/Photo/1/IMG_1743078145_000/MyImage.jpg"

> hdc shell mediatool delete file://media/Photo/1/IMG_1743078145_000/MyImage.jpg
[SUCCESS] delete success.
```

### Fully Resetting the Media Library Database

```shell
> hdc shell mediatool delete all
```

## Media Library URI Introduction/Acquisition Methods

The URI is the unique identifier for media library assets, with each URI corresponding to one media asset. mediatool uses URIs to determine the media asset objects to operate on.

URIs can be obtained in the following ways:

- Using `mediatool query` with the `-u` option returns the URI of the corresponding media asset. The display name of the asset (as shown in the gallery, including the file extension) must be provided.<!--Del-->
- `mediatool list all` retrieves a list of URIs for all media library assets, along with their display names.<!--DelEnd-->

Media library URIs can be used with the `mediatool recv` command to export specific media library assets or with the `mediatool delete` command to delete specific media library assets.

URI Example: `file://media/Photo/1/IMG_1743078145_000/MyImage.jpg`.
When using this URI in mediatool operations, both `file://media/Photo/1/IMG_1743078145_000/MyImage.jpg` and `file://media/Photo/1` will correctly locate the target asset.