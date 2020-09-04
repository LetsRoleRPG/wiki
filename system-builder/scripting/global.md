---
title: Global Functions
description: 
published: true
date: 2020-09-04T12:55:40.271Z
tags: 
editor: markdown
---


Those functions must be defined in the global scope. If you do not want to use
one of there features, simply don't define the function.

# `init(sheet)`
**`sheet`**, type: [`Sheet`](/system-builder/scripting/sheet), The sheet to initialize
Return `void`

Initialize a sheet, as a character sheet or a craft. You can see what type of sheet it is via `sheet.id`. Tabs entries are not initialized individually, and should be initialized as if they were part of the parent view.

Example: 
```javascript
init = function(sheet) {
    if (sheet.id() === "main") {
        initMain(sheet);
    } else if (sheet.id() === "weapon") {
        initWeapon(sheet);
    }
};

const initMain = function(sheet) {
    // initialize the main sheet
    sheet.get("hp"); //...
};

const initWeapon = function(sheet) {
    // initialize the weapon sheet
}
```

# `drop(from, to)`
**`from`**, type: [`Sheet`](/system-builder/scripting/sheet), Source's sheet
**`to`**, type: [`Sheet`](/system-builder/scripting/sheet), Target's sheet
Return `void|string`  

Called when dropping a craft onto a character sheet. If you simply want to append the data to a repeater, return the repeater's id. Otherwise, you'll have to manipulate the target sheet data.

For now, it is only possible to drop craft into character sheet.

Examples:
```javascript
drop = function(from, to) {
    if (from.id() === "weapon" && to.id() === "main") {
        return "weapons"; // "weapons" is a repeater id
    }
};
```

```javascript
drop = function(from, to) {
    if (from.id() === "heal" && to.id() === "main") {
        to.get("hp").value(
            from.get("maxhp").value()
        ); // set the target's hp to the source maxhp
    }
};
```

# `dropDice(result, to)`
**`result`**, type: [`DiceResult`](/system-builder/scripting/dice-result), A dice result from the dice log.

**`sheet`**
type: [`Sheet`](/builder/documentation/sheet)
Target's sheet

For some systems, it can be usefull to drag'n drop a dice result onto the sheet. With this function, you can create interaction between the dice log and a character sheet or craft.

Example:
```javascript
dropDice = function(result, sheet) {
    if (result.containsTag("heal")) {
        let hp = sheet.get("hp");
        hp.value(hp.value() + result.total); // the character is healed by the total of the roll
    }
}
```

# `initRoll(result, callback)`
**`result`**
type: [`DiceResult`](/builder/documentation/dice-result)
A dice result from the dice log.

**`callback`**
type: `Function`
A callback to render the dice result.

This function allows you to customize the rendering of a dice result. You should call the callback with two arguments : 

* `view`: `string` the id of the view you want to use to render the dice result
* `onRender`: `Function` a function called when rendering the view, where you can change the view values. Please note the view is also initialized in the global `init` function.

Example:
```javascript
initRoll = function(result, callback) {
    callback('diceresult', function(sheet) { // diceresult is the id of the view you want to use
        sheet.get('total').text(result.total); // apply various changes to the view
        
        if (result.total > 20) {
            sheet.get('total').addClass('text-large');
        }
    });
};
```

# `getReferences(sheet)`
**`sheet`**
type: [`Sheet`](/builder/documentation/sheet)
The sheet with references

If you want to create references programmatically, you can use this method. Return an object with the reference's id as key and the reference content  as value. Values are interpreted.

Example:
```javascript
getReferences = function(sheet) {
    return {
        "halfHp": sheet.get("hp").value() / 2, // numeric value
        "defaultBonus": "5 + 8", // simple reference,
        "bonus": "@strength + @defaultBonus", // reference others
    };
}
```

# `getBarAttributes(sheet)`
**`sheet`**
type: [`Sheet`](/builder/documentation/sheet)
The sheet

Players can connect bars to some attributes with this method. It is required to have a value, and a maximum value. The method should return an `Object` with the titles as keys, and an `Array(2)`, with the first element being the value, and the second the max value.

The bar updates when the sheet is changed, and the sheet updates when the bar value is changed.

Example:
```javascript
getBarAttributes = function(sheet) {
  	if (sheet.id() === "main") {
     	return {
            "HP": ["hp", "hpmax"],
            "Quick Resource": ["quickResource", "quickResourceMax"]
        };
    }
    
    if (sheet.id() === "monster") {
     	return {
            "HP": ["hp", "hpmax"],
            "Mana": ["mana", 30] // you can use numbers directly for maximums
        };
    }
    
    return {};
};
```