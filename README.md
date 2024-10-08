<div align="center">
    <img src="https://deps.rs/repo/github/notashelf/microfetch/status.svg" alt="https://deps.rs/repo/github/notashelf/microfetch">
    <!-- <img src="https://img.shields.io/github/v/release/notashelf/microfetch?display_name=tag&color=DEA584"> -->
    <img src="https://img.shields.io/github/stars/notashelf/microfetch?label=stars&color=DEA584">
</div>

<h1 align="center">Microfetch</h1>

Stupidly simple, laughably fast fetch tool. Written in Rust for speed and ease
of maintainability. Runs in a _fraction of a millisecond_ and displays _most_ of
the nonsense you'd see posted on r/unixporn or other internet communities. Aims
to replace [fastfetch](https://github.com/fastfetch-cli/fastfetch) on my
personal system, but [probably not yours](#customizing). Though, you are more
than welcome to use it on your system: it's pretty [fast...](#benchmarks)

<p align="center">
  <img
    alt="latest demo"
    src="./.github/assets/demo.png"
    width="850px"
  >
</p>

## Features

- Fast
- Really fast
- Minimal dependencies
- Actually really fast
- Cool NixOS logo (other, inferior, distros are not supported)
- Reliable detection of following info:
  - Hostname/Username
  - Kernel
    - Name
    - Version
    - Architecture
  - Current shell (from $SHELL, trimmed if store path)
  - WM/Compositor and display backend
  - Memory Usage/Total Memory
  - Storage Usage/Total Storage (for `/` only)
  - Shell Colors
- Did I mention fast?

## Benchmarks

Microfetch's performance is mostly hardware-dependant, however, the overall
trend seems to be < 2ms on any modern (2015 and after) CPU. Below are the
benchmarks with Hyperfine on my desktop system.

| Command      |   Mean [ms] | Min [ms] | Max [ms] |       Relative |
| :----------- | ----------: | -------: | -------: | -------------: |
| `microfetch` |   1.3 ± 0.0 |      1.3 |      1.4 |           1.00 |
| `pfetch`     | 254.2 ± 4.8 |    246.7 |    264.9 |  191.97 ± 7.10 |
| `neofetch`   | 735.4 ± 9.5 |    721.1 |    752.8 | 555.48 ± 19.08 |
| `fastfetch`  |  31.9 ± 0.8 |     30.8 |     33.8 |   24.08 ± 0.98 |

_As far as I'm concerned, Microfetch is faster than almost every fetch tool
there is. The only downside of using Rust is introducing more "bloated"
dependency trees and increasing build times. The latter is easily mitigated with
Nix's binary cache, though._

## Customizing

You can't.

### Why?

Customization, of any kind, is expensive: I could try reading environment
variables, parse command-line arguments or read a configuration file but all of
those increment execution time and resource consumption by a lot.

### Really?

To be fair, you _can_ customize Microfetch by... Well, patching it. It's not the
best way per se, but it will be the only way that does not compromise on speed.

## Contributing

I will, mostly, reject feature additions. This is not to say you should avoid
them altogether, as you might have a really good idea worth discussing but as a
general rule of thumb consider talking to me before creating a feature PR.

Contributions that help improve performance in specific areas of Microfetch are
welcome. Though, prepare to be bombarded with questions.

## Hacking

A Nix flake is provided. `nix develop` to get started. Direnv users may simply
run `direnv allow` to get started.

Non-nix users will need `cargo` and `gcc` installed on their system, see
`Cargo.toml` for available release profiles.

## License

Microfetch is licensed under [GPL3](LICENSE). See the license file for details.
