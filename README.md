  

# Asus A556U (X556UQ) - Mojave Hackintosh

  
⚠️ **Unmaintained, as I don't have this laptop anymore.**

Forks are welcome.
  

## Specs

  

  

Processor | Intel Core i5-6200U CPU (SkyLake)

  

  

Video | Integrated Intel HD 520 + Nvidia GTX 940MX

  

  

Memory | 12 GB DDR4 2133 Mhz 

  

  

Storage | Silicon Power 256 GB SSD

  

  

Connectivity | Wireless AC Atheros ATH9565 / QCA 9565 Bluetooth, RTL8111/8168/8411 PCI Express Gigabit Ethernet, Bluetooth 4.0

  

  

Audio | Realtek ALC255

  

  

Ports | 1x USB 2.0, 1x USB 3.0, 1x USB 3.1, HDMI, COMBO audio jack, SD card reader, LAN, VGA Port

  

  

TouchPad | Elan Touchpad (ELAN1000)

  

  

# What works

  

  

✅ Intel HD 520 (with QE/CI)

  

  

  

✅ VGA/HDMI (Audio + Video)

  

  

  

✅ All USB Type A ports

  

  

  

✅ USB type C port

  

  

  

✅ Keyboard

  

  

  

✅ Touchpad with all gesture provided by Voodooi2C

  

  

  

✅ Internal screen backlight change

  

  

  

✅ Onboard Ethernet

  

  

  

✅ Wi-Fi

  

  

  

✅ UVC HD Webcam

  

  

  

⚠️ Speaker + Headphone jack (auto detection) but internal microphone and headphone microphone (manual switch)

  

  

  

✅ Laptop lid

  

  

  

✅ Native power managment

  

  

  

✅ Battery status

  

  

✅ ️Sleep (takes a bit for going completely into sleep mode, but it works!)

  

  

⚠️ Bluetooth (Boot to Windows/Linux/VM to load firmware)

  

  

⚠️ FN Keys (brightness and volume control works - FN+F9 for disabling the touchpad does not work, sleep with FN+F1 crashes the system)

  

  

  

❌ Realtek SD card reader

  

  

  

❌ NVIDIA GeForce 940MX (Optimus - impossible to get working at the moment)

  

  

# BIOS/Firmware
**After my long testing I have concluded that the version 313 works just fine for this hackintosh.**

Versions 314 and 315 **DO NOT WORK**. 
There are some strange unknown problems with the Intel graphics card.

If you upgraded the BIOS, or Windows Update did that for you, **you should downgrade** or you might encounter some strange problems.

You can find the 313 version it in this repository (BIOS folder) or on the [ASUS website](https://www.asus.com/supportonly/F556UQ/HelpDesk_BIOS/)

**WARNING**: Please **make sure** that your computer model is **X556UQK (F556U)** **BEFORE** flashing the BIOS. 
If something goes wrong it's not my fault.

# Kexts list

  

  

#### Install into your CLOVER/kext/Other folder:

  

  

[Lilu](https://github.com/acidanthera/Lilu)

  

  

  

[RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X)

  

[WhateverGreen](https://github.com/acidanthera/WhateverGreen)  

  

[VirtualSMC](https://github.com/acidanthera/VirtualSMC)

  

  

  

[AppleALC](https://github.com/acidanthera/AppleALC)

  

  

[ATH9KFixup.kext](https://github.com/black-dragon74/ATH9KFixup)

  
  

[CPUFriend](https://github.com/acidanthera/CPUFriend)

  
  
  
[HibernationFixup](https://github.com/acidanthera/HibernationFixup)




[VoodooPS2Controller](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/)


#### Install in /Library/Extensions:

  

  

[VoodooI2C + VoodooI2CELAN (Need Patch DSDT)](https://github.com/alexandred/VoodooI2C)


  

  

#### Install in /System/Library/Extensions (Backup original file first):

[ATH9KInjector.kext](https://github.com/black-dragon74/ATH9KFixup)



[IO80211Family.kext]()

[corecrypto.kext]()

[corecapture.kext]()


## DSDT/SSDT patches

**DO NOT ASK** or **ATTEMPT** to use existing AML files. DSDT and SSDT tables can be different even on the same model.


[Extract your DSDT/SSDTs](https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/), modify the files as needed, compile and save your new AML files into CLOVER/ACPI/patched.

You could also check out check out CLOVER/ACPI/**patched_dsl** for working examples.
**hint**: use **diff** for finding out the main differences.

  
### Required patches (applied with MaciASL):

  

**_RehabMan Laptop Repo**

  

  

-  [syn] Fix PARSEOP_ZERO Error (aggressive)

  

  

-  [bat] ASUS N55SL-Vivobook

  

  

  

**_VoodooI2C-Patches Repo**

  

  

- Windows 10 Patch

  

  

  

- "custom made patch" (check out Scope (_SB.PCI0.I2C1) - Device (**ETPD**) from the DSL example)

  

  

## And now?
After creating the proper DSDT file everything should work out of the box using the Clover **config.plist** available here in the repo.

If you want to know what are the modifications needed for making everything function you can check the "i know what I'm doing section" :)

#### i know what I'm doing 
-  *AUDIO*: Clover ACPI Fixes (FixHPET, FixIPIC, FixRTC, FixTMR) and layout-id 27.

- *BRIGHTNESS*: ACPI->AddPNLF, Devices->SetIntelBacklight and SetIntelMaxBacklight

- *Wi-FI*: "-ath9565" as boot flag

-  *TOUCHPAD*: DSDT custom patch (0x55 pinout) along with dynamic KextPatch for disabling AppleIntelLpsss

  

# Credits

  

  

Thanks to everyone who made this possibile: RehabMan, alexandred, black-dragon74, Mieze, acidanthera, every contributor to the repos/guides and the whole Hackintosh community.
