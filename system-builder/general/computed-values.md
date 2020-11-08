---
title: Computed Values
description: 
published: true
date: 2020-09-04T10:50:32.629Z
tags: 
editor: undefined
---

A few mathematical operations are available in a computed value. Using references and variables, it's a great way to make a dynamic character sheet, without having to use scripting.

# Values types
You can create a string value by putting the value between double quote ("my string"). Here are the common rules of string values : 

* When using `+` between two strings, they will be concatenated : 
`"hello" + " there"` -> `hello there`
* When using `+` between a string and a number, the number will be converted
to a string : `"you have " + 5 + " hp"` -> `you have 5 hp`
* When using any other operation between two strings, or a string and a number,
the string will be converted to the number `1` : `4 - "general"` -> `3`

# Mathematical operation
You can use `+` (adding), `-` (substracting), `/` (dividing), `*` (multiplying) in a computed value.

# `round(value)`
Returns the value rounded to the nearest integer. If the value if .5, it is rounded to the higher integer (for example `round(4.5)` = 5).

# `floor(value)`
Returns the largest integer less than or equal to the value.

# `ceil(value)`
Always rounds the value up to the next largest whole number or integer.

# `avg(value1, value2, ...)`
Get the average for all the values in the arguments.

# `sum(value1, value2, ...)`
Get the sum of all the values in the arguments.

# `if(comparison, then, else)`
If the comparison is a success, returns the "then", otherwise the "else".
If "else" is not set, else equals 0.

## Examples

Using a reference and a variable:
```
round(@dexterity/2) + $proficiency
```

Adding references:
```
sum(@dexterity, @strength, @constitution) + 5
```

Conditional value:
```
$bonus + if(@dexterity > 10, 8) 
```