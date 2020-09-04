---
title: Guidelines
description: 
published: true
date: 2020-09-04T10:38:51.893Z
tags: 
editor: markdown
---

# Sheet layout
Since screens are mainly horizontal, you should design the sheet with landscape layout in mind.

# Required components
## Avatar
The avatar is required on character sheets and crafts. You can use any id you'd want, but you need to specify the id used in the view attribute : "Avatar's id".

## Color
Color is required on character sheets. The id should be : color.

# Computed values
Some component have the computed attribute, which allow them to have a value based on maths operations and references to other components.

Beware that computed values can be CPU-intensive, so you should not use too many of them.

# Scripting
**We strongly recommand you do not activate scripting if you don't know the Javascript langage.**

If you want to create advanced features, you can use Javascript to enhance your system.