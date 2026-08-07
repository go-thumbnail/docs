# go-thumbnail documentation

**A pure-Go (`CGO_ENABLED=0`) implementation of the freedesktop.org
[Thumbnail Managing Standard](https://specifications.freedesktop.org/thumbnail/latest-single/).**
No cgo, no external thumbnailer processes.

go-thumbnail generates and caches file thumbnails **exactly where and how the standard
prescribes**, so the thumbnails it writes are visible to other compliant tools — file
managers, image viewers — and vice-versa. A single portable module that cross-compiles
to a static binary.

## Module

| Module | freedesktop specification | What it gives you |
| --- | --- | --- |
| [`thumbnail`](thumbnail.md) | [Thumbnail Managing Standard](https://specifications.freedesktop.org/thumbnail/latest-single/) | Canonical cache under `$XDG_CACHE_HOME/thumbnails/{normal,large,x-large,xx-large}` (128 / 256 / 512 / 1024 px), the required PNG metadata, fail markers, and shared-repository handling. |

## Design

- **Pure Go, `CGO_ENABLED=0`** — a single portable module; cross-compiles to a static binary.
- **Spec-faithful cache** — canonical directory layout, PNG `tEXt` metadata and fail-marker semantics, so the cache interoperates with existing desktop tools.
- **100% test coverage** is the bar, error branches included.
- **BSD-3-Clause**.

## Links

- 🌐 Site — <https://go-thumbnail.github.io/>
- 💻 GitHub — <https://github.com/go-thumbnail>
- 🎨 Brand — <https://github.com/go-thumbnail/brand>
