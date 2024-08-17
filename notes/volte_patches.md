---
layout: default
title: VoLTE patches
parent: Notes
nav_order: 2
---

## Volte patchs
- Huawei made the ```/system``` partition into a ```erofs``` filesystem which is readonly. This complicates alot of things since we cannot simply unlock the bootloader and change ```build.props``` for VoLTE.
- The [pixel-volte-patch]({{ site.data.links.pixel_volte_patch.link }}) does not work since it uses api level 29 (aka Android 10). Unfortunately the Honor play only got updates to Android 9.1 which only has api level 28. 
  - [Android 10.0.0_r47](https://github.com/aosp-mirror/platform_frameworks_base/blob/android-10.0.0_r47/telephony/java/android/telephony/CarrierConfigManager.java#L3465)
  - [Android 9.0.0_r61](https://github.com/aosp-mirror/platform_frameworks_base/blob/android-9.0.0_r61/telephony/java/android/telephony/CarrierConfigManager.java#L2327)
  - [pixel-volte-patch](https://github.com/kyujin-cho/pixel-volte-patch/blob/ef16fb05ddc185609872c8903051b74aa4b74e47/app/src/main/java/dev/bluehouse/enablevolte/Moder.kt#L122)
  - This is important because api level 29 added in a hidden api to override the carrier config.
  - If we had Android 10 we can access this api by installing [shizuku]({{ site.data.links.shizuku.link }}) which gives apps the ability to run as ```shell```.
  - ```shell``` is granted to apps by extending the adb ```shell``` session.
- The Magisk module [volte-wifi-calling-enabler]({{ site.data.links.magisk_volte_wifi_calling_enabler }}) does not work since it tries to modify ```build.props``` directly. Unfortunately ```/system``` is behind a read only filesystem.
  - It also might not be working since it doesn't set ```ro.config.hw_volte_dyn``` to false (Manually setting this through ```MagiskHidePropsConf``` gets VoLTE toggle to show up on my phone).

