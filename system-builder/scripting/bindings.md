---
title: Bindings
description: 
published: true
date: 2020-09-04T13:47:43.582Z
tags: 
editor: undefined
---

Bindings allow players to reference an element of their character sheet in the chat. With this API, you have full control over what bindings are available, and how they are displayed.

A binding is created with 4 elements : 

 * **name** `string` : the name used in the chat to reference the binding
 * **componentId** `string` : the id of the component referenced. You can have several bindings for a single componentId, for example in repeaters
 * **viewId** `string` : the id of the view used to display the binding
 * **data** `Function` : a function that returns an object of data passed to the view for rendering. This data will be available in the view
 
Bindings are available thought the global `Bindings` constant.

# `Bindings.add(name, componentId, viewId, dataCallback)`
**`name`**, type: `string` *`required`*, The name used in the chat.
**`componentId`**, type: `string` *`required`*, The id of the component used.
**`viewId`**, type: `string` *`required`*, The view used for rendering.
**`dataCallback`**, type: `Function`, A function returning an object that will be passed to the view. The object must be serializable in JSON.

# `Bindings.send(sheet, name)`
**`sheet`**, type: `Sheet` *`required`*, The sheet element attached to the binding.
**`name`**, type: `string` *`required`*, The name of the binding.

Sends a binding into the chat. The binding must have been registered with `Binding.add()`.

# `Bindings.remove(name)`
**`name`**, type: `string` *`required`*, The name of the binding.

Remove one binding by its name.

# `Bindings.clear(componentId)`
**`componentId`**, type: `string` *`required`*, The component's id to clear.