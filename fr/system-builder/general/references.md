---
title: References
description: 
published: true
date: 2020-09-24T12:02:50.501Z
tags: 
editor: undefined
---

Les références sont utilisées pour connecter les valeurs des composants entre eux. Par exemple, vous pouvez avoir une composante numérique `charisme` et une autre `persuasion`. Si vous voulez que la valeur de `persuasion` soit égale à 5 + le charisme, définissez simplement la valeur calculée sur `5 + @charisma`. Lorsque l'utilisateur met à jour la valeur de `charisme`, la valeur de `persuasion` se met automatiquement à jour.

Il est possible de lier une référence à une autre référence. Par exemple, `charisme` pourrait avoir une valeur de `7 + @compétence` et ainsi de suite.

Il y n'y a qu'une seule restriction : vous ne pouvez pas avoir de références circulaires; comme `charisme=5+@beauté` et `beauté=2+@charisme` Si vous faites une référence circulaire, vous aurez une erreur dans la console et la valeur sera `0`.
