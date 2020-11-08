---
title: Rolling Dice
description: 
published: true
date: 2020-09-24T12:03:00.035Z
tags: 
editor: undefined
---

You can prompt a dice roll in a label component, using the "Roll on Click" property.

The whole dice rolling API can be found here : [https://roll.lets-role.com](https://roll.lets-role.com). The only difference is that you can use *component references* and *variables*.

Be aware that the **computed API** is not the same as the **dice rolling API**. This means you cannot use functions available in computed (like `if`) in dice rolling, and you cannot use dice like `3d6` in computed values. 

# References
See: [References](/system-builder/general/references).

You can reference other components in a roll, using the `@id` syntax. For example, if you have a number input with an id `dexterity` and a value of 8, you could set the roll to `1d20 + @dexterity`. When the user click on the label, they would roll 1d20 + 8. References can also be used in the chat window in a game, for example by writing `/roll 1d8 + @dexterity`. References are automatically updated.

# Variables
See: [Variables](/system-builder/general/variables).

Variable are like reference, but pointing to a value in a **table**. You can use the same functions and operations as in references. Variables are used via `$id`.