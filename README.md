# STM32F103C8-dx-sku-380789
This documents my efforts to use the STM32F103C8 development board on DealExtreme (dx.com) SKU 380789. Unfortunately this comes with absolutely no documention (although in fairness it shouldn't really be needed).

![STM32F103C8 ARM Cortex-M3 dev board from DX.com ](https://raw.githubusercontent.com/jdesbonnet/STM32F103C8-dx-sku-380789/master/doc/STM32F103C8-DX-380789.jpg)

Current status (7 May 2015): I can read the flash memory, but currently cannot program it. I can allow stop, step, restart the supplied blinky app with gdb.

My setup is attempting to program and debug via the SWD connector. I'm using a STM32F4-Discovery board with the CN3 jumpers removed so that the SWD connector (CN2) can be used to program/debug other boards.

I am using the following tools:

* https://github.com/texane/stlink
* https://launchpad.net/gcc-arm-embedded/

I have built this project and am currently attempt to program the resulting .elf file:
https://github.com/mkschreder/stm32f103c8t6_blink

## Board hardware

The board comes shipped with a 'blinky' app which blinks the blue LED on the board when first powered up. It is supplied with pin headers (unsoldered).

There are two LEDs: one for power (red) and a user LED (blue). The blue LED is connected to PB9. Jumper BT0 allows BOOT0 pin to be tied to Vdd. In theory this should put the MCU into bootloader mode which will allow it to be programmed via the MCU's UART or USB ports. However so far I have been unable to get this to work.  

I think BT1 is for BOOT1, but not sure about this.  

The USB mini connector is only for power. The USB data lines are not connected (although they are brought out to test pads on the underside of the board... so it should be possible to use some bodge wire to link up to the MCU's USB data pins).

There is a SWD connector (Vdd, SWCLK, SWDIO, GND) which is what I'm currently focusing my efforts. I've been able to use gdb to stop and start the shipped Blinky app. I've also been able to download the firmware. But so far I have not been able to program the flash. I have no doubt this is my fault and not due to any defect of the product.

## Random notes (to be organized later)

USB Data - : PA11

USB Data + : PA12


