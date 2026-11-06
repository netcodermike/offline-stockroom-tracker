# Offline Stockroom Tracker

Track local inventory counts, flag reorder levels, and print numeric Code 39 labels.

[![Build and verify](https://github.com/netcodermike/offline-stockroom-tracker/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/offline-stockroom-tracker/actions/workflows/verify.yml)

**Language:** TypeScript · **Platform:** Windows, macOS, Linux browser · **App type:** Browser inventory and barcode-label organizer

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- Numeric SKU inventory
- Validated count adjustments
- Browser save and JSON portability
- Printable Code 39 labels

## Requirements

Node.js 24.12+ and a modern browser; no npm dependencies.

## Quick start

```sh
git clone https://github.com/netcodermike/offline-stockroom-tracker.git
cd offline-stockroom-tracker
node server.ts
# Open http://127.0.0.1:3030
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Add SKU 123 with count 2 and minimum 3. Confirm LOW, increment/decrement stock, save/reload, export/import JSON, and print a label.

## Architecture, configuration, and data

core.ts validates 1–16 digit SKUs, unique item IDs, integer counts, and 2,000-item limits. Numeric Code 39 patterns include start/stop symbols and quiet zones, without an optional checksum. public/index.html renders safe text/SVG and stores one localStorage inventory. server.ts exposes only HTML and a stripped TypeScript module on loopback port 3030. Tests verify stock conservation/rejection and barcode guards. Pattern facts were checked against python-barcode’s Code 39 character table: https://github.com/WhyNotHugo/python-barcode/blob/master/barcode/charsets/code39.py .

## Verification

Build with the quick-start command where needed, then run:

```sh
node --test test.ts
```

Manual acceptance: Add SKU 123 with count 2 and minimum 3. Confirm LOW, increment/decrement stock, save/reload, export/import JSON, and print a label. Also test malformed inputs and an unwritable output destination.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

No camera/scanner integration, lot tracking, multi-user updates, autosave, item edit/delete, pricing, or cloud sync. Labels support numeric Code 39 only, no check digit; scanner/printer acceptance must be tested. Counts are unit quantities, not fractional stock. Browser saves are origin/profile-specific. JSON import replaces in-memory inventory; save explicitly.

## Troubleshooting

Use the exact platform/toolchain above. Preserve originals and use synthetic fixtures first. Errors are displayed in the UI or stderr. A headless machine can run the model tests but cannot verify native GUI/audio behavior. Output paths are chosen explicitly; keep backups of important data.

## Source map

- `core.ts`
- `package.json`
- `server.ts`
- `test.ts`
- `public/index.html`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
