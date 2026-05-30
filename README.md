# Pins and Bits

A mono repository for documenting microcontroller boards, firmware stacks, working configurations, experiments, and (finished) embedded projects.

The repository is organized around **devices first**, because the physical board is the common source of truth for pinouts, boot behavior, onboard peripherals, purchase notes, datasheets, and quirks. Tech stacks live inside each device folder when they have been tested on that device.
* [ ] [ESPHome](https://esphome.io/)
* [ ] [MicroPython](https://micropython.org/)
* [ ] [.NET nanoFramework](https://nanoframework.net/)
* [ ] [Zephyr](https://www.zephyrproject.org/)

## Current devices

| Device | MCU / Module | ESPHome | MicroPython | nanoFramework | Zephyr | Notes |
|---|---|---:|---:|---:|---:|---|
| [Waveshare ESP32-S3-Matrix](./devices/esp32-s3-matrix/) | ESP32-S3FH4R2 | ✅ | — | — | — | 8×8 RGB LED matrix, QMI8658 IMU |

Legend: ✅ working, ⚠️ partial/experimental, ❌ not working, — not documented yet.

## Repository layout

```text
hardware-lab/
  README.md
  LICENSE
  NOTICE.md
  DEPENDENCIES.md

  devices/
    README.md
    <device-folder>/
      README.md
      board.md
      pinout.md
      links.md
      notes.md
      photos/
      datasheets/
      <tech-stack>/
        README.md
        configs/
        projects/

  projects/
    README.md
    <project-folder>/
      README.md
      wiring.md
      bill-of-materials.md
      devices/

  docs/
    README.md
    conventions.md
    repo-structure.md
    secrets.md
    troubleshooting.md
    flashing/
    tech-stacks/
    dependencies/

  templates/
    device/
    project/
    tech-stack/
    esphome/

  external/
    README.md
```

## Documentation principles

1. Prefer documented, repeatable, known-good configurations over vague notes.
2. Keep secrets out of Git.
3. Pin external dependencies when possible.
4. Mark unverified facts as `TBD`.
5. Put board-level facts in `devices/<device>/`.
6. Put multi-device builds in `projects/<project>/`.
7. Keep external code out of this repository unless vendoring is intentional and license-compatible.