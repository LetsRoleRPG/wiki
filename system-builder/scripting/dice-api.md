---
title: Dice API
description: 
published: true
date: 2020-09-04T13:45:24.495Z
tags: 
editor: undefined
---

The Dice API allows you to roll dice. It is available through the global `Dice` object.

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
**`sheet`**, type: `Sheet` *`required`*, The sheet element attached to the roll.
**`expression`**, type: `string`|`DiceBuilder` *`required`*, The expression or Dice Builder instance.
**`title`**, type: `string`, The title of the roll.
**`visibility`**, type: `string` default: `all`, The visibility of the roll. Possible values are :
* `all`: the roll will be visible by everyone
* `gm`: the roll will be visible by the sheet owner and the GM
* `gmonly`: the roll will only be visible by the GM 

**`actions`**, type: `object`, Additionals actions for the roll. Actions are displayed as buttons on the roll's result,
in the main screen and the dice log. See Actions.

return: `void`

## `Dice.create(expression)`
**`expression`**, type: `string`, A base expression for the builder.
return: `DiceBuilder`

Create a DiceBuilder instance.

## Actions

Actions allows you to create interactives rolls, by creating one or more buttons on the roll result. The actions parameters is an `Object` with the title of the button as key, and the callback as value.

For example:
```javascript
Dice.roll(sheet, "1d20+2", "Attack", "all", {
    "Roll Damages": function(dice) {
        Dice.roll(sheet, "3d6[fire]", "Fireball"); // Rolled when the player clicks "Roll Damages"
    }
})
```
