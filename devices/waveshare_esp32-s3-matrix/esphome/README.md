# ESPHome: Waveshare ESP32-S3-Matrix

This folder documents the ESPHome setup for the Waveshare ESP32-S3-Matrix board.

## Status

| Field | Value |
|---|---|
| ESPHome | `2026.4.3` |
| ESP-IDF | `5.5.4` |
| Python | `3.14.4` |
| ESPHome board | `esp32-s3-devkitc-1` |
| ESPHome variant | `esp32s3` |
| ESPHome framework | `esp-idf` |
| Flash mode | `dio` via `platformio_options.board_build.flash_mode` |
| Upload method | ESPHome deployment via COM / serial |

## Hardware covered by this config

- Wi-Fi
- Captive portal fallback AP
- Home Assistant API with encryption
- OTA via ESPHome
- OTA via web server
- ESPHome web server v3
- Restart and safe-mode buttons
- Debug sensors
- Wi-Fi diagnostic sensors
- ESP32-S3 internal temperature sensor
- QMI8658 6-axis IMU over I2C
- QMI8658 orientation text sensor
- QMI8658 motion binary sensor
- 8×8 RGB LED matrix via `esp32_rmt_led_strip`
- LED test buttons

## Configurations

The following ESPHome configurations are available:

| Version | File | Notes |
|---|---|---|
| Full | [esp32-s3-matrix_full.yaml](./configs/esp32-s3-matrix_full.yaml) | Full feature YAML with full blown Webserver side |
| Axis | [esp32-s3-matrix_axis.yaml](./configs/esp32-s3-matrix_axis.yaml) | Configuration just showing the 6-Axis sensor |
| LED | [esp32-s3-matrix_LED.yaml](./configs/esp32-s3-matrix_LED.yaml) | Configuration just showing some LED capabilities |

## Required secrets

The config expects the following secrets to exist in ESPHome `secrets.yaml`:

```yaml
wifi_ssid: "..."
wifi_password: "..."
wifi_ap_ssid: "..."
wifi_ap_password: "..."
api_key: "..."
ota_password: "..."
```

## External components

### QMI8658

QMI8658 support currently requires an ESPHome external component.

- Dependency type: external component / sensor driver
- Used for: QMI8658 6-axis IMU
- Typical use: accelerometer, gyroscope, orientation, motion detection, temperature
- Exact implementation and version: documented in the device/project using it

| Component | Source | Status | Notes |
|---|---|---|---|
| `qmi8658` | `github://Djelibeybi/esphome-qmi8658@main` | Working | ESP-IDF-compatible implementation used by the known-good config. Pin to a commit SHA once the setup is stable. |
| `qmi8658` | `github://dala318/esphome-qmi8658` | Not working in this setup | Older Arduino-based implementation caused boot loops in the current environment. |

Current config:

```yaml
external_components:
  - source: github://Djelibeybi/esphome-qmi8658@main
    components: [qmi8658]
    refresh: 5s
```

This device-level file records the currently tested implementation. Project folders may pin a different branch, tag, or commit SHA as the project matures.

## Important ESP32 block

```yaml
esp32:
  board: esp32-s3-devkitc-1
  variant: esp32s3
  framework:
    type: esp-idf
    sdkconfig_options:
      CONFIG_I2C_SKIP_LEGACY_CONFLICT_CHECK: y
```

## Important ESPHome block

```yaml
esphome:
  platformio_options:
    board_build.flash_mode: dio
```

## I2C

```yaml
i2c:
  sda: GPIO11
  scl: GPIO12
  scan: true
```

## QMI8658

```yaml
qmi8658:
  id: imu_sensor
  address: 0x6B
  update_interval: 500ms
  accel_range: 4G
  gyro_range: 512DPS
  accel_odr: 500HZ
  gyro_odr: 500HZ
  rotation: 0
  invert_z: true
```

## LED matrix

⚠️ See [Notes](./../notes.md) regarding LED brightness. ⚠️

This section sets it to 100%

```yaml
light:
  - platform: esp32_rmt_led_strip
    name: "NeoPixel Light"
    id: pixel_matrix
    pin: GPIO14
    num_leds: 64
    chipset: ws2811
    rgb_order: RGB
    color_correct: [100%, 100%, 100%]
    gamma_correct: 1.0
    default_transition_length: 0s
    restore_mode: ALWAYS_OFF
```

## Web server organization

### Full Device Config config

The [esp32-s3-matrix_full.yaml](./esp32-s3-matrix_full.yaml) YAML uses `web_server` sorting groups to organize entities:

- Device Type and System Information
- Device System Statistics
- Device Network Information
- Device Sensory Data
- Device Control
- LED Control

## Known issue:

### Old Arduino example boot loops

The current ESPHome device page [example](https://github.com/esphome/esphome-devices/commit/bf5caf2c4d59dcee119d9294479a8f3313e968ac) is based on:

- framework `arduino`
- `github://dala318/esphome-qmi8658`
- Arduino libraries such as `Wire`, `SPI`, and `SensorLib`

That setup caused boot loops in the current environment. The working setup documented here uses ESP-IDF and `github://Djelibeybi/esphome-qmi8658@main` instead.

## Deployment notes

Typical workflow:

1. Connect board via USB-C.
2. Put the board into download mode if needed: hold BOOT, press/release RESET, then release BOOT.
3. Deploy from ESPHome using the serial COM port.
4. After first flash, OTA updates should work if Wi-Fi and API/OTA are configured correctly.

## Notes

- GPIO10 is listed as `QMI IRQ1` on the ESPHome device page.
- GPIO13 is listed as `QMI IRQ2` on the ESPHome device page.
- The ESPHome device page notes that IRQ1 does not work as well as IRQ2.
- A lot of online documentation recommends GPIO13 instead of GPIO10 as interrupt pin.
- The current ESPHome configuration works with no QMI8658 interrupt pin configured.
   - No `interrupt_pin`, `interrupt_pin_1`, or `interrupt_pin_2` is configured.
- Current ESPHome setup works without setting a QMI8658 interrupt pin.
- Older ESPHome device examples based on the Arduino framework and `dala318/esphome-qmi8658` are not considered known-good for this setup.
- The currently working setup uses `Djelibeybi/esphome-qmi8658` and ESP-IDF.

## TODO

- Add serial flashing command examples for deployment outside of ESPHome Web UI.
- Add screenshots of discovered Home Assistant entities.

## Dependency reproducibility note

This config currently uses `@main` for the QMI8658 external component because that is the working reference tested during setup. 
For a more reproducible project commit, think of forking external component and then pin + record that pin in the relevant project documentation, for example `projects/<project>/dependencies.md`.