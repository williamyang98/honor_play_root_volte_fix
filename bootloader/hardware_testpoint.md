---
layout: default
title: Hardware testpoint
parent: Unlocking bootloader
nav_order: 0
---

# Hardware testpoint

## 1. What is testpoint mode?
In order for the unlock tool to work it needs to enter a factory testpoint mode. The Honor Play requires physical access to short a testpoint on the mainboard to enter this mode. **Software methods do not work since it uses a Kirin 970**.

This will expose a serial interface via USB which these tools can use to upload factory commands to the phone. Unfortunately the Kirin 970 **does not work with free tools** like [PotatoNV]({{ site.data.links.potato_nv.homepage }}). **Only paid** alternatives like [HCU unlocker]({{ site.data.links.hcu_unlocker.homepage }}) work with this processor.

## 2. Opening phone
1. **Make sure your phone is turned off and unplugged when you start to do this**.
2. Unscrew the two security screws at the bottom of the Honor Play which holds the backcover on.
3. Use your fingernails or a very thin plastic prying tool to pry the backcover off. **Be careful** while you are doing this so you do not accidentally rip off the fingerprint sensor cable or puncture the battery.

![image](/assets/images/honor_play_screws.jpg)

<iframe width="560" height="315" src="https://www.youtube.com/embed/nZR5fKYuEgo?si=pQdmRj6qQ5kE4ky3&amp;start=27" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 3. Grounding testpoint
![image](/assets/images/honor_play_testpoint.jpg)
![image](/assets/images/honor_play_testpoint_zoom.jpg)
1. Identify location of correct testpoint from image.
2. Identify the location of ground (0 volts) where you can short the testpoint. The easiest location to use is the radio frequency shielding identified in the above image.
3. (Optional) Cover the surrounding testpoints with plastic tape to avoid shorting them by accident.

## 4. Activating testpoint mode
1. Use a wire or anything conductive to short that testpoint to ground.
  - I personally used the metal clip holding down the battery connector and connected the stripped end of a breadboard jumper to one of the screws. Then used the unstripped end to short the testpoint.
2. While it is shorted connect your phone via USB to your computer (has to be running Windows to install driver).
3. If it works you should see a unknown device pop up in device manager called ```USB SER``` in ```Other devices```.
4. You can then unshort the testpoint and it should remain in testpoint mode. **Be careful not to let it accidentally short out the rest of your phone**.

## 5. Installing Huawei testpoint driver
### Before driver
![image](/assets/images/huawei_testpoint_before_driver.png)
### After driver
![image](/assets/images/huawei_testpoint_after_driver.png)
1. Install the Huawei testpoint driver on Windows.
    - Driver was downloaded from [DC Unlocker homepage]({{ site.data.links.dc_unlocker.homepage }}) following the HCU unlocker tutorial.
    - [Link (Backup of Driver 1)](/assets/files/huawei_testpoint_driver.zip)
        {% for link in site.data.links.huawei_testpoint_drivers %}
        - [Driver {{ forloop.index }}]({{ link }})
        {% endfor %}
2. You may need to disable memory integrity in Window security if the driver fails to start. It should show a warning if this is necessary. (I do not know if this is safe but I had to do this to get it to work on my computer).
3. Once the driver is installed the phone should show up as a ```Huawei USB COM 1.0``` device under ```Ports (COM & LPT)``` in device manager.
4. (Optional) You may need to reactivate the testpoint mode again by shorting and plugging in the USB cable.
5. (Optional) You may need to restart your computer for the driver to work.
