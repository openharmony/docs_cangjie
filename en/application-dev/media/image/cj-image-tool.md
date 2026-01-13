# Editing Image EXIF Information

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

The image tool currently primarily provides the capability to read and edit image EXIF information.

EXIF (Exchangeable Image File Format) is a file format specifically designed for digital camera photos, which can record attribute information and shooting data of digital photos. Currently, only JPEG format images are supported.

In applications such as photo galleries, there is a need to view or modify the EXIF information of digital photos. Since parameters from manual lenses on cameras cannot be automatically written into EXIF information or due to issues like camera power loss, the shooting time may often be incorrect. In such cases, it becomes necessary to manually correct the erroneous EXIF data, and this functionality can be utilized for that purpose.

OpenHarmony currently supports viewing and modifying only certain EXIF information. For the specific scope of support, please refer to: [Exif Information](../../reference/ImageKit/cj-apis-image.md#enum-propertykey).

## Development Steps

For detailed information on the APIs related to reading and editing EXIF information, please refer to the [API Reference](../../reference/ImageKit/cj-apis-image.md#func-getimagepropertypropertykey-imagepropertyoptions).

1. Obtain the image and create an ImageSource.

   <!-- compile -->

   ```cangjie
   // Import the relevant module package.
   import kit.ImageKit.*

   // Obtain the sandbox path to create an ImageSource.
   let fd : Int32 = 0 // Obtain the file descriptor (fd) of the image to be processed.
   let imageSourceApi = createImageSource(fd)
   ```

2. Read and edit EXIF information.

    <!-- compile -->

    ```cangjie
    // Read EXIF information, BitsPerSample represents the number of bits per pixel.
    let options : ImagePropertyOptions = ImagePropertyOptions(index: 0, defaultValue: '9999')
    let data = imageSourceApi.getImageProperty(PropertyKey.BitsPerSample, options: options)

    // Edit EXIF information.
    imageSourceApi.modifyImageProperty(PropertyKey.ImageWidth, "120")
    ```