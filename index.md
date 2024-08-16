---
layout: default
title: Introduction
nav_order: 0
---
# What is VoLTE
Australia decided to decommision their 3G call services after September 2024 meaning that the Honor Play will no longer be able to make calls even though it has LTE. Instead all phones on their networks requires VoLTE (voice over LTE) in order to make calls. Although the Honor Play physically supports VoLTE and VoWIFI, this is option is not available unless Honor updates the carrier configuration file specific to your carrier.

# Unlocking VoLTE
Fortunately we can enable VoLTE by enabling the VoLTE toggle forcefully. However this will require:
1. Opening up the phone to ground a testpoint on the mainboard.
2. Unlocking the bootloader through a **paid** unlock tool.
3. Patching the stock ```recovery_ramdisk``` partition with Magisk to gain root access.
4. Flashing the patched recovery via ```fastboot```.
5. Downloading ```MagiskHidePropsConf``` module to modify ```build.props``` in a systemless manner.
6. Overriding VoLTE related fields in ```build.props``` with our desired values.

# Disclosure
> **WARNING:** This is a **paid** method to get Volte on your Honor Play from an **unofficial** source. I do not know whether this is a safe method or if the people behind it will do anything malicious to your device. I cannot guarantee that it will enable VoLTE on your phone and I am not responsible for any damage sustained from either the opening of your phone or use of their proprietary bootloader unlocking tool. I can only say that this worked for me and has allowed me to continue using this phone to make calls.
