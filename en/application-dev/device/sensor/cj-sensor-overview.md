# Sensor Development Overview

## Sensor Types

System sensors are device abstractions that allow applications to access underlying hardware sensors. By utilizing the [Sensor interface](../../reference/SensorServiceKit/cj-apis-sensor.md) provided by sensors, developers can query available sensors on the device, subscribe to sensor data, and develop various applications with customized algorithms based on sensor data, such as compasses, fitness tracking, games, etc.

| Sensor Type                  | Description               | Explanation                                                 | Primary Applications                          |
| ---------------------------- | ------------------------- | ----------------------------------------------------------- | --------------------------------------------- |
| ACCELEROMETER                | Accelerometer            | Measures acceleration (including gravity) applied to the device along three physical axes (x, y, and z), unit: m/s². | Motion state detection.                       |
| ACCELEROMETER_UNCALIBRATED   | Uncalibrated Accelerometer | Measures uncalibrated acceleration (including gravity) applied to the device along three physical axes (x, y, and z), unit: m/s². | Acceleration bias estimation.                 |
| LINEAR_ACCELEROMETER         | Linear Accelerometer      | Measures linear acceleration (excluding gravity) applied to the device along three physical axes (x, y, and z), unit: m/s². | Detection of linear acceleration on each axis. |
| GRAVITY                      | Gravity Sensor            | Measures gravitational acceleration applied to the device along three physical axes (x, y, and z), unit: m/s². | Gravity magnitude measurement.                |
| GYROSCOPE                    | Gyroscope Sensor          | Measures angular velocity of device rotation along three physical axes (x, y, and z), unit: rad/s. | Measurement of rotational angular velocity.   |
| GYROSCOPE_UNCALIBRATED      | Uncalibrated Gyroscope    | Measures uncalibrated angular velocity of device rotation along three physical axes (x, y, and z), unit: rad/s. | Measurement of rotational angular velocity and bias estimation. |
| SIGNIFICANT_MOTION          | Significant Motion Sensor | Detects significant motion of the device along three physical axes (x, y, and z); value 1 indicates significant motion, 0 indicates no motion. | Detection of significant device motion.       |
| PEDOMETER_DETECTION         | Pedometer Detection Sensor | Detects user's walking steps; value 1 indicates walking motion, 0 indicates no motion. | Detection of walking steps.                   |
| PEDOMETER                   | Pedometer Sensor          | Counts user's walking steps.                                | Provides step count data.                     |
| AMBIENT_TEMPERATURE         | Ambient Temperature Sensor | Measures ambient temperature, unit: Celsius (°C).           | Ambient temperature measurement.              |
| MAGNETIC_FIELD              | Magnetic Field Sensor     | Measures ambient geomagnetic field along three physical axes (x, y, z), unit: μT. | Compass creation.                             |
| MAGNETIC_FIELD_UNCALIBRATED | Uncalibrated Magnetic Field Sensor | Measures uncalibrated ambient geomagnetic field along three physical axes (x, y, z), unit: μT. | Geomagnetic bias estimation.                  |
| HUMIDITY                    | Humidity Sensor           | Measures relative humidity of environment, expressed as percentage (%). | Monitoring dew point, absolute and relative humidity. |
| BAROMETER                   | Barometer Sensor          | Measures ambient air pressure, unit: hPa or mbar.           | Ambient pressure measurement.                 |
| ORIENTATION                 | Orientation Sensor        | Measures device rotation angles around all three physical axes (z, x, y), unit: rad. | Measurement of screen rotation angles.        |
| ROTATION_VECTOR             | Rotation Vector Sensor    | Measures device rotation vector, a composite sensor derived from accelerometer, magnetic field sensor, and gyroscope. | Detection of device orientation relative to ENU coordinate system. |
| PROXIMITY                   | Proximity Sensor          | Measures proximity or distance of visible objects relative to device display. | Phone call positioning relative to user.      |
| AMBIENT_LIGHT               | Ambient Light Sensor      | Measures ambient light intensity around device, unit: lux.   | Automatic screen brightness adjustment, detection of screen obstruction. |
| HEART_RATE                  | Heart Rate Sensor         | Measures user's heart rate.                                 | Provides heart rate health data.              |
| WEAR_DETECTION              | Wear Detection Sensor     | Detects whether user is wearing the device.                 | Detection of wearable device usage.          |
| HALL                        | Hall Sensor               | Detects presence of magnetic attraction around device.      | Device flip cover mode.                       |

## Operational Mechanism

The sensor system consists of four modules: Sensor API, Sensor Framework, Sensor Service, and HDF layer.

**Figure 1** Sensor Architecture

![sensor](figures/sensor.png)

- **Sensor API**: Provides fundamental sensor APIs including sensor list query, data subscription/cancellation, and control commands, simplifying application development.
- **Sensor Framework**: Implements sensor subscription management, data channel creation/destruction, subscription management, and communication with SensorService.
- **Sensor Service**: Handles HD_IDL layer data reception, parsing, distribution, foreground/background policy control, device sensor management, and permission control.
- **HDF Layer**: Implements strategy selection for different FIFOs and frequencies, along with device adaptation.

## Constraints and Limitations

1. For the sensors listed below, developers must request corresponding permissions to access sensor data.

   | Sensor  | Permission Name  | Sensitivity Level  | Description  |
   | ------- | ---------------- | ------------------ | ------------ |
   | Accelerometer, Uncalibrated Accelerometer, Linear Accelerometer | ohos.permission.ACCELEROMETER  | system_grant | Allows applications to read accelerometer data, including: accelerometer, uncalibrated accelerometer, and linear accelerometer. |
   | Gyroscope, Uncalibrated Gyroscope    | ohos.permission.GYROSCOPE   | system_grant | Allows applications to read gyroscope data, including: gyroscope and uncalibrated gyroscope. |
   | Pedometer        | ohos.permission.ACTIVITY_MOTION  | user_grant   | Allows applications to read user's current motion state, such as determining whether user is active or counting steps. |
   | Heart Rate Sensor         | ohos.permission.READ_HEALTH_DATA | user_grant   | Allows applications to read user health data, such as heart rate data.  |

2. Sensor data subscription and unsubscription interfaces must be called in pairs. Developers must call the unsubscription interface to stop data reporting when sensor data is no longer needed.