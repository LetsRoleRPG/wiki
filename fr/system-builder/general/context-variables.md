---
title: Context Variables
description: 
published: true
date: 2020-09-04T10:51:41.134Z
tags: 
editor: markdown
---

Context variables are available in two places : 

* **Repeaters** read view, where the data of the editable view is available
* **Bindings** view, where the data passed in the scripting is available

Context variables are accessed with `#` followed by the name of the variable.

For example, you have a repeater with a field named `spellName` in the editable view. On the readable view, you can setup a computed label, with the value `#spellName`. The spell name will be displayed in the label.