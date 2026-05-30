# Repository Structure

This repository uses a device-first mono repo layout.

## Why device first?

The physical board is the shared source of truth for pinouts, onboard hardware, flashing behavior, power notes, purchase details, and known quirks. The same device may later support several tech stacks, so device-level facts should not be duplicated under each stack.

## Where things go

| Content | Location |
|---|---|
| Board specs, purchase info, onboard peripherals | `devices/<device>/board.md` |
| Pinout, reserved pins, tested pins | `devices/<device>/pinout.md` |
| Links, docs, datasheets | `devices/<device>/links.md` |
| Known issues, decisions, dated lab notes | `devices/<device>/notes.md` |
| ESPHome configuration for one board | `devices/<device>/esphome/` |
| MicroPython scripts for one board | `devices/<device>/micropython/` |
| Zephyr samples for one board | `devices/<device>/zephyr/` |
| Multi-device builds | `projects/<project>/` |
| Reusable documentation conventions | `docs/` |
| Reusable boilerplate | `templates/` |

## Git tracking of empty folders

Git does not track empty directories. Use `.gitkeep` if a folder should exist before it has content.
