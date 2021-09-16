---
layout: default
---

# Pi-Arduino Protocol

The Pi-Arduino protocol utilises Pyserial and Arduino's serial communication to communicate with each other. All communication would be done via plaintext.
When the Pi wishes to send a command to the Arduino, the Pi would send a '%' sign, followed by a capital letter denoting the specific command. For specific commands, follow-up data would be sent right after the capital letter, and would be terminated at a newline. The command set could be found in the below table:

| Letter | Meaning | Follow-up |
|-|-|-|
| A | Start moving | - |
| B | Stop moving | - |
| C | Change speed | 1, 2 or 3 denoting the speed of the robot |
| D | Rotate camera | Angular rotation of the camera in radians |
| E | Rotate robot | Angular rotation of the robot in radians |

The robot would send a JSON string to the Pi in intervals. The JSON strings would contain the following values:

```Javascript
{
   "temp":"28.4", // A string of the temperature (encased by double quotes), round to 1 decimal place
   "humidity":"65.4", // A string of the humidity in percentage (encased by double quotes), round to 1 decimal place
   "frontObstacle":"123.4", // A string of the distance to the front obstacle (encased by double quotes) in mm, round to 1 decimal place, if there is no obstacle found use "-1.00"
   "backObstacle":"-1.00", // A string of the distance to the back obstacle (encased by double quotes) in mm, round to 1 decimal place, if there is no obstacle found use "-1.00"
   "co":"0.0012", // A string of the raw value of CO measured (encased by double quotes)
   "ch4":"0.0001", // A string of the raw value of CH4 measured (encased by double quotes)
   "h2":"0.0000", // A string of the raw value of H2 measured (encased by double quotes)
   "lpg":"0.1750" // A string of the raw value of LPG measured (encased by double quotes)
}
```

An example of the protocol could be found in the Pi's [repository](https://github.com/team-unununium/robot-pi/blob/main/protocol/pi-arduino-protocol-example.txt).
