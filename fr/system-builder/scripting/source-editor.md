---
title: Directly editing the source of the tree
description: 
published: true
date: 2020-09-24T12:03:25.875Z
tags: 
editor: undefined
---

Si vous savez ce que vous faites, vous pouvez éditer le code source de l'arbre en cliant sur `Source Editor`

> Nous ne recommandons pas d'utiliser le source editor si vous ne savez pas comment gérer un document JSON. Il est extrêmement facile de détruire l'ensemble du système que vous êtes en train de construire.  
{.is-warning}

# Champs

Il y a quelques champs disponibles dans le source editor :

## Communs
Ces champs sont disponibles pour tous les composants.

### id `string`
### name `string`
### classes `string`
Les classes CSS appliquées au composant.
### children `array`
### className `string`
Le nom de la classe interne à Let's Role du composant.
### collapsed `boolean`
UI Only. Set to `true` to collapse the component in the *View* window.
System Builder uniquement. Définissez à `true` pour replier le composant dans l'onglet `View`.
### references `array`
> Ne pas éditer ce champ manuellement
{.is-danger}

Liste calculée automatiquement des champs référencés.

## Checkbox
### label `string`

## Liste de choix
### label `string`
### tableId `string`
La table (Let's Role) où les données sont sauvegardées.
### optional `boolean`
A cocher si le choix peut être vide.
### expanded `boolean`
### multiple `boolean`
### expandedClass `string`
La classe appliquée à chaque option en mode `expanded`.

## Column
### size `number`

## Container
### layout `string`
Orientation du container : `horizontal` ou `vertical`.

## Icon
### iconName `string`
Le nom de l'icone (sa classe CSS).
### roll `string`
Le lancer de dés à effectuer quand on clique sur l'icone.
### rollTitle `string`

## Label
### text `string`
### align `string`
Aligment du label : `Left`, `Right` ou `Center`.
### clickable `boolean`
### quickBar `boolean`
Si le label peut être ajouté à la quickbar.
### quickBarLabel `string`
### computed `boolean`
### roll `string`
La valeur de l'attribut "roll on click".

## NumberInput
### min `number`
### max `number`
### defaultValue `number`
### align `string`
Alignement du NumberInput :`Left`, `Right` ou `Center`.
### computed `boolean`
### computedValue `string`

## Repeater
### readViewId `string`
L'identifiant de la vue d'affichage.
### viewId `string`
L'identifiant de la vue d'édition.

## Tab
### tableId `string`
La table où les données des onglets sont sockés.
### titleAttribute `string`
Le nom de la colonne listant le titre de l'onglet.
### viewAttribute `string`
Le nom de la colonne listant l'identifiant de la vue de l'onglet.
### vertical `boolean`
### verticalWidth `number`
### verticalText `boolean`
Affiche le texte aussi verticalement.
### verticalAlign `string`
Position des onglets. Les valeurs peuvent être `left` ou `right`.

## Textarea
### placeholder `string`
### defaultValue `string`
Aussi utilisée pour la valeur calculée (`computed`).
### computed `boolean`

## TextInput
### placeholder `string`
### defaultValue `string`
Aussi utilisée pour la valeur calculée (`computed`).
### computed `boolean`

## View
### type `string`
Le type de vue, `Main` ou `SubComponent`.
### craft `boolean`
Si la vue représente un craft ?
### avatarId `string`
L'identifiant du champ avatar dans la vue.
### tokenizable `boolean`
Pour les crafts, si ils peuvent être utilisés comme jetons sur la carte.
### droppable `boolean`
Pour les crafts, si ils peuvent être glissés-déposés dans une feuille.
### width `number`
### height `number`