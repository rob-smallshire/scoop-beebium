# Beebium Scoop Bucket

A [Scoop](https://scoop.sh) bucket for [**Beebium**](https://github.com/rob-smallshire/beebium),
a BBC Micro emulator with a multi-process architecture: a headless emulation core
exposed over gRPC, driven by separate clients (Python, TypeScript, a macOS app).

This bucket distributes the **Windows server** — the headless emulator itself,
as a self-contained `x64` build. It is designed to be used as a tool for running
and testing BBC Micro software locally and in CI, driven from the Python or
TypeScript client.

## Install

```powershell
scoop bucket add beebium https://github.com/rob-smallshire/scoop-beebium
scoop install beebium-server
```

The build is self-contained apart from the Microsoft Visual C++ Redistributable
(present on virtually all Windows systems).

## What you get

Four server executables on your `PATH`, one per machine variant:

```
beebium-model-b            # BBC Model B
beebium-model-b-plus       # BBC Model B+ (64K)
beebium-model-b-plus-128k  # BBC Model B+ 128K
beebium-model-b-romram     # Model B with ROM/RAM board
```

Each server discovers its bundled ROMs, presets and peripheral extensions
relative to its own install location — no environment setup required. List the
available extensions with:

```powershell
beebium-model-b list-extensions
```

## Driving the server

The servers are headless and speak gRPC; you drive them from a client:

- **Python** — `pip install beebium` *(planned: PyPI)*
- **TypeScript** — `npm install beebium` *(planned: npm)*

See the [Beebium repository](https://github.com/rob-smallshire/beebium) for client
documentation and examples.

## Other platforms

- **macOS** — `brew tap rob-smallshire/beebium && brew install beebium-server`.
- **Linux** — the self-contained `.deb` (Debian/Ubuntu/Raspberry Pi OS) or
  `.tar.gz` (other distros), for `amd64` and `arm64`, from the
  [Beebium releases](https://github.com/rob-smallshire/beebium/releases).

## License

Beebium is free software under the
[GNU General Public License v3.0 or later](https://github.com/rob-smallshire/beebium/blob/master/COPYING.txt).
