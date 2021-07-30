---
title: Roll Builder
description: 
published: true
date: 2020-10-30T13:08:36.222Z
tags: 
editor: markdown
---

L'API Roll Builder vous permet de créer des jets de dés en utilisant une interface fluide.

## Initialisation

```javascript
let roller = new RollBuilder(sheet);
```

Où sheet est une instance de `Sheet`.

## Exemple

```javascript
        let roll = new RollBuilder(sheet);

        roll.expression("2d20")
            .visibility("visible")
            .addAction("Roll Damage", function() {
                Dice.roll(sheet, "3d6");
            })
            .onRoll(function(result) {
                sheet.get("rollresult").value("Total : " + result.total.toString());
            })
            .roll();
```

## API Methods

### `constructor(sheet)`
**`sheet`**, type: `Sheet`, La feuille à l'origine du lancer
retourne: `RollBuilder`

### `roll()`
retourne: `void`

Exécute le jet de dé.

### `expression(expr)`
**`expr`**, type: `string`|`DiceBuilder`, La formule de jet de dés ou l'instance `DiceBuilder` à exécuter
retourne: `RollBuilder`

### `title(title)`
**`title`**, type: `string`, Titre du jet de dés
retourne: `RollBuilder`

### `visibility(visibility)`
**`visibility`**, type: `string`, La visibilité du lancer (soit `visible`, `gm` ou `gmonly`).
retourne: `RollBuilder`

### `addAction(title, callback)`
**`title`**, type: `string`, Nom de l'action
**`callback`**, type: `Function`, La callback appelée quand l'utilisateur clique sur le bouton d'action
retourne: `RollBuilder`

### `removeAction(title)`
**`title`**, type: `string`, Nom de l'action à supprimer
retourne: `RollBuilder`

### `onRoll(callback)`
**`callback`**, type: `Function`, La fonction appelée quand le lancer est effectué. Le premier paramètre de la fonction est l'instance `DiceResult`.
retourne: `RollBuilder`