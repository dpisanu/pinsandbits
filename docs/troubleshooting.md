# Troubleshooting

## Board does not appear as a serial port

* Try another USB-C cable as some cables are power-only.
* Try another USB port.
* Check whether a USB serial driver is required.
* Press RESET.
* Enter bootloader/download mode manually.

## ESP32 manual bootloader mode

Typical flow:

1. Hold BOOT.
2. Press and release RESET / EN.
3. Release BOOT.
4. Start flashing.

## ESPHome build succeeds but device boot loops

Record:

* ESPHome version
* ESP-IDF or Arduino framework version
* Board type and variant
* External components and commit/version
* Last known-good config
* Serial logs if available

Then compare against the device-specific `notes.md`.

## I2C device not found

* Confirm SDA/SCL pins.
* Enable `scan: true` temporarily.
* Confirm pull-ups if using external devices.
* Confirm the device address.
* Check whether ESP-IDF needs additional `sdkconfig_options`.
