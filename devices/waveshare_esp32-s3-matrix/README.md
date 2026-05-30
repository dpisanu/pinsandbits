# Waveshare ESP32-S3-Matrix

Compact ESP32-S3 development board from Waveshare with an onboard 8×8 RGB LED matrix and QMI8658 6-axis IMU. 
This documents the board, known-good ESPHome configuration, pin usage, and known issues discovered while using current ESPHome / ESP-IDF builds.

## Summary

| Property | Value |
|---|---|
| Device | Waveshare ESP32-S3-Matrix |
| Folder | `waveshare_esp32-s3-matrix` |
| Status | Working with ESPHome using ESP-IDF and `Djelibeybi/esphome-qmi8658` |

## Current stack status

| Stack | Status | Notes |
|---|---|---|
| ESPHome | Working | Tested with ESPHome |
| MicroPython | - | - |
| nanoFramework | - | - |
| Zephyr | - | - |

## Safety notes

⚠️ See [LED brightness warning](./notes.md) regarding manufacturer recommendation for LED brightness.

## Open questions / TODO

- Add front and back photos of the specific board revision.
- Add exact board dimensions from measured hardware or official diagram.
- Add schematic if Waveshare publishes one or if it is discovered later.
- Record the exact COM port naming used on the local development machine.
- Confirm whether Bluetooth is used or intentionally disabled in the ESPHome build.

## References

See [`links.md`](./links.md).
