---
title: Dice Result
description: 
published: true
date: 2020-09-24T12:03:14.668Z
tags: 
editor: undefined
---

Represents a dice result, rolled by a player or the GM.

# Properties

## `title`
return: `string`

Only available in the top result.

## `expression`
return: `string`

Only available in the top result.

## `visibility`
return: `string`

The visibility of the current roll. Possible values are `visible`, `gm` or `gmonly`. Only available in the top result.

## `type`
return: `string`

The type of the current roll. Possible values are `number`, `dice` or `comparison`.

## `total`
return: `number`

* For a `dice` roll: the total value of the rolls
* For a `number` roll: the result of the operation
* For a `comparison` roll: the number of success

## `tags`
return: `string[]`

Get the tags for the current roll. If you want all the tags, including in the children, use `.allTags`.

## `allTags`
return: `string[]`

Get all the tags, including the one in the children.

## `all`
return: `SingleDiceResult[]`

Get all the results of the rolled dice, including in the children. A `SingleDiceResult` is an object composed of : 

* `dimension`: `number` the number of faces of the dice
* `value`: `number` the rolled number
* `discarded`: `boolean` is this roll discarded? (for example when using `keeph`)

## `children`
return: `DiceResult[]`

Get the children of the current roll.

## `size`
return: `number`

The number of rolled dice. For example 3d6, returns 3. Returns null if the roll is not of type `dice`.

## `dimension`
return: `number`

The dimension of the dice. For example 3d6, returns 6. Returns null if the roll is not of type `dice`.

## `values`
return: `number[]`

The results of the roll. Does not include the discarded values.
Returns null if the roll is not of type `dice` 

## `discarded`
return: `number[]`

The discarded results of the roll. Returns null if the roll is not of type `dice`.

## `left` 
return: `DiceResult`

The left part of the comparison. Returns null if the roll is not of type `comparison`.

## `right` 
return: `DiceResult`

The right part of the comparison. Returns null if the roll is not of type `comparison`.

## `success` 
return: `number`

The number of successes of the comparison. Returns null if the roll is not 
of type `comparison`.

## `failure` 
return: `number`

The number of failures of the comparison. Returns null if the roll is not of type `comparison`.

# Methods

## `containsTag(tag)`
`tag`, type: `string`, The tag to lookup
return: `boolean`

Check if the current roll or any of its children contains this tag.

