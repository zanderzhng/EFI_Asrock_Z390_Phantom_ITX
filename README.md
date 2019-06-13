# EFI_Asrock_Z390_Phantom_ITX
## Part List
| Item | Model | Notes |
| --- | --- | --- |
| CPU | Intel i7 8700 |  |
| MB | ASRock Z390 Phantom Gaming-ITX/ac |  |
| WIFI/BLE | DW1820A | Submodule 1028:0023 |
## Kext List
| Purpose | Kext | Notes |
| --- | --- | --- |
| IDK but everyone use this | VirtualSMC.kext |  |
| IDK but everyone use this | Lilu.kext |  |
| IDK but everyone use this | WhateverGreen.kext |  |
| Audio | AppleALC.kext |  |
| Ethernet | IntelMausiEthernet.kext |  |
| Wi-Fi | AirportBrcmFixup.kext | WIFI work without this actually. The device information will show Thrid Party Card instead. |
| BLE | BrcmNonPatchRAM2.kext | Modified, check commit history. |
| BLE | BrcmPatchRAM2.kext |  |
