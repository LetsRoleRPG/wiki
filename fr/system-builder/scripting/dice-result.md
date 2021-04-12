---
title: Dice Result
description: 
published: true
date: 2020-09-24T12:03:14.668Z
tags: 
editor: undefined
---

Représente le résultat d'un jet de dé effectué soit par un joueur soit pas un MJ.

# Propriétés

## `title`
return: `string`

Seulement disponible dans le premier résultat.

## `expression`
return: `string`

Seulement disponible dans le premier résultat.

## `visibility`
return: `string`

La visibilité du jet de dé en cours. Les valeurs possibles sont `visible` (tout le monde voit le jet), `gm` (le joueur et le MJ voit le jet) or `gmonly` (seul le MJ voit le jet). Seulement disponible dans le premier résultat.

## `type`
return: `string`

Récupère le type du jet courant. Les valeurs possibles sont `number`, `dice` or `comparison`.

## `total`
return: `number`

* Pour un jet de type `dice` : le total des valeurs des dés
* Pour un jet de type `number` : le résultat de l'opération
* Pour un jet de type`comparison` : le nombre de succès

## `tags`
return: `string[]`

Récupère les tags du jet courant. Si vous souhaitez tous les tags en incluant ceux des enfant, utilisez `.allTags`.

## `allTags`
return: `string[]`

Récupère tous les tags du jet, notamment celui des enfants

## `all`
return: `SingleDiceResult[]`

Récupère tous les résultats du jet en incluant ses enfants. `SingleDiceResult` est un objet composé de :

* `dimension`: `number` le nombre de face du dé
* `value`: `number` la valeur du dé
* `discarded`: `boolean` renvoie `true` si le dé est rejeté (par exemple quand `keeph` est utilisé)

## `children`
return: `DiceResult[]`

Récupère les enfants du jet courant.

## `size`
return: `number`

Le nombre de dés lancés. Par exemple 3d6 retourne 3 Retourne `null` si le jet n'est pas du type `dice`.

## `dimension`
return: `number`

Le nombre de faces du dé. Par exemple 3d6 retourne 6 Retourne `null` si le jet n'est pas du type `dice`.

## `values`
return: `number[]`

Les résultats du jet. N'inclut pas les valeurs rejetées. Retourne `null` si le jet n'est pas du type `dice`.

## `discarded`
return: `number[]`

Les résultats rejetés du jet. 

## `left` 
return: `DiceResult`

La partie gauche d'une comparaison. Retourne `null` si le jet n'est pas du type `comparison`.

## `right` 
return: `DiceResult`

La partie droite d'une comparaison. Retourne `null` si le jet n'est pas du type `comparison`.

## `success` 
return: `number`

Le nombre de succès lors d'une comparaison. Retourne `null` si le jet n'est pas du type `comparison`.

## `failure` 
return: `number`

Le nombre d'échecs lors d'une comparaison. Retourne `null` si le jet n'est pas du type `comparison`.

# Méthodes

## `containsTag(tag)`
`tag`, type: `string`, le tag à rechercher<br>
return: `boolean`

Vérifie si le jet courant ou ses enfants contient ce tag.

