# External Dependencies and ESPHome Components

## Recommended policy

For this repository, external dependencies should usually be **referenced, not vendored**.

**Example:**
An ESPHome YAML can point to an external component repository, but the third-party source code is not copied into this repo by default.

## Why reference instead of vendoring?

Advantages:

- Smaller repository.
- Less license-management overhead.
- Easy to compare with upstream.
- Upstream bug fixes are available without manually copying code.

Trade-off:

- Builds are less reproducible if you track a moving branch such as `main`.

## Pinning strategy

Use one of these strategies:

### 1. Experiment mode

Use this while testing:

```yaml
external_components:
  - source: github://owner/repository@main
    components: [COMPONENT_NAME]
    refresh: 5s
```

This is convenient, but upstream changes can alter behavior.

### 2. Known-good mode

Once a configuration is confirmed stable, pin to a specific commit SHA:

```yaml
external_components:
  - source: github://owner/repository@<commit-sha>
    components: [component_name]
```

Record the commit SHA in [`DEPENDENCIES.md`](../../DEPENDENCIES.md) and in the device's ESPHome `README.md`.

### 3. Vendor mode

Only vendor external code when necessary:

```text
external/vendor/esphome-{component_name}/
  LICENSE
  NOTICE.md
  components/{component_name}/
```

Before vendoring:

- Confirm the upstream license allows redistribution.
- Preserve upstream copyright and license files.
- Record the upstream URL and commit SHA.
- Avoid mixing modified and unmodified code without documenting the difference.

## Where to document dependency detail

Keep the top-level `DEPENDENCIES.md` broad and catalog-like. Put exact external component sources, branches, tags, commit SHAs, known-good versions, and known-bad migration notes in the relevant device or project folder.

Suggested locations:

```text
devices/<device>/<tech-stack>/README.md
projects/<project>/dependencies.md
```
