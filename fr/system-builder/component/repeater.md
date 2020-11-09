---
title: Repeater
description: 
published: true
date: 2020-09-24T12:02:29.036Z
tags: 
editor: undefined
---

Un *repeater* vous permet de créer une liste dynamique de *views/vues*. Les utilisateurs peuvent ajouter, modifier ou enlever des entrées.
Un *repeater* possède deux champs spéciaux, car il vas de paire avec deux vue de types *subcomponent* :

# Editable view
On y renseigne l'identifiant de la vue dans laquelle on édite l'entrée.

# Readable view
On y renseigne l'identifiant de la vue qui servira d'affichage à l'entrée.

### Usage
Dans la vue éditables, vous pourrez placer divers *choices*, *text imput* et *number imput* que l'utilisateur pourra remplir. Dans la vue lisible, vous pourez placer des *[labels](/system-builder/component/label)* qui afficherons les contenus des précédents *choices*, *text imput* et *number imput* grâce au système de [références](/en/system-builder/general/references).

### Craft
Vous pouvez permettre a un *reapeater* d'être "craftable", ce qui veut dire que le maître de jeu pourra créer une entrée dans l'onglet [content crafting](how-to/content-crafting) pour la déposé dans une fiche de personnage par la suite.
Pour faire cela, cochez les cases **Craft?** et **Droppable?** dans la vue éditable (attention au nom de cette vue, qui sera le nom de la catégorie de craft).
