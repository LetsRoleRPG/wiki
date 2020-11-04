---
title: Column
description: 
published: true
date: 2020-09-04T11:05:22.700Z
tags: 
editor: markdown
---

Les *colomn* devraient **toujours** être placer dans les composants *Row*. Retrouver plus d'information à propos des colonnes ici : https://getbootstrap.com/docs/4.5/layout/grid/

# Size
Ce champ vous permet d'ajuster la largeur de la colonne. Elle fonctionne sur une echelle de 1 à 12, 1 étant le plus mince et 12 tout l'espace disponible. 
Sans aucune valeur, les colonnes se repartissent équitablement l'espace :
#### exemples
* Une *colomn* dans une section/*row* prendra toute la largeur de la *row* (largeur de 12).
* Trois *colomn* dans une section/*row* prendrons un tier de la largeur de la *row* chacune (largeur de 4).
* Trois *colomn* dans une section/*row*, on donne à la première colonne une largeur de 2 ; les deux autres se répartirons l'espace restant, et auront donc une largeur de 5 chacunes.
#### Adaptation automatique de la largeur
Le *colomn* adaptent leur largeurs quand la largeur de la *row* change. Ainsi, quand un utilisateur affiche sa fiche de personnage, et modifie sa taille, les colonnes vont suivre la taille dans une certaine mesure.
Si les colonnes sont plus larges que l'espace disponible, la colonne la plus à droite sera déplacer sous la première colonne. Cela arrive notamment quand on réduit la taille de la fiche, mais que les colonnes contiennent des composants incompressibles.

### Style et espacement
Les option de [*styling*](https://lets-role.wiki/fr/system-builder/general/styling) sont utiles pour les *colomn*, notamment les options de *spacing*/espacement.
Par default, (sans qu'aucune *class* ne soit écrite) les *colomn* on un pading de 2 en largeur (ce qui correspond à la *class* `px-2`). Les composants à l'interrieur de la colonne seront donc éloigner de ces bords. Cet espacement compense parfaitement les marges négatives par défault des *row*.
