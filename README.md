# Plinky 12 Community Panels

This repository collects community-submitted Plinky 12 custom panel designs.
Panels listed here are shown in the Community section of the Plinky 12 web
panel library.

Community panels are not official Plinky examples. They are reviewed for basic
metadata and build compatibility, but they are not officially supported by
Plinky.

If you find a problem, please [file an issue](https://github.com/plinkysynth/community-panels/issues).

For more information about Plinky 12, go to https://plinky12.com

## Panel Layout

Use one author directory, then one directory per panel:

```text
author_slug/
  my_panel/
    my_panel.cpp
    README.md        # optional, but recommended
    artwork.png      # optional; artwork.webp is also accepted
```

Each author directory can contain one or more panel directories. Each panel
directory must contain exactly one `.cpp` file directly inside the directory.
Do not put panel `.cpp` files at the repository root or directly inside an
author directory, and do not use subdirectories inside a panel submission.

Inside each panel directory, the only other accepted files are:

- `README.md`: optional panel-specific notes.
- `artwork.png` or `artwork.webp`: optional square thumbnail artwork.

The community panel ID comes from the author and panel directory names:
`author_slug/panel_slug`. Directory slugs must be lowercase and contain only
letters, numbers, and underscores. Use the `@Name` metadata for display names
with spaces and punctuation.

The optional panel `README.md` is shown in the Plinky web IDE panel cover after
someone opens the panel from the library. The public library listing uses the
C++ metadata and artwork, not the README.

## Permalinks

Use your community panel ID in the Plinky web IDE community library URL:

```text
https://plinky12.com/ide.html?library=community&panel=author_slug/panel_slug
```

The panel ID is the author slug plus panel slug. This link opens the Community
library with the search narrowed to that panel, showing its larger panel page.

## Required Metadata

The first block comment in the panel `.cpp` file is used as the panel library
metadata. Every community panel must include:

```cpp
/*
@Name: My Panel
@Author: Your Name
@Documentation: https://example.com/my-panel
@Category: Sequencers
@Tags: midi, touch, clock
@Description: A one-sentence summary shown in the library.

Longer plain-text description can go here if you do not use @Description.
*/
```

Required fields:

- `@Author`: author or maintainer name.
- `@Documentation`: an `https://` or `http://` URL with usage notes,
  documentation, or a project page.

Optional fields:

- `@Name`: display name. If omitted, the panel class or filename is used.
- `@Description`: short in-page description.
- `@Category` or `@Level`: library category.
- `@Tags`: comma-separated search tags.
- `@Discussion`: an `https://` or `http://` URL for discussion or support.

Do not use `@Artwork` metadata in community panel submissions. If a panel has
artwork, include exactly one file named `artwork.png` or `artwork.webp` next to
the `.cpp` file.

## Code Requirements

Each panel must be one self-contained C++ source file that defines one class or
struct derived from `panel_t`. Do not use `#include` directives or rely on
local `.h` files; the Plinky 12 web IDE does not support includes in custom
panel source.

Do not include generated firmware binaries, build directories, or large media
assets in a panel submission. Artwork should be reasonably small and suitable
for display as a square library thumbnail.
