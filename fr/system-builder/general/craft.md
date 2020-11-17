---
title: Computed Values
description: 
published: true
date: 2020-11-17T10:08:44.104Z
tags: 
editor: Tsuna77
---

# Un craft, qu'est-ce que c'est

Un craft est une modèle de fiche que le créateur du système met à disposition du MJ pour ajouter du contenu à sa partie. Par exemple, des PNJ (Personnage non jouable), des ennemis, des objets, etc.

Un craft peut avoir plusieurs options d'utilisation. 
- Utilisable en tant que Token sur la carte
- Glissable sur une fiche pour l'affecter à un champs de type `repeater`

# Comment créer un craft

Pour créer un craft, il faut définir la vue principal. Cela peut être une vue dédié ou alors la vue d'édition d'un repeater.

Une fois cette vu définie, vous devez cocher l'option `Craft ?`. Cela l'ajoutera à la liste des type disponible dans la bloc `Content Crafting` de la table virtuelle.

Si votre Craft à pour objectif d'être déposer sur le terrain (un monstre par exemple). Vous devez aussi cocher la case `Tokenizable ?`

Si votre craft à pour objectif d'être glissé sur une autre fiche afin de l'ajouter à un `repeater` alors vous devez cocher la case `Droppable ?`

Enfin, si vous voulez que votre craft est une image, aussi bien dans la liste des `Content Crafting` que sur le terrain en mode token. Vous devez ajouter un composant `Avatar` dans la vue. et préciser dans le champs d'option `Avatar's id` du craft l'id du composant que vous venez d'ajouter.

## Exemples de crafts

![craft_exemple_monster.png](/medias/french/craft_exemple_monster.png)
Dans l'exemple ci-dessus, nous avons un craft utilisable sur le terrain. Il s'agit d'une fiche de monstre pour le système Dragons.

![craft_exemple_weapon.png](/medias/french/craft_exemple_weapon.png)
Dans ce nouvel exemple, il s'agit du craft des armes utilisé dans le système Dragons. Il s'agit de la vu utilisé par le `repeater` des armes du système Dragons. Le fait d'utiliser la vu du `repeater` permet d'éviter les duplications de code qu'il faut éviter au maximum lors des developpement.

# Les Drops

Lorsqu'un craft est de type `droppable` il faut ajouter un bout de script afin de configurer dans quel `repeater` la fiche doit être copier.

Il faut aussi respecter les noms des champs du `repeater` car les id des champs doivent être identiques. D'ou le fait d'utiliser directement la vu d'édition du `repeater` autant que possible.

## Un peu de code

La fonction à utilisé dans le scripting est la fonction Drop. décrite dans la page [scripting-global](/fr/system-builder/scripting/global.md)

La fonction drop fonctionne de la manière suivante :
- Elle fournit 2 paramètres en entrée
  - from : Fiche (`sheet`) d'origine. Le craft
  - to : Fiche (`sheet`) de destination. La fiche de personnage par exemple
- Elle attend en retour l'id du repeater de la fiche `to` qui devra contenir le craft glissé

**_WARNING_** Les valeurs des champs dans les fiche `from` et `to` ne sont pas retourné correctement actuellement. Ce bug à été signalé sur discord et n'est pas encore corrigé à l'heure d'aujourd'hui

Voici un exemple de Drop permettant de géré deux Craft, des sorts qui doivent être ranger dans le bon `repeater` en fonction de la valeur d'un des champs. et des armes qui vont directement dans le `repeater` associé

```javascript
drop = function(from, to) {
    log("drop de "+from.name()+" vers "+to.name())
    if (from.id() === "fiche_sorts" && to.id() === "main") {
        return "rep_sorts"+from.get("spell_level").value();
    }
    if (from.id() === "attackedit" && to.id() === "main"){
      return "repeteur_armes";
    }
};
```
