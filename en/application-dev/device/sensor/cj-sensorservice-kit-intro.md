# Introduction to Sensor Service Kit Development

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Usage Scenarios

Sensor Service Kit enables applications to obtain raw data from sensors and provides vibration control capabilities.

- The **Sensor** module is a device abstraction concept that allows applications to access underlying hardware sensors. Developers can subscribe to sensor data through the provided interfaces and develop various applications with customized algorithms based on the sensor data, such as compasses, fitness tracking, gaming, etc.
- The **Vibrator** module maximizes the capabilities of motor devices by extending vibration services to achieve integrated vibration and interaction designs. It creates refined and sophisticated vibration experiences with differentiated effects, improving user interaction efficiency, usability, and overall experience while enhancing brand competitiveness.

## Constraints and Limitations

### Sensor

- To use sensor functionalities, the device must be equipped with the corresponding sensor hardware.
- For certain sensors, developers need to request appropriate permissions to access the corresponding sensor data.
- Sensor data subscription and unsubscription interfaces must be called in pairs. When sensor data is no longer needed, developers must call the unsubscription interface to stop data reporting.

### Vibrator

- To use vibration functionalities, the device must be equipped with the corresponding hardware.
- For motor control, developers need to request appropriate permissions to utilize the feature.