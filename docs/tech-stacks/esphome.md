# ESPHome Conventions

## Folder layout

```text
devices/<device>/esphome/
  README.md
  configs/
    <device-name>.yaml
    <device-name>.minimal.yaml
  projects/
```

## Recommended metadata

Record the following in each ESPHome `README.md`:

- ESPHome version
- Python version
- ESP-IDF / Arduino framework version
- `esp32.board`
- `esp32.variant`
- framework type
- upload method
- required secrets
- external components
- known issues

## External components

Prefer pinning external components to an immutable reference once a config is known-good:

```yaml
external_components:
  - source: github://owner/repository@<commit-sha>
    components: [component_name]
```

Using `@main` is acceptable for active experiments, but it means a future upstream change may break reproducibility.
