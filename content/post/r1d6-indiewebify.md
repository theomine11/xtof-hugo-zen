---
title: "R1D6 : Premiers pas pour indiewebifier Hugo"
date: 2017-07-29
lastmod: 2017-08-18
tags: [indieweb]
bigimg: [{src: "/img/bureau-autriche-campagne.jpg", desc: "2ème bureau"}]
---

6ème jour. 2 heures pour raffiner un bouton "edit", aménager un dossier photos et amorcer les étapes d'indiewebification...<!--more-->

## Création et Mise en Forme du Bouton "Améliorer cette page"

- Création d'un partiel '/partials/page-edit.html` avec un bloc de [composants CSS bootstrap](https://v4-alpha.getbootstrap.com/components/buttons/)

```html
<h6 class="f4 dark-gray mb2">
    <a class="post-title p-name u-url" href="{{ .Permalink }}" class="hide-child link primary-color">
        <span class="nl3 child">{{ partial "svg/link-permalink.svg" (dict "size" "14px") }}</span>
        {{ .Title }}
    </a>
    a été mise à jour le  <time class="dt-updated" datetime="{{ .Lastmod.Format "2006-01-02T15:04:05Z07:00" | safeHTML }}">{{ .Lastmod.Format "02-01-2006"}}</time> {{ with .GitInfo }}: <a class="hide-child link primary-color" href="{{$.Site.Params.ghrepo}}/commit/{{ .Hash }}">{{ .Subject }} ({{ .AbbreviatedHash }})</a>{{end }} par <a rel="author" class="p-author h-card" href="{{ .Site.Author.site }}">{{ .Site.Author.name }}</a>
</h6>

<a class="btn btn-primary btn-success white hover-bg-green link" role="button"
   href="{{.Site.Params.ghrepo}}edit/master/content/{{.File.Path}}">
    Améliorez cette page</a>
```

## Iconographie 

- Ajouté un répertoire local `static/img` afin d'ajouter des images personnelles et reprendre un vieux défi de poster une photo par jour qui pourrait se placer dans la bannière.
- Galerie dans les posts : test du shortcode `gallery` (modèle [Photoswipe](/post/echantillon-photoswipe-gallery))

{{< gallery caption-effect="fade" >}}
  {{< figure link="/img/bureau-autriche-campagne.jpg" caption="2ème bureau" alt="Mon bureau dans le jardin" >}}
  {{< figure thumb="-thumb" link="/img/hexagon.jpg" >}}
  {{< figure thumb="-thumb" link="/img/sphere.jpg" caption="Sphere" >}}
{{< /gallery >}}


## IndieMark Niveau 1

Le web indépendant classique + IndieAuth

> IndieMark Level 1 has the general theme of owning your own domain, for sign-in, and publishing posts

- Référence <https://indieweb.org/IndieMark#Level_1>
- Validateur : <https://indiewebify.me/>

### connexion web (web sign-in)

- modifié (provisoirement pour 100 jours...) mon profil twitter avec l'url de ce site afin de faire fonctionner un "linkback".

![indiewebify linkback](https://monosnap.com/file/OO15UsKvvLM1bapRijTPClLENBwdXt.png)

### validation h-card 

Trop de h-cards selon le validateur indiewebify :  

![indiewebify.me](https://monosnap.com/file/caUAs9rggeCEReojYWzG9WLh8j4EnH.png)

- Modifié le fichier de configuration pour rajouter des variables de site `Author`.
- Installé dans un partiel `hcard.html` une h-card représentative inspirée du [modèle de Kevin Marks](https://github.com/ChristopherA/LifeWithAlacrityBlog/blob/master/blog/themes/indie-tufte/layouts/partials/hcard.html)

```
<div class="h-card">
<img class="u-photo" src="{{ .Site.Author.authorphoto }}" />
<h1><a href="{{ .Site.Author.authorurl }}" >{{ .Site.Author.name }}</a><h1>
</div>
```

#### email (option)

```html
<a rel="me" class="u-email" mailto:"{{ .Site.Author.authoremail }}">{{ .Site.Author.email }}</a>
```

#### ajouter une note / minibio (option)

```html
<p class="p-note">{{ .Site.Author.summary }}</p>
```
