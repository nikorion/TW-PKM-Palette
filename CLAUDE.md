# TW-Palette — contexte projet pour Claude

> **Avant toute tâche sur ce plugin, consulter d'abord le `CLAUDE.md` du workspace** (`../CLAUDE.md`) et ses `guides/`. Ci-dessous : uniquement le spécifique à TW-Palette.

## Ce que c'est
Plugin TiddlyWiki (`$:/plugins/nikorion/palette`, créé 2026-10-11) : la palette « Nikorion » (`$:/palettes/nikorion`, copie de `core/palettes/Vanilla.tid` à ajuster) + `$:/palette` qui la sélectionne. Compagnon de `TW-Theme`. **Personnel, git local seul** (ni remote, ni CI, hors `plugins.json`/bibliothèque).

## Décisions à ne pas défaire
- `select.tid` livre `$:/palette` : un vrai `$:/palette` dans un wiki le masque (kms-prod, wikis de dev).
- **Write-back navigateur → source** (`"twDev": {"writeBack": "src/palette"}`, `tw-dev/writeback.cjs`) : dans ce wiki de dev, ce qui est modifié dans l'UI est réécrit dans `src/palette/` puis supprimé de `wiki/tiddlers/` ; ne **pas** créer de fichier à la main dans `wiki/tiddlers/` pendant `pnpm dev`. Le wiki de TW-Theme route aussi les modifications de `$:/palettes/nikorion` ici (`writeBack.dirs`).
- Exclu de la synchro des préférences (`tw-dev/prefs.json`).
- Pas de JS, pas de `pnpm lint`.

## Structure
```
src/palette/
  plugin.info
  palette.tid     ← $:/palettes/nikorion
  select.tid      ← $:/palette
  readme.tid / history.tid / licence.tid / settings.tid, language/…
wiki/             ← wiki de dev : Playground, tiddler d'avis « Edits here become the palette »
```
