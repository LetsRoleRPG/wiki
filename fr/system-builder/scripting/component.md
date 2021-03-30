---
title: Component
description: 
published: true
date: 2020-11-20T14:41:04.810Z
tags: 
editor: markdown
---

Représente un composant qui est placé sur une feuille.

# Methods
## `parent()`
Retourne : `Component|null`.

Récupère le composant parent.

## `find(id)`
**`id`**, type: `string`, L'identifiant du composant enfant.
Retourne : `Component|null`.

Récupère un élément enfant.

## `on(event, callback)`
## `on(event, delegate, callback)`
**`event`**, type: `string`, Le nom de l'évènement. Valeurs possibles : `click`, `update`, `mouseenter`, `mouseleave`, `keyup`.
**`delegate`**, type: `string`, Le composant enfant auquel déléguer l'évènement.
**`callback`**, type: `Function`, La fonction qui sera appelée quand l'évènement surviendra. Le premier argument est l'évènement.
Retourne : `void`.

Si l'évènement survient à cause du script, il aura la propriété `computed` à `true`.
Il est possible de déléger les évènements à un composant enfant, pratique quand vous utilisez les repeaters.
Il n'est possible d'avoir qu'un évènement du même type à la fois pour un même composant.

## `off(event)`
## `off(event, delegate)`
**`event`**, type: `string`, Le nom de l'évènement. Valeurs possibles : `click`, `update`, `mouseenter`, `mouseleave`, `keyup`.
**`delegate`**, type: `string`, Le composant enfant auquel déléguer l'évènement.
Retourne : `void`.

Retire un évènement du composant ou de l'un de ses composants enfants délégués.

## `hide()`
Retourne : `void`.

Masque le composant.

## `show()`
Retourne : `void`.

Affiche le composant si celui-ci est masqué.

## `addClass(class)`
**`class`**, type: `string`, Une classe à ajouter au composant.
Retourne : `void`.

### `removeClass(class)`
**`class`**, type: `string`, Une classe à retirer du composant.
Retourne : `void`.

## `value()`
## `value(newValue)`
**`newValue`**, type: `number|string|object|null`, La nouvelle valeur du composant.
Retourne : `null|number|string|object`.

Récupère ou définit la valeur du composant. Si le composant est persistant, la valeur est sauvegardée de facon permanente. Faîtes attention à ne pas utiliser ce setter trop souvent sur des composants persistants, car le serveur a une limite au nombre d'appels possibles. Si le composant a une valeur virtuelle, c'est elle qui est retournée. Utilisez `component.rawValue()` pour récupérer la valeur de base, la valeur "non-virtuelle".

```javascript
let hp = sheet.get("hp"); // hp est un composant persistant
log(hp.value()); // 5
hp.value(11); // met à jour et sauvegarde la nouvelle valeur
```

## `rawValue()`
Retourne : `null|number|string|object`.

Récupère la valeur de base, "non virtualle", du composant.

```javascript
let hp = sheet.get("hp");
hp.value(17);
log(hp.value()); // 17

hp.virtualValue(20);
log(hp.value()); // 20
log(hp.rawValue()); // 17
``` 

## `virtualValue()`
## `virtualValue(newValue)`
**`newValue`**, type: `number|string|object|null`, La nouvelle valeur du composant.
Retourne : `number|string|object`.

Récupère ou définit la valeur virtuelle du composant. Les valeurs virtuelles sont utiles quand vous voulez changer une valeur à partir d'un calcul. Par exemple, vous pourriez avoir une armure qui donne au personnage +2 PV, et définir la valeur virtuelle du composant hp à sa valeur de base + 2. Le composant devrait afficher la valeur virtuelle par défaut, et la valeur de base quand il est survolé.

```javascript
let hp = sheet.get("hp");
hp.virtualValue(hp.rawValue() + 2);
```

## `text()`
## `text(replacement)`
**`newValue`**, type: `string`, Le texte à écrire.
Retourne : `null|string`.

Retourne ou définit le texte contenu dans un label. La valeur n'est pas évaluée et le HTML n'est pas autorisé.

```javascript
sheet.get("job").text("Warrior");
```

## `visible()`
Retourne : `boolean`.

Retourne `true` si le composant n'est pas masqué.

## `sheet()`
Retourne : [`Sheet`](/system-builder/scripting/sheet).

Retourne la feuille associée à ce composant.

## `setChoices(choices)`
**`choices`**, type: `object`, Les choix.
Retourne : `void`.

Seulement disponible pour les composants Choice, modifie les choix possibles.


```javascript
sheet.get('class').setChoices({
    "tiger": "Big cat",
    "mouse": "Mouse",
    "kitten": "Very smol"
});
```

## `name()`
Retourne : `string`.

Retourne le nom du composant tel qu'indiqué dans le system builder.

## `id()`
Retourne : `string`.

Retourne l'identifiant du composant tel qu'indiqué dans le system builder.