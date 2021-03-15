---
title: Choice
description: 
published: true
date: 2020-09-24T12:02:14.129Z
tags: 
editor: undefined
---

Ce composant vous permettra de créer des choix à menus déroulants, et des questionnaires à choix multiples ou à choix unique. 

# Options
## Table
On y renseigne la [table](/system-builder/scripting/tables) dans laquelle les choix possibles sont écrits. Il y aura un choix par ligne dans cette table.

## List Label
On y renseigne la colonne de la table dont le contenu sera affiché par le composant. Par défaut, la colonne "id" est utilisée.

## Optional
Cochée, elle ajoute un choix vide qui sera sélectionné par défaut (au lieux du choix de la première ligne de la table). Cela permet d'éviter de créer une ligne vide dans la table.

## Etendu
Cocher *Expanded* changera le menu déroulant en liste d'objet avec des cases à cocher ou des radiobox à gauche.

## Expanded item classes
Ce champ permet de modifier l'apparence des objets quand ils sont étendus, cela utilise les mêmes règles que les *classes* des composants.

## Multiple
Cette case à cocher permet de transformer un choix unique étendu (case *Expanded* cochée) en choix multiple.

# Script
## Référence
Quand vous faites référence à un choix/*choice*, la valeur de cette référence correspond à ce qui est indiqué dans la colonne "id" et dans la ligne du choix correspondant.
Si aucun choix n'est fait, la référence sera égale à 0. Si plusieurs choix sont cochés (Case *Multiple* cochée) chaque identifiant sera séparé d'une virgule.

# Spécificités
## Class et Race
Si votre choix a comme id `class` ou `race` dans votre fiche de personnage alors ces champs apparaîtront dans votre liste de personnage, juste en dessous du nom du personnage.
