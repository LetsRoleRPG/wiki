---
title: Roll Builder
description: 
published: true
date: 2020-10-30T13:08:36.222Z
tags: 
editor: markdown
---

The Roll Builder API allows you to create rolls using a fluid interface.

## Initialization
```javascript
let roller = new RollBuilder(sheet);
```

Where sheet is a `Sheet` instance.

## Example

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
**`sheet`**, type: `Sheet`, The sheet linked to the roll
return: `RollBuilder`

### `roll()`
return: `void`

Submit the roll.

### `expression(expr)`
**`expr`**, type: `string`|`DiceBuilder`, The dice formula or dice builder instance
return: `RollBuilder`

### `title(title)`
**`title`**, type: `string`, Title of the roll
return: `RollBuilder`

### `visibility(visibility)`
**`visibility`**, type: `string`, The visibility of the roll (either `visible`, `gm` or `gmonly`).
return: `RollBuilder`

### `addAction(title, callback)`
**`title`**, type: `string`, Name of the action
**`callback`**, type: `Function`, The callback when the user clicks on the action
return: `RollBuilder`

### `removeAction(title)`
**`title`**, type: `string`, Name of the action to remove
return: `RollBuilder`

### `onRoll(callback)`
**`callback`**, type: `Function`, The function to call when to roll is done. First parameter of the function is a `DiceResult` instance.
return: `RollBuilder`