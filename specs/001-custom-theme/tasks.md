# Tasks: Thème personnalisé « ambre »

**Input**: Design documents from `specs/001-custom-theme/`

**Prerequisites**: [plan.md](plan.md), [spec.md](spec.md), [research.md](research.md), [data-model.md](data-model.md), [quickstart.md](quickstart.md)

**Tests**: pas de suite de tests automatisés demandée ; la validation est un contrôle de contraste calculé et une vérification dans l'appli (constitution V).

## Format: `[ID] [P?] [Story] Description`

## Phase 1: Setup

- [X] T001 Vérifier la présence des polices `united_sans_medium.woff2`, `united_sans_light.woff2`, `fira_mono.woff2` dans src/assets/fonts/ et des `node_modules` à la racine et dans src/ (sinon `npm install` selon quickstart.md)

## Phase 2: Foundational

Aucune : la feature ne dépend d'aucune infrastructure nouvelle.

## Phase 3: User Story 1 - Activer son propre thème (Priority: P1) 🎯 MVP

**Goal**: un thème « ambre » sélectionnable par `"theme": "ambre"`.

**Independent Test**: régler `theme` sur `ambre`, lancer l'appli, constater l'habillage ambré sans erreur.

- [X] T002 [US1] Créer src/assets/themes/ambre.json avec toutes les clés et valeurs de data-model.md (colors r/g/b, black, light_black, grey, 15 couleurs ANSI ; cssvars ; terminal ; globe), indentation de 4 espaces comme tron.json
- [X] T003 [US1] Valider que src/assets/themes/ambre.json est un JSON valide et que chaque police déclarée correspond à un fichier de src/assets/fonts/
- [X] T004 [US1] Régler `"theme": "ambre"` dans %APPDATA%\eDEX-UI\settings.json (en notant la valeur initiale), lancer `npm run start` et constater le chargement sans modale d'erreur (quickstart.md §2)

**Checkpoint**: le thème se charge — MVP atteint.

## Phase 4: User Story 2 - Tout reste lisible (Priority: P1)

**Goal**: contraste suffisant dans les 5 zones.

**Independent Test**: contrôle calculé + parcours visuel zone par zone (quickstart.md §1 et §3).

- [X] T005 [P] [US2] Calculer les rapports de contraste WCAG de src/assets/themes/ambre.json selon les seuils de data-model.md (script dans le scratchpad, hors dépôt) ; ajuster les couleurs fautives dans ambre.json et recalculer jusqu'à ce que tout soit atteint
- [X] T006 [US2] Dans l'appli, vérifier un par un : panneaux, terminal (sortie colorée Red/Green/Blue/Magenta/Cyan/DarkGray), clavier, globe, explorateur ; consigner le résultat de chaque critère pour le rapport
- [X] T007 [US2] Prendre une capture d'écran de l'appli entière avec le thème actif (specs/001-custom-theme/capture-ambre.png, jointe au rapport final)

## Phase 5: Polish

- [X] T008 Remettre la valeur initiale de `theme` dans %APPDATA%\eDEX-UI\settings.json, relancer et vérifier l'apparence d'origine (quickstart.md §4)
- [X] T009 Vérifier par `git diff --stat master...HEAD` que le commit de la feature ne touche, sous src/, que src/assets/themes/ambre.json (FR-006, SC-004)

## Dependencies & Execution Order

- T001 → T002 → T003 → T004 → T006 → T007 → T008 ; T005 peut tourner dès T002, en parallèle de T003/T004 ; T009 en fin.
- US2 dépend de US1 (il faut le fichier de thème), mais se teste indépendamment par le calcul de contraste.

## Parallel Example

```text
Après T002 : lancer T005 (calcul de contraste) pendant T003/T004 (validation et lancement de l'appli).
```

## Implementation Strategy

MVP = US1 (T001–T004). US2 complète la qualité (contraste et vérification visuelle), puis le polissage garantit le retour arrière et l'absence de changement hors périmètre.
