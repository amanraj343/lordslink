# lordslink PowerToys Command Palette / PowerToys Run Extension (`lordslink-ptrun`)

`lordslink-ptrun` is a standalone, zero-dependency Rust helper that connects Windows launcher tools (PowerToys Command Palette, PowerToys Run, Flow Launcher, Raycast for Windows) to lordslink's [Local Authenticated API](../../docs/api.md).

## Building

```powershell
cargo build --release --manifest-path tools/powertoys-extension/Cargo.toml
```

## Prerequisites

1. Open **lordslink → Settings → Local automation API** and turn on **Enable local automation API**.
2. lordslink writes `%LOCALAPPDATA%\lordslink\api-token.json` containing the loopback port (`53320`) and a 256-bit Bearer token.

## Usage

### Querying Palette Items

```powershell
lordslink-ptrun query ""
lordslink-ptrun query "ring"
lordslink-ptrun query "https://lordslink.dev"
```

Outputs a JSON array of palette commands (`send-clipboard`, `ring`, `camera` `photo`/`scan`, `send-url`, `send-text`, plus recent timeline items).

### Invoking an Action

```powershell
lordslink-ptrun invoke ring
lordslink-ptrun invoke send-clipboard
lordslink-ptrun invoke camera photo
lordslink-ptrun invoke camera scan
lordslink-ptrun invoke send-url "https://lordslink.dev"
lordslink-ptrun invoke send-text "Copied from PowerToys"
lordslink-ptrun invoke send-file "C:\Users\Alice\Desktop\notes.pdf"
```
