---
layout: default
title: Fastboot OEM unlock
parent: Unlocking bootloader
nav_order: 2
---

# Fastboot unlock

## 1. Download Android SDK platform tools
- [Link (Backup)](/assets/files/android_sdk_platform_tools.zip)
- Official source of these tools are from the Android SDK website [here]({{ site.data.links.android_sdk_platform_tools.homepage }})

## 2. Enable ADB debugging on your Honor Play
![ADB Debugging](/assets/images/volte_about.jpg)
![ADB Debugging](/assets/images/volte_developer_adb_debugging.jpg)
![ADB Debugging](/assets/images/volte_developer_oem_unlocking.jpg)
1. Go to settings menu.
2. Go to ```About system```.
3. Click multiple times on the ```build version``` until you get a ```developer options``` unlocked message.
4. Go to the ```developer options``` menu and enable ```ADB debugging```.
5. (Optional) Select ```allow ADB debugging in charge mode``` to streamline your experience. (Be sure to disable this afterwards).
6. **Turn on the toggle silder for** ```OEM unlock```. (This must be on).

## 3. Reboot into fastboot
1. Unzip and open a terminal where ```adb.exe``` is located.
2. Reboot your phone into fastboot using: ```./adb.exe reboot bootloader```.
  - If it does not work run: ```./adb.exe devices``` to make sure your device is present in ADB mode.

## 4. Unlock in fastboot mode
![Fastboot image](/assets/images/fastboot_menu.png)
1. Wait for your phone to enter fastboot.
2. Unlock your bootloader by running: ```./fastboot.exe oem unlock [BOOTLOADER_CODE]```.
  - If it does not work run: ```./fastboot.exe devices``` to make sure your device is present in fastboot mode.
3. Reboot your phone by running: ```./fastboot.exe reboot```.

## 5. Confirm that bootloader is unlocked
![Bootloader unlocked](/assets/images/fastboot_unlocked.png)
1. When your phone is starting up you should see the above warning.
2. Either wait or press the power key to boot into your stock system rom.



