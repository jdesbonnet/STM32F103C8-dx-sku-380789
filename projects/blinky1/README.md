# First working Blinky

I found a 'blinky' project that I was able to make a trival change to which worked with this board. The code looks rather old (2007) which I think predates the CMSIS standard. But it *works* (where other examples failed for some reason). 

I found the download here:
https://www.olimex.com/Products/ARM/ST/STM32-H103/

The file is  OpenOCD-projects100.zip (SHA1 d5ce2d6f1403087b883c93d1c57a49e9083b6577). In subdirectory stm32f103-stk
I found a project which compiled without any modifcations with the latest bare-metal ARM GCC compiler (gcc-arm-none-eabi-4_9-2015q1).  I made some trivial modifications to blink PB9 instead of PC12 and uploaded with this command:

stm32flash -w main.bin -g 0x0 /dev/ttyUSB2

.. blinking LED!!

