---
title: Variables
description: 
published: true
date: 2020-09-04T10:48:45.886Z
tags: 
editor: undefined
---

On the **Table** tab, you can find a table named variables. You can add variables on the table, and reference them into computed values, or other variables, or rolls. The `id` is the name of the variable (without the $), and value is the content of the variable.

Beware that only mathematical results can be used in variable, you cannot store `string` or `object`.

To reference a variable, use the prefix `$`. The variable's name should only contain letters and underscores "_" and we strongly recommand you do not use uppercase letters.

You can set the variable's value to a simple number : 
```
23
```

You can also reference other variables and components in the value, for exemple with the following value for `bonus` : 
```
@dexterity + 3
```

So, in a label component, you could use the following roll : 
```
3d6 + $bonus
```

Then if the value of `@dexterity` is 5, the roll in this example should be `3d6 + 8`.

The variable `$bonus` can also be used in a manual roll made in the chat box, using for example `/roll 4d6 + $bonus`.

You can also set a variable to be a string, using double quotes :
```
"hello there"
```