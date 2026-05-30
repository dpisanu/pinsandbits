# Board Information: Waveshare ESP32-S3-Matrix

## Identity

| Field | Value |
|---|---|
| Product name | Waveshare ESP32-S3-Matrix |
| SKU | `27119` |
| Part number | `ESP32-S3-Matrix` |
| Manufacturer | Waveshare |
| Category | ESP32-S3 development board with onboard LED matrix and IMU |
| Repository folder | `devices/esp32-s3-matrix` |
| Purchased | 2025-03-21 |
| Purchase price | 16.99 EUR |

## Acquisition

| Field | Value |
|---|---|
| Purchase date | 2025-03-21 |
| Purchase price | 16.99 EUR |
| Purchase source | Amazon Germany product page listed in [`links.md`](./links.md) |

## Core hardware

| Field | Value |
|---|---|
| MCU | ESP32-S3FH4R2 |
| CPU | Xtensa 32-bit LX7 dual-core |
| Max CPU frequency | 240 MHz |
| SRAM | 512 KB |
| ROM | 384 KB |
| RTC SRAM | 16 KB |
| Flash | 4 MB |
| PSRAM | 2 MB |
| Wireless | 2.4 GHz Wi-Fi, Bluetooth LE / Bluetooth 5 LE |
| USB connector | USB Type-C |
| GPIO headers | 17 multi-function GPIO pins |

## Onboard resources

| Resource | Notes |
|---|---|
| 8×8 RGB LED matrix | 64 addressable RGB LEDs |
| LED matrix control pin | GPIO14 |
| QMI8658 / QMI8658C IMU | 3-axis accelerometer + 3-axis gyroscope |
| QMI8658 I2C SDA | GPIO11 |
| QMI8658 I2C SCL | GPIO12 |
| QMI8658 I2C address | `0x6B` in the working ESPHome config |
| QMI8658 IRQ1 | GPIO10 according to ESPHome device page |
| QMI8658 IRQ2 | GPIO13 according to ESPHome device page |
| BOOT button | Hold while resetting to enter download mode |
| RESET button | Resets the board |
| LDO | ME6217C33M5G, 800 mA max according to Waveshare |
| Dout pin | Used for extending the RGB matrix |

## Power

| Field | Value |
|---|---|
| Main power | USB-C |
| Header VCC | 3.3 V according to ESPHome device pinout |
| Logic level | 3.3 V |

## Development support

Waveshare documents support for these development approaches:

- ESP-IDF
- Arduino IDE
- MicroPython

## TODO

- Add measured board dimensions.
- Add board revision / production date if visible on PCB.
- Add high-resolution board photos.
- Add schematic link if available.
