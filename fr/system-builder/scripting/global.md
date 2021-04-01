---
title: Global Functions
description: 
published: true
date: 2020-09-24T12:03:24.369Z
tags: 
editor: undefined
---

Ces fonctions doivent être définies avec une portée globale. Si vous ne souhaitez pas utiliser une de ces fonctionnalités, ne définissez simplement pas la fonction.

# `init(sheet)`
**`sheet`**, type: [`Sheet`](/fr/system-builder/scripting/sheet), La feuille à initialiser.
Retourne `void`.

Initialise une feuille, comme une feuille de personnage ou de craft. Vous pouvez voir le type de feuille c'est via `sheet.id`. Les onglets de tabs ne sont pas initialisés individuellement, et devraient être initialisés comme s'ils faisaient partie de la vue parente.

Exemple : 
```javascript
init = function(sheet) {
    if (sheet.id() === "main") {
        initMain(sheet);
    } else if (sheet.id() === "weapon") {
        initWeapon(sheet);
    }
};

const initMain = function(sheet) {
    // initialize the main sheet
    sheet.get("hp"); //...
};

const initWeapon = function(sheet) {
    // initialize the weapon sheet
}
```

# `drop(from, to)`
**`from`**, type: [`Sheet`](/fr/system-builder/scripting/sheet), La feuille source.
**`to`**, type: [`Sheet`](/fr/system-builder/scripting/sheet), La feuille de destination.
Retourne `void|string`.

Cette fonction est appelée quand vous glissez-déposez un craft sur une feuille de personnage. Si vous voulez simplement ajouter les données à un repeater, retournez l'id de ce repeater. Sinon, vous devrez manipuler les données de la feuille de destination.

Pour le moment, il est seulement possible de déposer un craft dans une feuille de personnage.

Exemples :
```javascript
drop = function(from, to) {
    if (from.id() === "weapon" && to.id() === "main") {
        return "weapons"; // "weapons" is a repeater id
    }
};
```

```javascript
drop = function(from, to) {
    if (from.id() === "heal" && to.id() === "main") {
        to.get("hp").value(
            from.get("maxhp").value()
        ); // set the target's hp to the source maxhp
    }
};
```

# `dropDice(result, to)`
**`result`**, type: [`DiceResult`](/fr/system-builder/scripting/dice-result), Le résultat d'un jet de dé dans le dice log.
**`sheet`**, type: [`Sheet`](/fr/builder/documentation/sheet), La feuille de destination.
Retourne : `void`.

Pour certains systèmes, il peut être utile de glisser-déposer un résultat de jet de dé dans la feuille. Avec cette fonction, vous pouvez créer une interaction entre le dice log et une feuille de personnage ou un craft.

Exemple :
```javascript
dropDice = function(result, sheet) {
    if (result.containsTag("heal")) {
        let hp = sheet.get("hp");
        hp.value(hp.value() + result.total); // le personnage est soigné du total du jet de dé
    }
}
```

# `initRoll(result, callback)`
**`result`**, type: [`DiceResult`](/fr/system-builder/scripting/dice-result), Le résultat d'un jet de dé dans le dice log.
**`callback`**,type: `Function`, Une fonction callback pour afficher le résultat du jet.
Retourne : `void`.

Cette fonction vous permet de personnaliser l'affichage du résultat d'un jet de dé. Vous devrez appeler cette fonction callback avec ces deux arguments :

* `view`: `string` l'identifiant de la vue que vous voulez utiliser pour afficher le résultat du jet
* `onRender`: `Function` une fonction appelée lorsque la vue s'affichera, dans laquelle vous pouvez changer les données de cette vue. Merci de noter que la vue est aussi initialisée dans la fonction globale init.

Exemple :
```javascript
initRoll = function(result, callback) {
    callback('diceresult', function(sheet) { // diceresult est l'identifiant de la vue que vous voulez utiliser
        sheet.get('total').text(result.total); // appliquez différents changements à la vue
        
        if (result.total > 20) {
            sheet.get('total').addClass('text-large');
        }
    });
};
```

# `getReferences(sheet)`
**`sheet`**, type: [`Sheet`](/fr/system-builder/scripting/sheet), La feuille avec ses références.
Retourne `Object`.

Si vous souhaitez créer des références par programmation, vous pouvez utiliser cette méthode. Retourne un objet avec les identifiants des références comme clé et le contenu de la référence comme valeur. Les valeurs sont interprétées.

Exemple :
```javascript
getReferences = function(sheet) {
    return {
        "halfHp": sheet.get("hp").value() / 2, // numeric value
        "defaultBonus": "5 + 8", // simple reference,
        "bonus": "@strength + @defaultBonus", // reference others
    };
}
```

# `getBarAttributes(sheet)`
**`sheet`**, type: [`Sheet`](/fr/system-builder/scripting/sheet), La feuille à laquelle seront rattachées les barres de son token.
Retourne `Object`.

Les joueurs peuvent connecter les barres de leur token aux attributs de leur personnage avec cette fonction. Elle requière d'avoir une valeur et une valeur maximale. Cette méthode retourne un `Object` avec les titres des barres comme clés, et un `Array(2)` (tableau de deux éléments) où le premier élément est la valeur courante, et le second, la valeur maximale de la barre.

La barre du token se met à jour quand la feuille est changée, et la feuille se met à jour quand la valeur de la barre est modifiée

Exemple :

```javascript
getBarAttributes = function (sheet) { // [triggered when dropping a token onto a scene] adds options to the "Connect to" dropdown menu. The selected field will be displayed as a dynamic gauge on the token
   if (sheet.id() === "main") { // limits the code to the cases where it's a character being dropped onto the scene, as opposed to a craft for example.
      return {
         "Hunger": ['counter_hunger', 5],
         "Willpower": ["counter_willpower", "counter_willpower_max"],
         "Health": ['counter_health', 'counter_health_max']
      };
   }
   if (sheet.id() === "monster") {
     	return {
            "HP": ["hp", "hpmax"],
            "Mana": ["mana", 30] // you can use numbers directly for maximums
        };
    }
};
```

![getBarAttributes](https://user-images.githubusercontent.com/71561162/113360624-6ec1f500-934a-11eb-9b00-31f33a1198a0.png)

