
# X-LINUX_GNSS1_V1.2.0 Linux Package

## Introduction
**The X-LINUX-GNSS1-APP** is a Linux Software Package running on STM32MPU .This software provides user level applications for reading the NMEA GNSS data from X-STM32MP-GNSS1 plugged to the 40 pin connector of STM32MP157F-DK2 Discovery Board .
X-LINUX-GNSS1 includes user space applications using POSIX thread for task scheduling to ensure better asynchronous message parsing.This Software package also contains the RTK(Real-time kinematic) Library example Application using GNSS and IMU Data 
from X-STM32MP-GNSS1.It also contains the corresponding QT Application for Weston Wayland Build of OpenSTLinux.


![X-LINUX-GNSS1 Package](/_htmresc/X-LINUX-GNSS1_components_2020.png "X-LINUX-GNSS1 Package")

## Description

### X-LINUX-GNSS1 software features:

Its main feature are :
-Standalone applications to read the NMEA data over UART and I²C
-Complete software to build applications on Linux using Teseo-LIV3F GNSS module
-Middleware for the NMEA protocol
-RTK ( Real Time Kinematics ) Library example and QT application.
-POSIX thread task scheduling to ensure better asynchronous message parsing
-Easy portability across different Linux platforms
-Application example to retrieve and parse GNSS data and send them to DSH-ASSETRACKING for live tracking
-Python example to read the NMEA data over UART
-For detailed instructions refer "Getting started with X-LINUX-GNSS1 package for developing GNSS Applications on Linux : https://www.st.com/resource/en/user_manual/um2909-getting-started-with-xlinuxgnss1-package-for-developing-gnss-applications-on-linux-os-stmicroelectronics.pdf"  


### X-LINUX-GNSS1 Architecture:

The software uses STM32MPU Uart and I2C driver for accessign the GNSS data. For IMU ST MEMS Drivers are used


![System Components](/_htmresc/X-LINUX-GNSS1_components_2020.png "System Components")

![X-LINUX-SPN1 Architecture](/_htmresc/03_system_architecture.png "X-LINUX-SPN1 Architecture")

### X-LINUX-SPN1 Package Structure:

## Hardware Setup:

The current package provides software support for the following boards
 - [X-STM32MP-GNSSx board mounted on STM32MP157F-DK2](https://www.st.com/en/ecosystems/x-nucleo-ihm15a1.html) based on Teseo-LIV3FL and Teseo-LIV4FL. 
 - The board is also compatible with X-NUCLEO-GNSSx and X-NUCLEO-LIV* boards plugged to the Arduino Connectors

## Software Setup:

The section describes the software setup that is required for building, flashing, deploying, and running the application.

### Recommended PC prerequisites

A Linux® PC running Ubuntu® 20.04 or 22.04 is recommended. Developers can follow the link below for details.
https://wiki.st.com/stm32mpu/wiki/PC_prerequisites

Follow the instructions on the ST wiki page [Image flashing](https://wiki.st.com/stm32mpu/wiki/STM32MP15_Discovery_kits_-_Starter_Package#Image_flashing) to prepare a bootable SD card with the starter package.  
Alternatively, a Windows / Mac computer can also be used; in that case, the following tools would be useful:
- Use [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html) to flash the OpenSTLinux started package image onto the SD card
- Use [TeraTerm](https://github.com/TeraTermProject/osdn-download/releases/) or [PuTTY](https://putty.org/) to access the console interface via USB
- Use [winscp](https://winscp.net/eng/index.php) to copy the application to the MPU board

*The following conventions are used when referring to the code instructions.*
```
#Comments: Comment describing steps
PC>$ : Development or Host PC/machine command prompt. Text after $ is a command
Board>$ : STM32MP1 command prompt. Text after $ is a command
```
**STMPU Software Prerequisites**

The Python package ["pyserial"](https://github.com/hhk7734/python3-gpiod) is a prerequisite for the x-linux-spn1 software and must be installed onto the STM32MP1 board.
The Python package ["pynmea"](https://github.com/hhk7734/python3-gpiod) is a prerequisite for the x-linux-spn1 software and must be installed onto the STM32MP1 board.

```bash
#Install Python pip if not already installed
Board>$ apt-get install python3-pip
#Install gpiod
Board>$ python3 -m pip install gpiod
```

### Deploying the files to the MPU board

It is required to transfer the built binaries, Python scripts, and application resources to the STM32MP board from the development PC.

The resources can be transferred via any of the following methods:

1. **Using a network connection**

Refer to [How to Transfer a File Over a Network](https://wiki.st.com/stm32mpu/wiki/How_to_transfer_a_file_over_network)
 
To connect the MPU board to a network, you may connect it to a wired network via the Ethernet jack on the MPU board.  
 
**OR**  

To connect to a WLAN, refer to [How to Setup a WLAN Connection"](https://wiki.st.com/stm32mpu/wiki/How_to_setup_a_WLAN_connection)

2. **Using a serial protocol** (like zmodem from Teraterm or kermit)

For Linux hosts refer to [How to transfer a file over a serial console](https://wiki.st.com/stm32mpu/wiki/How_to_transfer_a_file_over_serial_console)  
For Windows hosts, refer to
[How to transfer files to Discovery kit using Tera Term](https://wiki.st.com/stm32mpu/wiki/How_to_transfer_files_to_Discovery_kit_using_Tera_Term_on_Windows_PC)

To evaluate the X-LINUX-GNSS1 package quickly, developers may copy the contents of the "application/Binaries" folder contained in the package to `/usr/local/demo/application` folder on the STM32MP board using any of the above methods.

```bash
# Go to the application folder
#>$ cd application
# Add execute permission to the deployment script
#>$ chmod +x <binary_name>
# Run the binary
#>$ ./<binary_name>
```

## License

Details about the terms under which various components are licensed are available [here](LICENSE.md)

## Release notes

Details about the content of this release are available in the release note [here](Release_Notes.md).

## Compatibility information

The software package is validated for the [OpenSTLinux](https://www.st.com/en/embedded-software/stm32-mpu-openstlinux-distribution.html) version 5.0. For running the software on other ecosystem versions customization may be needed.
The software is tested on the [STM32MP157F-DK2](https://www.st.com/en/evaluation-tools/stm32mp157f-dk2.html) board.


#### Related Information and Documentation:

- [X-STM32MP-GNSS1](https://www.st.com/en/evaluation-tools/x-stm32mp-gnss1.html)
- [STM32MP157F-DK2](https://www.st.com/en/evaluation-tools/stm32mp157f-dk2.html)
- [X-NUCLEO-GNSS1A1](https://www.st.com/en/ecosystems/x-nucleo-gnss1a1.html)
- [X-NUCLEO-GNSS2A1](https://www.st.com/en/ecosystems/x-nucleo-gnss2a1.html)
