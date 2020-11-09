---
title: Workflow
description: 
published: true
date: 2020-09-24T12:03:01.358Z
tags: 
editor: undefined
---

# System creation

Lors de la création d'un nouveau système, deux choses se produisent :

* Un système vierge que vous pouvez modifier est créé.

* Une nouvelle table de jeu est créée avec ce système. Cette table est utilisée dans le panneau "Run" du *system builder*, mais vous pouvez également y accéder via vos tables.

Veuillez noter que le contenu actuel est utilisé lors de l'accès à cette table depuis "Run", mais pas depuis la connexion classique (le dernier commit est utilisé lors de la connexion en tant que joueur).

# Etats acutels et _commits_

Lorsque vous enregistrez votre travail dans le générateur de système, il est enregistré dans **l'état actuel**. Cet état n'est pas disponible pour les personnes avec lesquelles vous avez partagé votre travail.

Si vous voulez que votre travail soit accessible à tous, vous devez **_commit_**.

Lors d'un *commit*, vous pouvez soumettre un message pour vous rappeler en quoi consiste le commit et choisir de publier ce commit. Lorsque le commit est publié, tous les utilisateurs utilisant le système utiliseront ce derniers.

Si vous avez fait une erreur, vous pouvez rammené votre travail à un ancien commit. **Veuillez noter que cela remplacera l'état actuel** par l'état dans lequel était le commit.

# Systèmes de partage

Vous recevrez un lien vous permettant de partager votre système lors de sa création. Ce lien ce trouve dans la page de résumé sur système. Toute personne disposant de ce lien peut utiliser votre système dans une table, et le fork.

# Forking

Le *Fork* (littéralement fourche) vous permet de modifier un système déjà créé en fonction de vos besoins.

Vous pouvez fourcher/*fork* un système partagé avec vous. Vous commencerez au dernier commit publié par le créateur.  
Veuillez noter que les demandes d'extraction (*pull request*) et la fusion (*merging*) ne sont pas possibles pour le moment, ce qui veut dire qu'un fork est indépendant de son original, et que les changements ne sont pas synchronisables.
