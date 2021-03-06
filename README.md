Xone-OSX
========

### Current Release: Beta 0.1 (Oct. 1, 2014)

### This is an unsigned, beta release. Use at your own discretion.

~~**NOTE: If you want to use the driver without access to the source code, download the latest version [here](https://mega.co.nz/#!DgpAhZxT!4jLE6xXmeQQekeRwvItyUUW4Ku3E6F5jRAT_kmkaPMI).**~~
**The installer is currently broken. The only way to use it currently is to follow these steps:**
 - Download the project.
 - Build the "Xbox One Controller Driver" project.
 - Copy the product into the "/tmp" folder
 - Type these commands into the terminal:
  - cd /tmp
  - sudo kextutil "Xone Driver.kext"
 - And then plug your controller in
 - You will have to run kextutil every time you want to use the controller. And if you reboot, you will have to follow all of the steps from copying the product again.

This is a kext and preference pane that allows users to use the Xbox One controller with their OS X computer. Because the Xbox One controller does not identify as a Human Interface Device, and requires custom startup code, a custom driver had to be made.

## Features
 - Performs custom startup and handles all buttons on the controller
 - Customizable deadzones for both sticks and triggers
 - Invert X and Y for each stick individually
 - Preference pane allows you to see your controller in action

## Support List:
 - DDHidLib (IE OpenEmu)
 - Steamworks Controller API (Steam Big Picture, and other Steam games that implement the API)

## Future Features
 - Force Feedback (Rumble)
 - Recognize controller as GCController
 - Change controller input to keyboard input (setting) so as to support unsupported games
 - Compatibility with games not using Steamworks API
 - Wireless implementation is probably unlikely, since Microsoft uses a proprietary wireless implementation for the controller

## Discussion
 - I've done my best to match the controls of the Xbox One controller to the Xbox 360 controller.
 - There doesn't appear to be any documentation as to how to implement a KEXT so that the controller is recognized as a GCController, so currently it is not.
 - I couldn't quite grasp how to convert the D-pad Data (4 consecutive bits with 0 for unpressed and 1 for currently pressed) into a proper HID implementation. So the D-Pad is currently bound to buttons 13 - 16.
 - I needed a game that supported rumble to implement rumble, and Bastion appears to not like my implementation of the controller. (Ex. The left trigger appears to take the place of every face button, and also appears to act as the left stick in game)
 - The guide button is handled in a separate packet, but I managed to have it recognized as button 11.
 - The sync button is also visible to the user and is encoded as button 12.


## Button Layout
| HID Button Number | Controller Button Name |
|:-----------------:|:----------------------:|
| 1                 | A                      |
| 2                 | B                      |
| 3                 | X                      |
| 4                 | Y                      |
| 5                 | Left Bumper            |
| 6                 | Right Bumper           |
| 7                 | View (Back)            |
| 8                 | Menu (Start)           |
| 9                 | Left Stick Click       |
| 10                | Right Stick Click      |
| 11                | Guide (Xbox)           |
| 12                | Sync                   |
| 13                | D-pad Up               |
| 14                | D-pad Down             |
| 15                | D-pad Left             |
| 16                | D-pad Right            |

| Axis ID           | Axis on Controller     |
|:-----------------:|:----------------------:|
| X                 | Left Stick X           |
| Y                 | Left Stick Y           |
| Z                 | Right Stick X          |
| Rx                | Right Stick Y          |
| Ry                | Left Trigger           |
| Rz                | Right Trigger          |


