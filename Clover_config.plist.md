Starting with the [Vanilla Coffee Lake](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/config.plist-per-hardware/coffee-lake) for getting the basics so it would boot. Read that if your UniBeast if failing and update accordingly

Page by Page here are the settings I am using.

### Acpi
#### Patches

|Comment|Find* [HEX]|Replace [HEX]|TgtBridge|Disabled| Note|
|-------|-----------|-------------|---------|--------|------|
|change XHCI to XHC|58484349|5848435F| | |USB host controller|
|change XHCI to XHC|58484331|5848435F| | |USB Host Controller|
|Rename HDAS to HDEF|48444153|48444546| | |Renames audo controller|
|change EHC1 to EH01|45484331|45483031| | |USB Host Controller|
|change EHC2 to EH02|45484332|45483032| | |More USB Host Controller|
|change GFX0 to iGPU|47465830|49475055| | |Rename onboard video to iGPU|

Notes:<br>
Yeah there is a lot of USB changing, I have not removed any of it just yet, i should thought.


#### Device Renames
Null

#### Fixes
##### Page 1
* FixPIX
* FixShutdown
* AddMCHC
* FixHPET

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
|DMAR | | | `this prevents some issues with Vt-d`|
|MATS | | | takes care of unprintable characters |


Notes:<br>
DMAR and MATS were given examples by the vanilla guide, and even though VT-D is disabled in the BIOS I still have this in.

#### SSDT
* PluginType
* Enable C6

Notes:<br>
Power management and sleep. So that the CPU runs nicer, and the machine will sleep and wake.

* AutoMerge
* FixHeaders

Notes:<br>
Automerge is for SSDT patching (I might do it some day)

FixHeaders is `this is just a double-up of our MATS table dropping`

### Boot
#### Arguments
* dart=0
* -lilubeta
* -alcbeta
* -v

##### LasBootedVolume
Never works, always defaults to OS X
##### PBR
Legacy is set to PBR and I can probably delete it.

Notes: <br>
`dart=0` Disables the VT-d again. I really want to make sure it is off <br>
`-lilubeta` and `-alcbeta` were both enabled for sound to work, on board `ALC1220-VB` works <br>
`-v` some odd reason, the hackintosh does not boot without the verbose flag


### Boot Graphics
Nothing here moving along

### CPU
Nothing Here, Next!

### Devices
#### USB
Now to the fun stuff
* Inject (enabled by default)
* FixOwnership

#### Audio
* Inject 1
* ResetHDA
`Inject=1` works for me, but I do not use front panel headphones, so this may take some tweaking. <br>
`ResetHDA` is used to "prime" the audio device and it works, so I am leaving it

#### Properties
##### Devices*
* PciRoot(0x0)/Pci(0x2,0x0)

|Properties Key*|Properties Value*|Value Type| Notes|
|-----------|-----------|-----------|-----------|
|framebuffer-stolenmem|00003001| DATA| For iGPU rendering (I thought I disabled this one ) |
|framebuffer-patch-enable|01000000|DATA|For iGPU rendering|
|AAPL,ig-platform-id|0300923E|DATA|Apple ID for video card|
|device-id|923E0000|DATA|Needed for iGPU Rendering (renames your deivce)|

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
* AppleIntelCPUPM
* KernelPm <br>
`Apple RTC` Does not reset the EFI on boot <br>
`AppleIntelCPUPM` restrict the use of MSR register can cause a kernel panic, no harm enabling it <br>
`KernelPm` Kernel power management patch, my sleep and wake work so I am leaving this

#### KextsToPatch
|Name*|Find* [HEX]|Replace* [HEX]| Comment| MatchOS|MatchBuild|Disable|InfoPlistPatch|
|--------|--------|--------|--------|--------|--------|--------|--------|
|AppleAHCIPort|45787465 726E616C|496E7465 726E616C|External icons patch| | | | | |

`AppleAHCIPort` is the "orange icons fix" for internal hard drives

### Rt Variables
The only thing of interest here is `CsrActiveConfig` and I have this set to load unsigned kexts, and that setting is `0x3`

### SMBIOS
Setup your brand new computer, I chose a 18,3 iMac. I have the RX 570 graphics card, and an i5 CPU. <br>
This setting is what I used and you can choose another setting that matches your hardware closer.  I have also removed my serial number, so you will have to update that.


### Systen Paramters
* Inject Kexts = Yes
* Inject System ID
