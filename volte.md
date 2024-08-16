---
layout: default
title: Enabling VoLTE
nav_order: 3
---

# Enabling VoLTE

## 1. Install the MagiskHidePropsConf module
![Magisk modules]({{ "/assets/images/magisk_modules.jpg" | relative_url }})

Since our ```/system``` folder is an erofs (enhanced read only file system), we cannot actually modify the ```build.props``` file to update our VoLTE settings. Instead we use this module which will substitute it with an modifiable proxy.

1. Download [MagiskHidePropsConf]({{ site.data.links.magisk_hide_props_conf.homepage }}) module as a zip file
  - [Link (Backup)]({{ "/assets/files/MagiskHidePropsConf-v6.1.2.zip" | relative_url }})
  - [Link (Github)]({{ site.data.links.magisk_hide_props_conf.download }})
2. Open Magisk and click on the ```Modules``` section.
3. Click on ```Install from storage```.
4. Select the ```MagiskHidePropsConf-*.zip``` module and install it.
5. **Reboot phone for module to take effect**.

## 2. Update systemless build.props
1. Enter ADB shell: ```./adb.exe shell sh```.
2. Gain root (superuser) access: ```su```.
3. Grant root permission when Magisk popup appears.
4. Check that we are root (superuser): ```whoami```.
  - If you are root you it should print ```root```.
  - If this didn't work it would print: ```shell```.
5. Set build.props properties using our module: ```props [field] [value]```.
  - Press `y` to confirm setting.
  - Press `n` to avoid reboot since we want to set multiple properties.
  - Refer to the following list of properties for our desired values.
6. After you are done reboot your phone.

| Field | Value |
| --- | --- |
| persist.data.iwlan.enable         | true |
| persist.dbg.ims_volte_enable      | 1 |
| persist.dbg.volte_avail_ovr       | 1 |
| persist.dbg.vt_avail_ovr          | 1 |
| persist.dbg.wfc_avail_ovr         | 1 |
| persist.radio.calls.on.ims        | 1 |
| persist.radio.data_con_rprt       | 1 |
| persist.radio.data_ltd_sys_ind    | 1 |
| persist.radio.rat_on              | combine |
| ro.config.hw_volte_dyn            | false |
| ro.config.hw_volte_icon_rule      | 2 |
| ro.config.hw_volte_on             | true |
| ro.config.hw_volte_show_switch    | true |
| ro.config.hw_vowifi               | true |
| ro.config.hw_vowifi_mmsut         | true |

Taken from the following links:
{% for link in site.data.links.build_props %}
- [Link {{ forloop.index }}]({{ link }})
{% endfor %}

## 3. Enable VoLTE
![Mobile settings]({{ "/assets/images/volte_network_settings.jpg" | relative_url }})
![Mobile settings]({{ "/assets/images/volte_dialer.jpg" | relative_url }})
1. Open ```Settings > Wirless & Networks > Mobile networks```.
2. Toggle the VoLTE option.
3. Perform a test call to confirm that VoLTE is working.
  - The VoLTE logo should also be present in the top left of your phone status bar.
  - Check your call history to see if the VoLTE logo is next to the call.

