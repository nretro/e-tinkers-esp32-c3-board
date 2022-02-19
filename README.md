# USB_JTAG mod of E-Tinkers ESP32-C3 Board

The ESP32-C3 chip has a USB to JTAG bridge built in, but no dev board directly makes use of it. So I modified
![ Henry Cheung's breakout board](https://github.com/e-tinkers/e-tinkers-esp32-c3-board/)

The main differences are:
  * micro USB connector with ESD protection (CM1231)
  * different LDO (TLV76733DRVR)
  * removed the flash button (not needed when using JTAG)
  * modified some footprints:
	** all necessary resistors and capacitors have 0805 footprints, which also allows to use 0603 parts
	** deleted the antenna from the module footprint since that interferes with panelizing 
	** stretched pads of the WS2812 footprint to aid hand soldering

Options:
  * added optional 22pF capacitors to D+ and D- lines on the bottom. They appear on the schematics of the official dev board, but seem not to be necessary.
  * populating R4 with a 0 ohm resistor will connect USB shield with GND. Usually shield is connected to GND at the host and not at devices downstream. Therefore R4 should be left unpopulated in most applications. 
  * the LDO can be disabled by connecting LDO_EN to GND to save energy when not used.

Please note that since I made some minor modifications after receiving
the first patch of PCBs, I have not yet used the gerbers in the
archive to fabricate actual boards. Therefore there is a small chance
that those contain errors.
