---
title: Rolling Dice
description: 
published: true
date: 2020-09-24T12:03:00.035Z
tags: 
editor: undefined
---

Vous pouvez lier un jet de dés à un label ou une icon, grâce à l'option "Roll on Click". Ainsi quand un utilisateur cliquera sur le label ou l'icon, les dés seront lancés automatiquement.

L' API des jet de dés est disponible ici : [https://roll.lets-role.com](https://roll.lets-role.com). La seul différence est que vous pouvez utiliser des références et des variables dans la formule de dés.

Attention : l'**API de calcul** *(computed API)* est différente de l'**API de lancer de dés** (dice API). Ce qui signifie que vous ne pouvez pas utiliser les fonctions disponibles en calcul, comme `if`, dans le lancer de dés ; et vous ne pouvez pas utiliser de formule de dés comme `3d6` dans les valeurs calculées.  
Notez que cette incompatibilité peut-être contournée grâce aux références et au variables, qui peuvent être utilisées par la *dice API* alors qu'elle sont calculées par la *computed API*.

# Réferences
A voir : [References](/system-builder/general/references).

Vous pouvez faire référence à un autre composant dans un jet de dés en écrivant `@id`.

Par exemple, si vous avez un *number input* dont l'identifiant est `dextérité` et dont la valeur est 8 ; vous pouvez écrire dans le champ "Roll on click" d'un label la formule `1d20 + @dextérité`, ce qui lancera `1d20 + 8`.  
Vous pouvez aussi utiliser les références dans la fenêtre de tchat (en écrivant `/roll 1d8 + @dextérité` par exemple)

# Variables
A voir : [Variables](/system-builder/general/variables).

Les variables sont comme les références, fonctionnent de la même manière et ont le même usage. Il y a cependant deux différence entre les deux :
* contrairement à ces dernières, les variables sont contenut dans la **table "variables"** et non dans un composant. (Cette table est disponible par défaut dans le système builder, mais est vide au départ.)
* On appelle les variables via `$id` (et non @).

### Exemple
Voici quelque exemple de formule de dés :  
`1d20 + @force`
`@forced8 - $faible`
`1d$force * @avantage`
