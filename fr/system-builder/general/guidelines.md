---
title: Guidelines
description: 
published: true
date: 2020-09-24T12:02:48.369Z
tags: 
editor: undefined
---

# Disposition de la feuille
Étant donné que les écrans sont principalement horizontaux, vous devriez concevoir la feuille avec la disposition paysage à l'esprit. 

# Composants requis
## Avatar
L'avatar est obligatoire sur les feuilles de personnage et les craft. Vous pouvez utiliser n'importe quel identifiant de votre choix, mais vous devez spécifier l'identifiant utilisé dans le champ de la *view*/vue *"Avatar's id"*.

## Color
*Color* est obligatoire sur les feuilles de personnage. L'identifiant doit être: color.

# Computed values
Certains composants ont l'attribut calculée/*computed*, qui leur permet d'avoir une valeur basée sur des opérations mathématiques et des références à d'autres composants.

Attention, les valeurs calculées/*computed* peuvent être gourmandes en ressources processeur, vous ne devez donc pas en utiliser trop.

# Scripts
**Nous vous recommandons vivement de ne pas activer les scripts si vous ne connaissez pas le langage Javascript.**

Si vous souhaitez créer des fonctionnalités avancées, vous pouvez utiliser Javascript pour améliorer votre système.
