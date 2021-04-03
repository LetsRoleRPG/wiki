---
title: Tables
description: 
published: true
date: 2020-09-24T12:03:28.035Z
tags: 
editor: undefined
---

Vous pouvez accéder aux tables créées dans le System Builder.

# Tables
Utilisez la constante `Tables` pour obtenir une instance de `Table`.

## `get(id)`
**`id`**, type: `string`, L'identifiant de la table.
Retourne : `Table|null`.

Retourne une instance de `Table`, ou `null` si la table n'existe pas.

# Table
Représente une table.

## `get(id)`
**`id`**, type: `string`, L'identifiant de la ligne.
Retourne : `Object|null`.

Exemple :
```javascript
let line = Tables.get("attributes").get('dexterity');
// Object { id: "dexterity", name: "Dexterity", short: "DEX" }
```

## `each(callback)`
**`callback`**, type: `Function`, La fonction appelée pour chaque ligne de la table.
Retourne : `void`.

Exemple :
```javascript
Tables.get("attributes").each(function(attribute) {
    log(attribute.name);
});
// Strength
// Dexterity
// Constitution
// ...
```

## `random(callback)`
## `random(count, callback)`
**`callback`**, type: `Function`, La fonction callback appelée avec la ligne aléatoirement sélectionnée (ou les lignes aléatoirement sélectionnées).
**`count`**, type: `number`, Le nombre de lignes à sélectionner aléatoirement. Ne doit pas être plus grand que le nombre de lignes de la table.
Retourne : `void`.

Récupère les lignes de la table en utilisant la génération aléatoire cryptographiquement sécurisée du serveur. Si `count` n'est pas spécifié ou est égal à 1, l'objet correspondant à la ligne est passé à la fonction callback. Sinon, un tableau des objets de chaque ligne est passé à la fonction callback.

```javascript
Tables.get("attributes").random(function(attribute) {
    log(attribute.name);
});
// Charisma
```

```javascript
Tables.get("attributes").random(3, function(attributes) {
    each(attributes, function(attribute) {
        log(attribute.name);
    });
});
// Strength
// Wisdom
// Dexterity
```