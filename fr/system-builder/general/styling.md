---
title: Styling
description: 
published: true
date: 2020-09-24T12:02:54.855Z
tags: 
editor: undefined
---

La mise en forme sur le *Systeme builder* utilise un système de **_"classes"_**.

Les classes sont des petites commandes que l'on ajoutes à un composant pour le faire changer de son apparence par défaut. On écrit ses commandes dans le champs "Classes" du composant. Tout les composants possède ce champs.  
Vous pouvez donner plusieurs classes à un composant ; elles devraient toutes être séparées par un espace, et il ne devrait y a voir aucun espace inutile après une classe.

Nous utilisons les classes de Bootstrap 4 comme base pour les classes de Let'role. Donc toutes les classes disponibles dans [les outils bootstrap](https://getbootstrap.com/docs/4.4/utilities/spacing/) sont aussi disponibles dans le systeme builder.

Cela étant dit, vous devriez essayer de ne pas trop changer la conception par défaut de Let's Role. C'est particulièrement important si vous souhaitez que votre feuille soit officialisée.

# Couleur de fond
Les classes `highlight-1` et `highlight-2` changent la couleur de fond du composant.

# Espacement
Par défaut, il n'y a pas d'espace entre les composants, ils sont donc collés les un aux autres. Les classes d'espacement permettent de donner un peu d'ordre et d'oxygène.
Il y a deux type d'espacement :
## Les marges
Elles sont l'espacement exterieur du composant. Les autres composants ne pourront pas s'approcher d'un composant avec des marges.
## Les "padding"
Les padding (traduisez rembourage ou mattelasure) sont des espaces intérieurs au composant : les composants à l'intérieur ne pourront pas toucher les bords du composant qui les contient avec un padding.

Ces classes on une nomenclature un peu spcécial, mais facile à comprendre grâce à cette [documentation](https://getbootstrap.com/docs/4.4/utilities/spacing/).  
En voici un bref résumé : `m[coté]-[n][chiffre]` :
* la première lettre est soit `m` pour marge soit `p` pour padding  
* la deuxième lettre désigne le coté ou appliquer l'espacement : gauche, droite, gauche et droite, haut, bas, haut et bas, associer respectivement au lettres l, r, x, t, b, y. S'il n'y a pas de lettre, l'espacement est de tout les cotés.
* Un tiret sépare l'endroit de l'espacement de sa valeur
* On peu ajouter un "n" devant le chiffre, pour appliquer un marge négative : au lieu de se séparé, les composants de superposeront. (Ne fonctionne pas avec les padding)
* Et enfin un chiffre entre 0 et 5 qui caractérise la taille de l'espace. (on peux mettre `auto` à la place d'un chiffre pour les marges)

# Mise en forme de text
On utilise les classes suivantes essentiellement dans les *label* et dans les *choices*.
## La taille du texte
Les classes `text-tiny`, `text-small`, `text-medium`, `text-large`, `text-giant`, `text-gargantuan` donnent une taille différente au texte (de gauche à droite, du plus petit au plus grand).

## Titre
La classe `text-title` donne l'aspect d'un titre au text.

## Mettre en gras
La classe `text-bold` met le texte en gras.

## Figer l'espace
La classe `text-monospace` remplace la police de texte par une autre dons les espacements sont fixes. Simules une police supplémentaire pour votre feuille. Utile pour une belle interface.

# Largeur et Hauteur
Vous pouvez donner une largeur et/ou une hauteur fixes (en pixel) à un composant grâce aux commandes `w-[nombre]px` et `h-[nombre]px`.  
"w" Pour *width* qui signifie largeur, et "h" pour *height* qui signifie hauteur.

Les nombres de pixels que vous pouvez choisir en largeur sont 25, 50, 75, 100, 125 150, 175, 200 et 300. (Exemple `w-25px`) Les autre nombres (comm 80 ou 101) ne fonctionneront pas.  
Les nombres de pixels que vous pouvez choisir en hauteur sont tous ceux de la largeur, plus 400, 500, 600 et 700. (Exemple `h-700px`)

# Cacher des composants
Il y a deux classes pour cela, avec une petite nuance entre elles deux :
* La classe `d-none` cache le composant comme s'il n'existait pas. Il ne prend ainsi plus aucun espace.
* La classe `invisible` cache le composant en conservant sa place et ses espacements. Pratique si vous voulez ajuster l'alignement entre deux lignes contenants des éléments différents.
Ces deux classes ne fonctionnent pas sur les *containers*.

# Montrer qu'un objet est cliquable
La class `clickable` affiche le curseur main et change le texte en orange lorsque vous survolez le composant. Exactement le même effet visuel que lorsque vous cochez l'option «Cliquable» pour un label. Si vous l'utilisez sur une colonne ou une rangé, elle s'applique à tous les composants qu'elle contient.
