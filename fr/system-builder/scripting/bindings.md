---
title: Bindings
description: 
published: true
date: 2020-09-24T12:03:05.729Z
tags: 
editor: undefined
---

Les bindings (liaison en français) permettent aux joueurs de faire référence à un élément de leur feuille de personnage dans le chat. Grâce à cette API, vous avez un contrôle total sur les liens disponibles et la façon dont ils sont affichés.

Un binding est créé avec 4 éléments :

 * **name** `string` : le nom utilisé dans le chat pour faire référence au binding 
 * **componentId** `string` : l'id du composant référencé. Vous pouvez avoir plusieurs binding pour un même componentID, notamment dans le cas des [repeaters](/system-builder/component/repeater)
 * **viewId** `string` : l'id de la [vue](/system-builder/component/view) utilisée pour afficher le binding
 * **data** `Function` : une fonction qui retourne l'objet de données transmis à la vue pour le rendu. Ces données seront disponibles dans la vue
 
Les bindings sont disponibles via la constante globale `Bindings`.

# `Bindings.add(name, componentId, viewId, dataCallback)`
**`name`**, type: `string` *`requis`*, le nom utilisé dans le chat
**`componentId`**, type: `string` *`requis`*, l'id du composant utilisé
**`viewId`**, type: `string` *`requis`*, l'id de la vue utilisée pour le rendu
**`dataCallback`**, type: `Function`, une fonction qui retourne l'objet de données transmis à la vue pour le rendu. L'objet doit être sérialisée en JSON.

# `Bindings.send(sheet, name)`
**`sheet`**, type: `Sheet` *`requis`*, la [fiche](/system-builder/scripting/sheet) liée au binding
**`name`**, type: `string` *`requis`*, le nom du binding

Envoie un binding dans le chat. Le binding doit avoir été enregistré avec la fonction `Binding.add()`.

# `Bindings.remove(name)`
**`name`**, type: `string` *`requis`*, le nom du binding

Enlève un binding à partir de son nom.

# `Bindings.clear(componentId)`
**`componentId`**, type: `string` *`requis`*, l'id du composant

Enlève tous les bindings liés à un composant.
