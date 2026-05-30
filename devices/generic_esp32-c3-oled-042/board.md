# Board Information: Generic ESP32-C3 OLED 0.42"

## Identity

| Field | Value |
|---|---|
| Product name | ESP32-C3 OLED 0.42" development board |
| Manufacturer | Generic / unknown |
| Common references | ESP32-C3 OLED 0.42", ESP32-C3 SuperMini OLED, ABRobot ESP32-C3 0.42 OLED |
| Category | Compact ESP32-C3 development board with onboard OLED |
| Repository folder | `devices/generic_esp32-c3-oled-042` |
| Purchased | 2024-11-24 |
| Purchase price | 3.59 EUR |

## Acquisition

| Field | Value |
|---|---|
| Purchase date | 2024-11-24 |
| Purchase price | 3.59 EUR |
| Purchase source | AliExpress product pages listed in [`links.md`](./links.md) |

## Core hardware

| Field | Value |
|---|---|
| MCU | ESP32-C3 / ESP32-C3FN4 or compatible variant |
| CPU | 32-bit RISC-V single-core |
| Max CPU frequency | 160 MHz |
| SRAM | 400 KB class |
| Flash | 4 MB |
| Wireless | 2.4 GHz Wi-Fi, Bluetooth LE / Bluetooth 5 class |
| Antenna | Onboard PCB / ceramic antenna, exact type TBD |
| USB connector | USB Type-C |
| GPIO headers | ? GPIO pins |

## Onboard resources

| Resource | Notes |
|---|---|
| 0.42" OLED display | Physically visible area about 72×40 px |
| OLED controller on this unit | SH1106 128×64 |
| OLED controller memory layout | 128×64 px |
| OLED visible top-left | x=27, y=9 inside the 128×64 controller coordinate space |
| OLED I2C address | `0x3C` |
| OLED I2C SDA | GPIO5 |
| OLED I2C SCL | GPIO6 |
| Onboard blue LED | GPIO8, inverted on this unit |
| BOOT button | Present / used for bootloader mode; exact label may vary |
| RESET button | Present / used for reset; exact label may vary |

## Display summary

This board has a tiny 0.42" OLED. The physically visible window is about 72×40 pixels, but this unit behaves like a **SH1106** display with a 128×64 controller memory layout.

| Item | Value |
|---|---|
| Working display model | SH1106 128×64 |
| I2C address | `0x3C` |
| Physical visible window | about 72×40 px |
| Controller memory layout | 128×64 px |
| Visible top-left | x=27, y=9 |
| Non-working model setting | SSD1306 128×64 |
| Non-working model setting | SSD1306 72×40 |
## Power

| Field | Value |
|---|---|
| Main power | USB-C |
| Header power input | 5 V / VBUS style input likely, exact marking TBD |
| Logic level | 3.3 V |

## Known hardware quirks

### Weak onboard antenna

The onboard antenna is weak in this specific unit. At default or high transmit power the board could not reliably establish or maintain Wi-Fi.

The working setup reduces Wi-Fi output power.

### OLED controller uncertainty

Online documentation and examples disagree about the OLED controller used on this board family.

Reported variants include:

- SSD1306 72×40
- SSD1306-compatible 128×64 with a 72×40 visible window
- SH1106 128×64 / SH1106-compatible variants

This specific unit works as SH1106 128×64 with manual drawing offsets. SSD1306 128×64 and SSD1306 72×40 did not work on this unit.

The visible display area and the controller coordinate space are not the same thing:

| Concept | Value |
|---|---|
| Physical visible OLED area | about 72×40 px |
| Controller memory layout | behaves like 128×64 px |
| Visible top-left in controller coordinates | x=27, y=9 |

A 72×40 display is 72 pixels wide and 40 pixels high. A 128×64 controller canvas is 128 pixels wide and 64 pixels high. On this board, only a small window of that larger canvas is visible.

## Development support

Documents support for these development approaches:

- ESP-IDF

## TODO

- Add measured board dimensions.
- Add board revision / production date if visible on PCB.
- Add high-resolution board photos.
- Add schematic link if available.