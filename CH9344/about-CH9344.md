# CH9344 Custom Board & Linux Driver

## Overview
This project integrates the **WCH CH9344** chip, which converts **1 USB port to 4 Serial (UART) ports**

## Hardware Design (Altium)
I designed a custom PCB for this chip using **Altium Designer**.
- Created a **custom footprint** and library since it wasn't available.
- Designed the schematic and routed the PCB for industrial use.

## Linux Driver Integration
The driver source code is from WCH, but I added a **custom Makefile** to compile it easily on Linux.

## Files
- `/Datasheet`: Official PDF datasheet.
- `/Altium`: PCB and Schematic files.
- `/Driver`: Source code and Makefile.
