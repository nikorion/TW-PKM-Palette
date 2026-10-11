# TW-Palette

**English** · [Français](README.fr.md)

A TiddlyWiki plugin shipping nikorion's colour palette: a copy of the default Vanilla palette to adjust, selected by default. Companion of TW-Theme.

## Overview

- `src/palette/palette.tid`: the palette `$:/palettes/nikorion`.
- `src/palette/select.tid`: `$:/palette`, pointing to it.
- `src/palette/styles/properties.tid`: CSS variables `--tpc-<key>` for the keys the core does not emit (the custom `nk-…` ones).
- `src/palette/theme-select.tid`: `$:/theme`, selecting the companion TW-Theme plugin (Vanilla is used if it is not loaded).

## Installation

Personal plugin, not published. Link `src/palette` as `nikorion/palette` in `TIDDLYWIKI_PLUGIN_PATH` and list `"nikorion/palette"` in the `plugins` of the wiki's `tiddlywiki.info`. A real `$:/palette` tiddler in the wiki would override the selection.

## Development

```
pnpm install
pnpm dev      # dev wiki + hot reload; edits made in the browser are written back to src/palette
pnpm build    # dist/TW-Palette-Plugin.json + docs/
```

## License

MIT License — see `LICENSE`. The palette is derived from TiddlyWiki's default palette (BSD 3-Clause).
