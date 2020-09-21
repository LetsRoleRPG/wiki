---
title: Checkbox
description: 
published: true
date: 2020-09-04T11:09:04.924Z
tags: 
editor: markdown
---

Une simple case à cocher.

# Champ "Label"
Ce que vous écrivez dedans se retrouvera à droite de la case à cocher. Cliquez sur le label choechera au décochera la case.

# Retour du composant lors d'une référence
Quand vous faites référence à une case à cocher, la référence aura soit la valeur *0*, soit la valeur *"true"*, soit la valeur *1*.
+ Si la case est décochchée, la référence aura la valeur *0*.
+ Si la case est cochée et :
+ Que la référence est seule, la valeur sera *true*.
+ Que la référence est à l'intérieur d'un calcul numérique, la valeur sera *1*. (exemple : 1+@id_de_la_case => 2)
+ Que la référence est à l'intérieure d'une phrase créé par concaténation, elle sera égale à *true*. (exemple : "Ceci est "+@id => Ceci est true )
+ Que la référence est précédé et suivi de calculs et de concaténation, ce sera le therme qui suit la référence qui influencera sa valeur : Exemple 1 : "Ceci est "+ @id + 1 => Ceci est 2 Exemple 2 : 1+ @id + "Ceci est " => 1trueCeci est 
