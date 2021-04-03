---
title: Repeater
description: 
published: true
date: 2020-09-04T11:12:00.044Z
tags: 
editor: undefined
---

A repeater allows you to setup a dynamic list of view. Users can add or remove entries. On a view, a repeater component is like a container that will contain one "readable view" for each item it contains. The "editable view" is initiated and show only to edit or add a new repeated item to the repeater.

# Editable view
The view used to edit the data. This view is initiated when you start to edit or add an item to the repeater. The ids of the components used in this view will create data that you can use in the readable view using the # in front of their id. For example, if you have a TextInput with an id "Name", you can refer this value in the readable view using a Computed Label, with the value #Name.

# Readable view
The view used by default to display informations about the entry. Use references with # to refer to the components' values used in the Editable view. If you need to parse the items in a repeater, you can use the each utility:

