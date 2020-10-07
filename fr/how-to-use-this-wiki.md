---
title: Comment utiliser ce Wiki ?
description: 
published: true
date: 2020-09-07T10:24:34.300Z
tags: 
editor: undefined
---

# Utiliser Github
La façon la plus simple de créer ou modifier une page est de faire une *pull request* sur le [repo github de ce wiki](https://github.com/LetsRoleRPG/wiki). Tous les changements acceptés sur le projet github sont synchronisés avec ce site toutes les 5 minutes.

## Proposer une modification
### Se créer un compte GitHub
Si vous n'avez pas encore de compte GitHub, rendez-vous sur https://github.com/join et créez-vous un compte.

### Forker le projet
Une fois connecté, rendez-vous sur https://github.com/LetsRoleRPG/wiki, puis cliquez sur *Fork* en haut à droite.

![github-fork.png](/medias/github-fork.png)

Cela va prendre quelques secondes.

### Faire les modifications
Le projet wiki a désormais été cloné chez vous. Parcourez les dossiers pour trouver le fichier que vous souhaitez éditer. Cliquez sur le nom du fichier pour l'ouvrir : 

![github-page-example.png](/medias/github-page-example.png)

Cliquez maintenant sur la petite icône d'édition à droite de *Raw | Blame*. Vous arriverez dans un editeur de texte qui vous permet de faire les modifications voulues.

#### Syntaxe et données
Vous remarquerez que la page commence par une liste entourée des caractères *---*. Vous pouvez changer le titre ici, mais vous ne devirez changer aucune autre information.

Pour formatter le texte en dessous des *---*, utilisez la [syntaxe markdown](https://www.markdownguide.org/basic-syntax/).

### Commit les modifications
Une fois vos modifications finies, scrollez un peu pour arriver à *Commit changes*. Entrez un titre qui décrit les modifications que vous avez faites, puis cliquez sur *Commit Changes*. Vous pouvez faire cela pour plusieurs fichiers.

### Faire la pull request
Vos changements sont enregistrés, mais seulement sur votre clone. Il faut maintenant propager les modifications sur notre projet. Retournez sur https://github.com/LetsRoleRPG/wiki, puis cliquez sur *Pull requests* dans les onglet. Cliquez maintenant sur **New pull request**.

![github-pull-request.png](/medias/github-pull-request.png)

Cliquez sur le lien **compare across forks**.

Dans *base repository*, gardez LetsRoleRPG/wiki, et dans *head repository*, choisissez votre fork (si votre pseudo github est kitten, choisissez *kitten/wiki*).

Vous pourrez voir les changements que vous avez fait par rapport au fichiers d'origine.

Cliquez sur **Create pull request**, indiquez ce que vous avez modifié dans le formulaire, plus recliquez sur **Create pull request**.

### Attendre que la modification soit validée
Les modérateurs et modératrices de Let's Role vont relire vos modifications, et si tout est bon, accepter la pull request. Si il y a un soucis, un commentaire vous indiquera le problème. Une fois votre pull request acceptée, votre modification sera rapidement passée en ligne.

# Demander des accès
Si vous avez déjà fait beaucoup de modifications avec succès, où que vous êtes un(e) membre de confiance de la communauté, vous pouvez contacter les modérateurs pour demander un accès direct en écriture au wiki. Vous pourrez alors modifier les pages directement sans passer par github.

# Licence
Toutes les pages de ce wiki utilisent la licence *Creative Commons Attribution-NonCommercial*, ce qui veut dire que vous êtes libres de partager et d'adapter le contenu, mais vous devez attribuer l'origine (avec au moins un lien vers ce wiki) et vous ne pouvez pas utiliser ce contenu a des fins commerciales.