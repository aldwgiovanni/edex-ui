# Master board — edex-ui
Mis à jour : 2026-11-04
Mode : pas-à-pas — Merges : sur accord

## Features
| # | Feature | Branche | Session | Phase | PR | Statut | Dépend de |
|---|---------|---------|---------|-------|----|--------|-----------|
| 001 | Thème personnalisé (`src/assets/themes/`) | — | — | — | — | à faire | — |
| 002 | Panneau GPU (charge, VRAM, température) | — | — | — | — | à faire | — |
| 003 | Panneau disques + alerte espace faible | — | — | — | — | à faire | — |
| 004 | Panneau Dockploy / Docker (conteneurs, état, CPU/RAM) | — | — | — | — | à faire | — |
| 005 | Panneau GitHub (PR, CI, notifications) | — | — | — | — | à faire | — |
| 006 | Panneau .NET (dotnet watch / tests) | — | — | — | — | à faire | — |
| 007 | Pluie « Matrix » en écran de veille | — | — | — | — | à faire | — |
| 008 | Assistant IA Claude intégré | — | — | — | — | à faire | — |
| 009 | Visualiseur audio sur le lecteur média | — | — | — | — | à faire | — |
| 010 | Globe des connexions sortantes | — | — | — | — | à faire | — |
| 011 | Migration vers un Electron récent | — | — | — | — | à faire | 001–010 (voir décisions) |

## Décisions / écarts
- 2026-11-04 : Spec Kit 0.15.0 initialisé (`--integration claude --script ps`). Commandes en `/speckit-*`.
- 2026-11-04 : base de travail = branche `chore/windows-prebuilt-pty` (contient le correctif node-pty indispensable pour lancer l'appli sous Windows) ; `master` du fork ne l'a pas encore. Les PR des features ciblent `master` et embarqueront ce correctif tant qu'il n'est pas mergé.
- 2026-11-04 : mode pas-à-pas par défaut (l'utilisateur a demandé de lancer seulement la première feature).
- 2026-11-04 : 011 (Electron récent) placée en dernier : elle touche tout le projet (dépendances, API Electron) et entrerait en conflit avec les features en cours. À réévaluer : la faire plus tôt réduirait la dette avant d'empiler les modules.
- Fichiers partagés : `src/_renderer.js`, `src/_boot.js` et `src/assets/css/main_shell.css` sont touchés par la plupart des panneaux (002–006, 008–010) → ces features passent en séquentiel ou avec rebase soigné ; 001 et 007 sont les plus indépendantes.

## Journal des retours
