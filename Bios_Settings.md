# Full Bios Settings

Here is the full settings for everything that I changed after loading "Optimized Defaults" in the Bios

## Testing Software
See the [Benchmarks](Benchmarks.md) for the results<br>

## Daily runnings

### M.I.T.
* Advanced Frequency Settings
  * CPU Clock 48


* Advanced Clock
  * CPU Flex Override - Disabled
  * Package Power Limit 1 (Watt) - 4090
  * Package Power Limit 2 (Watt) - 4090
  * Platform Power Limit 1 (Watt) - 4090
  * Platform Power Limit 2 (Watt) -4090
  * Power Limit 3 - 4090
  * DRAM Power Limit - 250
  * DRAM power Limit 2 - 250
  * Core Current Limit - 250
  * CPU Enhanced Half State (C1E) - Disabled
  * C3 State Support - Disabled
  * C6/C7 State Support - Disabled
  * C8 State Support - Disabled
  * C10 State Support - Disabled


* Extreme Memory Profile
  * Memory Profile 1


* Advanced Power Settings
  * CPU/Internal AC/DC load line - Turbo
  * CPU Core Load Line - Turbo


* CPU Core Voltage
  * CPU VCore - 1.300V
  * BCLK Adaptive Voltage - Enabled


### BIOS
 * Set the date and time
 * Boot option - Set to first hard drive
 * FastBoot - Disabled
 * Mouse Speed - x2
 * Windows 8/10 Features - Other OS
 * CSM Support - Disabled

### Peripherals
* Initial Display Output - PCIe  1 Slot
* LED in System Power On State - On
* Intel Platform Trust Technology - Disabled


* Super IO
  * Serial Port Disabled


* USB Configuration
  * XHCI Handoff - Enabled


* Network Stack
   Disabled


* SATA and RST Configuration
  * SATA Mode Selection - AHCI


### Chipset
* VT-D - Disabled
* Internal Graphics - Enabled
* DVMT Pre-allocated - 128M
* DVMT Total GXF Memory - 128M
* Above 4G  Decoding - Enabled
* Wake on LAN Enabled - Disabled


## More overclock
I was able to overclock the machine to 5.0Ghz but it was getting a little warmer than I wanted under heavy load. (I hit 85-90c) under extreme workloads <br>
These settings are what is different from above

### M.I.T
* Advanced Frequency Settings
  * CPU Clock 50


* Advanced Power Settings
  * CPU Core Load Line - Extreme


* CPU Core Voltage
  * CPU VCore - 1.375v


## Even More overclock!
Ok so getting greedy, I was able to get to 5.2Ghz. The temps were about the same as above and that would have been liveable, but the AVX workloads would cause instability until I put the AVX Offset in. This drops the CPU frequency under AVX loads. I would rather have all speeds all the time.

* Advanced Frequency Settings
  * CPU Clock 52


* Advanced Power Settings
  * CPU/Internal AC/DC load line - Extreme
  * CPU Core Load Line - UltraExtreme


* Advanced CPU Core Settings
  * AVX Offset - 4
  * TJMax - 105c


* CPU Core Voltage
  * CPU VCore - 1.450v
