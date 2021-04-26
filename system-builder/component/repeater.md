---
title: Repeater
description: 
published: true
date: 2021-04-25T18:21:00.044Z
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
Note that entryValues object only contains the values of the input components (Checkbox, NumberInput, TextInput) used in the Editable view and the Readable View. It is not a component by itself, so you cannot use the component methods on it.

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

2] The second method is using the find method of the components to get the components inside a repeater. To do so, you have to access first to the entry component, which is inside the repeater. This is not the first argument of the each method! Then, this entry component contains all the components used in the readable view AND in the editor view. Whith this method you can access to both components which might be usefull to configure the editor view (still, without any inti event triggered for the editor view, this can only be done at init of the main view for now). Here is a small example:
```javascript
let repeaterComponent = sheet.get("repeaterComponentId");
each (repeaterComponent.value(), function(entryValues, uniqueRandomEntryId){
  let entryComponent = repeaterComponent.find(uniqueRandomEntryId); // look inside the repeater to find the entry container component
  let entrySubComponent = entryComponent.find(entrySubComponentId); // it can be "myLabel" for example; this is the same id that is used in the Lets Role editor; this can also be a reference to a component of the editor view of the repeater
  // do whatever you want you want with the component (add an event handler, etc.)
});
```

# How to script init READABLE VIEW of a repeater

When Lets Role needs to show a repeater entry READABLE VIEW, it does not call the global `init` function. To alter the initialization of the READABLE VIEW of a repeater, you have to listen to the `update` event of the repeater. Inside this event, which is called each time an entry has been modified and or added, you have access to all the entries of the repeater using the previous code. Here is a small example where we would like to change an icon of the READABLE VIEW according to the choice (choice1) made in the EDIT view:
```javascript
init = function(sheet){
    if(sheet.id()=="main"){
        // tests on repeaters
        let repeater1Cmp = sheet.get("repeater1");
        // add update event to initialize the VIEW VIEW
        repeater1Cmp.on("update", function(repeater){
            log("UPDATE ON "+repeater.id());
            each(repeater.value(), function (entry, entryId){   // We do not know which entry has been modified, so we do this on all entries
                let entryCmp = repeater.find(entryId);
                log("   UPDATING "+entryId);
                let iconCmp = entryCmp.find("viewIcon");
                log("   icon component is "+iconCmp.id());
                let iconName;
                switch(entry.choice1){  // get the value of the choice made in the EDITOR VIEW
                    case "R1": iconName = "plus"; break;    // if R1 icon will be +
                    case "R2": iconName = "minus"; break;   // if R2 icon will be -
                    default: iconName = "ad"; break;        // else icon will stay ad
                }
                iconCmp.value(iconName);    // change the icon of the component by settins its value
                log("   READABLE VIEW has been updated");
            });
            log("END OF UPDATE");
        });
    }
```

# How to script init EDITOR VIEW of a repeater

When Lets Role needs to show a repeater entry EDITOR VIEW, it does not call the global `init` function. To alter the initialization of the EDITOR VIEW of a repeater, you have to listen to the `click` event of the repeater. Inside this event, which is called each time a click is made on a repeater (Add button, Edit button, anynwhere inside the repeater), you have access to all the entries of the repeater using the previous code, including the new entry if you hit Add button. Be careful, as you can imagine, this event is called very often, and you need to initialized the EDITOR VIEW only for the first time it is shown for new entry (most of the time anyway). To remember which entry has its EDITOR VIEW intialized, you will have to memorize the ones you have already initialized. One way to do this is to create a global array that will contain the ids of the entries that have been already initialized, and check this array before initializing a new entry. Here is a small example where we would like to change the choices of a choice2 component in the EDITOR VIEW according to the selected value of a choice1 component of this same EDITOR VIEW:
```javascript
// write your custom scripts here
let globalRepeaterEntryInits=[];

init = function(sheet){
    if(sheet.id()=="main"){
        // add click event to initialize the EDIT VIEW
        repeater1Cmp.on("click", function(repeater){
            log("CLICK ON "+repeater.id()+" containing ");
            log(Object.keys(repeater.value()));
            each(repeater.value(), function (entry, entryId){
                let entryCmp = repeater.find(entryId);
                if(!globalRepeaterEntryInits.includes(entryId)){    // Only do this once, check if this EDIT VIEW has already been initialized
                    log("   INITIALIZING "+entryId);
                    let choice1Cmp = entryCmp.find("choice1");      // Get the choice1 componentof the EDITOR VIEW
                    log("   choice1 component is "+choice1Cmp.id());
                    choice1Cmp.on("update", function (targetCmp){   // Add an update event on choice1 component, so we can set the choice2 component choices according to choice1 value
                        log("   UPDATE "+targetCmp.id());
                        let choice2Cmp = entryCmp.find("choice2");  // Get the choice2 component of the EDITOR VIEW to change its choices
                        let choice1Val = targetCmp.value();         // Get the value of the choice1 component which is the one with the event
                        let choices = {};                           // Create the choices using the choice1 value
                        choices[choice1Val+"_1"]=choice1Val+"_1";
                        choices[choice1Val+"_2"]=choice1Val+"_2";
                        choice2Cmp.setChoices(choices);             // Set the choices choice with setChoices method
                    });
                    globalRepeaterEntryInits.push(entryId);         // Do not forget to add the id of the entry to tell the system it has already been initialized
                    log("   EDITOR VIEW has been initialized");
                }
            });
            log("END OF CLICK");
        });
    }
    // ...
};
```

If you are interested in a little more complex example, feel free to fork: https://alpha.lets-role.com/sy/jPN4xbM2mUnWcdmx
