# How it was installed

## USB Installation
[Unibeast](https://www.tonymacx86.com/threads/unibeast-install-macos-mojave-on-any-supported-intel-based-pc.259381/#create_unibeast) was used to prep the USB device after downloading Mojave on a Macbook.

After it didn't boot correctly to the install, I started using the [Vanilla Install](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/config.plist-per-hardware/coffee-lake) for the config.plist
After following the guide for the vanilla install I was able to do the basics without issue.


### Installation and Fixes
Let's go over some basics.

It is recommended to skip MultiBeast all together and manually install Clover Boot Loader, and find the kexts you need but if you are reading this, then you are already beyond that point. From here on out, it requires that you know your hardware inside and out, so be warned there is no `simple solution` with the install.

#### Fixing the sound
Installed the [AppleALC](https://github.com/acidanthera/AppleALC/releases) kext for Sound
Manually removed the installed kexts from default injected location if you are using Multibeast, sound should now work. <br>
Also by having the AppleALC as an injected kext on boot, it allows you to update the system later without sound breaking again.

#### Fixing sleep
This was as easy as unhooking the Corsair H100i_v2 from the USB header on the mainboard. I still have the header tucked away in the case since I redid the pins for connecting it to the single USB2 port on the mainboard, so the cable for this and the cable for the BCM94360CS2 share the same USB2 header.

#### Fixing iGPU
** Updated **
With the update for MacOS 10.16.5 there was no need to have the framebuffer added. Just enable the iGPU in the bios and because the 9600K is the same chip as the 2019 iMac it loads fine in the OS, and even removed the random video export glitches.


#### Fixing USB
This was annoying. It was not difficult but just annoying. It involved following the instructions from [here](https://hackintosher.com/forums/thread/list-of-hackintosh-usb-port-limit-patches-10-14-updated.467/), [here](https://www.tonymacx86.com/threads/macos-10-14-3-supplemental-update.271209/), and finally [RehabMan again](https://bitbucket.org/RehabMan/os-x-usb-inject-all/overview). After constantly getting different results on reboots, I gave the [Hackintool](https://www.insanelymac.com/forum/topic/335018-hackintool-v204/) a try.

Follow the Hackintool instructions carefully here.

You need to plug and unplug a USB 2.0 device to each the ports and mark the ones you are not using. Then reboot and plug and unplug a USB 3 device into the ports.

You remove the ports that you are not using, and then create the `USBPorts.kext` or the `SSDT-EC.aml`, `SSDT-UIAC.aml`, and the `SSDT-USBX.aml`s that are created. Once you create the aml files, place them in EFI/CLOVER/ACPI/patched. Remember to re-enable all your USB ports, and disable/remove/delete the `inject-all-USB.kext`, and `XHCI-XXX-series-injector.kext` and the `FakePCIID.kext`. Then remove or disable the `USB 10.14.X` fixup Kexts to Patch in clover.
And then restart the machine.<br>  
Your USB should work if you followed the instructions from the Hackintool and have the proper speeds that you set.

Note:<br>
I also have the USB ports set the way that I use them, so keep that in mind before using the kext blindly.

####  The kexts used
I don't know why everyone switched away from using clover/kexts/10.14 to clover/kexts/Other but the world moved on, and so did I.
Kexts and downloads

* AppleALC
* SMCBatteryManager
* SMCLightSensor
* SMCProcessor
* SMCSuperIO
* VirtualSMC
* Lilu
* USBPorts
* WhateverGreen

[All sensor](https://github.com/acidanthera/VirtualSMC) <br>
[AppleALC](https://github.com/acidanthera/AppleALC/releases) <br>
[Lilu](https://github.com/acidanthera/Lilu/releases) <br>
USBPorts - Made for this machine by [Hackintool](https://www.insanelymac.com/forum/topic/335018-hackintool-v204/) <br>
[WhateverGreen](https://github.com/acidanthera/WhateverGreen)<br>

##### drivers64UEFI
This was an area that took a bit more work, it seems settings work differently for everyone. <br>
There is a default `OsxApitoFixDrv-64` installed, and my machine would not boot with it there. So I removed it and installed the [OsxApitoFix2Drv-free2000.efi](https://nickwoodhams.com/x99-hackintosh-osxaptiofixdrv-allocaterelocblock-error-update/) <br>

Also, if there is a memory `AptioMemoryFix-64` installed, it will cause issues booting with the `OsxApitoFix2Drv-free2000`  <br>
There was also a spot where I read that the `OsxApitoFix3Drv` should work since it was based on the free-2000 driver, but I did not have success with that one either.


#### Finding the serial
This part is up to you, the way my system is configured I choose a 18,3 iMac from 2017. There are several ways to generate the serial number, so you are on your own there.

#### iMessages fix
If you are using multiple network devices, and bluetooth counts as one, make sure your primary adapter is registered as `en0`, in my case it is my WIFI adapter. <br>
If it is not registered as `en0` go into System Preferences > Network > and remove all the devices. Then add the one you want to register as your primary as `en0` and restart. Once you have rebooted go back into the Network Settings and add the rest of your devices back. `iMessages` should now work along with the App Store and Continuity and Hand Off
