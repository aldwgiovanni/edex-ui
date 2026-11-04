# Quickstart: vérifier le thème « ambre »

## Prérequis (PowerShell)

```powershell
$env:Path = "D:\tools\node-v16.20.2-win-x64;" + $env:Path; $env:TEMP='D:\tmp'; $env:TMP='D:\tmp'; $env:npm_config_cache='D:\npm-cache'
npm install            # à la racine, si node_modules manque
cd src; npm install; cd ..
```

## 1. Contrôle de format et de contraste
- Parser `src/assets/themes/ambre.json` (ex. `node -e "JSON.parse(require('fs').readFileSync('src/assets/themes/ambre.json','utf8'))"`) : aucune erreur.
- Calculer les rapports de contraste WCAG selon les seuils de [data-model.md](data-model.md) : tous atteints.

## 2. Sélection dans l'appli
1. Dans `%APPDATA%\eDEX-UI\settings.json`, mettre `"theme": "ambre"`.
2. `npm run start`.
3. Attendu : interface ambrée sur fond brun-noir, sans modale d'erreur.

## 3. Lisibilité, zone par zone
- Panneaux gauche et droit (horloge, système, réseau) : libellés lisibles.
- Terminal : une sortie colorée (ex. `Write-Host` avec `-ForegroundColor` Red, Green, Blue, Magenta, Cyan, DarkGray) ; chaque couleur se distingue du fond.
- Clavier virtuel : touches et libellés lisibles.
- Globe : marqueurs visibles.
- Explorateur de fichiers : noms et icônes lisibles.
- Capture d'écran de l'appli entière.

## 4. Retour arrière
Remettre la valeur initiale de `"theme"`, relancer : apparence d'origine inchangée.
