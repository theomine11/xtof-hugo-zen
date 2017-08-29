---
title: "r1d36 - Tachyons, une CSS atomique statique"
subtitle: "Ailleurs on parle de classes de particules hypothétiques..."
slug: "tachyons-css"
date: "2017-08-29T08:31:45+02:00"
categories: []
tags: [100daysofcode, framework, gohugo, css, utilitaires, framework, librairie]
bigimg: [{src: "/img/tachyons-css.jpg", desc: "tachyons-css"}]
---

36ème jour de mon défi `#100daysofcode` où je parviens à la fin de mon apprentissage des fondamentaux HTML/[CSS](https://fr.wikipedia.org/wiki/Feuilles_de_style_en_cascade), bien accompagné par l'excellent [cours de Todd McLeod](https://www.greatercommons.com/learn/6708511014649856). Un cours "pur CSS" et où les frameworks CSS obèses comme "Bootcrap" sont clairement bannis. 

Durant les prochaines semaines, j'envisage de déroger à la règle et d'étudier [Tachyons](http://tachyons.io), un framework front-end CSS avec l'intention de décrypter et [hacker un joli thème GoHugo](http://gohugo.io/themes/customizing/). <!--more--> 

Exploré hier la bibliothèque d'utilitaires CSS <http://tachyons.io>. Si j'ai bien compris, on parle de [CSS Atomique](https://css-tricks.com/lets-define-exactly-atomic-css/), à savoir une approche d'architecture CSS qui favorise des petites classes nommées sur une fonction visuelle et avec un objectif unique.

La bibliothèque Tachyons est utilisée raisonnablement par Bud Parr, designer front-end éclairé du thème de la [doc GoHugo](https://github.com/gohugoio/gohugoioTheme/tree/master/src) et celui de [Notre Dame de Paris - Ananké](https://github.com/budparr/gohugo-theme-ananke). Bud est un grand fan de Tachyons. Il  nous explique [ici](https://discourse.gohugo.io/t/something-like-shortcodes-in-layouts/7604/5) comment il utilise cette *CSS atomique statique* pour la conception de thèmes et l'optimisation de worklfows. Je dois vous avouer ne pas être encore au niveau pour suivre mais je reste motivé pour étudier en profondeur son approche de design. 

## Aparté culturel... C'est quoi un tachyon ?

> Le <dfn>tachyon</dfn> est une *classe* de particules hypothétiques dont les principales caractéristiques sont d'avoir une vitesse toujours supérieure à la vitesse de la lumière dans le vide ( ), une masse imaginaire pure et une énergie qui diminue lorsque la vitesse augmente. -- [source wikipedia](https://fr.wikipedia.org/wiki/Tachyon)

... Une fois de plus, je ne capte pas encore tout, mais on parle bien de vitesse ! Ce qui a du sens, vu la pauvreté de ma connexion edge me rapprochant de l'ère des modems à 14.4kbauds.

## J'envisage d'Utiliser Tachyons pour aller Vite

Outre la volonté de décrypter le thème de base [GoHugo Ananké](https://themes.gohugo.io/gohugo-theme-ananke/), j'envisage d'utiliser Tachyon à court terme pour faire des petites choses *urgentes, rapides et sales* : un CV/portfolio pour retrouver quelques missions de conseil ... et trouver une solution simple pour l'affichage et le rendu de galeries et d'albums photos pour les artistes.
	
Bien lu ce matin "[So you need a CSS utilitary library](https://css-tricks.com/need-css-utility-library/)", un post éclairé de Chris Coyer. Son conseil : *saupoudrer* légèrement. Et bien garder à l'esprit de se retrouver effrayé face à ce type de HTML : 

```
<div class="module padding-2">
      <h2 class="section-header color-primary">Tweener :(</h2>
</div>
```

### Code échantillon illisible  

Penser à imprimer l'anti-sèche :) 

```html
<div class="mw9 center pa4 pt5-ns ph7-l">
          <time class="f6 mb2 dib ttu tracked"><small>27 July, 2015</small></time>
          <h3 class="f2 f1-m f-headline-l measure-narrow lh-title mv0">
            <span class="bg-black-90 lh-copy white pa1 tracked-tight">
              Too many tools and frameworks
            </span>
          </h3>
          <h4 class="f3 fw1 georgia i">The definitive guide to the JavaScript tooling landscape in 2015.</h4>
    </div>
```

## Extrait de la doc Tachyons 

Quelques notes de traduction pour mémoire, (extraites de la documentation Tachyons.)

<dfn>[tachyons.io](http://tachyons.io/)</dfn> c'est aussi une CSS fonctionnelle pour les designers. Un framework pour créer et concevoir  rapidement une nouvelle *Interface-Utilisateur* sans écrire de CSS.
 
> Create fast loading, highly readable, and 100% responsive interfaces with as little css as possible.


### Les Principes de Tachyons 

* Tout devrait être 100% responsive
* Tout doit être lisible sur n'importe quel appareil
* Tout devrait être aussi rapide que possible
* La conception dans le navigateur devrait être facile
* Il devrait être facile de changer n'importe quelle  interface ou une partie d'une interface sans briser les interfaces existantes
* Faire une chose extrêmement bien encourage la réutilisation et réduit la répétition
* La documentation aide à promouvoir la réutilisation et la connaissance partagée
* CSS ne doit pas entraver l'accessibilité ou la fonctionnalité par défaut du HTML
* Vous devez envoyer la plus petité quantité possible de code à l'utilisateur

### Fonctionnalités 

* Architecture CSS mobile-first
* 490 combinaisons de couleurs accessibles
* Grille de base 8px
* Plusieurs utilitaires de débogage pour réduire les conflits de mise en page
* Structure de classe à usage unique
* Optimisé pour une compression gzip maximale
* Léger (~ 14kB)
* Utilisable dans tous les projets
* Création d'une bibliothèque de composants open source
* Fonctionne bien avec le HTML simple, react, ember, angular rails et plus encore
* Système de grille responsive à l'échelle infinie
* Construit avec Postcss

### Démarrage

- La doc se trouve sur <http://tachyons.io/docs>
- Les modules sont généralement vraiment petits et par conséquent rapides et faciles à lire.

###  Utiliser le CDN

Le moyen le plus rapide et le plus facile pour commencer à utiliser *tachyons* est d'inclure une référence vers les fichier minifié dans le `head` de votre fichier html.

Vous pouvez aussi prendre la dernière version avec 

```html
<link rel="stylesheet" href="https://unpkg.com/tachyons/css/tachyons.min.css">
```

Vous pouvez aussi spécifier une version spécifique. La dernière version est 4.6.1

```html
<link rel="stylesheet" href="https://unpkg.com/tachyons@4.6.1/css/tachyons.min.css">
```

### Installation locale 

Clonez le repo à partir de github et installez les dépendances avec npm.

```bash
git clone https://github.com/tachyons-css/tachyons.git
cd tachyons
npm install
```

#### Dev

Si vous voulez simplement tout utiliser dans  `tachyons/src` comme point de départ et modifier tout le code vous-même, vous pouvez compiler tous vos changements merveilleux en lançant 

```npm start```

Cela affichera les versions minifiées et non modifiées du css dans le répertoire css et regardera le répertoire src pour les modifications.
C'est aliasé à la commande :

```npm run build:watch```

Si vous souhaitez simplement créer le css une fois sans regarder l'exécution du répertoire src

```npm run build```

Si vous voulez vérifier qu'une classe n'a pas été redéfinie ou «mutée», il est nécessaire de vérifier que toutes les classes n'ont été définies qu'une seule fois. Cela peut être utile si vous utilisez une autre bibliothèque ou si vous avez écrit certaines de vos propres css et souhaitez vous assurer qu'il n'y a pas de collisions de nommage. Pour ce faire, exécutez la commande :

```npm run mutations```

### Docs

Les documents de tachyons situés sur <http://tachyons.io> sont tous open source et se trouvent sur  <https://github.com/tachyons-css/tachyons-css.github.io>

Vous pouvez cloner les documents et les utiliser comme modèle pour documenter votre propre système de design / patterns / composants.
Bien que tout ne soit pas automatisé, la génération de la bibliothèque de composants rend extrêmement facile la génération et l'organisaton de la documentation pour les composants, comme indiqué sur <http://tachyons.io/components>

## Contribuer

Lisez SVP notre [code de conduite](https://github.com/tachyons-css/tachyons/blob/master/code-of-conduct.md) pour les contributeurs.

## Tachyons en Production

Une liste plus longue de sites utilisant les tachyons en production se trouve dans `sites.md`.
Nous aimons laisser la communauté voir ce que les gens construisent, alors ajoutez votre lien vers `sites.md` dans une PR ou en ouvrant une issue si vous êtes prêt à partager sur votre site ou votre projet.

**Sites Vedettes**

* <https://interfacelovers.com>
* https://friendstalkfrontend.com
* <https://gohugo.io>
* https://coralproject.net
* http://www.philipyoungg.com
* https://gitpoint.co
* https://2017.nodeconf.com.ar
* https://goldenstaterecord.com
* http://hicuties.com
* https://urlbox.io
* https://fontawesome.com
* https://purple3.herokuapp.com
* http://blunt.af/tachy.app/
* https://fenderdigital.github.io/css-utilities/intro/

Et bien sûr ...
* <http://tachyons.io>

## Premier essai avec des carrés d'images (abandonné)

Faute d'avoir envie d'alourdir ce thème hugo-zen avec de nouvelles déclarations CSS, je pose le code-échantillon d'une collections de carrés d'images avec un titre et un sous-titre. Le code déposé en-dessous me paraît encore trop illisible sans appel à l'[anti-sèche](https://roperzh.github.io/tachyons-cheatsheet/) dédiée ? 

Pour information, le rendu d'affichage original est visible [ici](http://tachyons.io/components/collections/square-title-subtitle/index.html)

```html
<section class="cf w-100 pa2-ns">
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://jekyll-for-craftman.netlify.com/images/medium/raku-Vases+vase-stri%C3%A9+principal+yasefanprod.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Vase en Raku</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Sous-titre de la pièce</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://jekyll-for-craftman.netlify.com/images/medium/raku-bols+coupe-turquoise+principal+yasefanprod.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Coupe Turquoise</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Sous-titre</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://jekyll-for-craftman.netlify.com/images/medium/raku-Vases+vase-rouge-bomb%C3%A9+principal+yasefanprod.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Vase Rouge</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Sous-titre de la pièce</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0004.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0007.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0008.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0009.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0010.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0011.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0012.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0013.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0014.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0015.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0016.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0017.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0018.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0019.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0020.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0021.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
  <article class="fl w-100 w-50-m  w-25-ns pa2-ns">
    <div class="aspect-ratio aspect-ratio--1x1">
      <img style="background-image:url(http://mrmrs.github.io/images/0022.jpg);" 
      class="db bg-center cover aspect-ratio--object" />
    </div>
    <a href="#0" class="ph2 ph0-ns pb3 link db">
      <h3 class="f5 f4-ns mb0 black-90">Title of piece</h3>
      <h3 class="f6 f5 fw4 mt2 black-60">Subtitle of piece</h3>
    </a>
  </article>
</section>
```