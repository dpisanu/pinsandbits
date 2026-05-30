# Generic ESP32-C3 OLED 0.42"

Compact ESP32-C3 development board with onboard 0.42" OLED display, Wi-Fi, Bluetooth LE, USB-C, and a small PCB / ceramic antenna.

This entry documents the specific AliExpress unit purchased for this repository. Online documentation for this board family is inconsistent, especially around the OLED controller and display coordinate mapping.

## Summary

| Property | Value |
|---|---|
| Device | Generic ESP32-C3 OLED 0.42" |
| Folder | `generic_esp32-c3-oled-042` |
| Status | Working with ESPHome using ESP-IDF |

## Current stack status

| Stack | Status | Notes |
|---|---|---|
| ESPHome | Working | Tested with ESPHome and ESP-IDF |
| MicroPython | - | - |
| nanoFramework | - | - |
| Zephyr | - | - |

## Key board observations

- The onboard antenna performs poorly at default / high Wi-Fi output power.
- Online examples disagree about the OLED controller.

See [notes.md](./notes.md) fur further notes on the general aspects of the board.

## References

See [`links.md`](./links.md).

## TODO

- Add front and back photos of the exact board.
- Add visible PCB markings / revision, if present.
- Confirm exact ESP32-C3 chip marking under magnification.
- Confirm exact USB serial / native USB behavior on this unit.
- Add measured display visible area and final preferred coordinate offsets.
