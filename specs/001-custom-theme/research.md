# Research: Thème « ambre »

## Chargement et sélection du thème
- **Decision**: déposer `ambre.json` dans `src/assets/themes/` et sélectionner avec `"theme": "ambre"`.
- **Rationale**: `src/_boot.js` (« Mirroring internal assets ») recopie à chaque lancement tous les thèmes intégrés dans le dossier utilisateur ; `src/_renderer.js` charge le thème nommé par le réglage.
- **Alternatives considered**: déposer le thème seulement dans le dossier utilisateur (non versionné).

## Couleurs ANSI du terminal
- **Decision**: déclarer explicitement les 16 couleurs (`black` … `brightWhite`) dans `colors`, toutes teintées chaud.
- **Rationale**: `src/classes/terminal.class.js` lit `colors.<nom>` et, à défaut, calcule une teinte grisée mêlée à 30 % d'accent ; avec un accent ambre très lumineux, ce calcul rapproche les couleurs entre elles. Les déclarer garantit FR-004.
- **Alternatives considered**: `terminal.colorFilter` (moins prévisible à contrôler) ; calcul par défaut (contraste non garanti).
- **Note**: `colors.black` sert à la fois de fond d'interface (`--color_black`) et de noir ANSI : quasi-noir `#050301`, comme les autres thèmes.

## Modales d'erreur et d'avertissement
- **Decision**: `colors.red` `#ff5f3a`, `colors.yellow` `#ffd060` (distinct de l'accent `#ffb000`).
- **Rationale**: `src/_renderer.js` lit `--color_red` / `--color_yellow` ; un jaune identique à l'accent rendrait l'avertissement indistinct.

## Polices
- **Decision**: United Sans Medium / Light pour l'interface, Fira Mono pour le terminal, curseur bloc.
- **Rationale**: choix de l'utilisateur (Clarifications) ; polices déjà dans `src/assets/fonts/`.

## Globe
- **Decision**: `base` `#000000` (sphère sombre comme `tron`), `marker`/`pin` accent `#ffb000`, `satellite` `#ffd060`.
- **Rationale**: marqueurs lisibles sur la sphère sombre ; satellite distinguable des marqueurs.

## injectCSS
- **Decision**: aucun.
- **Rationale**: le rendu standard suffit ; à reconsidérer seulement si la vérification dans l'appli révèle un défaut de lisibilité.
