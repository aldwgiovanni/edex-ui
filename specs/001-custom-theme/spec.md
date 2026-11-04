# Feature Specification: Thème personnalisé

**Feature Branch**: `claude/001-custom-theme-5623ae`

**Created**: 2026-11-04

**Status**: Draft

**Input**: User description: "Thème personnalisé : ajouter à eDEX-UI un thème original propre à l'utilisateur, dans src/assets/themes/<nom>.json, au même format que les thèmes existants (tron, matrix, nord). Identité visuelle cohérente (nom, palette, police déjà embarquée). Le thème se sélectionne via le réglage theme ; panneaux, terminal, clavier, globe et explorateur lisibles ; aucune modification du code hors besoin strict ; capture d'écran. Hors périmètre : sélecteur de thème dans l'interface, modification des thèmes existants."

## Clarifications

### Session 2026-11-04

- Q: Quelle identité visuelle le thème doit-il porter (nom, palette, ambiance) ? → A: piste A « ambre » : écran phosphore ambré rétro, accent #ffb000 sur fond brun-noir #0b0802, polices United Sans (interface) et Fira Mono (terminal), curseur bloc, globe ambré (choix de l'utilisateur relayé par la session maître).

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Activer son propre thème (Priority: P1)

L'utilisateur indique le nom de son thème dans le réglage `theme` de ses préférences, relance eDEX-UI et retrouve toute l'interface habillée de son identité visuelle.

**Why this priority**: c'est la valeur de la feature : un thème qui n'existe pas ou ne se charge pas ne sert à rien.

**Independent Test**: régler `theme` sur le nom du nouveau thème, lancer l'appli, constater que les couleurs et polices du thème sont appliquées partout.

**Acceptance Scenarios**:

1. **Given** une installation où le réglage `theme` vaut le nom du nouveau thème, **When** l'utilisateur lance eDEX-UI, **Then** l'interface s'affiche avec la palette et les polices du thème, sans message d'erreur.
2. **Given** le thème actif, **When** l'utilisateur remet `theme` sur `tron`, **Then** l'interface revient à l'apparence `tron` inchangée.

---

### User Story 2 - Tout reste lisible (Priority: P1)

Avec le thème actif, l'utilisateur lit sans effort le terminal (y compris les couleurs ANSI d'une sortie courante), les panneaux de gauche et de droite, le clavier virtuel, le globe réseau et l'explorateur de fichiers.

**Why this priority**: un thème beau mais illisible est un défaut, pas une feature.

**Independent Test**: thème actif, parcourir chaque zone et lancer une commande colorée dans le terminal ; vérifier le contraste texte / fond.

**Acceptance Scenarios**:

1. **Given** le thème actif, **When** l'utilisateur tape une commande qui produit du texte coloré, **Then** chaque couleur se distingue du fond.
2. **Given** le thème actif, **When** l'utilisateur regarde le clavier, le globe et l'explorateur, **Then** les libellés, marqueurs et noms de fichiers sont lisibles.

---

### Edge Cases

- Police déclarée absente du dossier des polices embarquées : le thème doit n'utiliser que des polices déjà livrées.
- Fenêtres modales d'erreur et d'avertissement : elles doivent rester distinguables (couleurs rouge / jaune) avec le thème.
- Les thèmes existants ne doivent pas être modifiés ni changer d'apparence.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: Un nouveau thème MUST être livré avec les thèmes intégrés, au même format que ceux-ci (couleur principale, noirs et gris de fond, polices, palette du terminal, couleurs du globe).
- **FR-002**: Le thème MUST être sélectionnable par son nom via le réglage `theme` existant, sans autre manipulation.
- **FR-003**: Le thème MUST n'utiliser que des polices déjà embarquées dans l'application.
- **FR-004**: Le texte principal du thème MUST présenter un rapport de contraste d'au moins 7:1 avec son fond, et chaque couleur ANSI du terminal (hors noir) au moins 4,5:1 avec le fond du terminal.
- **FR-005**: Le thème MUST définir les couleurs d'erreur et d'avertissement utilisées par les fenêtres modales.
- **FR-006**: La livraison MUST NOT modifier les thèmes existants ni le code de l'application, sauf besoin strict justifié.
- **FR-007**: Le thème MUST s'appeler « ambre » et porter l'ambiance d'un écran phosphore ambré : accent ambre #ffb000 sur fond brun-noir #0b0802, polices United Sans (interface) et Fira Mono (terminal), curseur bloc, globe ambré.

### Key Entities

- **Thème**: un fichier nommé d'après le thème ; contient couleur d'accent, fonds, polices, palette du terminal, couleurs du globe, styles additionnels éventuels.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Le thème se charge au premier lancement après réglage, sans erreur, dans 100 % des essais.
- **SC-002**: Les 5 zones (panneaux, terminal, clavier, globe, explorateur) sont jugées lisibles lors de la vérification dans l'appli.
- **SC-003**: Les rapports de contraste de FR-004 sont tous atteints (vérification calculée).
- **SC-004**: Zéro ligne modifiée dans les thèmes existants.
- **SC-005**: Une capture d'écran de l'appli avec le thème actif est jointe au rapport final.

## Assumptions

- La sélection passe par l'édition de `settings.json` puis relance ; aucun sélecteur dans l'interface (hors périmètre).
- Les thèmes intégrés sont recopiés dans le dossier utilisateur à chaque lancement : le nouveau thème y apparaît sans action manuelle.
- L'esthétique « science-fiction » d'eDEX-UI (interface sombre ou claire monochrome à accent unique) prime.
- Vérification sous Windows dans l'environnement de référence de la constitution.
