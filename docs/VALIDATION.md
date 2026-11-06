# Validation

Authoring date: November 6, 2026. Host: Windows. Target: Windows, macOS, Linux browser.

## Local result

Target-platform source CI is recorded after publication. This host has Python, Node.js, and .NET; other native toolchains are verified through CI. No unobserved GUI/device behavior is claimed.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `ubuntu-latest`:

```sh
node --test test.ts
node --check server.ts
```

## Manual acceptance

Add SKU 123 with count 2 and minimum 3. Confirm LOW, increment/decrement stock, save/reload, export/import JSON, and print a label. Also test malformed inputs and an unwritable output destination.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.

## Observed CI result

Passed: [target-platform build/check](https://github.com/netcodermike/offline-stockroom-tracker/actions/runs/42205297197). Source commit: `f3d57976f4cb382025c14af4ba162ec0fbb02257`. Later documentation-only changes do not alter the tested implementation. The reproducible commands above identify test scope; native GUI/audio/permissions are not implied by compilation.
