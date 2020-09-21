---
title: Prompt
description: 
published: true
date: 2020-09-10T10:41:23.738Z
tags: 
editor: markdown
---

The Prompt API allows you to ask the user to fill a small form before an action. For example, if you need a modifier before a dice roll, you can prompt a small popin asking the modifier's value.

The prompt itself consist of a title, a view's id, and a callback with the data collected from the view. The view is initialized in the global `init(sheet)` function.

Example
```javascript
sheet.get('attack').on('click', function() {
    sheet.prompt('Modifiers ?', 'rollprompt', function(result) { // rollprompt is the id of the view
        // result is an object of the data of the view
        // after the user clicks "continue".
        // if the user cancel the prompt, the function is not called
        if (result.advantage) {
            Dice.roll(sheet, 'keeph(2d20)'); 
        } else {
            Dice.roll(sheet, '1d20');
        }
    });
}); 
```

# `sheet.prompt(title, view, callback)`
**`title`**, type: `string` *`required`*, The title of the prompt window.
**`view`**, type: `string` *`required`*, The ID of the view to use.
**`callback`**, type: `Function` *`required`*, The callback to get the data once the user click the "next" button. The first argument is the view's data.

# `Prompt(title, view, callback)`
> This stand-alone function has been deprecated, use sheet.prompt() instead
{.is-warning}

**`title`**, type: `string` *`required`*, The title of the prompt window.
**`view`**, type: `string` *`required`*, The ID of the view to use.
**`callback`**, type: `Function` *`required`*, The callback to get the data once the user click the "next" button. The first argument is the view's data.