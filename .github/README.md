<h1>macOS Monterey/Ventura on Dell Vostro 3000 series using OpenCore</h1>


![Screenshot 2022-12-19 at 21 57 28](https://user-images.githubusercontent.com/90620939/208556688-cc17ed73-a96c-4bec-b3e7-1132ea41a6db.png)
![Screenshot 2022-12-19 at 21 57 56](https://user-images.githubusercontent.com/90620939/208556700-66c91d2d-876d-4b91-a9f9-8f82d83e6ec0.png)




## Important

- This EFI is being worked exclusively for macOS Ventura at the moment, some kext may not work with previous versions.
- This repo has a lot of things specific to my laptop, for example all the ACPI tables. It should work in a identic computer, but maybe it won't.

## Instructions

You **must** add your own serialnumber. I recommend [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS). Remember to use `MacBookPro14,1`. 

Use this a a starting point, this is no replacement of your own research, trial and error.

## Status

<details>  
<summary><strong>✅ What's working</strong></summary>
</br>

- [X] Intel WiFi & Bluetooth
- [X] Brightness / Volume Control
- [X] Battery Information
- [X] Audio (Audio Jack, Speaker & Mic)
- [X] USB Ports & Built-in Camera
- [X] Graphics Acceleration
- [X] Touchpad
- [X] Power management / Sleep
- [X] HDMI / VGA
- [X] SIP / FireVault 2
- [X] SDcard reader
- [X] iServices

</details>
<details>  
<summary><strong>⚠️ What's not working</strong></summary>
</br>

- [ ] Safari/Apple Music DRM ```Use Chrome/Firefox to watch Netflix, etc. For Apple Music you can listen no lossless music and without bluetooth headphones, use Cider instead.```
- [ ] Sidecar Wireless
- [ ] Apple Watch Unlock
- [ ] AirDrop & Continuity

</details>

## Additional info, quirks, findings, etc 

AppleALC layout-ID 13 works but it will make a weird screeching noise when you connect headphones.

When updating your `config.plist`, in order to use VoodooI2C without issues, delete `VoodooInput.kext` from `VoodooPS2Controller.kext/Contents/PlugIns/`.

You can change the laptop screen with a Latitude e7250 1080p ips. I don't have the exact screen model though.

If you use a SSD, force TRIM because it doesn't come enabled by default. It will make your experience so much better. 

You may have a strange bug that Keyboard/trackpad doesn't work, you could use an external keyboard/mouse.

If font looks blurry, apply this command to disable font smoothing `defaults -currentHost write -g AppleFontSmoothing -int 0`


<h2>Laptop Specs</h2>
<table>
  <thead>
    <tr>
      <td style="text-align: center">Feature</td>
      <td style="text-align: center">Specification</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Model</td>
      <td>Dell Vostro 3468</td>
    </tr>
    <tr>
      <td>Processor type</td>
      <td>Intel Core i5-7200U</td>
    </tr>
     <tr>
      <td>VGA</td>
      <td>Intel HD Graphics 620</td>
    </tr>
    <tr>
      <td>Audio</td>
      <td>Realtek ALC256 (layout-id: 21)</td>
    </tr>
    <tr>
    </tr>
  </tbody>
</table>

<details>  
<summary><strong>Changelog</strong></summary>
</br>

## Changelog

##### 02/jun/2023:

Keep up with OC 0.9.2

##### 28/dec/2022:

Happy Xmas :D

XHCI-Unsupported.kext removed

Remapped the USBs because I made a mistake doing it on Windows. Now Bluetooth works perfectly.

##### 21/dec/2022:

FileVault support added

##### 19/dec/2022:
  
New mantainer | Updated to OpenCore 0.8.7

Fixed Bluetooth in Monterey/Ventura.

Fixed SDcard reader.

Fixed Sleep.

Removed CPUfriend.

Fixed Brightness Keys.


##### 08/sep/2021:

Updated to OpenCore 0.7.2

Replaced ACPI files with my own compiled for my specific config. 

Framebuffer: Added missing entries and removed unused patches.

Added CPUfriend, now CPU goes below 1300MHz, this should improve battery life.

##### 06/sep/2021:

Now trackpad works using VoodooI2C, with a lot better experience using touchpad

Updated to OpenCore 0.7.2

Now completely cosmetic, no verbose or debug messages.

OCvalidator shows no errors anymore.

Switch from ugly XOSI to GPI0 for trackpad. 

##### 06/jul/2021:

Updated to OpenCore 0.7.1

Kexts updated

##### 08/jun/2021:

Updated to OpenCore 0.7.0

Kexts updated

Audio headphone jack fixed!  Problem was incorrect layout-id (correct is `layout-id` = `21`)

##### 23/mar/2021:

Updated to OpenCore 0.6.7

Added and updated a ton of kexts.

Big Sur now working (yay)!

Audio now works via `DeviceProperties` -> `Add` -> `PciRoot(0x0)/Pci(0x1F,0x3)`

##### 26/nov/2020: 

Removed: `XHCI-unsupported.kext`because is not needed

Added: `SMCDellSensors.kext`, `SMCProcessor.kext`, `SMCSuperIO.kext`for CPU and fan sensor support

Fixed: Wrong iGPU in `DeviceProperties`

Updated: Sleep and Wake findings

##### 25/nov/2020: 

First release

</details>
