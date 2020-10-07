---
title: References
description: 
published: true
date: 2020-09-24T12:02:50.501Z
tags: 
editor: undefined
---

References are used to connect components values between them. For example, you could have a number component `charisma`, and another `persuasion`. If you want the value of `persuasion` to be 5 + the charisma, simply set the computed value to `5 + @charisma`. When the user update the value of `charisma`, the value of `persuasion` would automatically update. 

It is possible to link a reference to another reference. For example, `charisma` could have a value of `7 + @proficiency`. And so on.

The only restriction is that you cannot have circular references. If you make a circular reference, you will have an error in the console, and the value will be `0`.