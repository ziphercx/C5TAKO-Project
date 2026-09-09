<div align="center">

# C5TAKO™

### Open-Source Wi-Fi & Bluetooth Testing Device

[![License](https://img.shields.io/badge/License-Custom-blue.svg)](LICENSE)
[![Firmware Release](https://img.shields.io/badge/Firmware-Latest-green.svg)](https://github.com/ZipherCyprex/C5TAKO-Project/releases)
[![Documentation](https://img.shields.io/badge/Docs-Online-orange.svg)](https://c5tako.ziphers.space)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-7289da.svg)](https://discord.gg/UXV38s6wAc)

<img src="docs/images/Zipher_c5tako.png" alt="C5TAKO Device" width="400"/>

**Firmware releases and documentation for DIY builders and developers**

</div>

<br>

## 📋 Table of Contents

- [About](#-about)
- [Downloads & Flashing](#-downloads--flashing)
- [Hardware Pinout](#-hardware-pinout)
- [Documentation](#-documentation)
- [Community & Support](#-community--support)
- [Legal Notice](#️-legal-notice)

<br>

## 🎯 About

This repository provides **firmware releases** and **installation tools** for the C5TAKO™ device. 

C5TAKO™ is a portable Wi-Fi (2.4/5 GHz) and Bluetooth LE testing device for security research and penetration testing. This repo is primarily for DIY builders and developers who want to flash firmware or contribute to the project.

> **For end-users**: Full user guides, feature documentation, and tutorials are available at **[c5tako.ziphers.space](https://c5tako.ziphers.space)**

<br>
<br>

## 📦 Downloads & Flashing

### Latest Firmware

### 🌐 Option 1: Firmware Flasher (Easiest)

Use the official web-based flasher - no installation required:

**👉 [Firmware Flasher - Ziphers](https://flash.ziphers.space)**

**Steps:**
1. Visit the flasher website
2. Connect your ESP32-C5 via USB-C
3. Click "Connect" and select your device port
4. The firmware will be flashed automatically

> **Recommended** - This is the fastest and most user-friendly method.

<br>

### 🔧 Option 2: ESP Web Tool

Use [ESP Web Tool](https://espressif.github.io/esptool-js/) for manual flashing:

**Steps:**
1. Download the `.bin` file from releases
2. Open ESP Web Tool in a Chromium-based browser (Chrome, Edge, etc.)
3. Connect your ESP32-C5 via USB-C
4. Click "Connect" and select your device
5. Set flash offset to `0x0`
6. Select the downloaded `.bin` file
7. Click "Program" to flash

<br>

### ⚙️ Option 3: Command Line (esptool)

For advanced users who prefer terminal:

```bash
esptool.py --chip esp32c5 --port COM3 write_flash 0x0 firmware.bin
```

Replace `COM3` with your device's serial port (`/dev/ttyUSB0` on Linux/Mac).

<br>

**Troubleshooting:** If flashing fails, see the [Firmware Update Guide](https://c5tako.ziphers.space/getting-started/update-firmware) or ask for help in our [Discord](https://discord.gg/UXV38s6wAc).

<br>
<br>

## 🔌 Hardware Pinout

### Required MCU: ESP32-C5 Development Board

**Recommended**: XIAO ESP32-C5 or any ESP32-C5 dev board

> **Important**: This firmware is designed specifically for ESP32-C5. Other ESP32 variants are not supported.

> **Hardware profile**: The pinout below is for the C5TAKO XIAO ESP32-C5 build.

<br>

### Pin Assignments

| Interface / Component | Signal | Pin | Notes |
|-----------------------|--------|-----|-------|
| **1.54\" TFT (240x240)** | SCK | GPIO8 | SPI clock |
| | SDA / MOSI | GPIO10 | SPI data to display |
| | RST / RES | EN | Connected to board reset; no separate reset GPIO |
| | DC | GPIO1 | Data / Command |
| | CS | GPIO7 | Chip Select |
| | BLK | GPIO25 | Backlight |
| **SD Card** | SCK | GPIO8 | SPI clock |
| | MOSI | GPIO10 | SPI data to SD card |
| | MISO | GPIO9 | SPI data from SD card |
| | CS | GPIO5 | Chip Select |
| **5-Way Button** | UP | GPIO24 | Active LOW |
| | DOWN | GPIO28 | Active LOW; boot button |
| | LEFT | GPIO23 | Active LOW |
| | RIGHT | GPIO0 | Active LOW |
| | CENTER | GPIO4 | Active LOW |
| **Buzzer / IR Expansion** | IR_BZER | GPIO3 | Shared buzzer and IR transmitter signal |
| **CC1101** | SCK | GPIO8 | SPI clock |
| | MOSI | GPIO10 | SPI data to CC1101 |
| | MISO | GPIO9 | SPI data from CC1101 |
| | CS | GPIO2 | Chip Select |
| | GDO0 | GPIO12 | Interrupt / data output |
| | GDO2 | GPIO11 | Interrupt / data output |
| **Battery Monitor** | BAT_VOLT | GPIO6 | Battery voltage ADC input |
| | BAT_VOLT_EN | GPIO26 | Enables battery voltage measurement |
| **Built-in LED** | Activity LED | GPIO27 | On-board buzzer activity LED; active LOW |

> **TFT wiring**: The firmware configures the display as write-only SPI, so the TFT does not use MISO. GPIO9 MISO is required by the SD card and CC1101 only.

### External Module Board (Planned)

The external module board requires additional connections and may not be included in the current hardware revision. The following modules are reserved for a future board:

| Module | Signal | Pin / Status |
|--------|--------|--------------|
| **GPS** | TX / RX | Pin assignment TBD |
| **CC1101** | SCK | GPIO8 |
| | MOSI | GPIO10 |
| | MISO | GPIO9 |
| | CS | GPIO2 |
| | GDO0 | GPIO12 |
| | GDO2 | GPIO11 |
| **IR transmitter (IRTX)** | IR_BZER | GPIO3; shared with the buzzer |
| **IRTX step-up circuit** | Power | External power circuit; no GPIO assignment |

### Physical Components

- **Display**: 240x240 ST7789 TFT LCD
- **USB-C**: Charging & firmware flashing
- **Power Switch**: ON/OFF toggle
- **5-Way Button**: Navigation control

<br>

> **Warning**: C5TAKO™ is **NOT waterproof**. Avoid moisture and handle with care during assembly.

<br>
<br>

## 🟢 Feature list

### WIFI
- AP Scan
- Station Scan
- Packet Monitor
- PCAP Capture
- PCAP Crack
- Channel Analyzer
- Hidden AP Finder
- Network Map
- Mini Nmap
- Whitelist
- Deauthentication
- Beacon Spam
- Captive Portal

### WIFI Device Detection
- Drone Remote ID
- Pwnagotchi
- Wi-Fi Pineapple
- ESP-NOW
- Wi-Fi Mesh
- Attack Alert
- 7+ more... 

### BLE
- BLE Monitor 
- BLE Inspector 
- Model Finder 
- BLE Spam (Raw+Pkt) 
- Bad BLE
- Ducky Script
- BLE HID Composite
- AirTag Trigger

### BLE Device Detection
- Apple Devices
- AirTag
- Samsung SmartTag
- Tile
- Android Fast Pair
- Flipper
- Pwnagotchi
- Meta Ray-Ban
- Card Skimmer Detection
- 20+ more...

### STORAGE & FILES
- LittleFS
- SD Card
- Web File Manager
- Serial File Transfer
- BLE File Transfer
- PCAP Storage
- Portal Data Storage
- Recovery Password Storage

### SYSTEM
- Display Menu
- USB Serial Commands
- BLE Serial Commands
- Display Stream Buffer 
- Settings
- Battery Monitor

### GAMES
- Dino Game
- Maze Game

<br>
<br>

## 📚 Documentation

Complete user guides, feature documentation, and DIY assembly instructions:

### 👉 **[c5tako.ziphers.space](https://c5tako.ziphers.space)**

<br>

**For DIY Builders:**
- [Serial Protocol Specification](https://c5tako.ziphers.space/developer/serial-protocol)
- [Firmware Update Guide](https://c5tako.ziphers.space/getting-started/update-firmware)
- [Troubleshooting](https://c5tako.ziphers.space/help/troubleshooting)

**For End Users:**
- [Getting Started](https://c5tako.ziphers.space/getting-started/unboxing-and-power)
- [Feature Overview](https://c5tako.ziphers.space/features/menu-overview)
- [WiFi & Bluetooth Guides](https://c5tako.ziphers.space/features/wifi-overview)

<br>
<br>

## 💬 Community & Support

<div align="center">

[![Discord](https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/UXV38s6wAc)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com/ziphers)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtube.com/@ziphers)
[![Facebook](https://img.shields.io/badge/Facebook-1877F2?style=for-the-badge&logo=facebook&logoColor=white)](https://facebook.com/ziphers)

</div>

### Get Help

- **Technical Support** - Join our [Discord Server](https://discord.gg/UXV38s6wAc) (11:00–00:00 GMT+7)
- **Bug Reports** - Open an issue in this repository
- **General Questions** - Visit [ziphers.space](https://www.ziphers.space/)

<br>
<br>

## ⚠️ Legal Notice

C5TAKO™ is designed for **educational purposes, security research, and authorized penetration testing only**.

### Allowed Usage

✅ Testing on your own devices and networks  
✅ Authorized security assessments with written permission  
✅ Educational research in controlled environments

### Prohibited Usage

❌ Unauthorized access to networks or devices  
❌ Malicious attacks or data theft  
❌ Interference with public infrastructure

<br>

> **Warning**: Unauthorized network testing may violate local laws. Users are solely responsible for compliance with applicable regulations. The developers of C5TAKO™ are not liable for misuse of this device.

<br>

**Legal Compliance:**
- Check local laws before testing any wireless network
- Obtain written permission before testing third-party systems
- Use only on networks and devices you own or have authorization to test
- Follow responsible disclosure practices for discovered vulnerabilities

<br>
<br>

<br>
<br>

<div align="center">

### Made with ❤️ by [zipher](https://ziphers.space)

**Other Projects**: [Zipher HID](https://hid.ziphers.space/) • [HERTZ](https://hertz.ziphers.space/)

[🌐 Website](https://www.ziphers.space/) • [📖 Docs](https://c5tako.ziphers.space) • [🔗 Linktree](https://linktr.ee/zipherqr)

<br>

**Star ⭐ this repository if you find it useful!**

</div>
