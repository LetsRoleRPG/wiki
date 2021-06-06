---
title: Sheet
description: 
published: true
date: 2020-10-07T11:55:13.504Z
tags: 
editor: undefined
---

Une instance de feuille représente une feuille de personnage ou un craft.

# Methodes

## `get(id)`
**`id`**, type: `string`, L'identifiant de l'élément.
Retourne : [`Component`](/fr/system-builder/scripting/component)`|null`.

Récupère un élément.

## `getVariable(id)`
**`id`**, type: `string`, L'identifiant de la variable.
Retourne : `number|null`.

Récupère la valeur d'une variable.

## `setData(data)`
**`data`**, type: `object`
Retourne : `void`.

Définit plusieurs données de la feuille en une seule fois (incluant les valeurs des composants).
Vous ne pouvez définir qu'un maximum de 20 données à la fois.
```javascript
sheet.setData({
    "hp": 30,
    "mp": 12
    //...
});
```

## `getData()`
Retourne : `Object`.

Retourne toutes les données de la feuille en une seule fois (incluant les valeurs des composants).
```javascript
let values = sheet.Data();
/* 
values = { 
	avatar: { avatar: "y/x/....png", token: "k/g/....png"},
  hp: 30,
  mp: 12,
  ...
}
*/
```

## `prompt(title, view, callback, callbackInit)`
Voir : [API Prompt](/fr/system-builder/scripting/prompt)

## `id()`
Retourne : `string`

L'identifiant de la feuille (c'est à dire l'identifiant de la vue principale de la feuille).

## `getSheetId()`
Retourne : `number`

L'identifiant unique de la feuille (c'est à dire un numéro d'ordre de création de la feuille sur Let's Role). Permet de distinguer une feuille d'une autre feuille du même type.

## `name()`
Retourne : `string`

Le nom de la feuille.