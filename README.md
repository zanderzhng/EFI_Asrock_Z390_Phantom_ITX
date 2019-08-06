# EFI_Asrock_Z390_Phantom_ITX
## Info
### Part List
| Item | Model | Notes |
| --- | --- | --- |
| CPU | Intel i7 8700 |  |
| MB | ASRock Z390 Phantom Gaming-ITX/ac |  |
| WIFI/BLE | DW1820A | Submodule 1028:0023 |
### Kext List
| Purpose | Kext | Notes |
| --- | --- | --- |
| IDK | VirtualSMC.kext | With SMCProcessor.kext and SMCSuperIO.kext |
| IDK | Lilu.kext |  |
| IDK | WhateverGreen.kext |  |
| Audio | AppleALC.kext |  |
| Ethernet | IntelMausiEthernet.kext |  |
| Wi-Fi | AirportBrcmFixup.kext | Wi-Fi work without this actually. The device information will show Thrid Party Card instead. |
| BLE | BrcmBluetoothInjector.kext, BrcmFirmwareData.kext, BrcmPatchRAM2.kext | [credit to nickhx](https://osxlatitude.com/forums/topic/11540-dw1820a-for-7490-help/?do=findComment&comment=92833) |
## Researches

### Wi-Fi

#### Without AirportBrcmFixup.kext

DW1820A's Wi-Fi works OOB, which means you don't have to add any kext nor paraments.

DW1820A's device ID `14e4:43a3` was included in `IO80211Family.kext`, and there's no need to fake it into any card else in Clover's device tab.

Sysinf will show `Third-Party Wireless Card`.

#### With AirportBrcmFixup.kext

Still no need to declare compatible devide ID to any other code.

Sysinf will show `AirPort Extreme  (0x14E4, 0x23)`.

Firmware Version says `  Firmware Version:	Broadcom BCM43xx 1.0 (7.77.61.2 AirPortDriverBrcmNIC-1305.8)`

### Bluetooth

#### Release firmware.

DW1820A's bluetooth module requires [firmware uploading(RAMUSB)](https://github.com/RehabMan/OS-X-BrcmPatchRAM#brcmpatchram).

By shutting down the system ( maybe also disconnect the power supply ), and waiting long enough (likely 20 secs), the uploaded firmware will be released.

If we enter macOS now, without a bluetooth firmware uploader(`BrcmFirmwareData.kext` or `BrcmFirmwareRepo.kext`), the bluetooth won't work, and the [firmware version will be 4096](https://github.com/RehabMan/OS-X-BrcmPatchRAM#troubleshooting), means no firmware was uploaded.

#### Upload firmware

So thanks to [nickhx from osxlatitude](https://osxlatitude.com/forums/topic/11540-dw1820a-for-7490-help/?do=findComment&comment=92833) I finally uploaded the firmware via macOS corectlly. It worked pretty well.

Although RehabMan's repo mentioned you shouldn't combine bluetoothinjector with data nor repo but that seems to be necessary with 10.15 Catalina ( and 10.14 Mojave ).

Anyone interested in the situation where we can't upload firmware via macOS and have to upload it via Windows please refer to previous commit.