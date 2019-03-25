Starting with the [Vanilla Coffee Lake](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/config.plist-per-hardware/coffee-lake) for getting the basics so it would boot. Read that if your UniBeast if failing and update accordingly

Page by Page here are the settings I am using.

### Acpi
#### Patches

Removed all the change/rename patches for USB and audio, everything works fine without the extra fluff.

#### Device Renames
Null

#### Fixes
##### Page 1
* FixShutdown - Left this because I am not 100% on removing it at this time

##### Page 2
* FixRTC
* FixTMR

Notes:<br>
These are all from the Vanilla guide, with the quote of `The remaining fixes help avoid IRQ conflicts and etc, and are not known to cause issues.` So I let them be, and have no had issues.

#### DSDT.aml
None

#### Drop Tables
|Signature*|Type/key|String[Tabled]/Number[Length]| Notes|
|---------|---------|---------|---------|---------|
|MATS | | | takes care of unprintable characters |


Notes:<br>
DMAR and MATS were given examples by the vanilla guide, and even though VT-D is disabled in the BIOS I still had this in as a tripple, but I am leaving MATS in for Now

#### SSDT
* PluginType
* ~~Enable C6~~ - This is now enabled in the bios and sleep works
* AutoMerge
* FixHeaders

Notes:<br>
Automerge is for SSDT patching (I might do it some day)

FixHeaders is `this is just a double-up of our MATS table dropping`

### Boot
#### Arguments
* -alcbeta
* alcid=1

##### LasBootedVolume

##### PBR
Legacy is set to PBR and I can probably delete it.

Notes: <br>
`-lilubeta` and `-alcbeta` were both enabled for sound to work, on board `ALC1220-VB` works <br>
`alcid=1` was recommended over `inject=1` below, so why not try it out


### Boot Graphics
Nothing here moving along

### CPU
Nothing Here, Next!

### Devices
#### USB

Now to the fun stuff
* Inject
* FixOwnership


#### Audio
* Inject = no
* ResetHDA

`ResetHDA` is used to "prime" the audio device and it works, so I am leaving it

#### Properties
##### Devices*
* PciRoot(0x0)/Pci(0x2,0x0)

|Properties Key*|Properties Value*|Value Type| Notes|
|-----------|-----------|-----------|-----------|
|AAPL,ig-platform-id|0300923E|DATA|Apple ID for video card|
|device-id|923E0000|DATA|Needed for iGPU Rendering (renames your deivce)|

After resetting the `DVMT Pre-allocated` and `DVMT Total GXF Memory` memory to 128M in the [bios](Bios_Settings.md) the `framebuffer-stolenmem` and `framebuffer-patch-enable` were removed with no ill effects


### Disable Devices
Nothing disabled

### GUI
These are the pretty options for clover, I just added `Hide Volumes`

#### Hidden Volumes
* Windows (even in dual boot this is not the one)
* BOOTX64.EFI
* Recovery
* Preboot

I also changed the theme to [ClassicalDark](https://sourceforge.net/p/cloverefiboot/themes/ci/master/tree/themes/ClassicalDark/)


### Graphics
Nothing added, nothing changed

### Kernel and Kext Patches
#### Checkboxes
* Apple RTC
* KernelPm <br>

`Apple RTC` Does not reset the EFI on boot <br>
`KernelPm` Kernel power management patch, my sleep and wake work so I am leaving this. Mainly for Haswell chips on 10.8.5 and 10.9  

#### KextsToPatch
|Name*|Find* [HEX]|Replace* [HEX]| Comment| MatchOS|MatchBuild|Disable|InfoPlistPatch|
|--------|--------|--------|--------|--------|--------|--------|--------|
|AppleAHCIPort|45787465 726E616C|496E7465 726E616C|External icons patch| | | | | |

`AppleAHCIPort` is the "orange icons fix" for internal hard drives

### Rt Variables
`CsrActiveConfig` = `0x67` <br>
I may switch it back to `0x3` later and that setting is `0x67` for just being able to load unsigned kexts.

### SMBIOS
Setup your brand new computer, I chose a 18,3 iMac. I have the RX 570 graphics card, and an i5 CPU. <br>
This setting is what I used and you can choose another setting that matches your hardware closer.  I have also removed my serial number, so you will have to update that.


### Systen Paramters
* Inject Kexts = Yes
* Inject System ID
