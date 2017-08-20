---
title: "R1D7 Indiemark Niveau 1"
subtitle: Chantier IndieMark Niveau 1
date: 2017-07-30T06:55:03+02:00
draft: false
tags: [indieweb]
bigimg: [{src: "/img/arc-en-ciel-autriche.jpg", desc: "arc-en-ciel"}]
---

- Lien de [référence indieweb : IndieMark](https://indieweb.org/IndieMark#Level_1) 

**Production du jour** : Les posts sont marqués avec  `h-entry` <https://indiewebify.me/validate-h-entry/> dans le thème "beautiful-hugo".

<!--more-->

### Création d'un partiel `h-card.html` 

Une h-card représentative est appelée dans le footer par le partiel suivant 

```
<span class="h-card">
<img class="u-photo"   
src="{{ .Site.Author.authorphoto }}" />   
<a rel="me" href="{{ .Site.Author.site }}"  
>{{ .Site.Author.name }}</a>
</span>
```

Le validateur suggère l'ajout d'un e-mail et d'une note/bio

```
<a rel="me" class="u-email">…</a>
<p class="p-note">…</p>
```


### Posts et `h-entry`
#### Instructions

Après modifications, les "h-entries" disposent des propriétés suivantes :

  * `e-content` — le contenu principal du post
  * `p-name` — pour le nom du post 
  * `dt-published` — le "datetime" auquel le post a été publié, en format ISO8601, avec un "timezone"
  * `u-url` — l'URL canonique du post, tout spécialement importante sur les pages répertoriant plusieurs posts.

Adopté la convention d'un datetime sous forme de lien vers le post en lui-même.

Voir la [doc h-entry](https://microformats.org/wiki/h-entry) pour une liste complète.

#### Travaux sur variables

- Modifié le fichier de configuration pour rajouter des variables de site `Author`.
- ajouté un partiel `auteur.html` dans `post-meta.html` (style à travailler)

```
<a rel="author" class="p-author h-card" 
href="{{ .Site.Author.authorurl }}"> 
{{ .Site.Author.name }}</a>
```

#### layout `list.html`

Ajouté `h-entry` et ses propriétés comme suit : 

```
<article class="post-preview h-entry">
              <a class="u-url" href="{{ .Permalink }}">
                <h2 class="post-title p-name">{{ .Title }}</h2>
    
                {{ if .Params.subtitle }}
                  <h3 class="post-subtitle">
                    {{ .Params.subtitle }}
                  </h3>
                {{ end }}
              </a>
    
              <p class="post-meta">
              Posté le <a class="u-url" href="{{ .Permalink }}">
              <time class="post-date dt-published" datetime="{{ .Date.Format "2006-01-02T15:04:05Z07:00" | safeHTML }}">{{ .Date.Day }} {{ index $.Site.Data.mois (printf "%d" .Date.Month) }} {{ .Date.Year }}</time>
              </a> 
              (<a rel="author" class="p-author h-card" href="{{ .Site.Author.site }}">{{ .Site.Author.name }}</a>)
              </p>
              <div class="post-entry e-content">
                {{ if .Truncated }}
                  {{ .Summary }}
                  <a href="{{ .Permalink }}" class="post-read-more">[{{ i18n "readMore" }}]</a>
                {{ else }}
                  {{ .Content }}
                {{ end }}
              </div>
    
              {{ if .Params.tags }}
                <span class="post-meta">
                  {{ range .Params.tags }}
                    #<a href="{{ $.Site.LanguagePrefix }}/tags/{{ . | urlize }}">{{ . }}</a>&nbsp;
                  {{ end }}
                </span>
              {{ end }}
```

##### Travaux validés avec suggestions : 

- Copies syndiquées à rajouter / ajouter les URLs des copies [POSSÉes](https://indieweb.org/POSSE) !

`<a rel="syndication" class="u-syndication" href="…">…</a>`

- Catégories

Ajouter quelques catégories !

`<a class="p-category" href="…">…</a>`

#### Layout `single.html`

- Ajouté une url de permalien (variable `.Permalink) dans le titre du contenu ```<a class="u-url" href="…">…</a>``` 

le code de `single.html` à cette heure :

```
{{ define "main" }}
<div class="container h-entry" role="main">
  <div class="row">
    <div class="col-lg-8 col-lg-offset-2 col-md-10 col-md-offset-1">
       <article role="main" class="blog-post e-content">
        {{ .Content }}
        
        <!-- bloc ameliorer la page -->
        {{ partial "page-edit.html" . }}
        <!-- /bloc ameliorer la page --> 
        
      </article>
```

avec son partiel `page-edit.html` dans lequel j'ai ajouté une propriété `p-name` et `u-url` sur le titre du post.  

```
<div class="btn footer btn-primary btn-lg"> 
<a class="post-title p-name u-url" href="{{ .Permalink }}">"{{ .Title }}"</a>
<time class="dt-published" datetime="{{ .Date.Format "2006-01-02T15:04:05Z07:00" | safeHTML }}"></time>
<time class="dt-updated" datetime="{{ .Lastmod.Format "2006-01-02T15:04:05Z07:00" | safeHTML }}">
<br>a été mise à jour le {{ .Lastmod.Format "02-01-2006"}}</time>
<br>par <a rel="author" class="p-author h-card" href="{{ .Site.Author.site }}">{{ .Site.Author.name }}</a>
<br>
<a class="btn btn-primary btn-success white hover-bg-green link" role="button" 
href="{{.Site.Params.ghrepo}}edit/master/content/{{.File.Path}}">
Améliorez cette page</a><br>
</div>
```

### Ressources briques basiques (Niveau 1 et 2)

- Les [briques de construction indieweb](https://adactio.com/journal/7698) essentielles
- pied de page à travailler 
	- personnaliser variable `site` pour `author` avec linkback
	- [h-card](http://microformats.org/wiki/h-card) représentative sur URL avec photo 
	- rel="me" sur les icônes sociales
- ajouter `h-entry` aux articles

```html
<article class="h-entry">
  <div class="e-content p-name">Hello world! This is my first indieweb post.</div>

  <a class="u-url" href="https://exemple.com/my-first-post">
    Publié le <time class="dt-published">2017-07-28 11:10:22+0000</time>
  </a>
</article>
```



#### Prochaines étape IndieMark : Webmentions

Ressources à compléter pour implémentation 

- [So long Disqus, hello Webmention](https://nicolas-hoizey.com/2017/07/so-long-disqus-hello-webmentions.html) Nicolas Hoizey - 2017-07-27 (plugin Jekyll)
- [indiewebify my static hugo web site](http://www.petersell.com/2017/indiewebify-my-static-hugo-website)
- [Webmention Rocks](https://webmention.rocks/) - série de tests 


