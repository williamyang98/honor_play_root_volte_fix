---
layout: default
title: (Optional) Patching recovery
parent: Rooting stock image
nav_order: 0
---

# (Optional) Patching recovery
I will be providing the original and patched ```recovery_ramdisk.img``` image.
- [recovery_ramdisk.img]({{ "/assets/files/recovery_ramdisk.img" | relative_url }})
- [recovery_ramdisk_magisk.img]({{ "/assets/files/recovery_ramdisk_magisk.img" | relative_url }})

The ```recovery_ramdisk_magisk.img``` image is the patched output from the following steps.

## 1. Download your stock image
1. Download from [HuaweiStockRom]({{ site.data.links.huawei_stock_rom.homepage }}).
2. Depending on whether or not the free links work or are expired, you may need to pay for a paid link.
  - [Link (Paid by me)]({{ site.data.links.huawei_stock_rom.our_link }})
  - [Original {{ site.data.links.huawei_stock_rom.image_version }}]({{ site.data.links.huawei_stock_rom.image_link }})
  - I was able to use the ```recovery_ramdisk.img``` from a different stock rom version than my own, but your milleage may vary.

## 2. Extracting recovery_ramdisk
![Output folder]({{ "/assets/images/splitu_app.png" | relative_url }})

1. Unzip your downloaded stock image.
2. Find the file ```UPDATE.APP``` which stores all of our partitions.
3. Download the image splitting Python script.
  - [Link (Backup)]({{ "/assets/files/split_image.py" | relative_url }})
  - [Github split_uapp]({{ site.data.links.homepage }})
4. Extract the partition: ```python ./split_image.py ./UPDATE.APP```.
5. Find the ```recovery_ramdisk.img``` image from the ```/output``` folder.

## 3. Patching recovery_ramdisk with Magisk
The following is based on the [following instructions]({{ site.data.links.magisk.instructions }}) from [Magisk]({{ site.data.links.magisk.homepage }}).

![Install]({{ "/assets/images/magisk_install.png" | relative_url }})
![Patch]({{ "/assets/images/magisk_patch.png" | relative_url }})

1. Copy the ```recovery_ramdisk.img``` to your phone.
  - Use USB cable and copy over to internal storage.
  - Or copy to a SD card and insert it into your phone.
2. Download and install Magisk to your phone (doesn't require root to patch image)
  - [Link (Backup)]({{ "/assets/files/Magisk-v27.0.apk" | relative_url }})
  - [Link (Official github)]({{ site.data.links.magisk.download }})
  - Requires you to enable permission to install APKs from external sources.
3. Open the Magisk app.
4. Press the ```Install``` button.
5. Select the ```Select and Patch a File``` option.
6. Browse to where the ```recovery_ramdisk.img``` image is located
7. Wait for the patching to finish.
8. Copy the patched image ```magisk_patched-*.img``` from the ```Downloads``` folder.
  - By default Magisk is configured to save patched images to ```Downloads```.
  - If it isn't present read the text log after patching to determine where it is located.

