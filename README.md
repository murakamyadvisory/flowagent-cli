# flowagent CLI

Binary releases of `flowagent`, the command-line client for [EvidentFlow](https://www.evidentflow.app).
The source is private; this repository only hosts release assets.

## Install

macOS and Linux:

```sh
curl -fsSL https://www.evidentflow.app/cli/install.sh | sh
```

Windows (PowerShell):

```powershell
irm https://www.evidentflow.app/cli/install.ps1 | iex
```

Both install the newest release into `$XDG_BIN_HOME`, else `~/.local/bin`
(`%USERPROFILE%\.local\bin` on Windows), and add it to `PATH` if needed. Then sign in:

```sh
flowagent login            # opens the browser
flowagent login --device   # SSH / headless
```

Using the CLI requires that an admin of your organization has enabled CLI access.

## Manual download

Every [release](https://github.com/murakamyadvisory/flowagent-cli/releases/latest) has archives for:

| Platform                         | x64                         | arm64                        |
| -------------------------------- | --------------------------- | ---------------------------- |
| Linux (glibc)                    | `x86_64-unknown-linux-gnu`  | `aarch64-unknown-linux-gnu`  |
| Linux (static/musl, e.g. Alpine) | `x86_64-unknown-linux-musl` | `aarch64-unknown-linux-musl` |
| macOS                            | `x86_64-apple-darwin`       | `aarch64-apple-darwin`       |
| Windows                          | `x86_64-pc-windows-msvc`    | `aarch64-pc-windows-msvc`    |

```sh
TARGET=aarch64-apple-darwin
BASE=https://github.com/murakamyadvisory/flowagent-cli/releases/latest/download
curl -fsSLO "$BASE/flowagent-cli-$TARGET.tar.xz"
curl -fsSLO "$BASE/flowagent-cli-$TARGET.tar.xz.sha256"
shasum -a 256 -c "flowagent-cli-$TARGET.tar.xz.sha256"   # Linux: sha256sum -c
tar -xJf "flowagent-cli-$TARGET.tar.xz"
install -m 0755 "flowagent-cli-$TARGET/flowagent" ~/.local/bin/flowagent
```

Windows archives are `.zip`; `sha256.sum` in each release lists every checksum. macOS binaries
are signed (Developer ID "Erwins Enkel") and notarized. Windows binaries are unsigned, so
SmartScreen may warn on first start.

## Issues

Please report problems through your EvidentFlow contact; issues on this repository are disabled.
