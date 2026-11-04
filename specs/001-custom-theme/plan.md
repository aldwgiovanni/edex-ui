# Implementation Plan: Thème personnalisé « ambre »

**Branch**: `claude/001-custom-theme-5623ae` | **Date**: 2026-11-04 | **Spec**: [spec.md](spec.md)

**Input**: Feature specification from `specs/001-custom-theme/spec.md`

## Summary

Livrer un thème intégré « ambre » (phosphore ambré rétro) sous la forme d'un unique fichier
`src/assets/themes/ambre.json`, au format des thèmes existants. Il est recopié dans le dossier
utilisateur à chaque lancement par `src/_boot.js` et se sélectionne avec `"theme": "ambre"` dans
`settings.json`. Aucune ligne de JavaScript ni de CSS d'application n'est modifiée.

## Technical Context

**Language/Version**: JSON (fichier de thème) lu par le renderer JavaScript d'eDEX-UI

**Primary Dependencies**: aucune nouvelle ; polices déjà embarquées (`united_sans_medium`, `united_sans_light`, `fira_mono`)

**Storage**: fichier `src/assets/themes/ambre.json`, recopié dans `%APPDATA%/eDEX-UI/themes/`

**Testing**: contrôle de contraste calculé (script hors dépôt, cf. quickstart) + vérification visuelle dans l'appli

**Target Platform**: Windows, Electron 12.2.2, Node 16.20.2 (environnement de référence de la constitution)

**Project Type**: desktop-app (Electron)

**Performance Goals**: sans objet (aucun code exécuté en plus)

**Constraints**: format de thème existant uniquement ; contraste texte ≥ 7:1, couleurs ANSI ≥ 4,5:1

**Scale/Scope**: 1 fichier de thème, 0 ligne de code

## Constitution Check

| Principe | Statut | Justification |
|---|---|---|
| I. Conventions existantes | ✅ | Même structure de clés que `tron.json` / `nord.json` ; nom de fichier = nom du thème. |
| II. Compatible avec tous les thèmes | ✅ | Aucun module touché ; les thèmes existants sont inchangés. |
| III. Sobre en ressources | ✅ | Aucun code ajouté. |
| IV. Sécurité | ✅ | Pas de secret ; pas d'`injectCSS`. |
| V. Vérifié dans l'appli | ⏳ | Prévu en phase d'implémentation ([quickstart.md](quickstart.md)). |
| VI. Changements chirurgicaux | ✅ | Un seul fichier ajouté. Code mort constaté et signalé, non modifié : `nord.json` déclare `lightBlack`/`light*` alors que le terminal lit `brightBlack`/`bright*`. |
| Interface (`design-patterns`) | ✅ | Aucun pattern du catalogue ne vise un thème de terminal ; règles transverses appliquées (contraste, couleurs par rôle, modales rouge/jaune distinctes). Écart signalé : la règle « pas de noir pur » est respectée par un quasi-noir teinté `#050301`, sauf `globe.base` `#000000`, repris de `tron` (convention eDEX). |

Post-design : inchangé, aucune violation.

## Project Structure

### Documentation (this feature)

```text
specs/001-custom-theme/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── checklists/requirements.md
└── tasks.md          # /speckit-tasks
```

Pas de dossier `contracts/` : la feature n'expose aucune interface nouvelle ; elle se conforme au
format de thème existant, décrit dans [data-model.md](data-model.md).

### Source Code (repository root)

```text
src/assets/themes/
└── ambre.json        # NOUVEAU — seul fichier livré
```

**Structure Decision**: un fichier de données dans le dossier des thèmes intégrés ; aucun autre fichier de `src/` n'est modifié.

## Complexity Tracking

Aucune violation à justifier.
