---
title: Repeater
description: 
published: true
date: 2020-09-24T12:02:29.036Z
tags: 
editor: undefined
---

Un répétiteur/*repeater* vous permet de créer une liste dynamique de [vues/*views*](/system-builder/component/view). Les utilisateurs peuvent ajouter, modifier ou enlever des entrées.
Dans une vue, un *repeater* sera comme une suite de *container*, un pour chaque entrées, avec une "vue affichage"/*"readable view"* à l'interieur de chaque.
Un *repeater* possède deux champs spéciaux car il va de pair avec deux vues de types *subcomponent* :

# Editable view
On y renseigne l'identifiant de la vue dans laquelle on édite l'entrée.
Notez que le nom de la vue elle même peut avoir son importance, voir si-après "craft".

# Readable view
On y renseigne l'identifiant de la vue qui servira d'affichage à l'entrée.

### Usage
Dans la vue éditable, vous pourrez placer divers [choix/*choices*](/system-builder/component/choice), [entrées textuelles/*text input*](/system-builder/component/text-input) et [entrées numériques/*number input*](/system-builder/component/number-input) que l'utilisateur pourra remplir. Dans la vue lisible, vous pourez placer des *[labels](/system-builder/component/label)* qui afficheront les contenus des précédents *choices*, *text input* et *number input* grâce au système de [références](/en/system-builder/general/references).

### Craft
Vous pouvez permettre à un *reapeater* d'être "craftable", ce qui veut dire que le maître de jeu pourra créer une entrée dans l'onglet [content crafting](how-to/content-crafting) pour la déposer dans une fiche de personnage par la suite.
Pour faire cela, cochez les cases **Craft?** et **Droppable?** dans la vue éditable (attention au nom de cette vue, qui sera le nom de la catégorie de craft).

### repeater et script
Si vous avez besoin de trouver des valeurs ou des donner dans les entrées de vos *repeater*, vous pouvez utiliser la fonction `each` sur les fonctions `.value()` du repeater; comme ceci
```javascript
each(repeaterComponent.value(), function(entryValues){
  // faites ce que vous voulez des valeurs de chaque entrées.
  // Si dessous, affiche dans la console la valeur du composant d'identifiant "firstComponentId"
  log (entryValues.firstComponentId);
});
```

Si vous avez besoin de chercher un composant dans la vue lisible d'un *repeater*, you dever trouver leur identifiants, et qui sont construit comme ceci : `idDuComposantRepeater.idUniqueAleatoireDeLEntre.idComposantReadableView`

Pour trouver "idUniqueAleatoireDeLEntre", you devez utiliser le deuxième paramètre de la fonction `each`. Exemple :
```javascript
let repeaterComponent = sheet.get("repeaterComponentId");
each (repeaterComponent.value(), function(entryValues, uniqueRandomEntryId){
  let myReadableViewComponent = repeaterComponent.find(uniqueRandomEntryId).find("myReadableViewComponentId");
  // do whatever you want you want with the component (add an event handler, etc.)
});```
