# multiplex-cli-releases

Downloadable builds of [`mpx`](https://multiplexterm.dev), the companion CLI
for [Multiplex](https://multiplexterm.dev). **There is no source here** — this
repository exists only to host release artifacts.

## Install

```sh
brew install multiplex-term/tap/mpx                        # macOS or Linux
curl -fsSL https://multiplexterm.dev/install-mpx-cli | sh  # macOS or Linux
```

Then, on the machine you want to add to the app:

```sh
mpx bind
```

Or grab an archive from [Releases](../../releases) by hand:

| Platform | Archive |
| --- | --- |
| macOS, Apple silicon | `mpx-<tag>-aarch64-apple-darwin.tar.gz` |
| macOS, Intel | `mpx-<tag>-x86_64-apple-darwin.tar.gz` |
| Linux, arm64 | `mpx-<tag>-aarch64-unknown-linux-musl.tar.gz` |
| Linux, x86_64 | `mpx-<tag>-x86_64-unknown-linux-musl.tar.gz` |

Each archive carries the `mpx` binary, a `multiplex` alias, the README, and the
licence. Linux builds are **statically linked against musl**, so one binary
covers glibc distributions and Alpine alike — `mpx bind` is usually run on a
server nobody wants to install a toolchain on.

Verify what you downloaded:

```sh
curl -fsSLO https://github.com/multiplex-term/multiplex-cli-releases/releases/latest/download/SHA256SUMS
shasum -a 256 -c SHA256SUMS --ignore-missing
```

## Why the source lives elsewhere

`mpx` is built from `multiplex-term/multiplex-cli`, which is not public. Both
install paths above need *anonymous* downloads, so the artifacts need a public
home of their own — this one. Nothing is published here by hand:
`multiplex-cli`'s release workflow builds all four platforms on a tag, uploads
them here, and opens a formula bump against
[`multiplex-term/homebrew-tap`](https://github.com/multiplex-term/homebrew-tap).

## Reporting problems

[Open an issue](../../issues) on this repository — include `mpx --version`
and your platform. For the app itself, start at
[multiplexterm.dev](https://multiplexterm.dev).

## Licence

MIT, same as the source. See the `LICENSE` inside any archive.
