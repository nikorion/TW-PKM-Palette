# TW-Palette

[English](README.md) · **Français**

Un plugin TiddlyWiki qui fournit la palette de couleurs de nikorion : copie de la palette Vanilla par défaut à ajuster, sélectionnée par défaut. Compagnon de TW-Theme.

## Vue d'ensemble

- `src/palette/palette.tid` : la palette `$:/palettes/nikorion`.
- `src/palette/select.tid` : `$:/palette`, qui pointe vers elle.
- `src/palette/theme-select.tid` : `$:/theme`, qui sélectionne le plugin compagnon TW-Theme (Vanilla si celui-ci n'est pas chargé).

## Installation

Plugin personnel, non publié. Reliez `src/palette` comme `nikorion/palette` dans `TIDDLYWIKI_PLUGIN_PATH` et listez `"nikorion/palette"` dans les `plugins` du `tiddlywiki.info` du wiki. Un vrai tiddler `$:/palette` dans le wiki surchargerait la sélection.

## Développement

```
pnpm install
pnpm dev      # wiki de dev + rechargement à chaud ; les modifications faites dans le navigateur sont réécrites dans src/palette
pnpm build    # dist/TW-Palette-Plugin.json + docs/
```

## Licence

Licence MIT — voir `LICENSE`. La palette dérive de la palette par défaut de TiddlyWiki (BSD 3-Clause).
