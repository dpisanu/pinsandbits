# Conventions

## Folder names

Use lowercase `kebab-case`:

```text
esp32-s3-matrix
esp32-devkit-v1
m5stack-core2
seeed-xiao-esp32c3
```

## Tech stack folder names

Use stable lowercase names:

```text
esphome/
micropython/
nanoframework/
zephyr/
```

## Status labels

| Label | Meaning |
|---|---|
| `working` | Confirmed on real hardware |
| `partial` | Some features work, but important gaps remain |
| `experimental` | Still changing; not trusted yet |
| `broken` | Known not to work in the recorded environment |
| `not tested` | Planned or possible, but not tried yet |
| `TBD` | Unknown; needs investigation |

## Markdown style

- Start every folder with a `README.md`.
- Use tables for stable facts.
- Use dated notes for experiments and failures.
- Mark assumptions clearly.
- Keep secrets, tokens, Wi-Fi names, and private IP details out of public examples.

## YAML style

- Use two-space indentation.
- Keep comments close to the setting they explain.
- Prefer `!secret` for private values.
- Include a minimal config where possible and a full config when useful.
