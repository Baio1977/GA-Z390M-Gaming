## Computer Configuration
Component | Brank
-|-
CPU | Intel i7 8700
MotherBoard | Gigabyte Z390M Gaming
Memory | Corsair Vengeance 32gb DDR4 3200
Graphic Card | Sapphire RX 5700XT Nitro+
SSD | Samsung 970 Pro 512gb
Net Card | BCM94360CD + BT
Power | Corsair RM 750x
Case | Banchetto 

## What's working?
- Both iGPU and eGPU are working fine.
- **NATIVE NVRAM** is working!
- BlueTooth and Wi-Fi are working fine, because of I brought it on purpose.
- USBs are working fine, I patch it with `USBPorts.kext`, thanks to hackintool.
- Sleep is fine, thanks to Gigabyte Z390M Gaming, it really saved my time.

## BIOS F9k Beta Changes

- Save & Exit
    - Load Optimized Defaults then make (or confirm) the following settings -- important settings in **bold**:
- M.I.T.
    - Extreme Memory Profile (X.M.P.) → **Profile 1**
- BIOS
    - Windows 8/10 Features → **Other OS**
    - CSM Support → **Disable**
        - Secure Boot will be disabled by default, but good to check
- Peripherals
    - Initial Display Output → PCIe Slot 1. If your discrete graphics card is in Slot 2, change this appropriately.
    - Intel Platform Trust Technology (PTT) → Disabled
    - Thunderbolt(TM) Configuration
        - TBT Vt-d Base Security → **Disabled**
        - Thunderbolt Boot Support → **Disabled**
        - Security Level → **No Security**
    - USB Configuration
        - Legacy USB Support → Enabled
        - XHCI Hand-off → **Enabled**
    - Network Stack Configuration
        - Network Stack → **Disabled**
- Chipset
    - Vt-d → **Enable**
    - Internal Graphics → **Enabled**
    - DVMT Pre-Alloc → 128M
    - DVMT Total Gfx Mem → MAX
    - Audio Controller → **Enabled**
    - Above 4G Decoding → **Enabled**
- Power
    - ErP → Disabled
    - RC6 (Render Standby) → Enabled
    
# Patch IGPU HDMI\DVI Output

These are the device properties to configure the iGPU as display output:
```
                <key>PciRoot(0x0)/Pci(0x2,0x0)</key>
                <dict>
                    <key>AAPL,GfxYTile</key>
                    <data>AQAAAA==</data>
                    <key>AAPL,ig-platform-id</key>
                    <data>BwCbPg==</data>
                    <key>device-id</key>
                    <data>mz4AAA==</data>
                    <key>device_type</key>
                    <string>Display controller</string>
                    <key>framebuffer-con0-busid</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-con0-enable</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-con0-flags</key>
                    <data>xwMAAA==</data>
                    <key>framebuffer-con0-index</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-con0-pipe</key>
                    <data>CQAAAA==</data>
                    <key>framebuffer-con0-type</key>
                    <data>AAQAAA==</data>
                    <key>framebuffer-con1-busid</key>
                    <data>AgAAAA==</data>
                    <key>framebuffer-con1-enable</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-con1-flags</key>
                    <data>xwMAAA==</data>
                    <key>framebuffer-con1-index</key>
                    <data>AgAAAA==</data>
                    <key>framebuffer-con1-pipe</key>
                    <data>CAAAAA==</data>
                    <key>framebuffer-con1-type</key>
                    <data>AAgAAA==</data>
                    <key>framebuffer-con2-busid</key>
                    <data>BAAAAA==</data>
                    <key>framebuffer-con2-enable</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-con2-flags</key>
                    <data>xwMAAA==</data>
                    <key>framebuffer-con2-index</key>
                    <data>AwAAAA==</data>
                    <key>framebuffer-con2-pipe</key>
                    <data>CgAAAA==</data>
                    <key>framebuffer-con2-type</key>
                    <data>AAgAAA==</data>
                    <key>framebuffer-con3-busid</key>
                    <data>AAAAAA==</data>
                    <key>framebuffer-con3-enable</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-con3-flags</key>
                    <data>IAAAAA==</data>
                    <key>framebuffer-con3-index</key>
                    <data>/////w==</data>
                    <key>framebuffer-con3-pipe</key>
                    <data>AAAAAA==</data>
                    <key>framebuffer-con3-type</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-fbmem</key>
                    <data>AAAAAA==</data>
                    <key>framebuffer-patch-enable</key>
                    <data>AQAAAA==</data>
                    <key>framebuffer-stolenmem</key>
                    <data>AACQAw==</data>
                    <key>model</key>
                    <string>Intel UHD Graphics 630</string>
                </dict>
```
And these are the device properties to setup the iGPU as computing only:
```
<key>PciRoot(0x0)/Pci(0x2,0x0)</key>
<dict>
    <key>AAPL,ig-platform-id</key>
    <data>AwDImw==</data>
    <key>AAPL,slot-name</key>
    <string>Internal@0,2,0</string>
    <key>device-id</key>
    <data>yJsAAA==</data>
    <key>device_type</key>
    <string>VGA compatible controller</string>
    <key>model</key>
    <string>Intel CoffeeLake-H GT2 [UHD Graphics 630]</string>
</dict>
```
## Credits

- [Acidanthera](https://github.com/acidanthera) for OpenCore and all the lovely hackintosh work.
- [Apple](https://apple.com) for macOS;
- [daliansky](https://github.com/daliansky)
- [Dortania](https://github.com/dortania)
- [Hackintoshlifeit](https://github.com/Hackintoshlifeit)
- [rehabman](https://github.com/RehabMan)

# If you need help please contact us on [Telegram](https://t.me/HackintoshLife_it) or [Web](https://www.hackintoshlife.it/)
