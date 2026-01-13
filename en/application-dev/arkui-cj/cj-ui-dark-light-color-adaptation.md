# Dark and Light Mode Adaptation for Applications  

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Overview  

The current system supports both dark and light display modes. To provide users with a better experience, applications should adapt to these dark and light modes.  

## Application Follows System Dark/Light Mode  

1. **Color Adaptation**  

    - **Custom Resource Implementation**  

      Add a dark mode qualifier directory (named `dark`) under the `resources` directory and create a `color.json` file to configure color resources for dark mode. For details, refer to [Resource Classification and Access](../cj-start/start/ide-resource-categories-and-access.md).  

      Example of the `resources` directory structure:  

      ![colorJsonDir](./figures/colorJsonDir.png)  

      For instance, developers can define the same color name in both `color.json` files but assign different color values.  

      `base/element/color.json` file:  

      ```json
      {
        "color": [
          {
            "name": "app_title_color",
            "value": "#000000"
          }
        ]
      }
      ```  

      `dark/element/color.json` file:  

      ```json
      {
        "color": [
          {
            "name": "app_title_color",
            "value": "#FFFFFF"
          }
        ]
      }
      ```  

    - **Implementation via System Resources**  

      Developers can directly use [system preset resources](../cj-start/start/ide-resource-categories-and-access.md#system-resources), i.e., layered parameters. The same resource ID may have different values under different configurations such as device type or dark/light mode. By using system resources, different developers can create applications with a consistent visual style without customizing two sets of color resources. The system will automatically switch between different color values in dark/light mode.  

      For example, developers can use the system-defined primary text color to define the text color in the application:  

      ```cangjie
      Text('Using System-Defined Colors')
        .fontColor(@r(sys.color.ohos_id_color_text_primary))
      ```  

2. **Image Resource Adaptation**  

    Use the resource qualifier directory approach. Similar to color adaptation, place the corresponding image for dark mode in the `dark/media` directory. Then, load the image resource key via `$r`. When the system switches between dark/light modes, it will automatically load the corresponding value from the resource file.  

    For simple SVG icons, the [fillColor](./cj-graphics-display.md#display-vector-graphics) property can be used with system resources to change the drawing color of the image. This eliminates the need for two sets of image resources while achieving dark/light mode adaptation.  

    ```cangjie
    Image(@r(app.media.pic_svg))
      .width(50)
      .fillColor(@r(sys.color.ohos_id_color_text_primary))
    ```  

3. **Web Component Adaptation**  

    The Web component supports dark mode configuration for frontend pages. Refer to [Web Component Dark Mode](../web/cj-web-set-dark-mode.md) for related configurations.