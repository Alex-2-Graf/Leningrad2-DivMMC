# Leningrad2-DivMMC

## DivMMC controller for ZX Spectrum computers.

> [English](README.en.md) | [Русский](README.md)

The DivMMC interface for the legendary "Leningrad-2" clone allows the use of modern SD cards as storage media. It runs under the ESXDOS operating system, providing instant loading of games and software (.TAP, .TRD, .SCL, .Z80, .SNA) along with full support for long filenames. 

The project is based on a proven circuit design by **AlexEkb** and is fully implemented using widely available, standard discrete logic components (74-series TTL chips).

***

## Historical Context

While the classic Beta Disk Interface (BDI/TR-DOS) was the gold standard of the 1990s, DivMMC is the definitive standard today for everyday retro-computing. 

This specific controller layout is tailored for seamless, plug-and-play connection to my custom motherboard revisions:
*   [**Leningrad-2-48k**](https://github.com/Alex-2-Graf/LENINGRAD-2-48k)
*   [**Leningrad-2-128k-SRAM**](https://github.com/Alex-2-Graf/Leningrad-2-128k-SRAM)

On these motherboards, the expansion bus is already fully prepared. However, this DivMMC interface can also be connected to any other standard or third-party "Leningrad-2" board with minimal wiring adjustments.

***

## Technical Features

*   **Storage Media:** Support for up to two SD cards (onboard MicroSD slot + extension header for a secondary card module).
*   **Logic Circuitry:** Built entirely on discrete logic gates **without** CPLD or FPGA chips. This makes the board incredibly easy to assemble, debug, and maintain using basic tools.
*   **Onboard Controls:** Dedicated **NMI** button (to trigger the ESXDOS file navigator overlay menu) and a hardware **RESET** button.
*   **OS Compatibility:** Fully compatible with ESXDOS (version 0.8.9 and newer) for running `.TAP`, `.TRD`, `.SCL`, and `.Z80` files.

### Hardware Project Files
*   [Interactive BOM (iBOM)](Schematics/DivMMC\_L2.html)
*   [Schematics](Schematics/DivMMC\_L2.pdf)
*   [Gerber Files](Gerber/DivMMC\_L2\_Gerber.zip)

---

## Connection & Integration

The controller plugs into the standard expansion system bus. All essential control lines (`MREQ`, `IORQ`, `M1`, `RD`, `WR`) alongside the standard data and address buses are fully utilized according to the core DivMMC specification.

⚠️ **Important Note:** The interface strictly requires a working, stable CPU **`M1`** signal. On my custom Leningrad-2 motherboard projects, this signal is already pre-routed to the expansion slot by default. If you are using a stock computer board, verify that the `M1` line is correctly connected.

---

## Software & ROM Firmware

To run this controller, you must flash an EPROM chip with the ESXDOS system firmware.

*   ⚠️ **Important:** This specific hardware layout uses a **modified firmware version**, which has been adapted to match AlexEkb's hardware architecture and the specific bus timings of the "Leningrad-2". The required ready-to-flash binary can be found inside the [/Firmware](Firmware/ROM.bin) folder of this repository.
*   **Official Website:** You can visit the official esxDOS project page at [esxdos.org](http://esxdos.org) to explore the system command list, features, and the required root directory structure for the SD card.

### SD Card Preparation
1. Format your SD card using the **FAT32** file system.
2. Unpack the system files [archive](Firmware/esxdos\_disk.zip) (found in the firmware folder) directly into the root directory of the SD card.
