# BL X1C LED Controller
<img src="https://github.com/FairyTaleLABs/blx1cledctrl/assets/76262830/2e49f325-7b0c-42e8-a985-115b8faf4b5d" width="50%" height="50%"> 

***
### Functionality and intended use

Unfortunately, the factory lighting of the X1C is not sufficient to illuminate the printer space properly. The X1C LED controller provides significantly improved illumination, as well as visual signaling when the status of the printer changes (e.g. in the event of errors or when printing has been successfully completed). 

The LED controller is supplied with 5V, can drive LED strips of type WS2812b accordingly and based on a ESP32 microcontroller. To do this, the 3D printer and the LED controller are connected to the same WiFi so that the LED controller can communicate with the 3D printer. The controller detects status changes and set the LED lighting accordingly: 
  * white = normal working light
  * red = printer error
  * green = print successfully completed

When the printer is switched off, the LED lighting also switches off and therefore the LED controller does not need to be disconnected from the power supply separately. The LED lighting also switches on when the printer is switched on. In addition, the LED lighting can be switched on or off via the printer display. 
***
### Requirements:

  * WS2812b LED's (normal strips or neon led strip):
      * e.g.: https://amzn.eu/d/6pVJu65
      * e.g.: https://amzn.eu/d/0JR6dhz
      * it doesn't matter which kind of strips you use, as long as they are WS2812b (5 volts)
      * length: 1.40 m, if you use WS2812b with 60 LED's/m you need 84 pixel of your strip but also strips with more or less LED's/m are possible
      * every USB 5V power supply with at least 2 A (2000 mA) are okay
      * USB-C cable between power supply and LED controller
  * Network:
      * your X1C has to be connected with a WiFi network
      * the LED Controller has to be connected to the same WiFi network as your X1C
      * without WiFi it is not possible to use the LED controller
  * Configuration devices:
      * PC, laptop, tablet, smartphone etc
      * to configure the LED controller you need an actual browser on your device
      * your device has to be connected to the same WiFi network as your X1C and your LED controller
      * in very rare cases micro USB cable to re-programming the microcontroller
   * X1C Firmware:
      * at least version 1.04

[Fancy link](#functionality-and-intended-use)
