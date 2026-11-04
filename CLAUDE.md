# edex-ui (fork personnel)

- Projet Spec Kit : constitution dans `.specify/memory/constitution.md`, suivi des features dans `.specify/memory/master-board.md` (session maître).
- Lancer l'appli sous Windows (Node 16 portable, TEMP sur D: car C: est plein) :
  `$env:Path = "D:\tools\node-v16.20.2-win-x64;" + $env:Path; $env:TEMP='D:\tmp'; $env:TMP='D:\tmp'; npm run start`
- Installer les dépendances de `src/` : `npm install` avec `npm_config_cache=D:\npm-cache` ; node-pty est l'alias `@homebridge/node-pty-prebuilt-multiarch@0.11.8` (binaire Electron 12 précompilé, ne pas recompiler).
- Pas de `codex.md` : projet JavaScript/Electron, pas .NET.
