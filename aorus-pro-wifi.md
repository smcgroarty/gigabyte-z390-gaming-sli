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
CPU Over Temperature Protection - 100 C 
FCLK Frequency for Early Power On - 1GHz 
Hyper-Threading Technology - Enabled
No. of CPU Cores Enabled - 8 
VT-D - Disabled 
Intel(R) Speed Shift Technology - Enabled 
CPU Thermal Monitor - Enabled 
Ring to Core offset (Down Bin) - Diabled 
CPU EIST Function - Enabled 
Race To Halt (RTH) - Auto 
Energy Efficient Turbo - Enabled 
Voltage Optimization - Disable 
Hardware Prefetcher - Auto 
Adjacent Cache Line Prefetch - Auto 
Intel(R) Turbo Boost Technology - Enable
CPU Flex Ratio Override - Disable 
~~CPU Flex Ratio Setting - 36~~ (Not Selectable)
Frequency Clipping TVB - Auto 
Voltage Reduction Initiated TVB - Auto 

Active Turbo Ratios - Auto

C-States Control - Disable 

Turbo Power Limits - Enabled 
Package Power Limit1 - TDP (Watts) - 255 
Package Power Limit1 Time - 127 
Package Power Limit2 - TDP (Watts) - 255 
Package Power Limit2 Time - 127 
Platform Power Limit1 (Watts) - 260 
Platform Power Limit1 (Time) - 127
Platform Power Limit2 (Watts) - 260 
DRAM Power Limit1 (Watts) - Auto 
DRAM Power Limit1 Time - Auto 
DRAM Power Limit2 (Watts) - Auto 
DRAM Power Limit2 Time - Auto 

Turbo Per Core Limit Control - Disable 

**< Back to Tweaker Main Page** 

Extreme Memory Profile (X.M.P.) - Profile1 (DDR4-3000 16-18-18-36-70-1.35)
System Mmory Multipler - Auto 
Memory Ref Clock - Auto 
Memord Odd Ratio (100/133 or 200/266) - Auto 

**Adcanced Memory Settings >**
Memory Multiplier Tweaker - Auto
Channel InterLeaving - Auto 
Rank Interleaving - Auto 
Memory Boot Mode - Auto 
Realtime Memory Timing - Auto 
Memory Enhancements Settings - 

SPD Info - view Memory settings 

Memory Channels Time > All Set to Auto 

**< Back to Tweaker Main Page** 

CPU Vcore - Normal 
Dynamic vCore (DVID) - +0.020 
SVID Offset - Disable 
BLCK Adaptive Voltage - Auto 
CPU Graphics Voltage(VAXG) - Auto 
DRAM Voltage (CH A/B) - Auto 
CPU VCCIO Voltage - Auto 
CPU System Agent Voltage - Auto 
VCC Sustained Voltage - Auto 
VCCPLL - Auto 
VCCPLL OC - Auto 
PCH Core - Auto 
**Advanced Voltage Setttings >**
RING PLL Ovevoltage (+mV) - Auto 
GT PLL Overvoltage (+mV) - Auto 
SA PLL Overvoltage (+mV) - Auto 
MC PLL Overvoltage (+mV) - Auto 
DRAM Training Voltage (CH A/B) - Auto
DDRVPP Voltage (CH A/B) - Auto
DRAM Termination (CH A/B) - Auto 
**CPU/VRM Settings >**
CPU Internal AC/DC Load Line - Power Saving 
CPU Vcore LoadLine Calibration - Medium

**Internal Control >*
I have not modified anything in here, and do not want to type all the settings out 

#### Settings 
##### Platform Power
Platform Powr Management - Disabled 
AC Back - Always Off (Your Choice here)
ErP - Off 
Soft-Off by PWR-BTTN - Instant-Off
Resume By Alarm - Disable 
Power Loading - Auto 
CEC 2019 Ready - Disable 
RC6(Render Standby) - Enabled
 
##### IO Ports 
 Initial Display Output - PCIe 1 Slot
 Internal Graphics - Enabled
 DVMT Pre-Allocated - 64M
 DVMT Total Gfx Mem - 128M 
 Aperture Size - 256MB
 Wi-Fi - Disabled
 Audio Controller - Enabled
 Above 4G Decoding - Enabled 
 Resize BAR Support - Disabled (This is new and I do not have NVidia graphics)
 PCH Lan Controller - Enabled 
 Wake on LAN Enable - Disable 
 IOAPIC 240119 Entries - Disabled 

 **USB Configuration >**
 Legacy USB Supprot - Enabled
 XHCI Hand-off - Enabled
 USB Mass Storage Driver Support - Enableed
 Port 60/64 Emulation - Disabled 

 **Network Stack Configuration >**
 Network Stack - Enabled
 Ipv4 PXE Support - Disabled 
 Ipv4 HTTP Support - Disabled 
 Ipv6 PXE Supprot - Diabled 
 Ipv6 HTTP Support - Disabled 
 IPSEC Certificate - Enabled 

PXE boot wait time 0
Media Detect Count - 1

**NVMe Configuration >**
Shows NVMe Drives in computers, nothing modifiable 

**SATA and RST Configuration >** 
SATA Controller(s) - Enable 
SATA Mode Selection - AHCI 
Agressive LPM Support Disable 

Everything else is the SATA Ports and what is connected to them 
Can disable ports or drives here 

**EZ RAID >**
Requires reboot to access RAID controller, no RAID in this system 

**Intel(R) Ethernet Connection (7) I219-V >**
Network configuration, good at leaving default unless troubleshooting 

##### Miscellaneous
LEDs in System Power On State - Off 
LEDs in Sleep, Hibernation, and Soft Off state - Off
Intel Platform Trust Technology (PTT) - Disabled 
Software Guard Extentions (SGX) - Disabled 
Max Link Speed - Auto 
3DMark01 Enhancement - Disable 

**Trusted Computing >** 
Secutiry Device Support - Disabled 

##### PC Health Status 
Reset Case Open Status - Disabled 
Nothing else configurable 

##### Smart Fan 5 
You are on your own for setting your own fan curves here.

### System Info 
Not covered here 

### Boot 
Boot
Bootup NumLock State - On 
CFG Lock - Enabled 
Security Option - System 
Full Screen LOGO Show - Enabled 

Boot Option Priorities 
Boot Option 1 - UEFI OS 
Boot Option 2 - Windows Boot Manager 

Fast Boot - Disabled 

Mouse Speed - 2X

Windows 8/10 Features - Windows 8/10 
CSM Support - Disabled 

Administrator Password > 
User Password > 

**Secure Boot >** 
Secure Boot Enable - Disabled 

Secure Boot Mode - Custom 
Restore Factory Keys > 

**Key Managment >**
Provision Factory Defaults - Disabled 
Everything else should Read 0| No Keys 

**<< Back to BOOT tab** 

Preferred Operating Mode - Auto 

### Save and Exit 
Save & Exit Setup
Exit Without Saving 

Load Optimized Defaults 

Boot Override 
Windows Boot Manager 
UEFI OS 

**SAVE PROFILE** - Save what you just changed and test 
**Load Profiles** - Load last configuration changes if something went wrong 