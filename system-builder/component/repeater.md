---
title: Repeater
description: 
published: true
date: 2020-09-04T11:12:00.044Z
tags: 
editor: undefined
---

A repeater allows you to setup a dynamic list of view. Users can add or remove entries. On a view, a repeater component is like a container that will contain one "readable view" for each entry it contains. The "editable view" is initiated and show only to edit or add a new repeated entry to the repeater.

# Editable view
The view used to edit the data. This view is initiated when you start to edit or add an entry to the repeater. The ids of the components used in this view will create data that you can use in the readable view using the # in front of their id. For example, if you have a TextInput with an id "Name", you can refer this value in the readable view using a Label, with the Computed value #Name.

# Readable view
The view used by default to display informations about the entry. Use references with # to refer to the components' values used in the Editable view. If you need to parse the entries in a repeater, you can use the `each` utility:
```javascript
each(repeaterComponent, function(entryValues){
  // do whatever you want with the data (values) of each entry
});
```
Note that repeatedEntry object only contains the values of the components used in the Editable view. It is not a component by itself, so you cannot use the component methods on it.

If you need to parse the components in a readable view of a repeater, you have to find their ids. Their ids are build as this: *repeaterId*.*uniqueRandomEntryId*.*readableViewComponentId*.

To get the *uniqueRandomEntryId*, you have to use the second parameter of the function used in the `each` utility. Here is a small example:
```javascript
let repeaterComponent = sheet.get("repeaterComponentId");
each (repeaterComponent, function(entryValues, uniqueRandomEntryId){
  let myReadableViewComponentFullId = "repeaterComponentId."+uniqueRandomEntryId+".myReadableViewComponentId"; // myReadableViewComponentFullId is the complete id of the component in the global view
  let myReadableViewComponent = sheet.get(myReadableViewComponentFullId);
  // do whatever you want you want with the component (add an event handler, etc.)
});
```
