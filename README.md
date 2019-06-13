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
| IDK | VirtualSMC.kext |  |
| IDK | Lilu.kext |  |
| IDK | WhateverGreen.kext |  |
| Audio | AppleALC.kext |  |
| Ethernet | IntelMausiEthernet.kext |  |
| Wi-Fi | AirportBrcmFixup.kext | Wi-Fi work without this actually. The device information will show Thrid Party Card instead. |
| BLE | BrcmNonPatchRAM2.kext | Modified, check commit history. |
| BLE | BrcmPatchRAM2.kext |  |
## Researches
* ### Wi-Fi
1. #### Without AirportBrcmFixup.kext
DW1820A's Wi-Fi works OOB.
DW1820A's device ID `14e4:43a3` was included in `IO80211Family.kext`, and there's no need to fake it into any card else in Clover's device tab.
Sysinf will show `Third-Party Wireless Card`.
2. #### With AirportBrcmFixup.kext
Still no need to fake devide ID.
Sysinf will show `AirPort Extreme  (0x14E4, 0x23)`.
Firmware Version says `  Firmware Version:	Broadcom BCM43xx 1.0 (7.77.61.2 AirPortDriverBrcmNIC-1305.8)`
* ### Bluetooth
1. #### Release firmware.
DW1820A's bluetooth module requires firmware uploading.
If we disconnect the power supply and motherboard battery, the uploaded firmware will be released.
(It's likely that if we just disconnect the power supply, and wait long enough, the uploaded firmware will be released too.)
If we enter macOS now, without a bluetooth firmware uploader(`BrcmFirmwareData.kext` or `BrcmFirmwareRepo.kext`), the bluetooth won't work, and the [firmware version will be 4096](https://github.com/RehabMan/OS-X-BrcmPatchRAM#troubleshooting).
2. #### Upload firmware via macOS
I havn't firgure out how to upload firmware via macOS correctly.
Using original `BrcmFirmwareData.kext` or `BrcmFirmwareRepo.kext`, I did see the bluetooth changed into version 5799 ( meaning firmware was uploaded ), but bluetooth won't work. It's hard to connect to bluetooth devices, and devices will keep disconnecting.
I thought it might be the firmware in the original kext being too old, so I tried recompiled the kext with newest firmware extracted from newest driver. The version changed into 4689, but still bluetooth was not working correctly.
And if I reboot into windows after this incorrect uploading, the device manager will told me that DW1820A was not correctly configured. I have to release the firmware by disconnecting the power supplys.
3. #### Upload firmware via Windows
I must release the firmware first, or the card will enter a weird condition, as I mentioned above.
Currently I'm uploading the firmware with `Windows`, firmware version 4689.
After uploading, rebooting into macOS with `BrcmNonPatchRAM2.kext` and `BrcmPatchRAM2.kext`, the bluetooth will work.
Someone mentioned he could upload the firmware via `Windows in virtual machine`. That should be able to save some rebooting.