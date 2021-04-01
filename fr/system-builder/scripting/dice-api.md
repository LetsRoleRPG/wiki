---
title: Dice API
description: 
published: true
date: 2020-09-24T12:03:10.215Z
tags: 
editor: undefined
---

L'API Dice vous permet de faire des lancers de dés. Elle est disponible au travers de l'objet global `Dice`.

Example:
```javascript
init = function(sheet) {
    if (sheet.id() === "main") {
        initMain(sheet);
    }
};

initMain = function(sheet) {
    sheet.get('charisma').on('click', function() {
        Dice.roll(sheet, "3d6", "Charisma Check!");
    });
};
```

## `Dice.roll(sheet, expression, title, visibility, actions)`
**`sheet`**, type: `Sheet` *`required`*, La feuille à laquelle est attachée le lancer.
**`expression`**, type: `string`|`DiceBuilder` *`required`*, L'expression ou une instance de Dice Builder.
**`title`**, type: `string`, Le titre du lancer.
**`visibility`**, type: `string` default: `all`, La visibilité du lancer. Les valeurs possibles sont :
* `all`: le lancer sera visible par tout le monde.
* `gm`: le lancer sera visible par le propriétaire de la fiche et le MJ.
* `gmonly`: le lancer sera visible seulement par le MJ.

**`actions`**, type: `object`, Actions additionnelles pour le lancer. Les actions sont affichées comme des boutons dans l'affichage du résultat à l'écran et dans le dice log. Regardez Actions.
Retourne : `void`.

## `Dice.create(expression)`
**`expression`**, type: `string`, Une expression de base pour le DiceBuilder.
return: [`DiceBuilder`](/fr/system-builder/scripting/dice-builder)

Crée une instance du `DiceBuilder`.

## Actions

Les actions vous permettent de créer des lancers interactifs en créant un ou plusieurs boutons dans la fenêtre de résultat. Le paramètre `actions` est un `Object` avec le titre du bouton comme clé, et la fonction callback en valeur.

Exemple :
```javascript
Dice.roll(sheet, "1d20+2", "Attack", "all", {
    "Roll Damages": function(dice) {
        Dice.roll(sheet, "3d6[fire]", "Fireball"); // Jet effectué quand le joueur clique sur "Roll Damages"
    }
})
```
