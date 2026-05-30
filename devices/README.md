# Devices

Device folders are the primary source of truth for hardware-specific information.

Each device should have:

```text
<device-folder>/
  README.md       # overview and current status
  board.md        # hardware identity, specs, purchase information
  pinout.md       # pin usage, safe pins, reserved pins, tested buses
  links.md        # product pages, docs, datasheets, source references
  notes.md        # lab notes, known issues, decisions, experiments
  photos/         # local photos, if safe to publish
  datasheets/     # local datasheets, only when redistribution is allowed
  <tech-stack>/   # ESPHome, MicroPython, nanoFramework, Zephyr, etc.
```

## Device index

| Device | MCU / Module | ESPHome | MicroPython | nanoFramework | Zephyr | Notes |
|---|---|---:|---:|---:|---:|---|
| [Waveshare ESP32-S3-Matrix](./waveshare_esp32-s3-matrix/README.md) | ESP32-S3FH4R2 | ✅ | — | — | — | 8×8 RGB LED matrix, QMI8658 IMU |
| [generic ESP32-S3-OLED](./generic_esp32-c3-oled-042/README.md) | ESP32-C3FN4 | ✅ | — | — | — | 0,42 inch OLED display |

Legend: ✅ working, ⚠️ partial/experimental, ❌ not working, — not documented yet.