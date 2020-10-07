---
title: Sheet
description: 
published: true
date: 2020-10-07T11:55:12.161Z
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

Set multiple sheet data at once (including components values).
```javascript
sheet.setData({
    "hp": 30,
    "mp": 12
    //...
});
```

## `getData()`

Returns all the sheet data at once (including components values).
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

## `prompt(title, view, callback)`
See: [Prompt API](/en/system-builder/scripting/prompt)

## `id()`
Return: `string`

The id of the sheet (ie the id of the top view component).

## `name()`
Return: `string`

The name of the sheet.