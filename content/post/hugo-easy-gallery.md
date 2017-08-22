---
title: "Shortcode Gallery"
subtitle: "Pour insérer facilement des galeries de photos"
slug: ""
date: "2017-08-22T10:44:34+02:00"
draft: false
categories: []
tags: [100daysofcode, photoswipe, photo, galerie]
bigimg: [{src: "/img/path.jpg", desc: "Sur la Route"}]
---
{{< figure src="/img/path.jpg" >}}

Installé [Hugo Easy Gallery](https://www.liwen.id.au/heg/) pour faciliter la création de galeries de photos. Le shortcode `gallery` génère une galerie css responsive de toutes les images dans un dossier.<!--more-->

## Créer une galerie à partir d'un dossier

```go
{{</* gallery dir="/img/auvers/" */>}} {{</* load-photoswipe */>}}
```

donne 

{{< gallery dir="/img/auvers/" />}} {{< load-photoswipe >}}

### Notes 

  * Les images sont automatiquement légendées avec le nom du fichier.
  * `[image].jpg` est utilisé pour l'image haute-résolution et `[image]-thumb.jpg` pour les vignettes.
  * Si `[image]-thumb.jpg` n'existe pas, alors `[image].jpg` sera utilisé pour à la fois les images hi-res et vignettes.
  * Le suffixe par défaut de la vignette est `-thumb`, mais vous pouvez en spécifier un différent, par ex. `thumb="-small"` or `thumb="_150x150"`.
  * Le layout est responsive - essayez de changer la taille de fenêtre de votre navigateur ou utilisez le [device mode](https://developers.google.com/web/tools/chrome-devtools/device-mode/) Chrome pour voir la flexibilité responsiveness.
  * `{{</* load-photoswipe */>}}` active PhotoSwipe. Vous n'avez besoin d'appeler ce shortcode qu'une fois par page. Si vous n'activez pas PhotoSwipe, vous aurez la même galerie d'images sur la page, mais si vous cliquez/tapez une image, elle liera directement à l'image hi-res (si vous en avez spécifié une) au lieu de charger le gadget PhotoSwipe carousel/lightbox. Pour savoir comment le PhotoSwipe fonctionne, voir ce [post précédent](https://www.liwen.id.au/photoswipe).

## PhotoSwipe 

Il existe plusieurs solutions pour implémenter [PhotoSwipe](http://photoswipe.com/) dans [Hugo](http://gohugo.io/), à savoir [HugoPhotoSwipe](https://github.com/GjjvdBurg/HugoPhotoSwipe) et le [post de blog de Tom Helmer](http://www.thehome.dk/article/photoswipe-gallery-hugo/), mais elles vous obligent à grouper toutes vos images à un seul endroit sur la page.

Cette solution offre : 

  * Une galerie style lightbox/carrousel qui charge toutes les images dans les posts, peu importe l'endroit où elles apparaissent; 
  * Fonctionne avec toutes les images existantes en utilisant le shortcode `figure` sans rien avoir à changer ; 
  * Ne requiert pas de [pré-définir les tailles d'image](http://photoswipe.com/documentation/faq.html#image-size);

**Tout le code est disponible sur [GitHub](https://github.com/liwenyip/hugo-pswp).**



{{< gallery caption-effect="fade" >}}
  {{< figure thumb="-thumb" link="/img/hexagon.jpg" >}}
  {{< figure thumb="-thumb" link="/img/sphere.jpg" caption="Sphere" >}}
  {{< figure thumb="-thumb" link="/img/triangle.jpg" caption="Triangle" alt="Ceci est long commentaire concernant un triangle" >}}
{{< /gallery >}}


## Usage 

  * Appelez {{</* pswp-init */>}} **une seule fois** et n'importe où sur chaque page où vous voulez utiliser PhotoSwipe
  * `{{</* figure src="image.jpg" */>}}` utilisera `image.jpg` pour la vignette et la lightbox
  * `{{</* figure src="thumb.jpg" link="image.jpg" */>}}` utilisera   `thumb.jpg` pour la vignette et `image.jpg` pour la lightbox
  * `{{</* figure thumb="-small" link="image.jpg" */>}}` utilisera  `image-small.jpg` pour la vignette et `image.jpg` pour la lightbox
  * `{{</* figure thumb="-small" link="image.jpg" size="1024x768"*/>}}` évite d'avoir besoin de pré-charger  `image.jpg` pour déterminer sa taille (optionnel)
  * Tous les [paramètres et fonctionnalités](https://gohugo.io/extras/shortcodes) du shortcode `figure` intégré dans Hugo fonctionnent normalement, à savoir `src`, `link`, `title`, `caption`, `class`, `attr` (attribution), `attrlink`, `alt`
  * `{{</* figure src="image.jpg" class="pswp-ignore" */>}}` sera ignoré par PhotoSwipe (si c'est ce que vous voulez vraiment faire)
  * entourez vos `figure`s entre `{{</* gallery title="titre de votre galerie (facultatif)" */>}}` et `{{</* gallery /*/>}}` pour arranger vos vignettes dans une boîte





