# BL Better Light Ctrl
## (INSTRUCTION ARE NOT YET COMPLETE,  WORK IN PROGRESS, STATE: 2023-12-09)
<p align="center">
<img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/9bfa1fce-3ea2-40f1-b9a7-e0c6704c8666" width="40%" height="40%"> 
<img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/000cd657-9c07-48bb-b9d5-f1f4415afc8f" width="40%" height="40%"> 
</p>
<p align="center">
<img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/467b2e95-0ed1-4c9a-a575-414aa159ab06" width="40%" height="40%"> 
</p>

***
### Tabele of content:
[1. Functionality and intended use](#1-functionality-and-intended-use)

[2. Requirements](#2-requirements)

[3. Preliminaries](#3-preliminaries)

[4. Connect to power supply and LED-Strip](#4-connect-to-power-supply-and-led-strip)

[5. Connect to WiFi](#5-connect-to-wifi)

[6. set 3D printer data](#6-set-3d-printer-data)

[7. start-up](#7-start-up)

[8. Operating states](#8-operating-states)

[9. Firmware update OTA](#9-firmware-update-ota)

***
### 1. Functionality and intended use:

Unfortunately, the factory lighting of the X1, X1C, P1P and P1S is not sufficient to illuminate the printer space properly. The "BL Better Light" LED controller provides significantly improved illumination, as well as visual signaling when the status of the printer changes (e.g. in the event of errors or when printing has been successfully completed). 

The "BL Better Light" LED controller is supplied with 5V, can drive LED strips of type WS2812b accordingly and based on a ESP32 microcontroller. To do this, the 3D printer and the LED controller are connected to the same WiFi so that the LED controller can communicate with the 3D printer. The controller detects status changes and set the LED lighting accordingly: 
  * white = normal working light
  * red = printer error
  * green = print successfully completed

When the printer is switched off, the LED lighting also switches off and therefore the LED controller does not need to be disconnected from the power supply separately. The LED lighting also switches on when the printer is switched on. In addition, the LED lighting can be switched on or off via the printer display. 
  <p align="center">
  <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/82933dbc-6a0b-4277-8730-78f9487e93cc" width="30%" height="30%"> 
  <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/6529b5d5-3a9d-4e01-9d8c-58f37a589566" width="30%" height="30%"> 
  <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/f643f6f0-2e3c-4713-9d7b-529004764e8d" width="30%" height="30%"> 
  </p>
  <p align="center">
  <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/b8c348f6-77eb-48dc-9592-2ccd2ea1fa62" width="30%" height="30%"> 
  </p>

***
### 2. Requirements:

  * WS2812b LED's (normal strips or neon led strip):
      * e.g.: https://amzn.eu/d/6pVJu65
      * e.g.: https://amzn.eu/d/0JR6dhz
      * it doesn't matter which kind of strips you use, as long as they are WS2812b (5 volts)
      * length: 1.40 m, if you use WS2812b with 60 LED's/m you need 84 pixel of your strip but also strips with more or less LED's/m are possible
      * every USB 5V power supply with at least 2 A (2000 mA) are okay
      * USB-C cable between power supply and LED controller
  * Network:
      * your 3D printer has to be connected with a WiFi network
      * the "BL Better Light" Controller has to be connected to the same WiFi network as your 3D printer
      * without WiFi it is not possible to use the LED controller
  * Configuration devices:
      * PC, laptop, tablet, smartphone etc
      * to configure the LED controller you need an actual browser on your device
      * your device has to be connected to the same WiFi network as your 3D printer and your "BL Better Light" LED controller
      * in very rare cases micro USB cable to re-programming the microcontroller
   * Firmware:
      * at least version 1.04 for X1C
***
### 3. Preliminaries:
   * WiFi access credentials from the WiFi to which your 3D printer is connected
   * You need several infos of your 3D printer:
      * IP address of your 3D printer (refer to the screenshots below)
      * access code of your 3D printer (refer to the screenshots below)
      * serial no of your 3D printer (refer to the screenshots below)
      You will find IP address and access code of your 3D printer as followed:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/01f745b6-b94b-4b68-9bfd-8c041db4d3d1" width="40%" height="40%"> 
       </p>
       * press SETTINGS button as marked as point 1
       * press NETWORK button as marked as point 2
       * under point 3 you will find the WiFi network to which your printer is connected. You will need to use the same WiFi later to connect your LED controller. 
       * note down the access code as marked as point 4
       * note down the IP address of your 3D printer as marked as point 5
      You will find the serial no of your 3D printer as followed:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/d6c11df7-82d1-4ce1-abbc-8427a67540bf" width="40%" height="40%"> 
       </p>
       * press SETTINGS button as marked as point 1
       * press GENERAL button as marked as point 2
       * note down the serial number as marked as point 3
***
### 4. Connect to power supply and LED strip:
   * connect your WS2812B LED strip to the LED Controller:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/860bbfa9-f963-47f2-86aa-7aba6310ec0d" width="40%" height="40%"> 
       </p>
       * Observe the labeling on the housing or circuit board and connect the LED strip accordingly. Please be careful and do not mix up the connections. This could damage the circuit board and/or the LED strip. Refer to the datasheet of your LED strip to find the correct cable assignment. 
   * connect a USB power supply to the "BL better light" LED Controller with an USB-C cable:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/0af45f8e-ff0c-4aeb-bfd0-d268da5a00af" width="40%" height="40%"> 
       </p>
       * You can use every commercially available power supply unit with at least 2A of current. If you use a power supply unit with less than 2A, color deviations may occur on the LED strip or not all LEDs will light up.
***
### 5. Connect to WiFi:
   * connect your "BL Better Light" LED controller with your power supply with an USB-C cable
   * the red led should light up
   * the "BL Better Light" LED controller will establish an own WiFi access point
   * search and connect to the WiFi access point "BL Better Light Ctrl SETUP", no password needed
   * after the connection is successful, navigate to the website http://192.168.4.1 with an actual browser of your choice
   * the following website should now open:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/c101a7ed-04a5-4839-b0e7-54f150d3ccf0" width="40%" height="40%"> 
       </p>
   * click on CONFIGURE WIFI, the following page should now open:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/e03c6f6c-ab89-4fd9-9d8b-40f99dc4dc8e" width="40%" height="40%"> 
       </p>
   * click on the WiFi network you want to connect to or type in the SSID manually, it has to be the same network which your 3D printer is connected with
   * type in your WiFi password credentials
   * click on SAVE
   * your "BL Better Light" LE controller will now reboot
   * the access point "BL Better Light Ctrl SETUP" will disappear after reboot if your WiFi credentials are correct, if not start from the beginning
   * if everything is correct your "BL Better Light" LED controller, your 3D printer and your browser device (e.g. PC, laptop, smartphone, tablet) should be in the same network
***
### 6. set 3D printer data
   * complete step 5 (Connect to WiFi)
   * connect your "BL Better Light" LED controller with your power supply with an USB-C cable if it is not anymore and with LED strip
   * the red controller LED should light up
   * navigate to the website http://blbetterlightctrl.local/ (this will not working in Android) or alternative http://<ip-address-of-your-led-controller/ (e.g. http://192.168.1.55), refer to the manual of your router if you need help to find this IP address
   * the configuration page should appear:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/4586630b-f151-4bc3-96d2-374d5bf98f09" width="40%" height="40%"> 
       </p>
   * you will need the information you noted in step 3 (Preliminaries)
   * type in the needed information for your 3D printer (IP address, access code, serial number)
   * also type in the type of your LED strip (color order, LED brightness in percent, amount of LED/pixel), refer to the datasheet of your LED strip to find the correct color order, if you set the wrong color order the colors will be wrong
   * click on SAVE ALL
   * your "BL Better Light" LE controller will now reboot
   * you can call up the setup page again at any time to change the data (e.g. if you misstyped something or if you want to change the type of your LED strip and so on)
***
### 7. start-up
   * complete step 5 (Connect to WiFi) and step 6 (set 3D printer data)
   * connect your "BL Better Light" LED controller with your power supply with an USB-C cable if it is not anymore and with your LED strip
   * the red controller led should light up
   * The "BL Better Light" LED controller performs an initial light sequence when switched on, the sequence of colors is RED to GREEN to BLUE. If you see a different sequence, you have set an incorrect color order on the setup page. Go back to the setup page (under point 6) and set the correct color order of your LED strip.
   * After the initial LED sequence the blue LED at the "BL Better Light" LED controller should light up. If not you have set the wrong 3D printer credentials (IP address or access code or serial no) on the setup page. Go back to the setup page (under point 6), check and set the correct values for your 3D printer
***
### 8. Operating states
   * after start up the LED should light up warm white and illuminate your printer chamber
   * during the printing process, the light will go out in certain phases not to influence the LiDAR measurements
   * if there is any error during the printing process your LED strip will light up red, it will go back to white if the error no longer exists
   * if the printing process has been successfully completed, your LED strip will light up green, after 10 minutes it will go back to white
   * The light can be switched off or on manually via the printer display and/or in your Bambu App on your smartphone. If the light has been switched off via the display, there is also no visual signaling in the event of an error or success:
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/77733627-c515-4865-9827-4f3e8daf2833" width="40%" height="40%"> 
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/03f6f572-2f33-448f-93f8-689e65de49f2" width="40%" height="40%"> 
       </p>
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/17c00433-0018-44ec-bb8f-f5c76a3ca8d3" width="30%" height="30%"> 
       </p>
***
### 9. Firmware update OTA
   * complete step 5
   * connect your "BL Better Light" LED controller with your power supply with an USB-C cable if it is not anymore
   * navigate to the page http://blbetterlightctrl.local/update (this will not working in Android) or alternative http://<ip-address-of-your-led-controller/update (e.g. http://192.168.1.55/update)
       <p align="center">
       <img align="center" src="https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/assets/76262830/1a496ab9-ae3a-4f53-bae9-2ef3df2ba5b2" width="40%" height="40%">
       </p>
   * check the shown firmware version
   * download the latest version from https://github.com/FairyTaleLABs/BL-Better-Light-Ctrl/, you will find the firmware in the FIRMWARE folder, you need the .bin file named with firmware_x.xx_OTA.bin (x.xx stands for the firmware version)
   * click on "CHOOSE FILE" and open the .bin file you downloaded before
   * click on "UPDATE"
   * the controller will now update the firmware and reboot afterwards


...... 
WORK IN PROGRESS
