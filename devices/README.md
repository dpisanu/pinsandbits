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

| Device | Folder | Status |
|---|---|---|
