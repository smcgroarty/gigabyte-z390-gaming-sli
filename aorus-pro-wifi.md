##  Aorus Z390 Pro Wifi 
#### Warning 
These are the settings I have made, The **Advanced CPU Options** are for my overclod on my CPU, they can all be left to Auto and let the BIOS handle all things with no overclocking.
I am at 4.9Ghz and under 1.3V for VCore. I do not have issues with heat, my temps under extreme workload (Prime95 hit 92c) and under normal work loads I don't see 70c (Exporting 4k video, picture editing, gaming)
I do not overclock the RAM and all settings are just with XMP Enabled. 
I have tested 5.1GHz and that was way to hot once load was applied (hit 100c quickly).
Tested 5GHz and under load it is at 95c with Vcore spiking to 1.42V, but I think a better air flow case would lower temps 
There is a noticable and benchmarkable improvement from stock settings to 4.9GHz on all core, but your mileage may vary. 

##### Hardware Configuration 
My hardware is: 
|Item | Name|
| ----------- | ----------- |
|Motherboard | Gigabyte Aorus Z390 Pro Wi-Fi |
|CPU | Intel Core i9-9900K|
|RAM | 32GB (4x8GB) Patriot Viper 4 DDR4 3000|
|CPU Cooler|  Corsair H115 RGB Pro 280mm AIO |
|Video Card | Sapphire Pulse RX 5600 XT (LED Disabled) |
|Wireless |  BCM94360CS2 Wi-Fi BlueTooth on PCIe Adapter |
|Hard Drives  | MacOS Opencore Samsung Evo 970 Plus 1TB |
| | Windows 10 Western Digital Black SN750 500GB| 
| | Seagate 7200 2TB Formated ExFAT |
|Power Supply| Thermaltake Smart 600w |
|Case | NZXT h510 | 
|Fans| 2x 120MM Corsair SP120 RGB Pro (Out) | 
| |  2x 140MM Corsair SP140 RGB Pro (In - Push) | 
|Fan RGB| Corsair Node Core | 
|RGB Lighting  | Corsair Commander Pro |
| | Corsair RGB Strips |
| Monitor | Samsung 28" 4k E590D|
|Keyboard| Ducky RGB TKL |
|Mouse| Glorious Model O|
|Mouse | Magic TrackPad| 

##### MacOS Configuration 
There is nothing special with the configuration, Folllowed the [Dortania Guide](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#starting-point) for Coffee Lake CPU and set the SMBIOS as iMac19,1 
###### Kexts 
- AppleALC
- IntekMausi
- Lilu
- NVMeFix (lowered Evo temps)
- SMCProcessor
- SMCSuperIO
- USBMap (Custom made)
- VirtualSMC 
- WhateverGreen

###### Drivers 
- AudioDxe 
- ExFatDxe
- GrubNTFS (For READ ONLY)
- HfsPlus
- OpenCanopy
- OpenRuntime 

##### Windows Configuration 
Again nothing special with this, I do not have the Gigabyte App Center, or any gigabyte software other then the @bios tool for loading a custom boot screen. 
###### Drivers Installed
- AMD Radeon Adrenalin 2020 
- BootCamp Driver for Wi-Fi and Bluetooth 
- Corsair iCue 


##### Oddities 
The Corsair Commander Pro is unplugged from the internal USB most of the time because the interal USB 2.0 is detected as a hub and if it is disabled in the USB map, it disables the bluetooth adapater.

I use Chrome for my web browser, Netflix, Hulu, Amazon Prime Video all work on those. 

Apple TV+ Will show trailers and the iGPU work, but it does not play movies or TV shows. 

Handoff, AirDrop and iMessage all work without issue, and this should not be an oddity. 

The 280MM AIO **BARELY** fites in the case. I would like to go to a pull configuration, but the radiator hits the top of the fron IO cables and there is no room. 

### Bios Settings 
Boot into the bios, and select F2 for advanced mode 
The following headeres are for the pages 

#### Advanced Mode 
CPU Base Clode - 100.00MHz 
Enahanced Multi-Core Performance - Disabled 
CPU Clock Ratio - 49 
Ring Ratio - 44 
IGP Ratio - Auto 
AVX Offset - 0 

**Advanced CPU Settins  >**
CPU Over Temperature Protection - 100 C <br>
FCLK Frequency for Early Power On - 1GHz <br>
Hyper-Threading Technology - Enabled<br>
No. of CPU Cores Enabled - 8 <br>
VT-D - Disabled <br>
Intel(R) Speed Shift Technology - Enabled <br>
CPU Thermal Monitor - Enabled <br>
Ring to Core offset (Down Bin) - Diabled <br>
CPU EIST Function - Enabled <br>
Race To Halt (RTH) - Auto <br>
Energy Efficient Turbo - Enabled <br>
Voltage Optimization - Disable <br>
Hardware Prefetcher - Auto <br>
Adjacent Cache Line Prefetch - Auto <br>
Intel(R) Turbo Boost Technology - Enable <br>
CPU Flex Ratio Override - Disable <br>
~~CPU Flex Ratio Setting - 36~~ (Not Selectable)<br>
Frequency Clipping TVB - Auto <br>
Voltage Reduction Initiated TVB - Auto <br>
<br>
Active Turbo Ratios - Auto<br>
<br>
C-States Control - Disable <br>
<br>
Turbo Power Limits - Enabled <br>
Package Power Limit1 - TDP (Watts) - 255 <br>
Package Power Limit1 Time - 127 <br>
Package Power Limit2 - TDP (Watts) - 255 <br>
Package Power Limit2 Time - 127 <br>
Platform Power Limit1 (Watts) - 260 <br>
Platform Power Limit1 (Time) - 127<br>
Platform Power Limit2 (Watts) - 260 <br>
DRAM Power Limit1 (Watts) - Auto <br>
DRAM Power Limit1 Time - Auto <br>
DRAM Power Limit2 (Watts) - Auto <br>
DRAM Power Limit2 Time - Auto <br>
<br>
Turbo Per Core Limit Control - Disable <br>
<br>
**< Back to Tweaker Main Page** 

Extreme Memory Profile (X.M.P.) - Profile1 (DDR4-3000 16-18-18-36-70-1.35)<br>
System Mmory Multipler - Auto <br>
Memory Ref Clock - Auto <br>
Memord Odd Ratio (100/133 or 200/266) - Auto <br>
<br>
**Adcanced Memory Settings >**
Memory Multiplier Tweaker - Auto<br>
Channel InterLeaving - Auto <br>
Rank Interleaving - Auto <br>
Memory Boot Mode - Auto <br>
Realtime Memory Timing - Auto<br> 
Memory Enhancements Settings - <br>
<br>
SPD Info - view Memory settings <br>
<br>
Memory Channels Time > All Set to Auto <br>
<br>
**< Back to Tweaker Main Page** 

CPU Vcore - Normal <br>
Dynamic vCore (DVID) - +0.020 <br>
SVID Offset - Disable <br>
BLCK Adaptive Voltage - Auto <br>
CPU Graphics Voltage(VAXG) - Auto <br>
DRAM Voltage (CH A/B) - Auto <br>
CPU VCCIO Voltage - Auto <br>
CPU System Agent Voltage - Auto <br>
VCC Sustained Voltage - Auto <br>
VCCPLL - Auto <br>
VCCPLL OC - Auto <br>
PCH Core - Auto <br>
<br>
**Advanced Voltage Setttings >**
RING PLL Ovevoltage (+mV) - Auto <br>
GT PLL Overvoltage (+mV) - Auto <br>
SA PLL Overvoltage (+mV) - Auto <br>
MC PLL Overvoltage (+mV) - Auto <br>
DRAM Training Voltage (CH A/B) - Auto<br>
DDRVPP Voltage (CH A/B) - Auto<br>
DRAM Termination (CH A/B) - Auto <br>
<br>
**CPU/VRM Settings >**
CPU Internal AC/DC Load Line - Power Saving <br>
CPU Vcore LoadLine Calibration - Medium<br>
<br>
**Internal Control >*
I have not modified anything in here, and do not want to type all the settings out <br>
<br>
#### Settings 
##### Platform Power
Platform Powr Management - Disabled <br>
AC Back - Always Off (Your Choice here)<br>
ErP - Off <br>
Soft-Off by PWR-BTTN - Instant-Off<br>
Resume By Alarm - Disable <br>
Power Loading - Auto <br>
CEC 2019 Ready - Disable <br>
RC6(Render Standby) - Enabled<br>
 
##### IO Ports 
 Initial Display Output - PCIe 1 Slot<br>
 Internal Graphics - Enabled<br>
 DVMT Pre-Allocated - 64M<br>
 DVMT Total Gfx Mem - 128M <br>
 Aperture Size - 256MB<br>
 Wi-Fi - Disabled<br>
 Audio Controller - Enabled<br>
 Above 4G Decoding - Enabled <br>
 Resize BAR Support - Disabled (This is new and I do not have NVidia graphics)<br>
 PCH Lan Controller - Enabled <br>
 Wake on LAN Enable - Disable <br>
 IOAPIC 240119 Entries - Disabled <br>

 **USB Configuration >**
 Legacy USB Supprot - Enabled<br>
 XHCI Hand-off - Enabled<br>
 USB Mass Storage Driver Support - Enableed<br>
 Port 60/64 Emulation - Disabled <br>
<br>
 **Network Stack Configuration >**
 Network Stack - Enabled <br>
 Ipv4 PXE Support - Disabled <br>
 Ipv4 HTTP Support - Disabled <br>
 Ipv6 PXE Supprot - Diabled <br>
 Ipv6 HTTP Support - Disabled <br>
 IPSEC Certificate - Enabled <br>

PXE boot wait time 0<br>
Media Detect Count - 1<br>

**NVMe Configuration >**
Shows NVMe Drives in computers, nothing modifiable <br>

**SATA and RST Configuration >** 
SATA Controller(s) - Enable <br>
SATA Mode Selection - AHCI <br>
Agressive LPM Support Disable <br>

Everything else is the SATA Ports and what is connected to them <br>
Can disable ports or drives here <br>

**EZ RAID >**
Requires reboot to access RAID controller, no RAID in this system <br>

**Intel(R) Ethernet Connection (7) I219-V >**
Network configuration, good at leaving default unless troubleshooting <br>

##### Miscellaneous
LEDs in System Power On State - Off <br>
LEDs in Sleep, Hibernation, and Soft Off state - Off<br>
Intel Platform Trust Technology (PTT) - Disabled <br>
Software Guard Extentions (SGX) - Disabled <br>
Max Link Speed - Auto <br>
3DMark01 Enhancement - Disable <br>

**Trusted Computing >** 
Secutiry Device Support - Disabled <br>

##### PC Health Status 
Reset Case Open Status - Disabled <br>
Nothing else configurable <br>

##### Smart Fan 5 
You are on your own for setting your own fan curves here.<br>

### System Info 
Not covered here <br>

### Boot 
Boot<br>
Bootup NumLock State - On <br>
CFG Lock - Enabled <br>
Security Option - System <br>
Full Screen LOGO Show - Enabled <br>

Boot Option Priorities <br>
Boot Option 1 - UEFI OS <br>
Boot Option 2 - Windows Boot Manager<br> 

Fast Boot - Disabled <br>

Mouse Speed - 2X<br>

Windows 8/10 Features - Windows 8/10 <br>
CSM Support - Disabled <br>

Administrator Password > <br>
User Password > <br>

**Secure Boot >** 
Secure Boot Enable - Disabled <br>

Secure Boot Mode - Custom <br>
Restore Factory Keys > <br>

**Key Managment >**
Provision Factory Defaults - Disabled <br>
Everything else should Read 0| No Keys <br>

**<< Back to BOOT tab** 

Preferred Operating Mode - Auto <br>

### Save and Exit 
Save & Exit Setup<br>
Exit Without Saving <br>

Load Optimized Defaults <br>

Boot Override <br>
Windows Boot Manager <br>
UEFI OS <br>

**SAVE PROFILE** - Save what you just changed and test <br>
**Load Profiles** - Load last configuration changes if something went wrong <br>