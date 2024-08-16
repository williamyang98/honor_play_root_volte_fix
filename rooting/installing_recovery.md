---
layout: default
title: Installing recovery
parent: Rooting stock image
nav_order: 1
---

# Installing recovery
I will be providing the original and patched ```recovery_ramdisk.img``` image.
- [recovery_ramdisk.img](/assets/files/recovery_ramdisk.img)
- [recovery_ramdisk_magisk.img](/assets/files/recovery_ramdisk_magisk.img)

The ```recovery_ramdisk_magisk.img``` image is the patched output from the following steps.

## 1. Download patched Magisk recovery
1. Download patched Magisk ```recovery_ramdisk_magisk.img``` (or whatever name you changed it to) to your computer where the Android SDK platform tools are located (where adb.exe, fastboot.exe is located).
2. Open a terminal inside that folder.

## 2. Flash patched Magisk recovery
1. Make sure ADB debugging is enabled and the bootloader is unlocked from previous steps. 
2. Reboot your phone into fastboot using: ```./adb.exe reboot bootloader```.
3. Flash your patched Magisk recovery by running: ```./fastboot.exe flash recovery_ramdisk recovery_ramdisk_magisk.img```.
4. Reboot your phone into your system: ```./fastboot.exe reboot```.

## 3. Boot into the patched Magisk recovery
![Successful magisk](/assets/images/magisk_success.jpg)
1. Wait for phone to boot back into system.
2. Reboot your phone into patched rooted Magisk recovery using: ```./adb.exe reboot recovery```.
3. Wait for phone to reboot. It will preset a warning about using an unlocked bootloader.
4. It should look like a regular power on into your login/swipe screen.
5. Unlock phone and check if Magisk has root permissions.
  - If it is rooted then the ```superuser``` and ```modules``` buttons on the bottom navigation bar will not be grayed out.
  - Press on those buttons and they should work and take you to their respective pages.

