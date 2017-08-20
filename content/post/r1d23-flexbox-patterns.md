---
title: "r1d23 Flexbox Patterns"
subtitle: "Un en-tête de site"
slug: ""
date: "2017-08-15T20:17:43+02:00"
lastmod: "2017-08-15T20:54:43+02:00"
draft: false
tags: [100daysofcode, flexbox, svg, color]
bigimg: [{src: "/img/flexbox-site-header.png", desc: "Flexbox-Patterns : En-tête de site"}]
---

Devoirs de vacances aujourd'hui avec quelques exercices extraits de [http://www.flexboxpatterns.com/](http://www.flexboxpatterns.com/). Ma production *100daysOfCode* du jour s'achèvera sur le [troisième exercice des flexbox patterns](http://www.flexboxpatterns.com/site-header) consistant à construire un **en-tête de site**. 

Vous trouverez ci-dessous mon échantillon de code, avec en bonus : 

1. Ma première "extraction SVG". Qui devrait théoriquement s'afficher dans IE9. 
2. Une couleur d'arrière-plan du menu extraite à la pipette sur le nouveau [Pantone  Prince](https://www.theguardian.com/music/2017/aug/14/prince-purple-pantone-color-institute-love-symbol-2) ! 

## CSS 

{{% codepen id="OjObjN" tab="css" %}}

Ce type d'échantillon de code (optimisé avec l'aide de mon mentor Todd McLeod) doit pouvoir s'utiliser un en-tête de site web. 

### Adieu `float`

La méthode typique pour la construction de ce composant était  d'envelopper l'image SVG et les boutons de navigation dans un élément, et les boutons "Paramètres" et "Déconnexion" à l'intérieur d'un autre élément. Ensuite, on utilisait `float` pour pousser un conteneur vers la gauche et l'autre conteneur vers la droite. Et il fallait rajouter un `clearfix` sur l'en-tête du site lui-même... 

Avec flexbox, fini ce cirque pour une mise en page simple ! Vous aurez encore besoin des éléments de conteneur, mais adieu aux classes spéciales pour ces conteneurs.

### Précisions CSS Flexbox

`justify-content: space-between` pousse les éléments enfants aussi loin de l'autre que possible. À savoir le logo et les boutons de nav à gauche, et le bouton paramètre à droite.

`align-items: center` centre tous les éléments enfants verticalement le long de l'axe principal dans les conteneurs. C'est important car le logo et les boutons de nav ont des hauteurs différentes. Sans le réglage de cette propriété, ils s'aligneraient par défaut sur le bord du haut.

{{% codepen id="OjObjN" tab="html" %}}

Attentif à toutes vos remarques sur les optimisations de code pour mes premiers pas sur flex.

