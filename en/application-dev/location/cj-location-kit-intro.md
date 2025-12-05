# Introduction to Location Kit

## Scenario Overview  

Mobile terminal devices have become deeply integrated into various aspects of people's daily lives, such as checking local weather, reading news and anecdotes, hailing rides, travel navigation, and exercise tracking. These commonplace activities all rely on locating the user's terminal device.  

When users engage in these diverse scenarios, the system's location capabilities can provide real-time and accurate position data. For developers, designing services with location-based experiences can make applications more tailored to each user's needs.  

When implementing device location-based features—such as driving navigation or recording exercise trajectories—applications can call the module's APIs to obtain location information.  

## Basic Concepts  

The location subsystem employs multiple positioning technologies to deliver services, including GNSS positioning, base station positioning, and WLAN/Bluetooth positioning (the latter two are collectively referred to as "network positioning technologies"). These technologies enable accurate device location determination, whether indoors or outdoors.  

- **Coordinates**  
  The system uses the World Geodetic System 1984 (WGS84) as a reference, describing a location on Earth with longitude and latitude data.  

- **GNSS Positioning**  
  Based on global navigation satellite systems, including GPS, GLONASS, BeiDou, and Galileo, this method determines a device's precise location through algorithms provided by navigation satellites and the device's chip. The specific positioning systems used depend on the hardware capabilities of the user's device.  

- **Base Station Positioning**  
  Estimates the device's current location based on the positions of its connected and neighboring base stations. This method offers relatively lower accuracy and requires the device to have access to a cellular network.  

- **WLAN and Bluetooth Positioning**  
  Estimates the device's current location by detecting surrounding WLAN and Bluetooth devices. The accuracy of this method depends on the distribution of fixed WLAN/Bluetooth devices nearby. Higher density yields better accuracy compared to base station positioning, but it also requires network access.  

## Constraints and Limitations  

As a fundamental service provided by the system, location capabilities require applications to actively initiate requests in their respective business scenarios and terminate these requests when the scenarios conclude. During this process, the system reports real-time positioning results to the application.  

Using the device's location capabilities requires user confirmation and manual activation of the location switch. If the location switch is disabled, the system will not provide positioning services to any application.  

Device location information is sensitive user data. Even if the location switch is enabled, applications must request location access permission from users before obtaining such data. The system only provides positioning services after user approval.  

Location Kit offers varying capabilities across different devices, with some functionalities dependent on hardware support. For example, devices equipped with GPS or BeiDou positioning chips can utilize GNSS positioning, while devices without such chips but with WLAN or cellular connectivity can access WLAN or base station positioning capabilities.