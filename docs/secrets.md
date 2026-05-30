# Secrets

Never commit real Wi-Fi credentials, API keys, OTA passwords, private certificates, or home network details.

## ESPHome

Use `!secret` references in YAML:

### Example configuration YAML

```yaml
wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password

api:
  encryption:
    key: !secret api_key

ota:
  - platform: esphome
    password: !secret ota_password
```

Keep the real `secrets.yaml` outside this repository or ignored by Git.

### Example secrets file

Commit examples only:

```yaml
wifi_ssid: "example-ssid"
wifi_password: "example-password"
wifi_ap_ssid: "example-fallback-ap"
wifi_ap_password: "example-fallback-password"
api_key: "example-base64-key"
ota_password: "example-ota-password"
```

## Sanitizing configs

Before committing:

- Search for real SSIDs.
- Search for private IP addresses if the repo is public.
- Search for API keys and OTA passwords.
- Confirm generated ESPHome build output is ignored.
