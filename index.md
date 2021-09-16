---
layout: default
---

# Team Unununium

Originated as a Hackathon project from Hack and Roll 2020, this project aims to develop an affordable remote controlled robot. This could be used in situations where it is difficult or dangerous for humans to explore, or it can be simply used for fun.

## Components

There are 3 main physical components that make up the project. They are:
- Robot: The physical robot itself!
- Server: Used to relay information between the robot and client
- Client: The device that would be used to control the robot

## Requirements

The requirements to build the project is as follows:

Robot:
- A Raspberry Pi 3 or better with Wifi capabilities
  - A MicroSD card (8GB or higher) for the Raspberry Pi
  - A compatible [mobile power supply](https://www.amazon.com/MakerHawk-Raspberry-Uninterruptible-Management-Expansion/dp/B082CVWH3R) for the Raspberry Pi
  - Batteries for the mobile power supply
- A Raspberry Pi Camera (With or without night vision is fine, but night vision is not supported)
  - A business card holder to be used as the camera casing
  - Acrylic boards (You would also need saws, files etc to machine the boards)
  - Heat sinks for the Raspberry Pi (It would be mounted onto the camera instead)
  - 2 metal strips to secure the heat sinks (We used metal strips of ~6cm x 0.5cm, but the length can definitely be adjusted)
  - 4 screws and nuts (Diameter must be smaller than width of metal strips)
  - Saws, files, drills (Equipment to machine acrylic boards)
  - Acrylic glue (We used liquid quartz)
  - Sealant
- TBC for Arduino

Server:
- Any OS distribution with port 80 and / or 443 available
- Node.JS v12 LTS or higher

Client:
- Any Android device running Marshmallow / 6.0 or higher
- A compatible bluetooth controller to control the robot

## Software

The following section would explain the working principle of the software that was used. Feel free to skip to the assembly section if you are not interested.

### [Android Client](https://github.com/team-unununium/robot-client-android)

The Android Client is an app that is capable of communicating to the server via the latest version of the [Socket.IO protocol](https://python-socketio.readthedocs.io/en/latest/intro.html), which at the time of writing would be 4.x version on the Node.JS server. A client can either be an operator or an observer; an operator would allow the client to control the robot via a bluetooth game controller, wheras an observer would only be allowed to view the live feed coming from the robot and its sensory data. There can be multiple observers connected to a single server, but there can only ever be one operator at a time. If a client attempts to connect as an operator when another operator already exists, the connection would fail and the client would revert back to being an observer.

The controls for the robot are as follows:

| Button | Function |
|-|-|
| X | Toggle start / stop moving |
| Y | Invert UI colour |
| A | Toggle UI visibility |
| Left Control Stick | Rotates camera |
| Right Control Stick | Rotates robot |
| L1 | Takes a screenshot |
| R1 | Toggles diagnostics mode visibility |
| Menu | Opens / closes settings |
| D-Pad | Increase / Decrease speed of robot |

More information can be found at the client's [repository](https://github.com/team-unununium/robot-client-android).

### [Server](https://github.com/team-unununium/robot-server)

The server is a Node.JS server that relays information to the client and robot via Socket.IO protocol. The latest version at the time of writing (4.x) is used. To ensure that the communication comes from a compatible client and robot, secret keys are used to verify the identity of the client (operator / observer) and the robot. The client and robot would attempt to acquire an access key via HTTP / HTTPS, which would then be used to establish a connection with the Socket.IO server.

More information can be found at the server's [repository](https://github.com/team-unununium/robot-server).

### [Pi](https://github.com/team-unununium/robot-pi)

The Raspberry Pi would be running a Python program that uses python-socketio version 5.x and python-engineio version 4.x to communicate to the server due to [version compatibilities](https://python-socketio.readthedocs.io/en/latest/intro.html) between the two libraries. It would send live feed to the client via the server's Socket.IO connection, relays sensory information from the Arduino to the client, and relays instructions by the operator to the Arduino. The Arduino is expected to be connected to the Raspberry Pi via a USB cable, which would be used for communcation between the two.

More information can be found at its [repository](https://github.com/team-unununium/robot-pi).

### [Arduino](https://github.com/team-unununium/robot-arduino)

The Arduino receives commands from the Raspberry Pi, which then translates it into machine commands that control the servos for the robot. In addition, the Arduino is also fitted with various sensors such as temperature sensors, humidity sensors and ultrasound sensors, which their data would be relayed to the clients via the Pi and the server.

More information can be found at its [repository](https://github.com/team-unununium/robot-arduino), as well as in the [Hardware](#Hardware) section below.

### Protocols

A detailed explanation of the communication protocol used can be found in the below 2 pages:

- [Client-Server-Pi Protocol](./software/csp-protocol)
- [Pi-Arduino Protocol](./software/pa-protocol)

## Hardware

The following section would explain the working principle of the hardware. Feel free to skip to the assembly section if you are not interested.

TBC

## Assembly

TBC

## Issues

### Internet connection

The main limitation that the robot would face would be its internet connection, as it is needed to relay live feed and for control. In conditions where Wifi signals may be weak or intermittent, there may be issues with transmitting the live feed and commands via the internet.

### Environmental Damage

Although the camera casing is designed to be water resistant, it has not been tested under rainy conditions, so its actual effectiveness is not known.

TBC for robot

## Future Plans

We do not have any future plans for this project, so feel free to fork it or build on it to create your own version of the robot.

## License

All the repositories within this project are licensed under the [GPL v3 license](https://tldrlegal.com/license/gnu-general-public-license-v3-(gpl-3)).
