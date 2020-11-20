---
title: Component
description: 
published: true
date: 2020-11-20T14:41:04.810Z
tags: 
editor: markdown
---

Represents a element that has been placed on a Sheet.

# Methods
## `parent()`
return: `Component|null`

Get the parent component.

## `find(id)`
**`id`**, type: `string`, The id of the child component.
Return: `Component|null`

Get a child component.

## `on(event, callback)`
## `on(event, delegate, callback)`
**`event`**, type: `string`, The name of the event. Possible values : `click`, `update`, `mouseenter`, `mouseleave`, `keyup`
**`delegate`**, type: `string`, Subcomponent to delegate the event to.
**`callback`**, type: `Function`, The function to call when the event is triggered. The first argument is the event.

If the event is triggered from code, it will have the property `computed` to `true`.
It's possible to delegate events to a subcomponent, useful when using repeaters.
It's only possible to have one event of the same type for a component at once. 

## `off(event)`
## `off(event, delegate)`
**`event`**, type: `string`, The name of the event. Possible values : `click`, `update`, `mouseenter`, `mouseleave`, `keyup`
**`delegate`**, type: `string`, Subcomponent to delegate the event to.

Remove an event on the component or one of its delegates.

## `hide()`
Hide the component.

## `show()`
Display the component if it has been hidden.

## `addClass(class)`
**`class`**, type: `string`, A class to add to the component.

### `removeClass(class)`
**`class`**, type: `string`, A class to remove from the component.

## `value()`
## `value(newValue)`
**`newValue`**, type: `number|string|object|null`, The new value to set.
Return: `null|number|string|object`

Get or set the value of the component. If the component is persisted, the value is permanently saved. Be carefull of not using this setter too often on persisted components, as the server has a limit of possible calls. If the component has a virtual value, it is returned. Use `component.rawValue()` to get the base, "non-virtual" value.

```javascript
let hp = sheet.get("hp"); // hp is a persisted component
log(hp.value()); // 5
hp.value(11); // update and save the new value
```

## `rawValue()`
type: `null|number|string|object`

Get or the base, "non-virtual" value of the component.

```javascript
let hp = sheet.get("hp");
hp.value(17);
log(hp.value()); // 17

hp.virtualValue(20);
log(hp.value()); // 20
log(hp.rawValue()); // 17
``` 

## `virtualValue()`
## `virtualValue(newValue)`
**`newValue`**, type: `number|string|object|null`, The new value to set.
Return: `number|string|object`

Get or set the virtual value of the component. Virtual values are usefull when you want to change a value based on calculation. For example, you could have a armor that give the character +2 HP, and set the virtual value of the hp component to its base value + 2. The the component would diplay the virtual value by default, and the raw value when hovering.

```javascript
let hp = sheet.get("hp");
hp.virtualValue(hp.rawValue() + 2);
```

## `text()`
## `text(replacement)`
**`newValue`**, type: `string`, The text to write.
Return: `null|string`

Get or set the text content of the label. The value is not computed and HTML is not allowed.

```javascript
sheet.get("job").text("Warrior");
```

## `visible()`
Return: `boolean`

Return `true` if the component is not hidden.

## `sheet()`
type: [`Sheet`](/system-builder/scripting/sheet) `readonly`

Return the sheet associated with this component.

## `setChoices(choices)`
**`choices`**, type: `object`, The choices.

Only available on Choice components, change the possible choices.

```javascript
sheet.get('class').setChoices({
    "tiger": "Big cat",
    "mouse": "Mouse",
    "kitten": "Very smol"
});
```

## `name()`
Return: `string`

Returns the name of the component as indicated in the system builder.

## `id()`
Return: `string`

Returns the id of the component as indicated in the system builder.