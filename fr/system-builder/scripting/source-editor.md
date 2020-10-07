---
title: Directly editing the source of the tree
description: 
published: true
date: 2020-09-24T12:03:25.875Z
tags: 
editor: undefined
---

If you know what you are doing, you can edit the source of the tree by clicking on *Source Editor*.

> We do not recommand using the source editor if you do not know how to manage JSON document. It's very easy to break the whole system you're building.
{.is-warning}

# Fields

There are a few fields available in the source :

## Common
There fields are available on all components.

### id `string`
### name `string`
### classes `string`
The CSS classes applied to the component
### children `array`
### className `string`
The internal class name of the component
### collapsed `boolean`
UI Only. Set to `true` to collapse the component in the *View* window.
### references `array`
> Do not edit this field manually
{.is-danger}

Automatically computed list of referenced fields.

## Checkbox
### label `string`

## Choice
### label `string`
### tableId `string`
The table where the data is stored
### optional `boolean`
If the choice can be empty
### expanded `boolean`
### multiple `boolean`
### expandedClass `string`
The class applied to each expanded option

## Column
### size `number`

## Container
### layout `string`
Either `horizontal` or `vertical`

## Icon
### iconName `string`
The name of the icon (its CSS class)
### roll `string`
The roll to throw when clicking the icon
### rollTitle `string`

## Label
### text `string`
### align `string`
Either `Left`, `Right` or `Center`
### clickable `boolean`
### quickBar `boolean`
Can the label be put in the quickbar
### quickBarLabel `string`
### computed `boolean`
### roll `string`
The "roll on click" value

## NumberInput
### min `number`
### max `number`
### defaultValue `number`
### align `string`
Either `Left`, `Right` or `Center`
### computed `boolean`
### computedValue `string`

## Repeater
### readViewId `string`
The view for reading data.
### viewId `string`
The view for editing data.

## Tab
### tableId `string`
The table where the tab data is stored
### titleAttribute `string`
The name of the column storing the title of the tab
### viewAttribute `string`
The name of the column storing the view id of the tab
### vertical `boolean`
### verticalWidth `number`
### verticalText `boolean`
Display the text also vertically
### verticalAlign `string`
Value can be either `left` or `right`.

## Textarea
### placeholder `string`
### defaultValue `string`
Also used for the computed value.
### computed `boolean`

## TextInput
### placeholder `string`
### defaultValue `string`
Also used for the computed value.
### computed `boolean`

## View
### type `string`
The type of the view, either `Main` or `SubComponent`.
### craft `boolean`
Is this view representing a craft ?
### avatarId `string`
The id of the avatar in this view
### tokenizable `boolean`
For crafts, if they can have tokens
### droppable `boolean`
For crafts, if they can be dropped on a sheet
### width `number`
### height `number`