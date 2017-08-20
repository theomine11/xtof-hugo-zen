---
title: Shoelace
subtitle: Un reset.css à étudier
comments: false
date: 2017-08-03
lastmod: 2017-08-03
draft: true
---

<dfn>[Shoelace.style](https://shoelace.style/)</dfn> est un kit de démarrage, pas un framework. Son auteur nous invite à le considérer comme une réinitialisation CSS saupoudrée de quelques composants utiles. Les utilisateurs de Bootstrap le trouveront familier, mais rafraîchissant.

Shoelace est personnalisable à travers les variables CSS. Il ne nécessite ni Less, ni Sass, ni aucun prétraitement. La version minifiée fait seulement 32.1KB et elle est beaucoup plus petite lorsqu'elle est compressée.

Faites simplement un lien vers `shoelace.css` et ajoutez les personnalisations à votre feuille de style.
    
```html
    <link rel="stylesheet" href="shoelace.css">
    
    <style>
      :root {
        --body-color: white;
        --body-bg-color: black;
        --color-primary: #09d;
      }
    </style>
   ```html 

Shoelace é été créé par [@claviska](https://twitter.com/claviska) pour [Surreal CMS](https://www.surrealcms.com/). Il est disponible sous la licence MIT.