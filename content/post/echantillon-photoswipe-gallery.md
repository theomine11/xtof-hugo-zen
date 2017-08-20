---
title: Échantillon de Galerie "Photoswipe"
subtitle: Produire une Galerie
date: 2017-07-27
tags: ["exemple", "photoswipe"]
---

Le thème Beautiful Hugo ajoute quelques shortcodes personnalisés créés par [Li-Wen Yip](https://www.liwen.id.au/heg/) et [Gert-Jan van den Berg](https://github.com/GjjvdBurg/HugoPhotoSwipe) pour produire des galeries avec [PhotoSwipe](http://photoswipe.com) . 

{{< gallery caption-effect="fade" >}}
  {{< figure thumb="-thumb" link="/img/hexagon.jpg" >}}
  {{< figure thumb="-thumb" link="/img/sphere.jpg" caption="Sphere" >}}
  {{< figure thumb="-thumb" link="/img/triangle.jpg" caption="Triangle" alt="Ceci est long commentaire concernant un triangle" >}}
{{< /gallery >}}

<!--more-->
## Exemple
La galerie au-dessus a été créée en utilisant les shortcodes suivants : 
```
{{</* gallery caption-effect="fade" */>}}
  {{</* figure thumb="-thumb" link="/img/hexagon.jpg" */>}}
  {{</* figure thumb="-thumb" link="/img/sphere.jpg" caption="Sphere" */>}}
  {{</* figure thumb="-thumb" link="/img/triangle.jpg" caption="Triangle" alt="Ceci est long commentaire concernant un triangle" */>}}
{{</* /gallery */>}}
```

## Usage
Pour les détails complets d'installation, regardez la page [GitHub hugo-easy-gallery](https://github.com/liwenyip/hugo-easy-gallery/). Les usages basiques au-dessus sont : 

- Créez une galerie avec des balises d'ouverture et de fermeture `{{</* gallery */>}}` and `{{</* /gallery */>}}`
- `{{</* figure src="image.jpg" */>}}` utilisera  `image.jpg` pour la vignette et la lightbox
- `{{</* figure src="thumb.jpg" link="image.jpg" */>}}` utilisera `thumb.jpg` pour la vignette et  `image.jpg` pour la lightbox
- `{{</* figure thumb="-petit" link="image.jpg" */>}}` utilisera `image-petit.jpg` pour la vignette et `image.jpg` pour la lightbox
- Tous les [fonctionnalités/paramètres](https://gohugo.io/extras/shortcodes) du shortcode intégré de Hugo `figure` fonctionneront normalement, c'est-à-dire `src`, `link`, `title`, `caption`, `class`, `attr` (attribution), `attrlink`, `alt`
- `{{</* gallery caption-effect="fade" */>}}` fait disparaître les légendes de toutes les images de cette galerie et les fait apparaître en survol
- Beaucoup de styles de galeries existent pour les vignettes  et le survol ; regardez le repo [GitHub hugo-easy-gallery](https://github.com/liwenyip/hugo-easy-gallery/) pour toutes les options.
- Notez que ce thème chargera par défaut le thème `photoswipe gallery` et les scripts, nul besoin de charger photoswipe sur vos pages individuelles.