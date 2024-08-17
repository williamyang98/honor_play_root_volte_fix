---
layout: default
title: Creating backup images
parent: Notes
nav_order: 3
---

## Creating backup images
1. After unlocking bootloader you can flash a ***semi*** working TWRP written for EMUI 8.0 instead of EMUI 9.1.
  - [twrp_cornell (Backup)]({{ "/assets/files/twrp_cornell-3.2.2.img" | relative_url }})
  - [twrp_cornell (Original)]({{ site.data.links.twrp_cornell.link }})
  - Mounting the ```/system``` and ```/vendor``` partitions doesn't work automatically since the filesystem was changed from ```ext4``` to ```erofs``` between EMUI 8.0 and EMUI 9.1.
  - You can manually mount it via a root shell by running: ```mount -t erofs /dev/block/by-name/system /system```.
  - Building a custom TWRP recovery might be possible but the build environment is very annoying to setup and the custom Honor Play TWRP recovery does not have a github repository which we can fork.
2. Enter a root shell through TWRP by running: ```./adb.exe shell sh``` while booted inside TWRP recovery.
3. Show the mapping between blocks and partition by running: ```ls -la /dev/block/by-name```.
4. For each mapping clone it to your SD card (which should be mounted) using ```dd```.
  - ```dd if=/dev/block/[block] of=/sdcard/[name].img```
  - Avoid cloning ```userdata``` since it is probably going to be larger than the 4GB limit of the FAT32 filesystem used for external SD cards. It might be possible to use ```./adb.exe``` or ```./fastboot.exe``` directly to pull this block if you want to backup your user data.
5. You can write back these images using: ```./fastboot.exe flash [partition_name] [image_name].img```.
- [Link (COR-L29 9.1.0.399 C636E3R1P12)]({{ site.data.links.huawei_stock_rom.our_cloned_link }})
  - Created by me using above method with TWRP and root ADB shell.
- [Link (COR-L29 9.1.0.405 C432E1R1P9T8)]({{ site.data.links.huawei_stock_rom.our_link }})
  - Downloaded from third party website.
  - Requires using [split_image.py]({{ "/assets/files/split_image.py" | relative_url }}) to unpack the ```UPDATE.APP``` file into the component images.

### Block mapping table
Taken from device with COR-L29 9.1.0.399 C636E3R1P12 firmware.

| Name | Block |
| --- | --- |
| bootfail_info | /dev/block/sdd18 |
| cache | /dev/block/sdd58 |
| certification | /dev/block/sdd5 |
| cust | /dev/block/sdd56 |
| ddr_para | /dev/block/sdd15 |
| dfx | /dev/block/sdd20 |
| dto | /dev/block/sdd43 |
| dts | /dev/block/sdd42 |
| eng_system | /dev/block/sdd39 |
| eng_vendor | /dev/block/sdd46 |
| erecovery_kernel | /dev/block/sdd35 |
| erecovery_ramdisk | /dev/block/sdd36 |
| erecovery_vbmeta | /dev/block/sdd48 |
| erecovery_vendor | /dev/block/sdd37 |
| fastboot | /dev/block/sdd28 |
| frp | /dev/block/sdc1 |
| fw_hifi | /dev/block/sdd32 |
| fw_lpm3 | /dev/block/sdd22 |
| hdcp | /dev/block/sdd24 |
| hhee | /dev/block/sdd26 |
| hisee_encos | /dev/block/sdd13 |
| hisee_fs | /dev/block/sdd27 |
| hisee_img | /dev/block/sdd25 |
| isp_boot | /dev/block/sdd30 |
| isp_firmware | /dev/block/sdd31 |
| kernel | /dev/block/sdd38 |
| misc | /dev/block/sdd19 |
| modem_fw | /dev/block/sdd45 |
| modem_om | /dev/block/sdd8 |
| modem_secure | /dev/block/sdd3 |
| modemnvm_backup | /dev/block/sdd10 |
| modemnvm_cust | /dev/block/sdd51 |
| modemnvm_factory | /dev/block/sdd9 |
| modemnvm_img | /dev/block/sdd11 |
| modemnvm_system | /dev/block/sdd12 |
| modemnvm_update | /dev/block/sdd50 |
| nvme | /dev/block/sdd4 |
| odm | /dev/block/sdd57 |
| oeminfo | /dev/block/sdd6 |
| patch | /dev/block/sdd65 |
| persist | /dev/block/sdc2 |
| preas | /dev/block/sdd59 |
| preavs | /dev/block/sdd60 |
| preload | /dev/block/sdd55 |
| prets | /dev/block/sdd63 |
| pretvs | /dev/block/sdd64 |
| product | /dev/block/sdd61 |
| recovery_ramdisk | /dev/block/sdd40 |
| recovery_vbmeta | /dev/block/sdd47 |
| recovery_vendor | /dev/block/sdd41 |
| reserved1 | /dev/block/sdc3 |
| reserved2 | /dev/block/sdd16 |
| reserved3 | /dev/block/sdd23 |
| reserved7 | /dev/block/sdd52 |
| rrecord | /dev/block/sdd21 |
| secure_storage | /dev/block/sdd7 |
| sensorhub | /dev/block/sdd34 |
| splash2 | /dev/block/sdd17 |
| system | /dev/block/sdd62 |
| teeos | /dev/block/sdd33 |
| trustfirmware | /dev/block/sdd44 |
| userdata | /dev/block/sdd66 |
| vbmeta | /dev/block/sdd49 |
| vector | /dev/block/sdd29 |
| vendor | /dev/block/sdd54 |
| veritykey | /dev/block/sdd14 |
| version | /dev/block/sdd53 |
| vrl | /dev/block/sdd1 |
| vrl_backup | /dev/block/sdd2 |

