---
title: Computed Values
description: 
published: true
date: 2020-09-24T12:02:44.104Z
tags: 
editor: undefined
---

Quelque opérations sont disponibles dans une valeur calculée. En utilisant des références et des variables, elles sont un bon moyen de rendre une feuille de personnage dynamique sans utiliser le *scripting*. 

# Values types
Vous pouvez créer une *ligne de texte* en mettant une valeur entre guillemet ("ligne de text"). Voici les règles pour les *lignes de texte* : 

* En utilisant `+` entre deux lignes de texte, elles seront concaténées :
`"hello" + " there"` -> `hello there`
* En utilisant `+` entre une ligne de texte et un nombre, le nombre sera converti en ligne de texte :
`"vous avez " + 5 + " PV"` -> `vous avez 5 PV`
Ici `5` a été changer en `"5"`.
* En utilisant n'importe quelle autres operations entre deux lignes de texte, ou entre une ligne de texte et un nombre, les lignes de texte seront convertis en le nombre `1` :
`4 - "general"` -> `3` ou `"pomme"/" terre"` -> `1`

# Mathematical operation
Vous pouvez utiliser `+` (addition), `-` (soustraction), `/` (division), `*` (multiplication) dans le calcul d'une valeur.

# Fonctions
Les fonctions prennent des termes pour leur appliquer des opérations qui ne sont pas aussi simple que les opérations mathématiques si-dessus. Les voici résumé :

# `round(value)`
Cette fonction donne l'arrondi à l'entier le plus proche d'un nombre. Pour rappel, l'entier le plus proche de 0,50 et 1, et l'entier le plus proche de 0,49 est 0.

# `floor(value)`
Donne l'arrondi inferieur d'un nombre.

# `ceil(value)`
Donne l'arrondi supérieur d'un nombre.

# `avg(value1, value2, ...)`
Donne la moyenne de tout les nombres dans les arguments.

# `sum(value1, value2, ...)`
Donne la somme des nombres dans les arguments.

# `if(comparison, then, else)`
Cette fonction vas comparé un nombre à un autre nombre (argument "comparison"), puis donner l'argument "then", ou l'argument "else".
##### Comparison
Cette argument doit contenir deux nombres, avec un comparateur entre eux. Les comparateurs sont `>`, `<` et `=`.
##### Then
Cette argument peut contenir un nombre ou une ligne de texte. Il sera afficher si la comparaison est vrais (`5 > 1` -> vrais).
##### Else
Cette argument peut contenir un nombre ou une ligne de texte ou être vide. Il sera afficher si la comparaison est fausse (`6 = 2` -> faux). S'il est vide, "else" vaux 0.

## Examples

On peu utiliser une références et une variable:
```
round(@dexterity/2) + $proficiency
```

Sommer des références:
```
sum(@dexterity, @strength, @constitution) + 5
```

On peu aussi utiliser des références comme des valeurs conditionnelles :
```
$bonus + if(@dexterity > 10, 8) 
```
