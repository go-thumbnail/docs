# thumbnail

[![Go Reference](https://pkg.go.dev/badge/github.com/go-thumbnail/thumbnail.svg)](https://pkg.go.dev/github.com/go-thumbnail/thumbnail)

Implements the freedesktop.org
[**Thumbnail Managing Standard**](https://specifications.freedesktop.org/thumbnail/latest-single/) —
generate and cache file thumbnails **exactly where and how the standard prescribes**, so
the cache interoperates with file managers and image viewers. Pure Go, `CGO_ENABLED=0`.

- Canonical cache under `$XDG_CACHE_HOME/thumbnails/{normal,large,x-large,xx-large}` — the 128 / 256 / 512 / 1024 px buckets.
- Required PNG `tEXt` metadata (`Thumb::URI`, `Thumb::MTime`, …) written and validated.
- Fail markers for sources that cannot be thumbnailed, and shared-repository handling.

## Install

```sh
go get github.com/go-thumbnail/thumbnail
```

## Usage

```go
package main

import (
	"fmt"

	"github.com/go-thumbnail/thumbnail"
)

func main() {
	// Package-level helpers use a default normal-size (128px) cache.
	path, err := thumbnail.Get("/home/jens/photo/me.png")
	if err != nil {
		panic(err)
	}
	fmt.Println("cached thumbnail at", path)

	// A configured cache: 256px bucket, custom fail-dir app name.
	c := thumbnail.New(thumbnail.Large, thumbnail.WithAppName("myapp"))
	img, err := c.GetImage("/home/jens/photo/me.png")
	if err != nil {
		panic(err)
	}
	fmt.Println("thumbnail bounds:", img.Bounds())
}
```

The full API is on [pkg.go.dev](https://pkg.go.dev/github.com/go-thumbnail/thumbnail).
Source: [github.com/go-thumbnail/thumbnail](https://github.com/go-thumbnail/thumbnail).
