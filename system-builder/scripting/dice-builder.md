---
title: Dice Builder
description: 
published: true
date: 2020-09-04T13:40:14.405Z
tags: 
editor: markdown
---

The Dice Builder is a fluid API to create dice rolls.

# Examples

Basic usage : 
```javascript
let dice = Dice.create(8).add(5); // 8 + 5
```

```javascript
let dice = Dice.create("3d6").add(5); // 3d6 + 5
let dice = Dice.create("3d6").add('@dexterity'); // 3d6 + @dexterity
let dice = (new DiceBuilder("3d6")).add(5); // 3d6 + 5
```

```javascript
let dice = Dice.create("3d6");
let extra = Dice.create("2d8").minus(5);
let final = dice.add(extra); // 3d6 + (2d8 - 5)
```

Using functions : 
```javascript
let dice = Dice.create("1d20")
    .add(5)
    .divide(2)
    .round();
    // round((1d20 + 5)/2)
```

Advanced example :
```javascript
let dice = Dice.create("3d6")
    .compare(">", 10)
    .ternary("1d20", "1d10")
    .tag("fire", "attack")
    // (3d6 > 10 ? 1d20 : 1d10)[fire, attack]
```

Dice Builder instances can be directly passed to the `Dice.roll` method :
```javascript
init = function(sheet) {
    sheet.get('attack').on('click', function() {
        let dice = Dice.create('2d20')
            .keeph()
            .tag('advantage');
        
        Dice.roll(sheet, dice, 'My attack with advantage');
    });
};
```

# Methods

Theses methods are available:

* `.add(value)`
* `.minus(value)`
* `.multiply(value)`
* `.divide(value)`
* `.tag(tag1, tag2, ...)`
* `.compare(type, right, weights)`
* `.round()`
* `.ceil()`
* `.floor()`
* `.keeph(max)`
* `.keepl(max)`
* `.remh(max)`
* `.reml(max)`
* `.expl(explode1, explode2, ...)`
* `.expladd(explode1, explode2, ...)`
* `.mul(multiplier)`
* `.reroll(reroll1, reroll2, ...)`
* `.rerolln(reroll1, reroll2, ..., max)`
* `.ternary(then, else)`