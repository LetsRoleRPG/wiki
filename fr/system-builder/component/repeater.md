---
title: Repeater
description: 
published: true
date: 2021-04-25T18:21:00.044Z
tags: 
editor: undefined
---

Un répétiteur/*repeater* vous permet de créer une liste dynamique de [vues/*views*](/system-builder/component/view). Les utilisateurs peuvent ajouter, modifier ou enlever des entrées.
Dans une vue, un *repeater* sera comme une suite de *container*, un pour chaque entrées, avec une "vue affichage"/*"readable view"* à l'interieur de chaque.
Un *repeater* possède deux champs spéciaux car il va de pair avec deux vues de types *subcomponent* :

# Editable view
Cette view est utilisée pour éditer les données d'une entrée. Cette view est initiée quand vous commencez à éditer une entrée ou à en créer une nouvelle dans le repeater. Les ids des composants utilisés dans cette EDITABLE VIEW vont générer les données que vous utiliserez pour remplir la READABLE VIEW, notamment en utilisant des composants auto complétés et le symbole `#` devant l'id du composant de l'EDITABLE VIEW dont vous voulez utiliser la valeur. Par exemple, si vous avez un TextInput avec l'id Name dans l'EDITABLE VIEW, que vous voulez afficher dans un composant Label de la READABLE VIEW, vous avez juste besoin de rendre ce Label auto calculé (Auto Computed), avec comme contenu `#Name`.
Notez que le nom de la vue elle même peut avoir son importance, voir si-après "craft".

# Readable view
Cette view est utilisée pour afficher les informations d'une entrée du repeater. Cette view est donc répétée pour chaque entrée. Pour utiliser une référence d'une view d'un repeater (EDITEABLE ou READABLE), il suffit d'utiliser l'id du composant de saisie utilisé, précédé par un `#`. Si vous devez parcourir les entrées d'un repeater, vous pouvez utiliser la fonction globale `each` sur la valeur du repeater (`repeaterComponent.value()`) :
```javascript
each(repeaterComponent.value(), function(entryValues){
  // faire ce que vous voulez avec les entryValues de chaque entrée
});
```
Remarquez que l'objet entryValues ne contient que les valeurs des composants de saisie de données (TextInput, NumberInput, Checkbox, etc.) des vues EDITABLE et READABLE. L'objet entryValues ne contient pas les composants eux-mêmes, vous ne pouvez donc l'utiliser pour ajouter des événements par exemple.

Si vous devez parcourir les composants d'une READABLE VIEW d'un repeater, vos devez récupérer l'id de l'entrée du repeater qui vous intéresse. Cet id est généré automatiquement et aléatoirement, et est unique (on l'appelera entryUID). Pour ce faire, il suffit de récupérer le second argument lors de l'appelle à `each` qui est cet identifiant.

Une fois l'identifiant de l'entrée récupéré, vous avez 2 moyens d'accéder aux composants :

1] La première méthode utilise l'identifiant global des composants des repeater. Cet identifiant est construit comme suit : *repeaterId*.*uniqueRandomEntryId*.*readableViewComponentId*. Cette méthode ne permet que d'accéder aux composants existant dans la vue au moment de son appel. Ainsi, si l'EDITABLE VIEW n'est pas affichée (création d'une entrée ou modification d'une entrée), il sera impossible d'accéder au composants de cette EDITABLE VIEW. Voici une petit exemple :
```javascript
let repeaterComponent = sheet.get("repeaterComponentId");
each (repeaterComponent.value(), function(entryValues, uniqueRandomEntryId){
  let myReadableViewComponentFullId = "repeaterComponentId."+uniqueRandomEntryId+".myReadableViewComponentId"; // myReadableViewComponentFullId est l'identifiant complet du composant de la READABLE VIEW que l'on cherche à modifier
  let myReadableViewComponent = sheet.get(myReadableViewComponentFullId);
  // Vous pouvez faire ce que vous voulez avec myReadableViewComponent, c'est le vrai composant donc vous pouvez lui ajouter des événements, etc.
});
```

2] La seconde méthode utilise la méthode `find` des composants. Pour accéder aux omposants à l'intérieur d'une entrée d'un repeater, il faut d'abord trouver le composant qui correspond à l'entrée du repeater (qui est lui-même une sorte de container). Ce composant d'entrée n'est as le premier argument passé lors du parcours de repeater (cf. ci-dessus). Pour trouver ce composant, nous allons utiliser la méthode find sur le composant repeater avec comme argument l'id de l'entrée (second argument passé à la fonction dans le `each`). Une fois ce composant entrée trouvé, nous allons à nouveau utiliser la méthode `find` pour trouver les composants qui se trouvent dans l'entrée. On peut ainsi accéder à tous les composants (EDITABLE VIEW and READABLE VIEW). Voici un petit exemple :
```javascript
let repeaterComponent = sheet.get("repeaterComponentId");
each (repeaterComponent.value(), function(entryValues, uniqueRandomEntryId){
  let entryComponent = repeaterComponent.find(uniqueRandomEntryId); // recherche à l'intérieur du composant repeater pour trouver le composant qui correspond à l'entrée
  let entrySubComponent = entryComponent.find(entrySubComponentId); // grâce au composant de l'entrée on peut accéder à tous ses composants grâce à leurs id (ceux définis dans l'éditeur de Lets Role), par exemple un Label avec "myLabel" comme id pourra être trouvé grâce à entryComponent.find("myLabel"); cette méthode peut également trouver des composants de l'EDITABLE VIEW
  // Vous pouvez faire ce que vous voulez avec myReadableViewComponent, c'est le vrai composant donc vous pouvez lui ajouter des événements, etc.
});
```

# Comment initiliser avec un script la READABLE VIEW d'un repeater

Quand Lets Role a besoin d'afficher la READABLE VIEW d'une entrée d'un repeater, il n'appelle pas la fonction gloable `init`. Pour intervenir sur cette initialisation, vous devez utiliser l'événement `update` du repeater. Lorsque cet événement se déclenche, c'est-à-dire à chaque fois qu'une entrée est ajoutée ou modifiée, vous pouvez parcourir toutes les entrées en utilisant l'une des deux méthodes vues précédemment. Voici un petit exemple dans lequel nous allons changer un icone de la READABLE VIEW en fonction du choix (composant choice1) fait dans l'EDITABLE VIEW :
```javascript
init = function(sheet){
    if(sheet.id()=="main"){
        let repeater1Cmp = sheet.get("repeater1");
        // abonnement à l'événement update du repeater
        repeater1Cmp.on("update", function(repeater){
            log("UPDATE ON "+repeater.id());
            each(repeater.value(), function (entry, entryId){   // on ne sait pas quelle entrée a été modifiée ou ajoutée donc on les fait toutes
                let entryCmp = repeater.find(entryId); // on trouve le composant correspondant à l'entrée
                log("   UPDATING "+entryId);
                let iconCmp = entryCmp.find("viewIcon");  // on trouve le composant de l'entrée correspondant à l'icone
                log("   icon component is "+iconCmp.id());
                let iconName;
                switch(entry.choice1){  // on récupère la valeur du choix (composant choice1) directement depuis les données fournies par each, pas besoin du composant ici
                    case "R1": iconName = "plus"; break;    // si R1 l'icone sera +
                    case "R2": iconName = "minus"; break;   // si R2 l'icone sera -
                    default: iconName = "ad"; break;        // sinon icone par défaut
                }
                iconCmp.value(iconName);    // change la valeur de l'icone (permet de changer l'icone)
                log("   READABLE VIEW has been updated");
            });
            log("END OF UPDATE");
        });
    }
```

# Comment initialiser une EDITABLE VIEW d'un repeater par script

Quand Lets Role a besoin de montrer l'EDITABLE VIEW d'eun entrée d'un repeater, il n'appelle pas la fonction gloable `init`. Pour influencer l'initialisation de l'EDITABLE VIEW d'un repeater, il faut utiliser l'événement `click` du repeater. Dans la fonction de l'événement `click`, il est possible d'accéder à toutes les entrées du repeater mais également aux composants de l'EDITABLE VIEW. Attention, l'événement `click`est appel très souvent, à chaque fois que l'on clique quelque part sur le repeater (Add, Modify, mais également n'importe où ailleurs). L'avantage du `click` c'est que nous avons accès à ce moment aux composants de l'EDITABLE VIEW, notamment aux nouveaux composants lorsque l'utilisateur vient de cliquer sur Add. Nous ne devons donc initialiser les EDITABLE VIEW qu'une seule fois (et pas à chaque `click`). Pour ce faire, nous allons créer un tableau global qui contiendra tous les id des entrées que nous avons déjà initilisées. Je vous conseille de faire un tableau par repeater ou un objet contenant les différents tableaux. Il suffit alors de tester que l'enrtée n'est pas dans le tableau avant de l'initialiser. Voici un exemple dans lequel nous voulons changer le contenu des choix possibles d'un Choice (composant choice2) dans l'EDITABLE VIEW en fonction du choix effectué dans un autre choice (choice1) de cette même EDITABLE VIEW :
```javascript
// write your custom scripts here
let globalRepeaterEntryInits=[];  // tableau permettant de stocker tous les id des entrées déjà initialisées

init = function(sheet){
    if(sheet.id()=="main"){
        // on s'abonne à l'événement click pour initialiser l'EDITABLE VIEW
        repeater1Cmp.on("click", function(repeater){
            log("CLICK ON "+repeater.id()+" containing ");
            log(Object.keys(repeater.value()));   // on affiche les indices du repeater pour vérifier que nous avons bien la nouvelle entrée lorsqu'on clique sur Add
            each(repeater.value(), function (entry, entryId){  // On parcourt les entrées du repeater
                let entryCmp = repeater.find(entryId);
                if(!globalRepeaterEntryInits.includes(entryId)){    // on vérifie si l'id de l'entrée est déjà initialisée, sinon on initialise
                    log("   INITIALIZING "+entryId);
                    let choice1Cmp = entryCmp.find("choice1");      // on récupère le composant choice1 de l'EDITABLE VIEW
                    log("   choice1 component is "+choice1Cmp.id());
                    choice1Cmp.on("update", function (targetCmp){   // on ajoute l'événement update sur choice1 pour pouvoir modifier choice2
                        log("   UPDATE "+targetCmp.id());
                        let choice2Cmp = entryCmp.find("choice2");  // on récupère choice2 de l'EDITABLE VIEW
                        let choice1Val = targetCmp.value();         // on récupère la valeur de choice1
                        let choices = {};                           // en fonction de cette valeur on fixe les choix de choice2
                        choices[choice1Val+"_1"]=choice1Val+"_1";
                        choices[choice1Val+"_2"]=choice1Val+"_2";
                        choice2Cmp.setChoices(choices);             // en utilisant setChoices on change les choix de choice2
                    });
                    globalRepeaterEntryInits.push(entryId);         // ne pas oublier d'ajouter l'entrée dans le tableau des entrées déjà initialisées
                    log("   EDITOR VIEW has been initialized");
                }
            });
            log("END OF CLICK");
        });
    }
    // ...
};
```

Si l'exemple complet vous intéresse, n'hésitez à forker : https://alpha.lets-role.com/sy/jPN4xbM2mUnWcdmx

### Craft
Vous pouvez permettre à un *reapeater* d'être "craftable", ce qui veut dire que le maître de jeu pourra créer une entrée dans l'onglet [content crafting](how-to/content-crafting) pour la déposer dans une fiche de personnage par la suite.
Pour faire cela, cochez les cases **Craft?** et **Droppable?** dans la vue éditable (attention au nom de cette vue, qui sera le nom de la catégorie de craft).
