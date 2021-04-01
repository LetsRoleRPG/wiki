---
title: Prompt
description: 
published: true
date: 2020-09-24T12:03:19.111Z
tags: 
editor: undefined
---

L'API Prompt vous permet de demander à l'utilisateur de remplir un petit formulaire avant une action. Par exemple, si vous avez besoin d'un modificateur avant un lancer de dé, vous pouvez afficher une petite fenêtre pour demander la valeur du modificateur.

Le prompt lui-même possède un titre, un identifiant de la vue à afficher, une fonction callback avec les données collectées depuis la vue. La vue est initialisée dans la fonction globale `init(sheet)`.

Exemple :
```javascript
sheet.get('attack').on('click', function() {
    sheet.prompt('Modifiers ?', 'rollprompt', function(result) { // rollprompt is the id of the view
        // result is an object of the data of the view
        // after the user clicks "continue".
        // if the user cancel the prompt, the function is not called
        if (result.advantage) {
            Dice.roll(sheet, 'keeph(2d20)'); 
        } else {
            Dice.roll(sheet, '1d20');
        }
    });
}); 
```

# `sheet.prompt(title, view, callback, callbackInit)`
**`title`**, type: `string` *`required`*, Le titre du prompt.
**`view`**, type: `string` *`required`*, L'identifiant de la vue à utiliser.
**`callback`**, type: `Function` *`required`*, La fonction callback pour récupérer les données une fois que le joueur clique sur le bouton "next". Le premier argument est l'objet données de la vue prompt.
**`callbackInit`, type: `Function`, La fonction callback appelée quand le prompt s'ouvre qui vous permet de modifier les éléments de la vue du prompt à partir d'informations provenant de la feuille qui appelle `sheet.prompt(...)`. Le premier argument est la vue du prompt, c'est à dire une instance de la vue `view`. Vous pouvez la manipuler avec les fonctions habituelles de vues, par exemple si vous la nommez `promptView`, vous pouvez en cacher des composants avec `promptView.get('componentId').hide()`.

`Prompt(title, view, callback)`
> This stand-alone function has been deprecated, use sheet.prompt() instead
{.is-warning}

**`title`**, type: `string` *`required`*, Le titre du prompt.
**`view`**, type: `string` *`required`*, L'identifiant de la vue à utiliser.
**`callback`**, type: `Function` *`required`*, La fonction callback pour récupérer les données une fois que le joueur clique sur le bouton "next". Le premier argument est l'objet données de la vue prompt.
Retourne `void`.
