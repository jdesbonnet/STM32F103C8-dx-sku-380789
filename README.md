# STM32F103C8-dx-sku-380789
This documents my efforts to use the STM32F103C8 development board on DealExtreme (dx.com) SKU 380789. Unfortunately this comes with absolutely no documention (although in fairness it shouldn't really be needed).

Current status (6 May 2015): I can read the flash memory, but currently cannot program it. 

My setup is attempting to program and debug via the SWD connector. I'm using a STM32F4-Discovery board with the CN3 jumpers removed so that the SWD connector (CN2) can be used to program/debug other boards.

I am using the following tools:

* https://github.com/texane/stlink
* https://launchpad.net/gcc-arm-embedded/

I have built this project and am currently attempt to program the resulting .elf file:
https://github.com/mkschreder/stm32f103c8t6_blink

## Board hardware

There are two leds. One red for power and a blue user LED. This is connected to PB9. Jumper BT0 (I believe) allows BOOT0 to be tied high. I think BT1 is for BOOT1, but not sure about this.  The USB mini connector is only for power. The USB data line are not connected (although they are brought out to test pads on the underside of the board... so it should be possible to use some bodge wire to link up to the MCU's USB data pins).
