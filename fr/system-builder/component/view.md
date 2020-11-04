---
title: View
description: 
published: true
date: 2020-09-04T11:03:09.469Z
tags: 
editor: markdown
---

Une vue est l'élément principal d'une fiche/*sheet*, d'un *craft*, d'un élément de la fiche (comme le contenu d'un onglet ou un *reapeater*) ou d'un *prompt*.
Elle se trouve au sommet de l'arborescence. On en créé de nouvelle en en cliquant sur le + au dessus de "*source editor*". On les supprime avec un clique droit et on les modifie comme les autres composants, grâce au champs sur le droite de l'écran.

# Les types de vues/views
## Main View
C'est le type destiné à la feuille de personnage, car c'est la vue/view de ce type qui sera utilisée lors de la création d'un nouveau personnage. __Il ne peut y avoir qu'une seule *Main View*.__

## SubComponent View
Les *SubComponent Views* peuvent être utilisée comme des parties d'autre vues/views. Par exemple, les vues de ce type associées à un [onglet/*tab*](/system-builder/component/tabs) seront affichées dans la vue ou ce dernier ce trouve. Ce type de vue est aussi utiliser dans les *craft*, les [*reapeater*](/system-builder/component/repeater) et les *prompt*.

# Options

## Type
Vous pouvez changer le type de vue après création.

## Craft
Cocher la case rend disponible la vue en tant que *craft* dans le *content crafting*.

## Width, Height
Ce sont les dimensions de la vue en pixels. Elles s'affichent en points-tillé dans le mode preview du système builder. Le minimum est 400x275, le maximum 950x600.

## Tokenizable
Seules les vues craftable peuvent cocher cette case leur permettant d'être glissée déposée sur la carte par le maître de jeu depuis le *content crafting*. On l'utilise notamment pour les monstres et les personnages non joueurs.
La vue doit aussi contenir un composant [Avatar](/system-builder/component/avatar) pour que cela fonction (vous pourrez cochez la cases, mais sans avatar, aucun token n'apparaîtra).

## Droppable
Disponible seulement pour les craft, cette case permet au maître de jeu de glisser déposer le *craft* depuis le *content crafting* vers une fiche de personnage ou un autre craft.
Un script qui dicte ce que doit ce passer quand le craft est déposé est requis.

## Avatar's id
On y renseigne l'identifiant du composant *avatar* qui correspond à la vue.
