# Pinout: Generic ESP32-C3 OLED 0.42"

## Known onboard pin usage

| Function | ESP32-C3 GPIO | Notes |
|---|---:|---|
| OLED I2C SDA | GPIO5 | Working on this unit |
| OLED I2C SCL | GPIO6 | Working on this unit |
| OLED I2C address | `0x3C` | Working on this unit |
| Onboard blue LED | GPIO8 | Inverted on this unit |
| BOOT button | GPIO9 | Reported by several community references; confirm on this unit |
| UART RX | GPIO20 | Commonly reported UART0 RX |
| UART TX | GPIO21 | Commonly reported UART0 TX |
| GND | GND | Ground |
| 3V3 | 3V3 | 3.3 V output / logic reference |
| 5V / VBUS | 5V | Power input, exact board marking TBD |

## Current working I2C configuration

```text
sda: GPIO5
scl: GPIO6
address: 0x3C
frequency: 400kHz
```

## Safe / avoid pins

| Category | Pins | Notes |
|---|---|---|
| Known-good OLED I2C | GPIO5, GPIO6 | Reserved by onboard OLED on this unit |
| Onboard LED | GPIO8 | Also produces strapping-pin warnings during compile; avoid for external use |
| Boot / strapping-sensitive | GPIO8, GPIO9 | Use with caution; GPIO9 is commonly BOOT |
| UART candidate pins | GPIO20, GPIO21 | Commonly reported UART pins |
| External GPIOs | TBD | Add after testing external peripherals |
| Pins to avoid | GPIO5, GPIO6, GPIO8, GPIO9 | Avoid unless intentionally using onboard OLED, LED, or boot button behavior |

## TODO

- Add a full header-by-header pinout table from a verified board photo.
- Confirm BOOT button GPIO on this specific unit.
- Test free GPIO pins with a simple LED or logic probe.
- Record which pins interfere with boot, USB, Wi-Fi, or OLED operation.
