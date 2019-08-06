# EFI_Asrock_Z390_Phantom_ITX
## Info
### Part List
| Item | Model | Notes |
| --- | --- | --- |
| CPU | Intel i7 8700 |  |
| MB | ASRock Z390 Phantom Gaming-ITX/ac |  |
| WIFI/BLE | BCM94360CS2 |  |
### Kext List
| Purpose | Kext | Notes |
| --- | --- | --- |
| IDK | VirtualSMC.kext | With SMCProcessor.kext and SMCSuperIO.kext |
| IDK | Lilu.kext |  |
| IDK | WhateverGreen.kext |  |
| Audio | AppleALC.kext |  |
| Ethernet | IntelMausiEthernet.kext |  |
| Wi-Fi |  | OOB |
| BLE |  | OOB |
## Researches
I switched to this card to see how to fix the problem of auto unlock, which worked once only with my dw1820a, and not working with my oob config with BCM94360CS2.
### Wi-Fi and Bluetooth
This BCM94360CS2 works totally OOB. No kext, no config.plist modification required.
