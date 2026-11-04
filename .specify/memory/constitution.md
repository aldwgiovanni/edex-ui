# Constitution — eDEX-UI (fork aldwgiovanni)

Fork personnel et expérimental d'eDEX-UI (archivé en amont depuis 2021).
But : s'amuser en ajoutant des modules utiles et spectaculaires, sans casser
l'existant.

## Principes

### I. Suivre les conventions du code existant (NON NÉGOCIABLE)
JavaScript « vanilla » côté renderer, sans framework ni bundler. Un module
d'interface = une classe dans `src/classes/<nom>.class.js`, son CSS dans
`src/assets/css/mod_<nom>.css`, et son instanciation dans `src/_renderer.js`.
Un réglage = une clé dans `settings.json` (valeur par défaut gérée dans
`src/_boot.js`). Pas de nouvelle dépendance npm sans justification dans
`plan.md`.

### II. Compatible avec tous les thèmes
Un module tire ses couleurs et polices des variables CSS du thème actif
(`--color_r`, `--color_g`, `--color_b`, `--font_main`…), jamais de couleurs en
dur. Il doit rester lisible avec au moins `tron`, `matrix` et `nord`.

### III. Sobre en ressources
Collecte de données à intervalle explicite (≥ 1 s, configurable si coûteuse),
sans bloquer le thread de rendu. Un module qui échoue (outil absent, réseau
coupé) affiche un état dégradé lisible et n'interrompt pas les autres.

### IV. Sécurité
Aucun secret (token GitHub, clé API) dans le dépôt, les logs ou le DOM. Les
secrets viennent de l'environnement ou d'un fichier de config local ignoré par
Git. Toute commande système lancée par un module est fixe ou paramétrée de
façon sûre (pas d'interpolation de saisie utilisateur dans un shell).

### V. Vérifié dans l'appli
Une feature n'est terminée que lancée et constatée dans eDEX-UI sous Windows.
Environnement de référence : Node 16.20.2 portable
(`D:\tools\node-v16.20.2-win-x64`), Electron 12.2.2, node-pty précompilé
(`@homebridge/node-pty-prebuilt-multiarch@0.11.8`), cache npm et TEMP sur D:.
Les critères d'acceptation de `spec.md` sont vérifiés un par un.

### VI. Changements chirurgicaux
Chaque ligne modifiée se rattache à la feature. Pas de refactor opportuniste
du code voisin ; le code mort existant est signalé, pas supprimé.

## Interface
Tout travail d'écran charge d'abord le skill `design-patterns` ; l'esthétique
« science-fiction » existante d'eDEX-UI prime : un écart se signale.

## Gouvernance
Une feature = une branche = une PR vers `master` du fork. La constitution
prime sur les autres pratiques ; tout amendement est daté et justifié ici.

**Version** : 1.0.0 | **Ratifiée** : 2026-11-04 | **Dernière modification** : 2026-11-04
