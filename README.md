## Marlin Dual Endstop Firmware for BigTreeTech SKR1.3 with TMC2208 UART drivers
Modified Marlin 2.0 firmware for the BigTreeTech SKR1.3 with TMC2208 UART drivers for the MPCNC. Includes dual end stops.

## Features:
* Compatibility with <a href="https://www.amazon.com/BIGTREETECH-Mother-Screen-TMC2208-Printer/dp/B07WH6P9RC/ref=sr_1_7?crid=1IER3G7Y9PKIQ&dchild=1&keywords=bigtreetech+skr+v1.3&qid=1591711657&sprefix=bigtreetech+sk%2Caps%2C202&sr=8-7">SKR1.3 from BigTreeTech</a>
* Immediate compatibility with TMC2208 in UART mode with driver monitoring enabled
* Works with the MPCNC with 5 motors via 5 stepper drivers and with end stops enabled
* Marlin M122 enabled to allow diagnostics of TMC drivers
* Babystepping is enabled to allow slight Z changes when running a project
* Uses the heated bed pins as the "fake" extruder (so these are not available for use)

## Possible changes to use with your MPCNC:
Marlin\configuration.h
* If you have 3 wire end stops or your end stop isn't working as expected in Marlin\configuration.h change true/false on the appropriate ENDSTOP_INVERTING from lines 648-655
* If you have a 16tooth pulley then you are good to go. If you have a 20 tooth then edit line 734 to have the values of 80, 80, 400, 80
* You can change X_BED_SIZE and Y_BED_SIZE on lines 1096 and 1097 to match your cutting area to assist the firmware with not allowing you to crash once homed (I have not gotten software max endstops to work perfectly yet)

Marlin\Configuration_adv.h
* If your motors aren't moving the axis the same direction go change INVERT_X2_VS_X_DIR or INVERT_Y2_VS_Y_DIR from true to false (or flip the motor wires). If both motors are working as they should but going the wrong way check lines 482-515 in Configuration_adv.h (or flip the motor wires)
* StealthChop is disabled by default.  To enable uncomment lines 2242-2244 containing STEALTHCHOP_ 
* SpreadCycle chopper parameters CHOPPER_TIMING CHOPPER_DEFAULT_19V have been updated to reflect the 19v power supply I'm using.  If you're using another input voltage level, change the value on line 2260 from the list in the comment section above it.

## Source info:
* Firmware is based on Ryan's <a href="https://www.v1engineering.com/marlin-firmware/">original MPCNC firmware</a> from V1Engineering 
* The version of Marlin 2.0.X used is "<a href="https://github.com/MarlinFirmware/Marlin/tree/2.0.5.3">Tag 2.0.5.3</a>" from "2020-03-31".
* Thanks to <a href="https://github.com/BlomsD/MPCNC-SKR1.3-TMC2208UART">BlomsD</a> for the initial Marlin 2.0.x build
* Thanks to <a href="https://www.youtube.com/channel/UCbgBDBrwsikmtoLqtpc59Bw">TeachingTech</a> for info on the SKR1.3 and pins.

## Marlin 2.0

Marlin 2.0 takes this popular RepRap firmware to the next level by adding support for much faster 32-bit and ARM-based boards while improving support for 8-bit AVR boards. Read about Marlin's decision to use a "Hardware Abstraction Layer" below.

Download earlier versions of Marlin on the [Releases page](https://github.com/MarlinFirmware/Marlin/releases).

## Building Marlin 2.0

To build Marlin 2.0 you'll need [Arduino IDE 1.8.8 or newer](https://www.arduino.cc/en/main/software) or [PlatformIO](http://docs.platformio.org/en/latest/ide.html#platformio-ide). Detailed build and install instructions are posted at:

  - [Installing Marlin (Arduino)](http://marlinfw.org/docs/basics/install_arduino.html)
  - [Installing Marlin (VSCode)](http://marlinfw.org/docs/basics/install_platformio_vscode.html).
