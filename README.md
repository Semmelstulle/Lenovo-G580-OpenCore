# Lenovo-G580-2189-OpenCore


Testing on:

Model | G580 Type 2189
------------- | ---------------
CPU | Intel Core i5-3210M
iGPU | Intel HD 4000
dGPU | NVIDIA GT630M (disabled in BIOS)
RAM | 8 GB DDR3
WiFi | Broadcom BCM4313 (unsupported)
Software | macOS 11.5.1 Big Sur

## What works?

* to be determined

## What doesn't work?

* to be determined

## How to install

Download this repo and place the EFI folder into your internal drive's EFI partition... That's it.

## How to Install macOS Big Sur

There are two ways you can make a USB installer:

1. Have a working install of macOS, download the Installer from the App Store, then make a bootable Installer with `createinstallmedia` by using this command in Terminal `sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. If you are using Windows, use [macrecovery.py](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) from the offical OpenCore release package.

After you have created a bootable Installer, copy the EFI folder to the EFI partition and install as usual. After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

## Generating your own serial and Editing ROM

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookPro11,1

use PlistEdit Pro or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, and UUID)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

You should also put in your ethernet adapter's MAC address into the ROM section.


## Credits

Thanks to:

* me
* acidanthera (for making OpenCore and the kexts)
* dortania (helping with their guide)
* USBToolBox
* and to our tester