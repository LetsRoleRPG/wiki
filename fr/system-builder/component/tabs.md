---
title: Tabs
description: 
published: true
date: 2020-09-04T11:12:38.424Z
tags: 
editor: markdown
---

Les *Tabs* sont les composants qui permettent de créer des onglets. Un peu comme les *[reapeater](/system-builder/component/repeater)*, ils fonctionnent en trio avec une table et des vues de types *sub component*. 
Dans le composant *tab* lui même, il y a les champs spéciaux suivants :

# Table
On y renseigne la table dans laquelle les informations sur les onglets seront prises. (les informations sont le titre de l'onglets, et l'identifiant de leur vue)

# Title
On y renseigne le nom de la colonne de la table qui contient les titre des onglets (qui seront afficher en haut).

# View's ID
On y renseigne le nom de la colonne de la table qui contient les identifiants des vues dans lesqelles se trouvent les onglets.

Ainsi, les onglets sont affichés par le composant *tab*, mais sont créés dans une autre vue. C'est dans cette dernière que vous allez placer les composants de votre onglet.

### Des problèmes ?
*Tab* ne fonctionne pas dans le mode preview, vous devez lancer un "run" de la fiche pour vérifier que vos onglets fonctionnent.
*Tab* ne fonctionne pas si un (ou plusieurs) identifiant de la table ne correspond à aucune vue. Ainsi, l'erreur la plus courante est une faute de frappe dans l'identifiant de la vue. S'il manque une vue, l'effet est le même.
Dans cette situation, il est possible après la création d'une vue de corriger son identifiant.
