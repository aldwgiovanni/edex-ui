# Data Model: fichier de thème `ambre.json`

Format imposé par les thèmes existants (lu par `src/_renderer.js`, `src/classes/terminal.class.js`, `src/classes/locationGlobe.class.js`).

| Clé | Valeur « ambre » | Rôle |
|---|---|---|
| `colors.r/g/b` | 255 / 176 / 0 | Accent (`--color_r/g/b`) : textes, bordures, clavier, explorateur |
| `colors.black` | `#050301` | Fond d'interface (`--color_black`) et noir ANSI |
| `colors.light_black` | `#0b0802` | Fond des panneaux (`--color_light_black`) |
| `colors.grey` | `#2e2412` | Filets et éléments secondaires (`--color_grey`) |
| `colors.red` … `colors.brightWhite` | 15 couleurs ANSI teintées chaud | Palette du terminal ; `red`/`yellow` servent aussi aux modales |
| `cssvars.font_main` / `font_main_light` | `United Sans Medium` / `United Sans Light` | Polices d'interface |
| `terminal.fontFamily` | `Fira Mono` | Police du terminal |
| `terminal.cursorStyle` | `block` | Curseur |
| `terminal.foreground` / `cursor` / `cursorAccent` | `#ffb000` | Texte et curseur du terminal |
| `terminal.background` | `#0b0802` | Fond du terminal |
| `terminal.selection` | `rgba(255,176,0,0.3)` | Sélection |
| `globe.base` / `marker` / `pin` / `satellite` | `#000000` / `#ffb000` / `#ffb000` / `#ffd060` | Globe réseau |

## Règles de validation
- JSON valide ; toutes les clés ci-dessus présentes.
- Polices : un fichier `<nom en minuscules, espaces → _>.woff2` existe dans `src/assets/fonts/` pour chaque police.
- Contraste (WCAG) : accent ≥ 7:1 sur `black` et `light_black` ; `terminal.foreground` ≥ 7:1 sur `terminal.background` ; chaque couleur ANSI sauf `black` ≥ 4,5:1 sur `terminal.background` ; `red`/`yellow` ≥ 4,5:1 sur `colors.black`.
