---
title: r1d28 Migration Jekyll vers Hugo
date: 2017-08-20T08:21:00Z
lastmod: 2017-08-21T01:00:00+02:00
tags: [100daysofcode, gohugo, jekyll]
---

J'en rêvais depuis quelques mois. [Après quelques années vécues sur jekyll](/2013/12/03/premier-pas-sur-jekyll/), je migre aujourd'hui vers le framework [GoHugo](https://gohugo.io/) avec le thème minimaliste "hugo-zen" : 

> <dfn>Hugo Zen</dfn> is a minimal hugo theme with Skeleton and has ~100 lines of custom CSS.

Nouvelle aventure d'apprentissage sur la rénovation à venir de mon site personnel. Peu à l'aise sur les gros frameworks obèses comme Bootstrap, j'ai choisi ce thème pour repartir de zéro avec  le [framework Skeleton](http://getskeleton.com/#intro). Un boilerplate simple et responsive. 

## Pourquoi cette migration 

Jekyll demeure un générateur de site statique incroyable. Et je ne voudrais en aucun cas le dénigrer dans ce post. Mon *mentor* Bertrand Keller vous en parlera mieux que moi. Lisez son dernier post ["Jekyll et Hugo sont dans un bateau"](https://bertrandkeller.info/2017/07/03/jekyll-hugo-sont-bateau/). 

Disons que comme d'autres [utilisateurs moins néophytes](https://jamstatic.fr/2017/06/07/migration-de-jekyll-a-hugo/), j'étais agacé face aux avertissemements et erreurs de build incessants dans la fenêtre du terminal :

![Jekyll build et version Ruby](https://monosnap.com/file/kXoJF1LsSSFVsjamdrTw37klKqc7C4.png)

## L'appel GoHugo

L'annonce de la [nouvelle version de Smashing Magazine](https://jamstatic.fr/2017/03/17/smashing-mag-va-dix-fois-plus-vite/), les encouragements de la communauté jamstatic, la qualité de la documentation et les premiers [essais sur un sous-domaine "100daysofcode"](https://100daysofcode.christopheducamp.com/page/thanks) m'ont conforté dans ma décision de franchir le pas.

Je continuerai cependant à utiliser Jekyll. Je conserve une instance de famille pour effectuer des tests. Et dès la rentrée, j'accompagnerai ma chérie dans la prise en main de son nouveau site professionnel conçu par Bertrand Keller. Une motorisation  jekyll avec une [belle invitation à jongler avec des milliers de photos](http://jekyll-for-craftman.netlify.com/) pour organiser la présentation de ses collections de céramique. 

## Minimalisme "hugo-zen"

Ce que que je vous raconterai au fil de l'eau sur ce site sera mon expérience personnelle de non-développeur. Si vous êtes développeur web, vous aurez sûrement de meilleures astuces. Le point qui me fascine toujours dans Hugo -outre la vitesse hallucinante du "build"- c'est la visualisation live en local du rendu d'affichage durant les modifications de code. Oui, ne plus avoir à rafraîchir la page s'avère à l'usage très pratique pour l'apprentissage du code et les futures itérations de design css.

![terminal : hugo serve](/img/migration-gohugo/hugo-zen-hugo-serve.png)

Faute de me sentir à l'aise pour [créer un thème à partir de zéro](https://gohugo.io/categories/themes), j'ai choisi le thème minimaliste "[hugo-zen](https://github.com/rakuishi/hugo-zen)" pour repartir sur des bases simples à itérer. Ma ligne d'apprentissage sera d'essayer de m'accrocher à ce thème et de [parvenir à le personnaliser](https://gohugo.io/categories/themes).

## Récapitulatif des travaux du jour 

1. *utilisé* la [commande import](https://gohugo.io/commands/hugo_import_jekyll/) `hugo import jekyll` pour importer deux  instances jekyll. 
2. *nettoyé* les en-têtes (front-matter) des posts, notes et pages 
2. *déposé* les photos et images dans le dossier `static\img` que je compte réorganiser par sous-dossiers thématiques
2. <q>[Cool URIs don't change](https://www.w3.org/Provider/Style/URI)</q> : *paramétré* les "[permalinks](https://gohugo.io/content-management/urls/)" dans le fichier `config.toml` pour conserver la structure des URLs jekyll (format ISO9601 AAAA/MM/JJ). 
3. amorcé une localisation de date en français dans les deux templates `list` et `single`
5. déployé le site sur [netlify](https://www.netlify.com/) à partir de mon nouveau repo github. Accessible sur <https://github.com/ChristopheDucamp/xtof-hugo-zen>
	6. Archive et sécurité : l'ancien repo source jekyll est conservé [ici](https://github.com/ChristopheDucamp/xtof-clean-blog) sur github à titre d'archive.

## Yeah !

Je m'arrête là pour ce soir. Heureux retrouver la vitesse et la simplicité vécues lors de mes premiers pas sur Jekyll. 

## Chantier prévu cette semaine 

- mise en forme (menu page d'accueil, layouts à revoir),
- [optimisation et performance](https://developers.google.com/speed/pagespeed/insights/?url=christopheducamp.com&tab=mobile) 
- [indiemark](https://indieweb.org/IndieMark).

  





