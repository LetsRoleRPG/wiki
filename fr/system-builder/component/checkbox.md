---
title: Checkbox
description: 
published: true
date: 2020-09-24T12:02:11.984Z
tags: 
editor: undefined
---

Une simple case à cocher.

# Options
## Label
Ce que vous écrivez dans ce champ se retrouvera à droite de la case à cocher. Cliquer sur ce label cochera ou décochera la case.

# Computed
## Retour du composant lors d'une référence
Quand vous faites référence à une case à cocher, la référence aura soit la valeur *"false"*, soit la valeur *"true"*, soit la valeur *1*, soit la valeur *0*.
+ Si la case est cochée et que :
  + La référence est seule, la valeur sera *true*.
  + La référence est à l'intérieur d'un calcul numérique, la valeur sera *1*. (exemple : `1+@id_de_la_case` => 2)
  + La référence est à l'intérieur d'une phrase créée par concaténation, elle sera égale à *true*. (Exemple : `"Ceci est "+@id` => *Ceci est true* )
  + La référence est précédée et suivie de calculs et de concaténations, ce sera le terme qui suit la référence qui influencera sa valeur (Exemple 1 : `"Ceci est "+ @id + 1` => *Ceci est 2* | Exemple 2 : `1+ @id + "Ceci est "` => *1trueCeci est*)
+ Si la case est décochée et que :
  + La référence est seule, la valeur sera *false*.
  + La référence est à l'intérieur d'un calcul numérique, la valeur sera *0*.
  + La référence est à l'intérieur d'une phrase créée par concaténation, elle sera égale à *false*.
  + La référence est précédée et suivie de calculs et de concaténations, ce sera le terme qui suit la référence qui influencera sa valeur.
