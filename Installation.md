# How it was installed

## USB Installation
[Unibeast](https://www.tonymacx86.com/threads/unibeast-install-macos-mojave-on-any-supported-intel-based-pc.259381/#create_unibeast) was used to prep the USB device after downloading Mojave on a Macbook.

After it didn't boot correctly to the install, I started using the [Vanilla Install](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/config.plist-per-hardware/coffee-lake) for the config.plist
After doing the basics within there I was able to boot and install Mojave 10.14.2


### First Installation
The first installation was done to get the kinks worked out and to make sure things like Wi-Fi, Bluetooth, and sound worked.
So let's go over some basics.

Installed MultiBeast, and had issues with that. I was unaware that a few people had issues with MultiBeast in general, but things almost worked when I did it.

MuiltiBeast Non-Working Items (for me):<br>
* Sound
* USB 3.0
* Sleep
* iGPU
* Sensors
* Boot inconsistent  

None of this stuff was the fault of MultiBeast. MultiBeast is a way to make it easier for people to install OS X and it does that well enough.

#### Fixing boot
Initially I had set the iGPU disabled in the bios, and then rebooted till the settings worked.

#### Fixing the sound and sensors
Installed the [AppleACL](https://github.com/acidanthera/AppleALC/releases) kext for Sound and [OS X Fake PCI](https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads/) for the sensors.
Manually removed the installed kexts from default install location. <br>
By having them installed as boot loaded kexts it allows me to update them easier later.

#### Fixing sleep
This was as easy as unhooking the Corsair H100i_v2 from the USB header on the mainboard. I still have the header tucked away in the case since I redid the pins for connecting it to the single USB2 port on the mainboard, so the cable for this and the cable for the BCM94360CS2 share the same USB2 header.

#### Fixing iGPU
This one was a bit harder, after a bunch of reading I finally just copied the settings that were in the config.plist from cmer's build located [here](https://github.com/cmer/gigabyte-z390-aorus-master-hackintosh). The vanilla build steps really did not work for me and would not let me boot half the time. After making the changes everything work and things like Final Cut exports work a 1000x faster.

#### Fixing USB
This was annoying. It was not difficult but just annoying. It involved following the instructions from [here](https://hackintosher.com/forums/thread/list-of-hackintosh-usb-port-limit-patches-10-14-updated.467/), [here](https://www.tonymacx86.com/threads/macos-10-14-3-supplemental-update.271209/), and finally [RehabMan again](https://bitbucket.org/RehabMan/os-x-usb-inject-all/overview). After constantly getting different results on reboots, I gave the [Hackintool](https://www.insanelymac.com/forum/topic/335018-hackintool-v204/) a try. That generated the kexts, and the patch. I tried the patch first and still had issues so I went with the kexts it registered. Your milage may vary. I also kept the RehabMan FakePCI for USB along with the inject-all-USB kexts.

I also have the USB ports set the way that I use them, so keep that in mind before using the kext blindly.

####  The kexts used
I don't know why everyone switched away from using clover/kexts/10.14 to clover/kexts/Other but the world moved on, and so did I.
Kexts and downloads

* AppleACL
* FakePCIID_XHCMux
* FakePCIID
* FakeSMC_ACPISensors
* FakeSMC_CPUSensors
* FakeSMC_CPUSensors
* FakeSMC_LPCSensors
* FakeSMC_SMMSensors
* FakeSMC
* Lilu
* USBPorts
* WhateverGreen
* XHCI-300-series-injector

[All sensor]((https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads/) <br>
[AppleACL](https://github.com/acidanthera/AppleALC/releases) <br>
[FakePCIID](https://bitbucket.org/RehabMan/os-x-fake-pci-id) - For USB <br>
[Lilu](https://github.com/acidanthera/Lilu/releases) <br>
USBPorts - Made for this machine by [Hackintool](https://www.insanelymac.com/forum/topic/335018-hackintool-v204/) <br>
[WhateverGreen](https://github.com/acidanthera/WhateverGreen)<br>
[XHCI-300-series-injector](https://bitbucket.org/RehabMan/os-x-usb-inject-all) <br>

##### drivers64UEFI
These are the default UEFI drivers except for the default `OsxApitoFix` driver. I removed the original one, and I cannot remember the name, and added the [OsxApitoFix2Drv-free2000.efi](https://nickwoodhams.com/x99-hackintosh-osxaptiofixdrv-allocaterelocblock-error-update/) <br>


### Second installation
After getting everything setup from above, I reinstalled and everything worked with the kexts listed below. I have not changed anything from the second install to the third.
I did 3 installs total. First one was 'get everything working' <br>
The second install was 'Prove it works' <br>
The third install was 'this is what i am going with'<br>
During this step is when I did the dance to find a valid serial key, and the final settings for the ability to register the machine. This is important to do if you want to use iMessage/App Store/iTunes/Continuity(Hand Off)/Or the other Apple apps. <br>
It is also important during this step to get your network situated. I have my onboard NIC disabled because I have no plans to use it. With that I had to remove the adapter order to make sure that `en0` was the Wi-Fi card and that `en1` was the Bluetooth. After this step, and I was able to verify that sound, network, video, and overclocks were working correctly.


### The Third Install
After everything was setup in the second step, and the reinstall completed, I have not made any changes to the [clover.plist](Clover_config.plist.md).
I think the only change I made in step 3 was removing all the extra stuff for USB that was no longer needed from the vanilla installer guide.
