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
| SMC Emulator | VirtualSMC.kext | Emulates an SMC Chip so you can boot your hack, without it... NO HACK FOR YA |
| CPU Temp Reading | SMCProcessor.kext | self explanatory | 
| Fan RPM Reading | SMCSuperIO.kext | self explanatory |
| Plugin Loader | Lilu.kext | Good ol' Lilu, a rootkit basically, mandatory kext |
| GPU | WhateverGreen.kext | Fixes your GPU, so you can use it in macOS, mandatory |
| Audio | AppleALC.kext | Fixes your audio, needs a layout id. |
| Ethernet | IntelMausiEthernet.kext | Good ol' Ethernet, witout it, well... You can't use your hack pretty much. |
| Wi-Fi | None | OOB, since its a native Apple card. |
| Bluetooth | None | OOB, since its a native Apple card. |
## Researches
I switched to this card to see how to fix the problem of auto unlock, which worked once only with my dw1820a, and not working with my oob config with BCM94360CS2 {native Apple card}. 
### Wi-Fi and Bluetooth
This BCM94360CS2 works totally OOB. No kext, no config.plist modification required. [The reason is that this is a native apple card, from a macbook air.]
