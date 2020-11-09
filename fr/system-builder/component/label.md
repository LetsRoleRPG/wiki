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
Ce champ contient ce qu'affichera le label. L'HTML n'est pas permis. Si le label est *computed*, l'affichage sera determiner à partir de la formule écrite dans ce champ.

# Computed
Cocher cette case si vous vouler que l'affichage du label soit calculé.

# Markdown
Check this box if you want to activate markdown support for your label. 
Current markdown mark allowed :

- _italic_ `_italicText_`
- **bold** `**boldText**`
- icons like the [Icon](/system-builder/component/icon) component `:icon:` -- [Full list here](https://fontawesome.com/icons?d=gallery&s=solid&m=free).

If you need more support please ask for an update on discord

# Roll on click
Ce champ peux contenir l'expression d'un jet de dés qui sera lancer en cliquant sur le label. Vous n'avez **pas** besoin de cocher "*clickable*" si vous avez rempli ce champ. Vous pouvez utiliser des références dans ce champs.

# Clickable
Cocher cette case permet au label d'être cliquer. Cocher n'est pas obligatoir si vous avez ajouter un "Roll on click". Cette case est utile quand vous utiliser l'évènement "click" dans un script.

# Droppable in the QuickBar
Quand cette case est cochée, le label peux être glissé-déposé dans la barre des raccourcis du joueur.

# QuickBar label
Le titre de l'élément s'il est placer dans la barre des raccourcis. S'il est vide, le titre sera le contenut du label.
