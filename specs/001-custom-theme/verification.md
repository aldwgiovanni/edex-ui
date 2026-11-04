# Vérification dans l'appli — thème « ambre »

**Date** : 2026-11-04 | **Environnement** : Windows 11, Node 16.20.2 portable, Electron 12.2.2, `npm run start` depuis la worktree.

Capture : [capture-ambre.png](capture-ambre.png) (appli entière, thème actif, sortie colorée dans le terminal).

| Critère | Résultat | Constat |
|---|---|---|
| SC-001 / FR-002 : sélection par `"theme": "ambre"` | ✅ | Chargé au premier lancement, sans modale d'erreur. |
| FR-003 : polices embarquées | ✅ | United Sans Medium / Light et Fira Mono présentes dans `src/assets/fonts/` et rendues. |
| SC-003 / FR-004 / FR-005 : contrastes calculés | ✅ | Accent 10,9:1 et 11,2:1 sur les fonds ; texte du terminal 10,9:1 ; couleurs ANSI de 4,58:1 (`brightBlack`) à 18,2:1 ; modales rouge 6,8:1 et jaune 14,2:1. |
| SC-002 : panneaux | ✅ | Horloge, système, CPU, mémoire, processus, réseau : libellés lisibles. |
| SC-002 : terminal | ✅ | Les 16 couleurs PowerShell (`-ForegroundColor 0..15`) se distinguent ; seul `Black` (0) est invisible sur le fond, comme dans tous les thèmes sombres. |
| SC-002 : clavier | ✅ | Touches et symboles secondaires lisibles. |
| SC-002 : globe | ✅ (partiel) | Sphère et libellé « OFFLINE » lisibles ; le réseau étant hors ligne pendant le test (indépendant du thème), les marqueurs n'ont pas pu être observés. Leur couleur est l'accent, validé ci-dessus. |
| SC-002 : explorateur | ✅ | Icônes, noms de fichiers et barre d'espace disque lisibles. |
| Retour arrière | ✅ | `"theme": "tron"` rétabli, relancé : apparence `tron` d'origine. |
| SC-004 / FR-006 : périmètre | ✅ | Seul `src/assets/themes/ambre.json` ajouté sous `src/`. |
| SC-005 : capture | ✅ | `capture-ambre.png`. |
