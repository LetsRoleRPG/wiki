---
title: Sheet
description: 
published: true
date: 2020-10-07T11:51:20.081Z
tags: 
editor: undefined
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

Get a variable's value. See : [variables](/en/system-builder/general/variables)

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

## `prompt(title, view, callback, callbackInit)`
See: [Prompt API](/en/system-builder/scripting/prompt)

## `id()`
Return: `string`

The id of the sheet (ie the id of the top view component).

## `getSheetId()`
Return: `number`

The unique ID of the sheet (ie a sheet creation order index on Let's Role). Used to distinguish a leaf from another leaf of the same type.

## `name()`
Return: `string`

The name of the sheet.