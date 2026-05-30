# Dependencies

This repository documents hardware devices, firmware configurations, and embedded software experiments.

Dependencies are documented at two levels:

1. This top-level file lists known dependency families used across the repository.
2. Device and project folders document exact versions, commit SHAs, configuration details, and known-good combinations.

## Dependency policy

External dependencies are not vendored into this repository by default. (See corresponding entry in [NOTICE.md](./NOTICE.md))

Prefer this order:

1. Reference the upstream dependency.
2. Pin to a known-good release, tag, or commit SHA when stability matters.
3. Vendor the dependency only when local patches, offline builds, archival, or upstream instability make it necessary.

## Dependency types

| Type | Description | Where exact versions belong |
|---|---|---|
| Toolchain | Build tools, compilers, SDKs, CLIs | Device or project documentation |
| Framework | Firmware/application framework | Device or project documentation |
| External component | Third-party ESPHome or framework component | Device or project documentation |
| Driver/library | Runtime or firmware library | Device or project documentation |
| Vendor documentation | Datasheets, schematics, pinouts, manuals | Device `links.md` or `datasheets/` |
| Host tooling | Local development tools used on the workstation | `docs/tech-stacks/` or project docs |

## Known dependency families

### ESPHome

[ESPHome](https://esphome.io/) is used for declarative firmware configurations, Home Assistant integration, OTA updates, diagnostics, sensors, and device web interfaces.

- Dependency type: framework / toolchain
- Typical location: `devices/<device>/esphome/`
- Config location: `devices/<device>/esphome/configs/`
- Exact versions: documented inside the relevant device or project

#### ESPHome external components

ESPHome external components are third-party or local components loaded through the `external_components:` section in ESPHome YAML.

- Dependency type: external component
- Typical location: referenced in ESPHome YAML
- Exact source, tag, branch, or commit SHA: documented in the relevant device/project folder
- Vendoring policy: do not vendor by default

### ESP-IDF

[ESP-IDF](https://developer.espressif.com/tags/esp-idf/) is the Espressif IoT Development Framework used directly or through ESPHome when `framework: esp-idf` is selected.

- Dependency type: framework / SDK
- Typical location: referenced from ESPHome configuration
- Exact versions: documented inside the relevant ESPHome device/project documentation

### Arduino framework for ESP32

The [Arduino](https://www.arduino.cc/) framework may be used by some ESPHome configurations or older examples.

- Dependency type: framework
- Status: use only where required
- Exact versions: documented inside the relevant device or project
- Note: some devices may be more stable with ESP-IDF than Arduino

### MicroPython

[MicroPython](https://micropython.org/) is used for Python-based firmware experiments on microcontrollers.

- Dependency type: firmware runtime / language environment
- Typical location: `devices/<device>/micropython/`
- Exact firmware version and flashing notes: documented in the relevant device/project

### .NET nanoFramework

[.NET nanoFramework](https://nanoframework.net/) is used for C#/.NET-based embedded experiments.

- Dependency type: firmware runtime / framework
- Typical location: `devices/<device>/nanoframework/`
- Exact firmware, target, and deployment tool versions: documented in the relevant device/project

### Zephyr

[Zephyr](https://www.zephyrproject.org/) is used for RTOS-based embedded development.

- Dependency type: RTOS / SDK / build system
- Typical location: `devices/<device>/zephyr/`
- Exact Zephyr version, SDK version, board target, and west commands: documented in the relevant device/project

## Vendored dependencies

Vendored dependencies, if any, should live under:

```text
external/vendor/
```

Each vendored dependency should include:

```text
external/vendor/<dependency-name>/
  README.md
  LICENSE
  NOTICE.md
  VERSION.md
```

The `VERSION.md` file should explain:

- upstream repository
- upstream commit/tag/release
- reason for vendoring
- local modifications, if any
- update procedure

## What not to put in this file

Do not put frequently changing per-device details here, such as:

- exact ESPHome versions for one board
- exact ESP-IDF versions for one board
- COM ports
- local Python versions
- project-specific YAML snippets
- external component commit SHAs used by one config
- known-good build combinations for one device
- known-bad implementation notes for one board

Those belong in the relevant device or project folder.

## Related documentation

- [`docs/dependencies/external-components.md`](./docs/dependencies/external-components.md)
- [`docs/tech-stacks/esphome.md`](./docs/tech-stacks/esphome.md)
- `devices/<device>/<tech-stack>/README.md`
- `projects/<project>/README.md`
- `projects/<project>/dependencies.md`
