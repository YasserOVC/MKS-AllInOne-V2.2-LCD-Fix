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


# MKS All-In-One V2.2 LCD Fix & Firmware

This repository is a specialized fork and enhancement of the [UGEelectronics 3D Printer](https://github.com/UGEelectronics/3d-printer) firmware. It specifically addresses the common display initialization and pinout errors found when using the **MKS All-In-One V2.2** board with standard 12864 LCDs or MKS Mini displays.

## 🛠 The Problem
Many users of the UGE/MKS All-In-One V2.2 boards experience:
* **Blank Blue Screens:** The LCD lights up but shows no text.
* **Garbled Characters:** Timing issues between the MCU and the LCD driver.
* **Pin Mismatch:** Standard Marlin configurations often swap the EXP1/EXP2 definitions for this specific board revision.

## ✅ The Fix (What’s Changed?)
I have modified the configuration files to ensure hardware compatibility:
1.  **Pin Mapping:** Corrected the `pins_MKS_BASE.h` (or relevant pins file) to match the V2.2 hardware trace layout.
2.  **Timing Delays:** Added `ST7920_DELAY` tweaks in `Configuration_adv.h` to stabilize the SPI communication for the display.
3.  **Contrast Settings:** Optimized default contrast values for better visibility out of the box.

## 🚀 How to Use

### 1. Requirements
* **Board:** MKS All-In-One V2.2 (Integrated Driver Version)
* **IDE:** VS Code with **PlatformIO** (Recommended) or Arduino IDE.

### 2. Installation
1.  Clone this repository:
    ```bash
    git clone [https://github.com/YasserOVC/MKS-AllInOne-V2.2-LCD-Fix.git](https://github.com/YasserOVC/MKS-AllInOne-V2.2-LCD-Fix.git)
    ```
2.  Open the folder in **PlatformIO**.
3.  Verify your `platformio.ini` is set to the correct environment (usually `mega2560`).
4.  Build and Upload to your printer.

## 🔌 Hardware Wiring Note
If your screen is still blank after flashing:
* Ensure the **EXP1** and **EXP2** ribbons are not reversed.
* On some MKS V2.2 boards, the plastic "shrouds" on the 10-pin connectors are installed backwards from the factory. You may need to trim the notch on your cable and rotate the connector 180°.

## 🤝 Credits & Relations
* **Original Firmware:** Based on the [UGEelectronics](https://github.com/UGEelectronics) 3D Printer repository.
* **Maintenance & Fixes:** Maintained by [YasserOVC](https://github.com/YasserOVC).

---
*If this fix helped you get your printer back online, consider giving this repo a ⭐!*

