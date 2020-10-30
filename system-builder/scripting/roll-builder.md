---
title: Roll Builder
description: 
published: true
date: 2020-10-30T13:04:33.008Z
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
                sheet.get("rollresult").value("You rolled a total of **" + result.total.toString() + "** !");
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

###