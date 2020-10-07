---
title: Tables
description: 
published: true
date: 2020-09-04T13:52:06.064Z
tags: 
editor: undefined
---

You can access the tables created in the builder.

# Tables
Use the `Tables` constant to get a `Table` instance.

## `get(id)`
**`id`**, type: `string`, The id of the table.

Returns : a `Table` instance, or `null` is the table does not exists.

# Table
Represents a table.

## `get(id)`
**`id`**, type: `string`, The id of the line.

Example:
```javascript
let line = Tables.get("attributes").get('dexterity');
// Object { id: "dexterity", name: "Dexterity", short: "DEX" }
```

## `each(callback)`
**`callback`**, type: `Function`, The function called on each line.

Example:
```javascript
Tables.get("attributes").each(function(attribute) {
    log(attribute.name);
});
// Strength
// Dexterity
// Constitution
// ...
```

## `random(callback)`
## `random(count, callback)`
**`callback`**, type: `Function`, The function called with the random line (or random lines).
**`count`**, type: `number`, The number of random lines. Cannot be larger than the size of the table.

Extract lines from the table using server side cryptographically secure randomness. If `count` is not specified or `count` is 1, the line is passed to the callback. Otherwise, an array of lines is passed to the callback.

```javascript
Tables.get("attributes").random(function(attribute) {
    log(attribute.name);
});
// Charisma
```

```javascript
Tables.get("attributes").random(3, function(attributes) {
    each(attributes, function(attribute) {
        log(attribute.name);
    });
});
// Strength
// Wisdom
// Dexterity
```