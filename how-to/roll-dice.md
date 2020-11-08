---
title: How to roll dice
description: 
published: true
date: 2020-09-08T10:04:24.014Z
tags: 
editor: undefined
---

# Via your character sheet
Most of character sheets include the roll dice functionality. You can click on a text or a button to see your dice roll automatically!

# Via the chat
You can also roll dice through the chat by typing `/r formula`. The formula is based on our roll syntax [which you can test here](https://roll.lets-role.com/).

A few examples: 

 - `/r 3d6`
 - `/r 1D100>55`
 - `/r keeph(2d20)`

There are several commands you can use to roll dice:

 - `/roll` (or `/r`) will throw dice visible to anyone
 - `/gmroll` (or `/gr`) will throw dice only visible to you and the GM
 - `/gmonlyroll` (or `/gor`) will throw dice only visible to the GM (not even yourself)

## Using references within rolls
You can add references to some elements from your character sheet within a roll by using `@`. For example:

 - `/r 1d20 + @str_mod`