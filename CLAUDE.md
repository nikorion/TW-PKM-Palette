# TW-Palette — contexte projet pour Claude

> **OBSOLÈTE (2026-10-11) : fusionné dans `TW-Theme`** (`palette.tid`, `palette-select.tid`, `styles/properties.tid`). Ce dossier n'est plus chargé par aucun wiki ; il peut être supprimé par l'utilisateur. Ne pas y travailler.

> **Avant toute tâche sur ce plugin, consulter d'abord le `CLAUDE.md` du workspace** (`../CLAUDE.md`) et ses `guides/`. Ci-dessous : uniquement le spécifique à TW-Palette.

## Ce que c'est
Plugin TiddlyWiki (`$:/plugins/nikorion/palette`, créé 2026-10-11) : la palette « Nikorion » (`$:/palettes/nikorion`, copie de `core/palettes/Vanilla.tid` à ajuster) + `$:/palette` qui la sélectionne. Compagnon de `TW-Theme`. **Personnel, git local seul** (ni remote, ni CI, hors `plugins.json`/bibliothèque).

## Décisions à ne pas défaire
- `select.tid` livre `$:/palette` ; `theme-select.tid` livre `$:/theme` = `$:/plugins/nikorion/theme` (un thème ne peut pas se sélectionner lui-même, un plugin ordinaire le peut ; sans le plugin thème, TW retombe sur Vanilla). Un vrai `$:/palette` / `$:/theme` dans un wiki les masque (c'est le cas de kms-prod, voulu).
- **Write-back navigateur → source** (`"twDev": {"writeBack": "src/palette"}`, `tw-dev/writeback.cjs`) : dans ce wiki de dev, ce qui est modifié dans l'UI est réécrit dans `src/palette/` puis supprimé de `wiki/tiddlers/` ; ne **pas** créer de fichier à la main dans `wiki/tiddlers/` pendant `pnpm dev`. Le wiki de dev charge aussi `theme` (`$:/theme` réel = `$:/plugins/nikorion/theme`) : `writeBack.dirs` couvre palette **et** thème, `createNew: false` (les titres inconnus des deux plugins restent dans le wiki, rien de nouveau n'est créé). Le wiki de TW-Theme route aussi les modifications de `$:/palettes/nikorion` ici (`writeBack.dirs`).
- Exclu de la synchro des préférences (`tw-dev/prefs.json`).
- **Clés propres au thème** : en plus des clés de la palette Vanilla, `palette.tid` porte les couleurs de TW-Theme (`nk-site-title`, `nk-hljs-*`, `nk-info-*`, `nk-interro-*`, `nk-alert-*`, `nk-light-*`, `nk-tiddler-border`, `nk-footnote-counter`, `nk-background`) ; TW-Theme les lit par `var(--tpc-<clé>)` ; les variables de ces clés propres sont émises par `styles/properties.tid` (le cœur n'émet que celles des clés Vanilla), pour isoler nos ajouts sans surcharger le tiddler du cœur. Les renommer ou les retirer casse le thème.
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
