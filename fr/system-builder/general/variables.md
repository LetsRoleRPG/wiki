---
title: Variables
description: 
published: true
date: 2020-09-24T12:02:59.171Z
tags: 
editor: undefined
---

Dans l'onglet **Table**, vous pouvez trouver une table nommée *variables*. Vous pouvez ajouter des variables dans cette table et les utiliser ensuite dans des valeurs et des label calculées/computed, d'autres variables, et même des jet de dés.  
Dans la colonne `id` se trouve les nom des variables (sans le $), et leur valeur sont contenu dans la colonne `value`.

Attention, seuls les valeurs mathématiques peuvent être utilisés dans une variable, vous ne pouvez pas stocker des `string` (ligne de text) ou des `object`.

Pour utiliser une variable, utiliser le prefix `$`. Le nom de la variable ne doit contenir que des lettres et des underscores `_` (tiré du huit) et nous vous recommandons vivement de ne pas utiliser de majuscules.

Vous pouvez définir la valeur de la variable comme un simple nombre :
```
23
```

Vous pouvez également appelé d'autres variables et composants dans *value*. On peu donné la valeur suivante pour `bonus` par exemple :
```
@dexterity + 3
```

Ainsi, dans un label, vous pouvez utiliser la formule de jet de dés suivante :
```
3d6 + $bonus
```

Ainsi, si la valeur de `@dexterity` est 5, le jet dans cet exemple doit être `3d6 + 8`.

La variable `$bonus` peut également être utilisée dans un jet manuel effectué dans la boîte de tchat, en utilisant par exemple `/roll 4d6 + $bonus`.

Vous pouvez également définir une variable comme une linge de texte (*string*), en utilisant des guillemets :

```
"hello there"
```
