---
title: Context Variables
description: 
published: true
date: 2020-09-04T10:51:41.134Z
tags: 
editor: markdown
---

Les variables contextuelles sont utilisable en deux endroits :

* La vue affichage d'un **Repeaters**, où les données de la vue éditable sont disponible.
* Les vues **"Bindings"**, où les données qui sont dans le script sont disponibles.

Les variables contextuelles sont appellées avec un `#` suivi du non de la variable.

Par exemple, vous avez un *repeater* avec un champ nommé `spellName` dans la vue modifiable. Sur la vue affichage, vous pouvez configurer un *label* *computed*, avec la valeur `# spellName`. Le nom du sort sera affiché dans le *label*.
