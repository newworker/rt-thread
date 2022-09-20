# ESP32-C3 BSP Introduction

[中文](README_ZH.md) | English

This document records the execution instruction of the BSP (board support package) for the [ESP32-C3](http://luatos.com/t/esp32c3) development board.

The document is covered in two parts:

- Board Resources Introduction
- Quickly Get Started

## Resources Introduction

We tested 2 development boards, it all works, but due to the different LED pins of the two development boards, so we'll need to select the corresponding development board in the menuconfig. 

- [LUATOS_ESP32C3](https://wiki.luatos.com/chips/esp32c3/board.html)

![LUATOS_ESP32C3](images/luatos_esp32c3.png)

- [HX-DK-商](https://docs.wireless-tech.cn/doc/7/)

![hongxu](images/hx_shang.png)

The mainly-used resources of LUATOS_ESP32C3 are shown as follows:

- MCU: [esp32-c3](https://www.espressif.com/sites/default/files/documentation/esp32-c3_datasheet_en.pdf)，Main Frequency 160MHz, 407.22 CoreMark; 2.55 CoreMark/MHz
- Built-in Chip: 384KB ROM, 400KB SRAM
- Peripherals
  - Red LED: 2, LED: D4 (IO12), D5（IO13）
  - Button: 2, K1（BOOT） K2(RST)
  - SPI FLASH: 4M
- Common-used interfaces: USB, UART, etc.

### For more details about this board, please refer to [Here](https://wiki.luatos.com/chips/esp32c3/board.html).

## **Peripheral Condition**

Each peripheral supporting condition for this BSP is as follows:

| **On-board Peripherals** | ****Support**** | ****Remark****                                               |
| ------------------------ | --------------- | ------------------------------------------------------------ |
| GPIO                     | Support         |                                                              |
| UART                     | Support         | Using LUATOS_ESP32C3 development board requires connecting serial port to USB chip UART0_TX and UART0_RX (such as CP2102) |
| JTAG debug               | Support         | ESP32C3 usb-linked development boards can be debugged        |

## Quick Start Guide

1. Download ESP-IDF package
```
pkgs --update
```
2. Go to ESP-IDF package directory and install IDF tools. This command only needs to be run once after the package is downloaded for the first time.
```
cd packages/ESP-IDF-latest
./install.sh
# Use install.bat in Windows environment
```
3. Under the ESP-IDF package directory, export IDF environment variables. This commands need to be run every time when the BSP is built in a new terminal.
```
. export.sh
# Use export.bat in Windows environment
```
4. Configure RT-Thread under the BSP directory
```
scons --menuconfig
```
5. Whenever RT-Thread configuration is changed with `scons --menuconfig`, a new `CMakeLists.txt` needs to be generated with the command below
```
scons --target=esp-idf
```
6. Use `idf.py` to compile and upload the program. Refer to [Espressif official documents](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c3/get-started/index.html#build-your-first-project) for reference.
7. Once the project is successfully downloaded, the system runs automatically, the red LED will blink in 1s on cycles.

## Notes

- The basic functions are now supported, but it needs more, welcome any contributions and feedback. 


Maintainer: 

- [supperthomas](https://github.com/supperthomas) email address: [78900636@qq.com](mailto:78900636@qq.com)
-  [tangzz98](https://github.com/tangzz98) email address: [tangz98@outlook.com](tangz98@outlook.com)

Special thanks to [chenyingchun0312](https://github.com/chenyingchun0312) for providing support on the RISC-V part working.

