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
The view used by default to display informations about the entry. Use references with # to refer to the components' values used in the Editable view. If you need to parse the entries in a repeater, you can use the `each` utility on the value() of the repeater:
```javascript
each(repeaterComponent.value(), function(entryValues){
  // do whatever you want with the data (values) of each entry
});
```
Note that entryValues object only contains the values of the input components (Checkbox, NumberInput, TextInput) used in the Editable view and the Viewer View. It is not a component by itself, so you cannot use the component methods on it.

If you need to parse the components in a readable view of a repeater, you have to find the id of the entry in the repeater (which we call the unique random entry id). This is really simple because the id of each entry of a repeater is passed as the second argument when calling the each method.

You can then access the components by two methods:

1] The first is using the global id of the components which is build as this: *repeaterId*.*uniqueRandomEntryId*.*readableViewComponentId*. Note that this method does not allow you to access component from the editor view. These components (those of the editor view) are only in the sheet during editing. Since there is no event triggered during edition, those components are not accessible with this method. Here is a small example:
```javascript
let repeaterComponent = sheet.get("repeaterComponentId");
each (repeaterComponent.value(), function(entryValues, uniqueRandomEntryId){
  let myReadableViewComponentFullId = "repeaterComponentId."+uniqueRandomEntryId+".myReadableViewComponentId"; // myReadableViewComponentFullId is the complete id of the component in the global view
  let myReadableViewComponent = sheet.get(myReadableViewComponentFullId);
  // do whatever you want you want with the component (add an event handler, etc.)
});
```

2] The second method is using the find method of the components to get the components inside a repeater. To do so, you have to access first to the entry component, which is inside the repeater. This is not the first argument of the each method! Then, this entry component contains all the components used in the viewer view AND in the editor view. Whith this method you can access to both components which might be usefull to configure the editor view (still, without any inti event triggered for the editor view, this can only be done at init of the main view for now). Here is a small example:
```javascript
let repeaterComponent = sheet.get("repeaterComponentId");
each (repeaterComponent.value(), function(entryValues, uniqueRandomEntryId){
  let entryComponent = repeaterComponent.find(uniqueRandomEntryId); // look inside the repeater to find the entry container component
  let entrySubComponent = entryComponent.find(entrySubComponentId); // it can be "myLabel" for example; this is the same id that is used in the Lets Role editor; this can also be a reference to a component of the editor view of the repeater
  // do whatever you want you want with the component (add an event handler, etc.)
});
```

If you are interested in a little more complex example, feel free to fork: https://alpha.lets-role.com/sy/jPN4xbM2mUnWcdmx
