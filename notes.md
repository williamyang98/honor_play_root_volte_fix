---
layout: default
title: Notes
nav_order: 5
---

# Notes
- [PotatoNV]({{ site.data.links.potato_nv.homepage }}) does not work since the Honor Play has the Kirin 970 which is unsupported.
- [firmwarefile.com]({{ site.data.links.firmware_file.link }}) gives corrupted zip files so it is possibly fake.
- [huaweistockrom.com]({{ site.data.links.huawei_stock_rom.homepage }}) gives a valid zip file and a ```update.app``` file that we can unpack correctly into all of its partitions.
- Huawei made the ```/system``` partition into a ```erofs``` filesystem which is readonly. This complicates alot of things since we cannot simply unlock the bootloader and change ```build.props```.
- The [pixel-volte-patch]({{ site.data.links.pixel_volte_patch.link }}) does not work since it uses api level 29 (aka Android 10). Unfortunately the Honor play only got updates to Android 9.1 which only has api level 28. 
  - [Android 10.0.0_r47](https://github.com/aosp-mirror/platform_frameworks_base/blob/android-10.0.0_r47/telephony/java/android/telephony/CarrierConfigManager.java#L3465)
  - [Android 9.0.0_r61](https://github.com/aosp-mirror/platform_frameworks_base/blob/android-9.0.0_r61/telephony/java/android/telephony/CarrierConfigManager.java#L2327)
  - [pixel-volte-patch](https://github.com/kyujin-cho/pixel-volte-patch/blob/ef16fb05ddc185609872c8903051b74aa4b74e47/app/src/main/java/dev/bluehouse/enablevolte/Moder.kt#L122)
  - This is important because api level 29 added in a hidden api to override the carrier config.
  - If we had Android 10 we can access this api by installing [shizuku]({{ site.data.links.shizuku.link }}) which gives apps the ability to run as ```shell```.
  - ```shell``` is granted to apps by extending the adb ```shell``` session.
