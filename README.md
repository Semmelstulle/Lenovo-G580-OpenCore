# Lenovo-G580-OpenCore

### Before you give this EFI a try, make sure you read [this](#Generating-your-own-serial-and-Editing-ROM)!

This repo includes an OpenCore EFI for the G580 (Model Type 2189). For anyone having a diffrent model of this machine, we like to hear feedback in the issues page. It will **NOT** work on any of the Pentium models unless you upgrade the CPU to an Ivy Bridge i3 or higher (iX-3xxxM)

Testing on:

Model | G580 Type 2189
------------- | ---------------
CPU | Intel Core i5-3210M
iGPU | Intel HD 4000
dGPU | NVIDIA GT 630M (disabled in BIOS)
RAM | 8 GB DDR3
WiFi | AzureWare CE-123H (BCM94352HMB)
macOS | Big Sur

## What works?

- Audio
- Battery readout
- Boot
- USB
- Ethernet
- GPU acceleration
- Keyboard + Trackpad
- Sleep
- Brightness Control
- Function Keys
- Bluetooth
- Power Management

## What doesn't work?

- SD card slot

## BIOS settings

***Configuration***

* Wireless LAN: Enabled
* SATA Controller Mode: AHCI
* (If using a dGPU model) Graphics Device: UMA Graphic
* Intel Virtual Technology: Enabled

***Security***

* Secure Boot: Disabled

***Boot***

* Boot Mode: UEFI / UEFI + Legacy

## How to install

Download this repo and place the EFI folder into your internal drive's EFI partition... That's it.

## How to Install macOS Big Sur

There are two ways you can make a USB installer:

1. Have a working install of macOS, download the Installer from the App Store, then make a bootable Installer with `createinstallmedia` by using this command in Terminal `sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. If you are using Windows, use [macrecovery.py](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) from the offical OpenCore release package.

After you have created a bootable Installer, copy the EFI folder to the EFI partition of the installer drive and install as usual (GUID Partiton Map; APFS). After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

## Generating your own serial and Editing ROM

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookPro11,1

use PlistEdit Pro or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, and UUID)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

You should also put in your ethernet adapter's MAC address into the ROM section.

## Replacing the WiFi card

To replace the stock unsupported BCM4313 WiFi card, you first have to remove the whitelist from the bios. Here's a tutorial: 

[![IMAGE ALT TEXT](http://img.youtube.com/vi/BItGfpyyHnI/0.jpg)](http://www.youtube.com/watch?v=BItGfpyyHnI "Video Title")

Recommended WiFi cards: Azureware AW-CE123H, Dell DW1550, Lenovo Lite-On WCBN606BH


## Credits

Thanks to:

* me and [SkyrilHD](https://github.com/SkyrilHD) (for making the EFI)
* acidanthera (for making OpenCore and the kexts)
* dortania (helping with their guide)
* USBToolBox (for their excellent USB mapping tool)
* [PewDieMelon](https://github.com/PewDieMelon) (for being our tester)
* [5T33Z0](https://www.hackintosh-forum.de/forum/thread/53009-guide-x86platformplugin-xcpm-f%C3%BCr-ivy-bridge-cpus-unter-catalina-und-big-sur-akti/) (for making the XCPM patch for Ivy Bridge)
