# Shield Protection Mode

Shield Protection Mode is a system-level security mode designed for users with high-security requirements. This mode enhances security by restricting basic device functionalities, effectively defending against targeted attacks from remote attack surfaces.

## HTML5 Features Restricted by ArkWeb

When Shield Protection Mode is enabled, ArkWeb reduces the attack surface by restricting the following HTML5 features:

- Disables WebAssembly capability.
- Disables WebGL and WebGL2 capabilities.
- Disables PDF Viewer preview functionality.
- Disables MathML capability.
- Disables Web Speech API speech recognition capability.
- Disables the RTCDataChannel interface.
- Disables the MediaDevices.getUserMedia interface from prompting users to allow access to media input devices.
- Disables Service Worker capability.
- Disables non-proxied UDP traffic to prevent WebRTC from leaking the real source IP.
- Disables Just-In-Time (JIT) compilation capability.

## Evaluating Impact on Applications

To assess the impact and compatibility of an application under Shield Protection Mode, navigate to "Settings > Privacy & Security > Shield Protection Mode" to enable this mode.

<!--RP1--><!--RP1End-->

> **Note:**
>
> To evaluate the compatibility of a debug version (not yet published on the app market), you must first enable Developer Options before activating Shield Protection Mode.

After running the relevant features of the application, you can determine if they are affected in the following ways:

- Check if the frontend code contains WebAssembly-related interface calls. WebAssembly provides the ability to run compiled targets of low-level languages like C/C++ on the web, commonly used in high-performance scenarios such as gaming and codecs. Under Shield Protection Mode, WebAssembly cannot be invoked.
- Check if the frontend code contains WebGL-related interface calls. WebGL provides 3D graphics rendering capabilities, which cannot be invoked under Shield Protection Mode.
- Check for scenarios requiring online PDF display. PDFs cannot be displayed online when Shield Protection Mode is enabled, such as loading PDF links via the `loadUrl` interface.
- Check if HTML pages contain MathML syntax embedded in `<math>` tags. Under Shield Protection Mode, MathML syntax cannot be parsed correctly, leading to display anomalies.
- Check if the frontend code contains interface calls like `SpeechRecognition` (speech recognition) or `SpeechSynthesis` (speech synthesis). These interfaces cannot be invoked under Shield Protection Mode.
- Check if the frontend code contains interface calls like `RTCDataChannel` or `createDataChannel`. These interfaces are features of the WebRTC API, enabling bidirectional data channel connections for real-time data exchange between peers. Under Shield Protection Mode, these interfaces cannot be invoked.
- Check if the frontend code contains `MediaDevices.getUserMedia` interface calls. This interface requests user permission to access streaming media devices (e.g., cameras, microphones). Under Shield Protection Mode, calling this interface will throw the exception message: "can't use getUserMedia on advancedSecurityMode!"
- Check if the frontend code contains Service Worker-related interface calls. This mechanism is used for offline caching, network request interception, and push notifications, but Service Workers cannot be created successfully under Shield Protection Mode.
- Under Shield Protection Mode, WebRTC prohibits non-proxied UDP transmission, which affects network connectivity. Applications must verify and evaluate network functionality and performance in WebRTC scenarios.
- JIT involves performance optimization. Applications must evaluate JavaScript performance under Shield Protection Mode.