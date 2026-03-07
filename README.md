# kicad-neo-libraries

KiCad official symbol and footprint libraries converted to JSON for [kicad-neo](https://github.com/hulryung/kicad-neo) web EDA.

## Contents

- `symbols/` - KiCad symbol libraries (.kicad_sym) converted to JSON
- `footprints/` - KiCad footprint libraries (.kicad_mod) converted to JSON
- `index.json` - Lightweight search index (name, description, keywords, pin/pad count)

## Source

Converted from [KiCad official libraries](https://gitlab.com/kicad/libraries) using the parser in [kicad-neo](https://github.com/hulryung/kicad-neo).

## Stats

- **223** symbol libraries, **22,583** symbols
- **155** footprint libraries, **15,415** footprints
- Source: KiCad 9.0

## Usage

Fetch the index for browsing/search, then lazy-load individual library files:

```typescript
// Load search index
const index = await fetch('https://hulryung.github.io/kicad-neo-libraries/index.json').then(r => r.json());

// Lazy-load a specific symbol library
const device = await fetch('https://hulryung.github.io/kicad-neo-libraries/symbols/Device.json').then(r => r.json());
```

## Updating

```bash
# Requires kicad-neo repo with Rust toolchain
cargo run --release --manifest-path ../kicad-neo/crates/kicad-parser/Cargo.toml \
  --bin kicad-lib-convert -- --output .
cargo run --release --manifest-path ../kicad-neo/crates/kicad-parser/Cargo.toml \
  --bin kicad-lib-index -- -o index.json
```
