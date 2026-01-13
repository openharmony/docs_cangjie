# Using ImagePacker for Image Encoding

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

Image encoding refers to the process of converting a PixelMap into archived images of different formats. Currently supported formats include JPEG, WebP, PNG, and HEIF (availability may vary across different hardware devices), which can be used for subsequent processing such as storage or transmission.

## Development Procedure

For detailed information about image encoding APIs, please refer to: [Image Encoding Interface Documentation](../../reference/ImageKit/cj-apis-image.md#class-imagepacker).

### Encoding Images into File Streams

1. Create an ImagePacker object for image encoding.

    <!-- compile -->

    ```cangjie
    // Import relevant module packages.
    import kit.ImageKit.*

    let imagePackerApi = createImagePacker()
    ```

2. Set the encoding output stream and encoding parameters.

    - format specifies the image encoding format; quality indicates image quality, ranging from 0-100 with 100 being the best quality.

        > **Note:**
        >
        > According to MIME standards, the standard encoding format is image/jpeg. When using image encoding, set PackingOption.format to image/jpeg. The file extension for encoded images can be .jpg or .jpeg, and can be used on platforms that support image/jpeg decoding.

        <!-- compile -->

        ```cangjie
        var packOpts = PackingOption('image/jpeg', 98)
        ```

    - Encode as HDR content (requires the source to be HDR, supports JPEG format).

        <!-- compile -->

        ```cangjie
        packOpts.desiredDynamicRange = PackingDynamicRange.Auto
        ```

3. [Create a PixelMap object or create an ImageSource object](./cj-image-decoding.md).

4. Perform image encoding and save the encoded image.

    Method 1: Encoding via PixelMap.

    <!-- compile -->

    ```cangjie
    // data is the file stream obtained from packing, which can be written to a file to save as an image.
    let imagePacker = createImagePacker()
    let data = imagePacker.packToData(pixelMap, packOpts)
    ```

    Method 2: Encoding via ImageSource.

    <!-- compile -->

    ```cangjie
    // data is the file stream obtained from packing, which can be written to a file to save as an image.
    let imagePacker = createImagePacker()
    let data = imagePacker.packToData(imageSource, packOpts)
    ```

### Encoding Images into Files

During encoding, developers can specify a file path, and the encoded memory data will be directly written to the file.

Method 1: Encoding PixelMap into a file.

<!-- compile -->

```cangjie
import kit.CoreFileKit.*

var abilityContext = Global.abilityContext
// Get the resourceManager.
let resourceManager = abilityContext.resourceManager   
        
let img = resourceManager.getMediaContent(@r(app.media.layered_image))
let imageSource = createImageSource(img)
let cacheDir = "/data/storage/el2/base/haps/entry/cache"
let filePath = cacheDir + '/test.jpg'

let file = FileIo.open(filePath, mode: OpenMode.CREATE | OpenMode.READ_WRITE)
// Directly pack into the file.
let imagePacker = createImagePacker()
imagePacker.packToFile(imageSource, Int32(file.fd), PackingOption("image/jpeg", 100))
FileIo.close(file.fd)
```

Method 2: Encoding ImageSource into a file.

<!-- compile -->

```cangjie
import kit.CoreFileKit.*

var abilityContext = Global.abilityContext
// Get the resourceManager.
let resourceManager = abilityContext.resourceManager   
        
let img = resourceManager.getMediaContent(@r(app.media.layered_image))
let imageSource = createImageSource(img)
let cacheDir = "/data/storage/el2/base/haps/entry/cache"
let filePath = cacheDir + '/test.jpg'

let file = FileIo.open(path, mode: OpenMode.CREATE | OpenMode.READ_WRITE)
// Directly pack into the file.
let imagePacker = createImagePacker()
imagePacker.packToFile(imageSource, Int32(file.fd), PackingOption("image/jpeg", 100))
FileIo.close(file.fd)
```