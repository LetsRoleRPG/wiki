---
title: Column
description: 
published: true
date: 2020-09-24T12:02:18.400Z
tags: 
editor: undefined
---

Les colonnes/*column* devraient **toujours** être placées dans les composants [rangée/*Row*](/system-builder/component/row). Retrouvez plus d'informations à propos des colonnes ici : https://getbootstrap.com/docs/4.5/layout/grid/

# Size
Ce champ vous permet d'ajuster la largeur de la colonne. Elle fonctionne sur une echelle de 1 à 12, 1 étant le plus mince et 12 tout l'espace disponible. 
Sans aucune valeur, les colonnes se repartissent équitablement l'espace :
#### Exemples
* Une colonne dans une rangée/*row* prendra toute la largeur de la *row* (largeur de 12).
* Trois colonnes dans une rangée/*row* prendront un tiers de la largeur de la *row* chacune (largeur de 4).
* Trois colonnes dans une rangée/*row*, on donne à la première colonne une largeur de 2 ; les deux autres se répartiront l'espace restant, et auront donc une largeur de 5 chacune.
#### Adaptation automatique de la largeur
La colonne/*column* adapte sa largeur quand la largeur de la *row* change. Ainsi, quand un utilisateur affiche sa fiche de personnage, et modifie sa taille, les colonnes vont suivre la taille dans une certaine mesure.
Si les colonnes sont plus larges que l'espace disponible, la colonne la plus à droite sera déplacée sous la première colonne. Cela arrive notamment quand on réduit la taille de la fiche mais que les colonnes contiennent des composants incompressibles.

### Style et espacement
Les options de [*styling*](https://lets-role.wiki/fr/system-builder/general/styling) sont utiles pour les *columns*, notamment les options de *spacing*/espacement.
Par défaut, (sans qu'aucune classe/*class* ne soit écrite) les *column* ont un padding de 2 en largeur (ce qui correspond à la *class* `px-2`). Les composants à l’intérieur de la colonne seront donc éloignés de ces bords. Cet espacement compense parfaitement les marges négatives par défault des *row*.
