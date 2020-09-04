---
title: Utilities
description: 
published: true
date: 2020-09-04T13:53:57.854Z
tags: 
editor: markdown
---

# `log(var1, var2, ...)`
Log variables to the console.

# `wait(ms, callback)`
**`ms`**, type: `number`, Duration in milliseconds to wait.
**`callback`**, type: `Function`, The function to call when the timer is done.

# `parseInt(value)`
**`value`**, type: `any`, The value to convert.

Converts any value to an integer.

# `_(text)`
**`text`**, type: `string`, The text to translate.

Translate a message to the current locale.

# `each(data, callback)`
**`data`**, type: `Object` `Array`, The data to iterate over.

**`callback`**, type: `Function`, The function called for each element in the data. Return `false` if you want to stop the iteration. The first argument is the item, the second the index.

Iterates over an object or array.

Examples : 
```javascript
let animals = {
    "cat": "Meow",
    "dog": "Woof",
    "bird": "Chirp"
};

each(animals, function(noise, type) {
    log(noise);
});
``` 
# `Math`
The [Math API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math) is exposed.