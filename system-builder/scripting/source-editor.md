---
title: Directly editing the source of the tree
description: 
published: true
date: 2020-09-11T12:25:00.017Z
tags: 
editor: markdown
---

If you know what you are doing, you can edit the source of the tree by clicking *Source Editor*.

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

##