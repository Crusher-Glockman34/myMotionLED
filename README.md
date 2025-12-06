# myMotionLED – Professional-Grade ESP32-S3 LED Controller

**300 individually addressable WS2812B LEDs • Heltec WiFi Kit 32 V3 • Full Web UI • True OTA Updates • Daily Scheduler • Auto DST**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PlatformIO](https://img.shields.io/badge/built%20with-PlatformIO-orange)](https://platformio.org)
[![ESP32-S3](https://img.shields.io/badge/ESP32--S3-240MHz-blue)](https://www.espressif.com)

## Features

- 4 × 75-LED strips (300 total) driven by FastLED on a Heltec WiFi Kit 32 V3
- 14 stunning effects including Rainbow, realistic Fire, StarField, Christmas twinkle, 9-1-1, solid colors, and CycleAll
- Full-featured responsive web interface (mobile-friendly)
- Daily on/off scheduler with 15-minute granularity and automatic DST handling (US rules)
- True Over-The-Air (OTA) firmware updates via ElegantOTA at `/update` (password protected)
- Automatic versioned .bin creation on every build (`myMotionLED_vX.Y.Z_YYYYMMDD-HHMM.bin`)
- Firmware version displayed on main page
- OLED status display with configurable timeout
- WiFi Manager with captive portal + saved credentials
- Safe reboot-after-OTA workflow
- Zero blocking code – rock-solid 24/7 operation

## Hardware

- Heltec WiFi Kit 32 V3 (ESP32-S3)
- 4 × WS2812B LED strips (75 LEDs each) on GPIO 2,3,4,5
- On-board 0.96″ OLED (SSD1306)
- GPIO 0 button (short press = wake OLED, long press = reset WiFi settings)

## Installation / First Boot

1. Flash the firmware using PlatformIO (or the pre-built .bin from Releases)
2. Power on – the device creates a WiFi AP named `myMotionLED_XX`
3. Connect to it, open 10.0.1.1, and configure your home WiFi
4. Device reboots and connects to your network
5. Open the IP shown on the OLED (or find `myMotionLED_XX.local`) in your browser

## Updating Firmware (OTA)

1. Build → a perfectly named .bin appears in the `releases/` folder
2. Open `http://your-device-ip/update`
3. Enter username: admin and Password: admin1234
4. Select **Firmware** mode → upload the .bin
5. Click **Reboot Device** on the main page → new firmware boots instantly

## Screenshots

*(Add these later – they look great on GitHub)*

| Main Control Page | OTA Update Page | Scheduler Active |
|------------------|-----------------|------------------|
| ![Main](screenshots/main.png) | ![OTA](screenshots/ota.png) | ![Scheduler](screenshots/scheduler.png) |

## Building

```bash
# Clone and open in VS Code + PlatformIO
git clone https://github.com/Crusher-Glockman34/myMotionLED.git
code myMotionLED

# Build (creates dated .bin automatically)
pio run

# Upload via USB-C
pio run -t upload

# Upload over the air (after first flash)
pio run -t upload --upload-port <IP_ADDRESS>
