---
title: "R1D5 : FuckingGoDateFormat, https et un lien `Améliorez la Page`"
date: "2017-07-28T11:40:36+02:00"
draft: false
bigimg: [{src: "/img/path.jpg", desc: "Sur la Route"}]
tags: [100daysofcode, https, dates]
---

<!--more-->

- déploiement netlify : ajout certificat **https** 
- [dates en français](/2017/07/27/r1d4--mise-en-forme-des-dates-dans-gohugo/). [FuckingGoDateFormat](http://fuckinggodateformat.com/)
	- ajouté une date de modification en pied de page
- lien "**améliorez cette page**" pointant vers repo github.
- complété l'[archétype](https://gohugo.io/content-management/archetypes/#readout) `default.md` avec les types de contenu `lastmod`, `tags`, `bigimg`.
- **schéma url** pour les post : faute d'équivalent du `%j` jour de l'année qui n'existe pas nativement en Go, réglé au format `root/AAAA/MM/JJ/nom-post`

```toml
[permalinks]
  post = "/:year/:month/:day/:title/"
```

