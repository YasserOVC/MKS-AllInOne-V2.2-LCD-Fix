# MKS-AllInOne-V2.2-LCD-Fix
these "All-in-One" boards are poorly documented, creating a GitHub repository is a fantastic idea.

# MKS All-In-One Plus V2.2 LCD Blank Screen Fix

This repository contains the working Marlin 1.1.x configuration and the patched U8glib library for the **Integrated Mini12864 LCD** on the "All-in-One Plus" board.

## The Problem
The screen shows the Marlin logo but goes blank when loading the menu. This is due to incorrect pin mapping and a driver conflict in the standard U8glib library.

## The Fixes Included:
1. **Pins:** Forced mapping of `DOGLCD_CS` (16) and `DOGLCD_A0` (17) in `pins_MKS_13.h`.
2. **Library:** Replaced `u8g_dev_uc1701_mini12864.c` in the U8glib library to fix timing.
3. **Contrast:** Forced `u8g.setContrast(255)` in `dogm_lcd_implementation.h`.
4. **SD Card:** Configured shared SPI pins to prevent the "SD Init Fail" crash.

## How to use:
1. Copy the `U8glib` folder to your `Documents/Arduino/libraries`.
2. Open the Marlin sketch and set Motherboard to `47`.

AllinoneMarlin Firmware Flashing Tutorial
Download and install the Arduino IDE.

## Original setup from manufactory:
1.Install the U8glib library and update it to the latest version.
2.Copy the file u8g_dev_uc1701_mini12864.c to the following directory: C:\Users\YourUserName\Documents\Arduino\libraries\U8glib\src\clib and replace the original file existing in that folder.
3.Use the Arduino IDE to flash the firmware.

