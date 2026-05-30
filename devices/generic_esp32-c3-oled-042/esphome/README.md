# ESPHome: Generic ESP32-C3 OLED 0.42"

This folder documents the ESPHome setup for the generic ESP32-C3 OLED 0.42" board.

## Status

| Field | Value |
|---|---|
| ESPHome | `2026.4.3` |
| ESP-IDF | `5.5.4` |
| Python | `3.14.4` |
| ESPHome board | `esp32-c3-devkitm-1` |
| ESPHome variant | `esp32c3` |
| ESPHome framework | `esp-idf` |
| Flash size | `4MB` |
| Upload method | ESPHome deployment via COM / serial |
| Display platform | `ssd1306_i2c` |
| Working display model | `SH1106 128x64` |
| Display address | `0x3C` |

## Hardware covered by this config

- Wi-Fi with reduced output power
- Captive portal fallback AP
- Home Assistant API with encryption
- OTA via ESPHome
- OTA via web server
- ESPHome web server v3
- Debug sensors
- Wi-Fi diagnostic sensors
- Uptime sensor
- Onboard blue LED on GPIO8
- Onboard 0.42" OLED over I2C
- Template text input for OLED text
- Template number controls for OLED X/Y placement
- Template select for OLED font size

## Configurations

The following ESPHome configurations are available:

| Version | File | Notes |
|---|---|---|
| Full | [esp32-c3-oled.yaml](./configs/esp32-c3-oled.yaml) | Full feature YAML with full display interaction via the Webserver |

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

## Important ESP32 block

```yaml
esp32:
  board: esp32-c3-devkitm-1
  variant: esp32c3
  flash_size: 4MB
  framework:
    type: esp-idf
```

## Wi-Fi stability

This board required reducing Wi-Fi output power to achieve a stable connection.

```yaml
wifi:
  output_power: 10dB
  power_save_mode: none
  fast_connect: true
  reboot_timeout: 0s
```

The antenna issue is documented as a board-level observation in [`../notes.md`](../notes.md).

## I2C

```yaml
i2c:
  sda: GPIO5
  scl: GPIO6
  scan: true
  id: bus_a
  frequency: 400kHz
```

## OLED display

The working unit uses the ESPHome `ssd1306_i2c` platform with the SH1106 model.

```yaml
display:
  - platform: ssd1306_i2c
    model: "SH1106 128x64"
    address: 0x3C
```

The visible area is about 72×40 px even though the controller memory area behaves like 128×64.

Working ESPHome display details:

| Item | Value |
|---|---|
| Platform | `ssd1306_i2c` |
| Model | `SH1106 128x64` |
| Address | `0x3C` |
| Visible top-left | x=27, y=9 |
| Physical visible window | about 72×40 px |
| Non-working model | `SSD1306 128x64` |
| Non-working model | `SSD1306 72x40` |

Do **not** rely on `offset_x` / `offset_y` for this correction unless retested. The current working setup shifts the drawing coordinates directly.

```cpp
const int X0 = 27;
const int Y0 = 9;
```

## Onboard LED

```yaml
output:
  - platform: gpio
    id: onboard_led_output
    pin:
      number: GPIO8
      inverted: true
```

GPIO8 will produce strapping-pin warnings during compile. Use this LED only intentionally.

## Full device config

The current full config is [`configs/esp32-c3-oled.yaml`](./configs/esp32-c3-oled.yaml).

## Deployment notes

Typical workflow:

1. Connect board via USB-C.
2. Put the board into download mode if needed: hold BOOT, press/release RESET, then release BOOT.
3. Deploy from ESPHome using the serial COM port.
4. After first flash, OTA updates should work if Wi-Fi and API/OTA are configured correctly.

## TODO

- Add serial flashing command examples for deployment outside of ESPHome Web UI.
- Add screenshots of discovered Home Assistant entities.
