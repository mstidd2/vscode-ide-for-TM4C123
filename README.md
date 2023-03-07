This document describes how to use an Ubuntu 22.04 machine for compiling, flashing, and debugging TM4C123GXL devices using a common IDE used on Linux, Visual Studio Code (VS Code).  VS Code is an alternative to, and a more generalizable solution than, using Texas Instrument's (TI’s) IDE Code Composer Studio (CCS) for software/firmware development on Linux. 

## Software Installation

**Visual Studio Code**
 - Purpose: IDE
 - Version: 1.76.0
 - Source: Repos (snap)
     - `$ sudo apt-get install code`
 - Extensions
    - Cortex-Debug (version 1.8.0)
    - C/C++ (version 1.14.4)
    - Python (version 2022.10.1)
    - Others as neccessary or you see fit

 **GTKTerm**
- Purpose: Connecting/Reconnecting to UART serial interface
- Version: 1.1.1
- Source: Repos
    - `$ sudo apt-get install gtkterm`

**gcc-arm-none-eabi**
- Purpose: Cross complier for ARM Cortex R/M processors
- Version: 10.3.1
- Source: Repos
    - `$ sudo apt-get install gcc-arm-none-eabi`

**lm4flash**
- Purpose: Flashing binary files to device
- Version: 0.1.3
- Source: Repos
    - `$ sudo apt-get install lm4flash`

**OpenOCD**
- Purpose: Allow the debugger (gdb-multiarch) to connect to the on chip debugger
- Version: 0.12.0
- Source: https://sourceforge.net/projects/openocd/
    - The Cortex-Debug extension in vscode expects openocd's config files to be in /usr/local/share/openocd/scripts/; however, version 0.10 and 0.11 both store them in /usr/share/openocd/scripts/ using slightly different names.  Version 0.12.0 does store the scripts in the expected location; therfore, 0.12.0 was installed. 
    - Download and extract the openocd-0.12.0.tar.bz2 from the link above
    - The README indicates to install/verify the installation of the following:
        - make
            - Version used for this guide: 4.3
            - Source: repos
        - libtool
            - Version used for this guide: 2.4.6
            - Source: repos
        - pkg-config
            - Version used for this guide: 0.29.2
            - Source: repos
        - libusb-1.0
            - Version used for this guide: 1.0.25
            - Source: repos
        - `$ sudo apt-get install make libtool pkg-config libusb-1.0`
    - As per the README run the following commands:
        - `./configure`
            - No option flags were needed.
            - You should see something like the following when it is done:

            - ```
OpenOCD configuration summary
--------------------------------------------------
MPSSE mode of FTDI based devices        yes (auto)
ST-Link Programmer                      yes (auto)
TI ICDI JTAG Programmer                 yes (auto)
Keil ULINK JTAG Programmer              yes (auto)
Altera USB-Blaster II Compatible        yes (auto)
Bitbang mode of FT232R based devices    yes (auto)
Versaloon-Link JTAG Programmer          yes (auto)
TI XDS110 Debug Probe                   yes (auto)
CMSIS-DAP v2 Compliant Debugger         yes (auto)
OSBDM (JTAG only) Programmer            yes (auto)
eStick/opendous JTAG Programmer         yes (auto)
Olimex ARM-JTAG-EW Programmer           yes (auto)
Raisonance RLink JTAG Programmer        yes (auto)
USBProg JTAG Programmer                 yes (auto)
Espressif JTAG Programmer               yes (auto)
Andes JTAG Programmer (deprecated)      no
CMSIS-DAP Compliant Debugger            no
Nu-Link Programmer                      no
Cypress KitProg Programmer              no
Altera USB-Blaster Compatible           no
ASIX Presto Adapter                     no
OpenJTAG Adapter                        no
Linux GPIO bitbang through libgpiod     no
SEGGER J-Link Programmer                yes (auto)
Bus Pirate                              yes (auto)
Use Capstone disassembly framework      no
```
        - `make`
        - `sudo make install`









