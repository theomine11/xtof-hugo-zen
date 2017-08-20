---
title: "R1D4 : mise en forme des dates dans GoHugo"
date: 2017-07-27
lastmod: 2017-07-28
tags: [100daysofcode, log, date, localisation]
bigimg: [{src: "/img/path.jpg", desc: "Path"}]
---

Premier post sur ce nouveau site dédié à compléter mon [log 100daysofcode](https://github.com/ChristopheDucamp/100-days-of-code-xtof). Bien installé dans les massifs à proximité de [Sank Pölten](https://fr.wikipedia.org/wiki/Sankt_Pölten). Temps pluvieux, les photos suivront demain... <!--more--> En ce "R1D4" (4ème jour d'engagement du premier round de 100daysofcode, je suis excité à l'idée de compléter mon [log 100daysofcode](https://github.com/ChristopheDucamp/100-days-of-code) en mettant les mains dans le générateur de site statique [GoHugo](https://gohugo.io/). ([thème multilingue "beautiful hugo"](https://github.com/halogenica/beautifulhugo).)

## Intention 

Améliorer ce site pour restituer des formats de date avec un  rendu d'affichage en français, "plus humain" et correct sémantiquement (ajouter la balise `time`).

- `mardi 1<sup>er</sup> août`
- `Donnerstag, 27 Juli` pour les amis autrichiens de [vienna.html](https://github.com/viennahtml) quand la mise en page des dates fonctionnera 

### Statut : chantier en cours 

**Intentions** : 

1. Étudier les ressources au calme pour écrire un partiel `post_meta.html` de personnalisation de la date.
2. En bas de chaque article, ajouter un bouton "améliorer la page" et un horodatage sur la date de dernière modification 

## Production du jour 

- Un repo github [`100daysofcode-site`](https://github.com/ChristopheDucamp/100-days-of-code-site) 

## Code et Ressources pour personnaliser la Date

Les fichiers du thème en cours de modification : 
![Création d'un fichier Layouts à la racine](https://monosnap.com/file/x6Om2981dbukYvMEffVFLYPePmAPeU.png)

### Code 

#### un fichier data `mois.yaml` 

(placé dans `data/mois.yaml`)

```yaml
1: "janvier"
2: "février"
3: "mars"
4: "avril"
5: "mai"
6: "juin"
7: "juillet"
8: "août"
9: "septembre"
10: "octobre"
11: "novembre"
12: "décembre"
```

#### Partiel de date

- `post_meta.html` ajouté dans le dossier `/layouts/partials`


```golang
<span class="post-meta">
Posté le <time class="post-date dt-published" datetime="{{ .Date.Format "2006-01-02T15:04:05Z07:00" | safeHTML }}">{{ .Date.Day }} {{ index $.Site.Data.mois (printf "%d" .Date.Month) }} {{ .Date.Year }}</time>
</span>
```

**todo** : à raffiner avec l'ajout du jour de la semaine.

#### bouton de modification horodaté avec accès github

Inspiré de la doc Hugo, j'aimerais ajouter un bouton en bas de chaque post libellé "modifier la page" pointant sur le fichier github lié.

```golang
<!-- partiel de date publication et mise a jour au format fr a raffiner. ex : <nomdujour> 1er -->

dernière mise à jour le : 
<time class="dt-updated" datetime="{{ .Lastmod.Format "2006-01-02T15:04:05Z07:00" | safeHTML }}">{{ .Lastmod.Day }} {{ index $.Site.Data.mois (printf "%d" .Lastmod.Month) }} {{ .Lastmod.Year }}</time> <br> 

        {{ partial "page-edit.html" . }}
        
```

### Ressources à étudier et classer

- [FuckingGoDateFormat](http://fuckinggodateformat.com/)
- [GoHugo : dateFormat](https://gohugo.io/functions/dateformat/) (non supportée sur les sites multilingues)
- Exemples de dates publiés sur [docsHugo : format](https://gohugo.io/functions/format/)
- [GoHugo : multilingual mode / customize dates](https://gohugo.io/content-management/multilingual/#customize-dates)
- [Formatting a date with suffix (2nd)](https://discourse.gohugo.io/t/formatting-a-date-with-suffix-2nd/5701) - forum de discussion Hugo
- [dates only in english](https://discourse.gohugo.io/t/dates-only-in-english/1317/38) - forum discussion Hugo
- [Francisation de la date](https://github.com/nicolinuxfr/voiretmanger-hugo/commit/5ecc162a0e89d803997fff5e9ef0a2507c0ff6d0) - (repo voiretmanger- hugo)
- [Parsing dates in templates](https://discourse.gohugo.io/t/parsing-dates-in-templates/603/12)
- [Slack jamstatic](https://jamstatic-fr.slack.com/archives/C5MTQPL4E/p1500985424553770)
> tu peux découper ton {{.Date}} en {{.Day}} {{.Month}} et {{.Year}}
> ici un exemple de code où je récupère un timestamp PHP et je le convertis en date humaine :

```php
Publié le {{$time := time (div (int .Params.dateAdd) 1000)}}{{ $monthindex := index $.Site.Data.mois (printf "%d" $time.Month) }} {{$time.Day}} {{$monthindex}} {{$time.Year}}
```

