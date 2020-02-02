# ASUS A556U (X556UQ) - Hackintosh Mojave 10.14.6

---

### Screenshot

---

![](Screenshot/Screen%20Shot%202020-02-01%20at%2001.09.34.png)

![](Screenshot/Screen%20Shot%202020-02-01%20at%2001.10.23.png)

![](Screenshot/Screen%20Shot%202020-02-01%20at%2001.15.49.png)

![](Screenshot/Screen%20Shot%202020-02-01%20at%2001.16.55.png)

![](Screenshot/Screen%20Shot%202020-02-01%20at%2001.18.23.png)

### Technical Specifications

---

| Name              | Specifications                                                                                                                           |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Processor         | Intel Core i5 - 6200U                                                                                                                    |
| Memory            | 1x 4 GB DDR4 2133 Mhz + 1x 8 GB DDR4 2133 Mhz                                                                                            |
| Storage           | SSD M.2 SATA Silicon Power 240 GB                                                                                                        |
| Video             | Integrated Intel HD 520 + NVIDIA 940MX                                                                                                   |
| Wi-Fi + Bluetooh  | Qualcomm Atheros 9565                                                                                                                    |
| Ethernet          | Realtek RTL8111                                                                                                                          |
| Audio             | Realtek ALC255                                                                                                                           |
| Touchpad          | ELAN 1000 I2C Interface                                                                                                                  |
| Screen Size       | 15,6 Inch                                                                                                                                |
| Screen Resolution | 1920 x 1080                                                                                                                              |
| Others            | 1x Card Reader, 1x WebCam, 1x VGA Port, 1x HDMI, 1x Combo Audio Jack, 1x USB 2.0, 1x USB 3.0 Type A, 1x USB 3.0 Type C, 1x Optical Drive |

### What Works Well

---

✅ Intel HD 520 (With QE/CI)

✅ All USB Port

✅ VGA Port

✅ Keyboard

✅ Touchpad

✅ Onboard Ethernet

✅ Wi-Fi

✅ Webcam

✅ Battery Status

✅ FN Keys (Almost all key working)

✅ Native Power Management

✅ Optical Drive

### What Works (with Notes)

---

⚠️ Audio (Internal mic work but not auto switchable)

⚠️ Bluetooth (Boot to Windows/Linux/VM to load firmware)

⚠️ Restart, Sleep, Shutdown (Sleep with Apple Logo Menu and FN + F1 works fine, but on close and open LID the screen is turned off but the laptop engine and LED indicator are still on and when wake up its open login screen again)

### Does Not Work

---

❌ NVIDIA 940MX (Optimus - impossible to get working at the moment)

❌ iMessage (TODO fix)

❌ FaceTime (TODO fix)

### Not Tested

---

1. SD Card Reader

2. HDMI

### Kexts List

---

- **CLOVER/Kext/Other**
  
  [Lilu](https://github.com/acidanthera/Lilu)
  
  [AppleALC](https://github.com/acidanthera/AppleALC)
  
  [AsusSMC (Need Patch DSDT/SSDT)](https://github.com/hieplpvip/AsusSMC)
  
  [CPUFriend](https://github.com/acidanthera/CPUFriend)
  
  [HibernationFixup](https://github.com/acidanthera/HibernationFixup)
  
  NoTouchID
  
  [RealtekRTL8111](https://bitbucket.org/RehabMan/os-x-realtek-network/downloads/)
  
  [RTCMemoryFixup](https://github.com/acidanthera/RTCMemoryFixup)
  
  [USBInjectAll (Need Patch DDST/SSDT)](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)
  
  [VirtualSMC + All Plugins](https://github.com/acidanthera/VirtualSMC)
  
  [VoodooPS2Controller](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/)
  
  [WhateverGreen](https://github.com/acidanthera/WhateverGreen)

- **Library/Extensions**
  
  [VoodooI2C + VoodooI2CELAN (Need GPIO Pinning)](https://github.com/alexandred/VoodooI2C)

- **System/Library/Extensions (Backup original file first)**
  
  IO80211Family.kext (For ATH9565)
  
  corecrypto.kext
  
  corecapture.kext

### SSDT/DSDT Patches

---

- [syn] Rename _DSM methods to XSDM

- [audio] Audio Layout 27 (edited from other audio patch)

- [bat] ASUS N55SL/VivoBook

- [igpu] Brightness fix

- [usb] USB3 _PRW 0x0D Skylake (instant wake)

- [sys] SMBUS Fix

- [sys] IRQ Fix

- [sys] HPET Fix

- [sys] Fix Mutex with non-zero SyncLevel

### Additional DSDT/SSDT Patches for kext and other fix

- VoodooI2C + VoodooI2CELAN
  
  [Follow this tutorial](https://voodooi2c.github.io/#Installation/Installation)

- AsusSMC
  
  [Follow this tutorial](https://github.com/hieplpvip/AsusSMC/wiki/Installation-Instruction)

- Disable DGPU
  
  [Follow this tutorial](https://www.insanelymac.com/forum/topic/295584-disabling-nvidia-optimus-card-on-all-laptops/)

- USBInjectAll
  
  [Follow hackintool USB Port Patching](https://www.tonymacx86.com/threads/release-hackintool-v2-8-6.254559/)

### Credits

Thanks to everyone who made this possibile: RehabMan, alexandred, black-dragon74, Mieze, acidanthera, every contributor to the repos/guides and the whole Hackintosh community.
