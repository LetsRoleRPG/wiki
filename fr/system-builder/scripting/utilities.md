---
title: Utilities
description: 
published: true
date: 2020-09-24T12:03:30.201Z
tags: 
editor: undefined
---

# `log(var1, var2, ...)`
Retourne `void`.
Trace le contenu des variables dans la console.

# `//region` `//endregion`
Ajoutez `//region` pour commencer une section de code que vous voulez rendre pliable, et `//endregion` pour la terminer. Ca ajoutera une flèche de pliage/dépliage.

# `wait(ms, callback)`
**`ms`**, type: `number`, La durée en millisecondes de l'attente.
**`callback`**, type: `Function`, La fonction qui sera appelée quand l'attente sera terminée.
Retourne `void`.

# `parseInt(value)`
**`value`**, type: `any`, La valeur à convertir.
Retourne `void`.

Convertit n'importe quelle valeur en un entier.

# `_(text)`
**`text`**, type: `string`, Le texte à traduire.
Retourne `string`.

Traduit un message dans la langue choisie.

# `each(data, callback)`
**`data`**, type: `Object|Array`, Les données sur lesquelles itérer.
**`callback`**, type: `Function`, La fonction appelée pour chaque élément des données. Doit retourner `false` si vous voulez arrêter l'itération. Le premier argument est l'élément courant, le second son index.
Retourne `void`.

Itère sur un objet ou un tableau.

Examples : 
```javascript
let animals = {
    "cat": "Meow",
    "dog": "Woof",
    "bird": "Chirp"
};

each(animals, function(noise, type) {
    log(noise);
});
``` 

# `Math`

L'[API Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math) est disponible.