# TW-PKM-Palette

[English](README.md) · **Français**

![Status](https://img.shields.io/badge/status-experimental-orange)

Un plugin TiddlyWiki qui fournit la palette de couleurs de nikorion : copie de la palette Vanilla par défaut à ajuster, sélectionnée par défaut. Compagnon de TW-PKM-Theme.

## Vue d'ensemble

- `src/palette/palette.tid` : la palette `$:/palettes/nikorion`.
- `src/palette/select.tid` : `$:/palette`, qui pointe vers elle.
- `src/palette/styles/properties.tid` : variables CSS `--tpc-<clé>` des clés que le cœur n'émet pas (les `nk-…` propres).
- `src/palette/theme-select.tid` : `$:/theme`, qui sélectionne le plugin compagnon TW-PKM-Theme (Vanilla si celui-ci n'est pas chargé).

## Installation

Installez-le depuis la [bibliothèque de plugins nikorion](https://nikorion.github.io/TW-Plugin-Library/), ou depuis les sources : reliez `src/palette` comme `nikorion/palette` dans `TIDDLYWIKI_PLUGIN_PATH` et listez `"nikorion/palette"` dans les `plugins` du `tiddlywiki.info` du wiki. Un vrai tiddler `$:/palette` dans le wiki surchargerait la sélection.

## Développement

```
pnpm install
pnpm dev      # wiki de dev + rechargement à chaud ; les modifications faites dans le navigateur sont réécrites dans src/palette
pnpm build    # dist/TW-PKM-Palette-Plugin.json + docs/
```

## Licence

Licence MIT — voir `LICENSE`. La palette dérive de la palette par défaut de TiddlyWiki (BSD 3-Clause).
