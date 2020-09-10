---
title: Sheet
description: 
published: true
date: 2020-09-10T10:43:10.340Z
tags: 
editor: markdown
---

A Sheet instance represents a Character Sheet or Craft.

# Methods

## `get(id)`
**`id`**, type: `string`
return: [`Component`](/system-builder/scripting/component)`|null`

Get a component.

## `getVariable(id)`
**`id`**, type: `string`
Return: `number|null`

Get a variable's value.

## `setData(data)`
**`data`**, type: `object`

Set multiple components values at the same time.
```javascript
sheet.setData({
    "hp": 30,
    "mp": 12
    //...
});
```

## `.prompt(title, view, callback)
See: [Prompt API](/en/system-builder/scripting/prompt)

## `id()`
Return: `string`

The id of the sheet (ie the id of the top view component).