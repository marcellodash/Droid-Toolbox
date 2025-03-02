# Droid Toolbox
This is an [Arduino IDE](https://www.arduino.cc/en/software) sketch for ESP32-based devices to interact with [Galaxy's Edge droids](https://disneyworld.disney.go.com/shops/hollywood-studios/droid-depot/). It can emit a bluetooth beacon that droids will react to, scan for nearby droids, and connect to droids and command them to play specific audio tracks from their personality chip. A YouTube video of the Droid Toolbox in action is available at https://www.youtube.com/watch?v=0sHTIEbTevk.

This code was specifically designed for [LILYGO TTGO T-Display](http://www.lilygo.cn/prod_view.aspx?Id=1126) and [LILYGO T-Display-S3](http://www.lilygo.cn/prod_view.aspx?Id=1413) devices and may not display correctly on other ESP32 devices without modification.

*Use at your own risk.*

## Features
* Select between emitting a beacon or scanning for nearby droids.
* When the beacon is activated, a random location beacon is generated.
* Connect to droid and make is play a specific track from a specific audio group.
* Change the volume level of the droid.
* Auto shut-off.

## Setup and Installation
### Video Tutorials
* This YouTube video (https://www.youtube.com/watch?v=wEwg2-N3HqM) provides instructions on the process of setting up the Arduino environment, installing the Arduino ESP32 core and libraries, downloading the Droid Toolbox code, and programming a T-Display and T-Display-S3 with the Droid Toolbox software. 
* This follow-up video (https://www.youtube.com/watch?v=kiu0b0Uf0Nw) provides instructions on this process from a MacOS perspective.

### Resources
* [LilyGo TTGO T-Display GitHub Repository](https://github.com/Xinyuan-LilyGO/TTGO-T-Display) - Contains links to drivers, setup instructions, and sample code
* [LilyGo T-Display-S3 GitHub Repository](https://github.com/Xinyuan-LilyGO/T-Display-S3/)
* [Arduino IDE Software](https://www.arduino.cc/en/software)
* [ESP32 Core for Arduino](https://github.com/espressif/arduino-esp32)
* [TFT_eSPI Library](https://github.com/Bodmer/TFT_eSPI)

## Button Labeling / TTGO Orientation
![Image of a TTGO with the Droid Toolbox boot screen.](images/v0.51_01_start.jpg)
* Droid toolbox is designed to be operated with the TTGO held horizontally with the USB port on facing the left.
* The button at top-left (above the USB port) is Button 1.
* The button at the bottom-left (below the USB port) is Button 2.

## Operation
![Image of a TTGO with the menu screen showing SCANNER band BEACON options.](images/v0.54_02_top_menu.jpg)
* Upon startup, press either button 1 or 2 to enter the main menu.
* Press button 2 to change options in the main menu.
* Press button 1 to select the highlighted option from the main menu.

### Button Press Types
* A button press is not registered until the button is released.
* Droid toolbox detects short and long button presses.
* A short press is any press in which the button is held down for less than 500ms.
* A long press is any press that lasts for 500ms or longer.
* If a button press type is not explicitly stated in the instructions below, either press type applies.

### Beacon
![Image of a TTGO showing "BEACON ON" on the display.](images/v0.1_05_beacon.jpg)
* Press button 1 to toggle the beacon on and off.
* The beacon is a location beacon. The location is chosen at random every time it is activated.
* Press button 2 to exit the beacon mode. If a beacon is active when button 2 is pressed it will be deactivated.

### Scanning
![Image of a TTGO with the text 'SCANNING' across the screen.](images/v0.1_03_scanning.jpg)
![Image of a TTGO showing a list of nearby droids including their bluetooth address, their affiliation, and personality chip.](images/v0.51_04_scan_results.jpg)
* Upon selecting the scanner option a scan is initiated. After a few seconds the results of the scan are displayed
* If no droids are detected, a message will be displayed.
* If more than one droid is detected, a button 1 short press will step to the next droid in the results.
* A button 1 long press will cause the droid toolbox to attempt to connect to the droid.
* A button 2 press will return to the main menu.

### Connected
![Image of a TTGO showing SOUNDS and VOLUME menu options with the SOUNDS option highlighted.](images/v0.54_07_connected_menu.jpg)
* If the connection attempt fails, be sure your droid's remote is turned off and that the droid is still on.
* Once connected to a droid a menu is displayed letting you select between playing SOUNDS from the droid's personality chip and managing the droid's VOLUME.
* A button 1 press will select the highlighted menu item.
* A button 2 short press will step through the menu items.
* A button 2 long press will disconnect from the droid and return to the droid scan results.

### Playing Sounds
![Image of a TTGO showing TRACK and GROUP selections and a PLAY button.](images/v0.51_06_track_play.jpg)
* The SOUNDS option allows you to play a selected track from a selected group within a droid's personality chip. Droids that don't have a personality chip installed still have an internal personality chip from which tracks are played.
* A button 1 short press will increment GROUP or TRACK depending on which is highlighted. If PLAY is highlighted, it will command the droid to play the selected track from the selected group.
* A button 1 long press will either move to the next option (TRACK or PLAY) or play the track when PLAY is highlighted. *This behavior will be changed in a future update.*
* A button 2 short press will step through the options to select a group number, a track number, and play.
* A button 2 long press will exit from SOUNDS screen and return to the previous menu.

### Volume Control
![Image of a TTGO showing TRACK and GROUP selections and a PLAY button.](images/v0.54_08_volume.jpg)
* The VOLUME option allows you to set the volume level of the sounds played through the droid. 
* Volume can be set between 0 and 100 in increments of 10. 
* There is no way to read the current volume level of a droid. Upon first connection to a droid, Droid Toolbox will assume a volume level of 100, but it may not represent the actual volume level of the droid until you set the volume level.
* A button 1 press will execute the highlighted action: volume increase (VOL+), volume decrease (VOL-), and SET VOLUME. The SET VOLUME option must be used to set the droid's volume to the currently selected value. If you do not SET VOLUME the droid's volume will not be changed.
* A button 2 short press will step through the options VOL+, VOL-, and SET VOLUME. The currently selected option will appear in green text.
* A button 2 long press will exit from VOLUME screen and return to the previous menu.

### Auto Shut-Off
Droid-toolbox will go to sleep after 5 minutes of inactivity. It will not sleep if a beacon is active. To restart the droid toolbox press the reset button.

### T-Display-S3 Supported
![Image of a LilyGo T-Display-S3, inside a LilyGo T-Display-S3 case, running Droid Toolbox=](images/v0.54_99_S3_display.jpg)
The LilyGo T-Display-S3 is like the LilyGo TTGO T-Display, but with a larger screen and more program space. The Droid Toolbox code will work with either a T-Display or T-Display-S3 without the need to modify any of the code. 

## About Audio Tracks
Galaxy's Edge droids have [personality chips](https://plandisney.disney.go.com/question/dose-droid-personality-406556/). Droids come with a built-in personality chip, but can be modified by plugging in an extra personality chip which overrides the internal personality chip. The personality chip is a collection of audio clips which play when a droid reacts to location beacons, nearby droids, or button presses on the droid's remote control. The audio clips are divided into 12 separate groups. The first 7 groups represent 7 areas within Galaxy's Edge and are what plays when a droid reacts to a beacon. Group 8 through 12 contain special audio clips used with droid accessories (for R-units) and special circumstances, such as when a droid is first activated inside Droid Depot. 

Droid Toolbox allows you to select between the 12 groups and select an audio track within that group. The number of audio clips for a given group can vary between personality chips. While we know how many clips there are for stock personality chips, custom personality chips could have as many audio clips as you want. As such you'll be able to select up to audio track 99, even though the number of tracks typically goesn't go beyond 6. If you try to play an audio track number that doesn't exist the droid will simply do nothing.

### Audio Groups and Their Uses
|Group|Purpose|
|---|---|
|1|Location: Market Area|
|2|Location: [Droid Depot](https://disneyworld.disney.go.com/shops/hollywood-studios/droid-depot/)|
|3|Location: Resistance Area|
|4|Location: Unkown \*|
|5|Location: [Oga's Cantina](https://disneyworld.disney.go.com/dining/hollywood-studios/ogas-cantina/) \*\*|
|6|Location: [Dok-Ondar's Den of Antiquities](https://disneyworld.disney.go.com/shops/hollywood-studios/dok-ondars-den-of-antiquities/)|
|7|Location: First Order Area|
|8|Droid Activation|
|9|Unused R-unit Accessory|
|10|Unused and Empty|
|11|Blaster R-Unit Accessory|
|12|Thruster R-Unit Accessory|

*\* No location beacon for this value has been seen inside Galaxy's Edge*

*\*\* Only seen at the entrance to Oga's; possibly the droid detectors?*

## References
* [Controlling Disney’s Droids from Droid Depot with WebBluetooth](https://medium.com/@baptistelaget/controlling-disneys-droids-from-droid-depots-with-webbluetooth-febbabe50587)
* [bashNinja's BLE scan from Galaxy's Edge](https://discord.com/channels/478345594641973248/596058282087546968/626179189115977748) shared with the #makerspace channel of the [Galaxy's Edge Discord Server](http://swgediscord.com)
* [Dead Bothans Society Beacon Map](https://docs.google.com/spreadsheets/d/1zIZb7uUxUe7ewypnTGrzrX1FA85U5mn2XtULZbcXqI8/edit#gid=0)
* [VProFX's Interactive Map of Beacon Locations](http://galaxysedgetech.epizy.com/?i=1)
* [Galaxy's Edge Research - Bluetooth Beacons](https://docs.google.com/spreadsheets/d/13P_GE6tNYpGvoVUTEQvA3SQzMqpZ-SoiWaTNoJoTV9Q/edit#gid=372067469)
