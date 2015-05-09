# STM32F103C8-dx-sku-380789
This documents my efforts to use the STM32F103C8 development board on DealExtreme (dx.com) SKU 380789. Unfortunately this comes with absolutely no documention (although in fairness it shouldn't really be needed).

![STM32F103C8 ARM Cortex-M3 dev board from DX.com ](https://raw.githubusercontent.com/jdesbonnet/STM32F103C8-dx-sku-380789/master/doc/STM32F103C8-DX-380789.jpg)

Current status (9 May 2015): Verified operation of Serial Wire Debug (SWD) port for reading, writing and debugging. I have also been able to activate the built-in bootloader by setting the BT0 (BOOT0) pin jumper. With the boot loader and stm32flash utility (using USART1 on pins PA9, PA10) I'be been able to download the 'blinky' program that came shipped with it and re-upload it. 

Blinky now working!! Will update with source and make file shortly.

## Programming MCU

Two ways to upload a new program to flash:

1. Use the bootloader. Set BOOT0 to high using BT0 jumper (move it to the postition closer to the RESET switch), BT1 to low. You need a UART cable (eg FTDI cable). FTDI cable TX goes to MCU USART1RX (PA10) and cable RX to USART1TX (PA9) and connect cable ground to board ground.  TODO: provide photos. Use stm32flash utility. [TODO: provide example]

2. Use the Serial Wire Debug port. You'll need a SWD probe. I'm using a STM32F4-Discovery board with the CN3 jumpers removed so that the SWD connector (CN2) can be used to program/debug other boards. Use st-flash tool from stlink (https://github.com/texane/stlink) to upload/download.

I am using the following software tools:

* https://code.google.com/p/stm32flash/
* https://github.com/texane/stlink
* https://launchpad.net/gcc-arm-embedded/

## Board hardware

The board comes shipped with a 'blinky' app which blinks the blue LED on the board when first powered up. It is supplied with pin headers (unsoldered).

Hardware features include:

* Two LEDs: one for power (red) and a user LED (blue). The blue LED is connected to PB9. 
* Jumper BT0 allows BOOT0 pin to be tied to Vdd. This will put the MCU into bootloader mode after a power cycle or reset which will allow it to be programmed via the MCU's UART port. Only UART bootloader is available on the STM32F103C8.
* Reset microswitch
* USB mini connector for power. The USB data lines are not connected (although they are brought out to test pads on the underside of the board, so it should be possible to use some wire to link to the MCU's USB data pins). A Holtek HT7533-1 LDO provides 3.3V for the MCU. 
* 8MHz crystal
* SWD connector (Vdd, SWCLK, SWDIO, GND).

## MCU Documentation
* STM32F103xx family web page: http://www.st.com/web/en/catalog/mmc/FM141/SC1169/SS1031/LN1565
* STM32F103C8 product web page: http://www.st.com/web/en/catalog/mmc/FM141/SC1169/SS1031/LN1565/PF164476
* STM32F103x8 STM32F103xB Datasheet: http://www.st.com/st-web-ui/static/active/en/resource/technical/document/datasheet/CD00161566.pdf
* RM0008 Reference Manual (covering STM32F103xx range, includes details on peripheral registers etc) http://www.st.com/st-web-ui/static/active/en/resource/technical/document/reference_manual/CD00171190.pdf
* AN2606 STM32 microcontroller system memory boot mode: http://www.st.com/web/en/resource/technical/document/application_note/CD00167594.pdf
* AN3155 USART protocol used in the STM32 bootloader: http://www.st.com/web/en/resource/technical/document/application_note/CD00264342.pdf
* AN1356 USB DFU protocol used in the STM32 bootloader: http://www.st.com/st-web-ui/static/active/en/resource/technical/document/application_note/CD00264379.pdf

## Random notes (to be organized later)

* USB Data - : PA11
* USB Data + : PA12
* USART1_TX : PA9
* USART1_RX : PA10

