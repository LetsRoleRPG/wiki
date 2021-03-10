---
title: Label
description: 
published: true
date: 2020-09-24T12:02:24.791Z
tags: 
editor: Tsuna77
---

Un affichage de texte non modifiable.

# Text
Ce champ contient ce qu'affichera le label. L'HTML n'est pas permis. Si le label est *computed*, l'affichage sera determiné à partir de la formule écrite dans ce champ.

# Computed
Cocher cette case si vous voulez que l'affichage du label soit calculé.

# Markdown
Cocher cette case si vous voulez activer le support markdown pour votre label.
Balises markdown actuellement autorisées :

- _italique_ `_texte en italique_`
- **gras** `**texte en gras**`
- icônes similaires à celle du composant [icône/*icon*](/system-builder/component/icon) `:icon:` -- [Liste complète accessible ici](https://fontawesome.com/icons?d=gallery&s=solid&m=free).

Si vous avez besoin de plus de balises, faites-en la demande sur Discord.

# Roll on click
Ce champ peut contenir l'expression d'un jet de dés qui sera lancé en cliquant sur le label. Vous n'avez **pas** besoin de cocher *clickable* si vous avez rempli ce champ. Vous pouvez utiliser des références dans ce champ.

# Clickable
Cocher cette case permet au label d'être cliqué. Cocher n'est pas obligatoire si vous avez déjà selectionné un *Roll on click*. Cette case est utile quand vous utiliser l'évènement "click" dans un script.

# Droppable in the QuickBar
Quand cette case est cochée, le label peut être glissé-déposé dans la barre des raccourcis du joueur.

# QuickBar label
Le titre de l'élément s'il est placé dans la barre des raccourcis. S'il est vide, le titre sera le contenu du label.
