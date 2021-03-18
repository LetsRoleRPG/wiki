---
title: Guidelines
description: 
published: true
date: 2020-09-04T10:39:44.294Z
tags: 
editor: undefined
---

# Sheet layout
Since screens are mainly horizontal, you should design the sheet with landscape layout in mind.

# Required components
## Avatar
The avatar is required on character sheets and crafts. You can use any id you'd want, but you need to specify the id used in the view attribute : "Avatar's id".

## Color
Color is required on character sheets. The id should be : `color`.

# Display character level, race and class in *My Characters* manager
It is possible to display the level, race and class of your character on its miniature in the *My Characters* menu.
To do so, use the exact `level`, `race`, and/or `class` ids respectively for the matching components in your sheet.

You can also use the race or class id on a component to display any string of your choice instead, by populating it with a custom string. You could for example use script to concatenate other fields than level, race or class.

# Computed values
Some component have the computed attribute, which allow them to have a value based on maths operations and references to other components.

Beware that computed values can be CPU-intensive, so you should not use too many of them.

# Scripting
**We strongly recommand you do not activate scripting if you don't know the Javascript langage.**

If you want to create advanced features, you can use Javascript to enhance your system.
