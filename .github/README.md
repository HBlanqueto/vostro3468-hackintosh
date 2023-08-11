<h1>Dell Vostro 3468 Hackintosh</h1>

<img src="https://raw.githubusercontent.com/HBlanqueto/vostro3468-hackintosh/main/.github/assets/vostro.png" alt="img" align="right" width="220px">

## Disclaimer

This repo has a lot of things specific to the laptop, use this a a starting point, this is no replacement of your own research, trial and error due to all ACPI tables are exclusively for my current hardware.

> Note
>
> Use `MacBookPro14,1` to generate your own serial with [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).

## Status
### ✅ What's working

- Intel WiFi & Bluetooth
- Brightness / Volume Control
- Battery Information
- Audio (Audio Jack, Speaker & Mic)
- USB Ports & Built-in Camera
- Graphics Acceleration
- Touchpad
- Power management / Sleep
- HDMI / VGA
- SIP / FireVault 2
- SDcard reader
- iServices

### ❌ What's not working

- Safari/Apple Music DRM
- Sidecar Wireless
- Apple Watch Unlock
- AirDrop & Continuity

## Troubleshooting

- AppleALC layout-ID 13 works but it will make a weird screeching noise when you connect headphones.

- When updating your `config.plist`, in order to use VoodooI2C without issues, delete `VoodooInput.kext` from `VoodooPS2Controller.kext/Contents/PlugIns/`.

- You can change the laptop screen with a Latitude e7250 1080p ips. I don't have the exact screen model though.

- If you use a SSD, force TRIM because it doesn't come enabled by default. It will make your experience so much better.

- You may have a strange bug that Keyboard/trackpad doesn't work, you could use an external keyboard/mouse.

- If font looks blurry, apply this command to disable font smoothing `defaults -currentHost write -g AppleFontSmoothing -int 0`