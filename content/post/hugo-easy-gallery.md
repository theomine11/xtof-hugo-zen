---
aliases: [photoswipe]
title: "Galerie Photoswipe"
subtitle: "Pour insérer une galerie de photos"
slug: ""
date: "2017-08-22T10:44:34+02:00"
draft: true
categories: []
tags: [100daysofcode, photoswipe, photo, galerie]
bigimg: [{src: "/img/path.jpg", desc: "Sur la Route"}]
---

Installé [Hugo Easy Gallery](https://www.liwen.id.au/heg/) après un [premier essai convaincant de ce système de galeries photos sur le thème Beautiful Hugo](https://100daysofcode.christopheducamp.com/2017/07/27/%C3%A9chantillon-de-galerie-photoswipe/).

Le shortcode `gallery` génère une galerie css responsive de toutes les images dans un dossier. 

La css proposée en *sortie de boîte*  reste à bricoler afin d'afficher des vignettes carrées sur le thème hugo-zen.<!--more-->


## Créer une galerie à partir d'un dossier

Le truc pour créer une galerie d'images à partir d'un dossier :

```
{{</* gallery dir="/img/votre-dossier-images/" */>}}
{{</* load-photoswipe */>}}
```

### Rendu sur Hugo-zen : css à revoir 

{{< gallery caption-effect="fade" >}}
  {{< figure thumb="-thumb" link="/img/hexagon.jpg" >}}
  {{< figure thumb="-thumb" link="/img/sphere.jpg" caption="Sphere" >}}
  {{< figure thumb="-thumb" link="/img/triangle.jpg" caption="Triangle" alt="Ceci est long commentaire concernant un triangle" >}}
{{< /gallery >}}

### Notes 

- Les images sont automatiquement légendées avec le nom du fichier.
- `[image].jpg` est utilisé pour l'image haute-résolution et `[image]-thumb.jpg` pour les vignettes.
- Si `[image]-thumb.jpg` n'existe pas, alors `[image].jpg` sera utilisé tant pour les images en haute résolution que les vignettes.
- Le suffixe par défaut de la vignette est `-thumb`, mais vous pouvez en spécifier un différent, par ex. `thumb="-small"` or `thumb="_150x150"`.
- Le layout est "responsive" - essayez de changer la taille de fenêtre de votre navigateur ou utilisez le [simulateur de mobiles "device mode"](https://developers.google.com/web/tools/chrome-devtools/device-mode/) de Chrome pour voir la flexibilité.
- `{{</* load-photoswipe */>}}` active PhotoSwipe. Vous n'avez besoin d'appeler ce shortcode qu'une fois par page. Si vous n'activez pas PhotoSwipe, vous aurez la même galerie d'images sur la page, mais si vous cliquez/tapez une image, elle liera directement à l'image hi-res (si vous en avez spécifié une) au lieu de charger le gadget PhotoSwipe carousel/lightbox. Pour savoir comment PhotoSwipe fonctionne, voir ce [post](https://www.liwen.id.au/photoswipe).


Pour spécifier des fichiers images individuels

```
{{</* gallery */>}}
  {{</* figure src="image1.jpg" */>}}
  {{</* figure src="image2.jpg" */>}}
  {{</* figure src="image3.jpg" */>}}
{{</* /gallery */>}}
```

Paramètres optionnels :

- `caption-position` - détermine la position de la légende sur l'image : 
  - `bottom` (par défaut)
  - `center`
  - `none` cache les vignettes sur la page (ils ne s'affichent que dans PhotoSwipe)
- `caption-effect` - détermine si/comment les vignettes apparaissent sur hover. Options :
  - `slide` (par défaut)
  - `fade`
  - `none` (vignettes toujours visibles)
- `hover-effect` - détermine comment les images changent sur hover. Options :
  - `zoom` (par défaut)
  - `grow`
  - `shrink`
  - `slideup`
  - `slidedown`
  - `none`
- `hover-transition` - détermine comment les images changent sur hover. Options :
  - not set - transition douce (par défaut)
  - `none` - transition dure 


## CSS Hackers

`hugo-easy-gallery.css` est conçu pour fournir des carreaux carrés dans un conteneur avec `max-width: 768px`.

Voici quelques pointeurs si vous voulez adaptez la CSS :

 - Changez `.gallery {max-width: 768px;}` si vous voulez une galerie plus large que 768px.
 - Changez `min-width` dans les styles `@media`  pour modifier les largeurs d'écran sur lesquelles le layout change
 - Changez `min-width: 9999px` dans le dernier style  `@media` vers quelque chose de sensible si vous voulez utiliser un layout 4-carreaux
 - Si vous voulez plus de 4 carreaux par ligne, réglez  `width`à 100% / nombre de carreaux par ligne
 - `padding-bottom` = `width` donne les carreaux carrés. Changez le padding-bottom si vous voulez d'autres radio d'aspect, par ex. `width: 33.3%; padding-bottom: 25%` donne un ratio d'aspect 4:3.

## Question 

Testé avec le thème [beautifulhugo](https://github.com/halogenica/beautifulhugo), les choses ne fonctionnent pas proprement sur ce thème hugo-zen. J'essaierai de réparer plus tard.


## PhotoSwipe 

Il existe plusieurs solutions pour implémenter [PhotoSwipe](http://photoswipe.com/) dans [Hugo](http://gohugo.io/), à savoir [HugoPhotoSwipe](https://github.com/GjjvdBurg/HugoPhotoSwipe) et le [post de blog de Tom Helmer](http://www.thehome.dk/article/photoswipe-gallery-hugo/), mais elles vous obligent à grouper toutes vos images à un seul endroit sur la page.

Cette solution offre : 

  * Une galerie style lightbox/carrousel qui charge toutes les images dans les posts, peu importe l'endroit où elles apparaissent; 
  * Fonctionne avec toutes les images existantes en utilisant le shortcode `figure` sans rien avoir à changer ; 
  * Ne requiert pas de [pré-définir les tailles d'image](http://photoswipe.com/documentation/faq.html#image-size);

**Tout le code est disponible sur [GitHub](https://github.com/liwenyip/hugo-pswp).**


## Usage 

  * Appelez {{</* pswp-init */>}} **une seule fois** et n'importe où sur chaque page où vous voulez utiliser PhotoSwipe
  * `{{</* figure src="image.jpg" */>}}` utilisera `image.jpg` pour la vignette et la lightbox
  * `{{</* figure src="thumb.jpg" link="image.jpg" */>}}` utilisera   `thumb.jpg` pour la vignette et `image.jpg` pour la lightbox
  * `{{</* figure thumb="-small" link="image.jpg" */>}}` utilisera  `image-small.jpg` pour la vignette et `image.jpg` pour la lightbox
  * `{{</* figure thumb="-small" link="image.jpg" size="1024x768"*/>}}` évite d'avoir besoin de pré-charger  `image.jpg` pour déterminer sa taille (optionnel)
  * Tous les [paramètres et fonctionnalités](https://gohugo.io/extras/shortcodes) du shortcode `figure` intégré dans Hugo fonctionnent normalement, à savoir `src`, `link`, `title`, `caption`, `class`, `attr` (attribution), `attrlink`, `alt`
  * `{{</* figure src="image.jpg" class="pswp-ignore" */>}}` sera ignoré par PhotoSwipe (si c'est ce que vous voulez vraiment faire)
  * entourez vos `figure`s entre `{{</* gallery title="titre de votre galerie (facultatif)" */>}}` et `{{</* gallery /*/>}}` pour arranger vos vignettes dans une boîte





