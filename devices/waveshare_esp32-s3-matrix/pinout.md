# Pinout: Waveshare ESP32-S3-Matrix

## Known onboard pin usage

| Function | ESP32-S3 GPIO | Notes |
|---|---:|---|
| QMI8658 I2C SDA | GPIO11 | - |
| QMI8658 I2C SCL | GPIO12 | - |
| QMI8658 IRQ1 | GPIO10 | - |
| QMI8658 IRQ2 | GPIO13 | often mentioned online as the preferred QMI8658 interrupt pin- |
| 8×8 RGB LED matrix data | GPIO14 | - |
| VCC | VCC | 3.3 V power input |
| GND | GND | Ground |

## Current working I2C configuration

```text
  sda: GPIO11
  scl: GPIO12
```

## Safe / avoid pins

| Category | Pins | Notes |
|---|---|---|
| Known-good onboard I2C | GPIO11, GPIO12 | Used for onboard QMI8658 |
| Known-good LED matrix | GPIO14 | Used for onboard RGB matrix |
| QMI interrupt candidates | GPIO10, GPIO13 | Not required in current working config |
| Pins to avoid | TBD | Add after testing external peripherals |
| Input-only pins | TBD | Add after reviewing ESP32-S3 pin capabilities and board routing |
| Strapping / boot-sensitive pins | TBD | Add board-specific guidance after testing |

## TODO

- Add a full header-by-header pinout table from the Waveshare pinout image.
- Add tested external peripheral examples: UART, SPI, additional I2C devices.
- Add notes for pins that cause boot problems or interfere with onboard hardware.
