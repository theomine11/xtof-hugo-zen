---
date: 2016-12-14T07:53:00Z
tags:
- plugin
- jekyll
- ux
- ui
title: Installation jekyll-admin
url: /2016/12/14/installation-jekyll-admin/
---

Pour faciliter l'ajout de nouveaux posts, installé pour essayer un plugin de Jekyll qui se rapproche d'une interface graphique de type CMS pour publier du contenu et administrer les sites Jekyll :

[https://jekyll.github.io/jekyll-admin/](https://jekyll.github.io/jekyll-admin/)

Un gros progrès comparé à l'ajout manuel de post. Je trouve curieux de ne pas avoir intégré par défaut la mise à jour automatique des champs de métadonnées pour les posts ? 

## Ajout de post avec jekyll-admin

Si vous optez pour jekyll-admin, pensez à ajouter quelques champs de métadonnées. Dans mon cas et en m'appuyant sur l'exemple du premier post, j'ai donc ajouté au-dessous de la fenêtre de publication les 3 champs de méta-données : 

1. le `layout` avec `post`
2. un champ `date` 
3. un champ `tags`  

Ce qui visuellement pour ce post, l'interface sur la fenêtre de publication ressemble à ce qui suit : 

![jekyll-plugin-metadata](/Jekyll%20Admin%202016-12-14%2007-02-14.png)

## Prochaines étapes 

### Interface-utilisateur pour ajouter des posts 

* [Edit] Work in progress. Séduit par SiteLeaf après avoir essayé quelques alternatives afin de trouver une interface-utilisateur plus conviviale afin d'inviter des utilisateurs néophytes à publier. Petit tour rapide sur GitHub/[Prose.io](http://prose.io), [Forestry.io](http://forestry.io) et [Site Leaf](https://www.siteleaf.com/) suite aux recommandations de Frank :  

> Tu peux commencer avec Github/Prose.io, sous Jekyll Siteleaf ou Forestry.io sont très simples d’utilisation, CloudCannon c’est encore le niveau au dessus avec l’édition de régions côté front. Un peu plus technique et plus complet : Contenful ou Prismic.io qui permettent de générer les structures de contenus via un service et génèrent une API pour ses contenus consommable par d’autres services. (Frank Taillandier, [jamstatic](https://jamstatic-fr.slack.com/?redir=%2Farchives%2Fgeneral%2Fp1481708085000019), 2016-12-14)


* Voir le [tableau comparatif des offres d'hébergement statique / CMS](https://docs.google.com/spreadsheets/d/1FuiC29pnWsRemqvQh3UcHAZSkz_3p-pq-5-6m5ZHdzU/edit#gid=0) 

### Autres travaux à envisager 
 
* Localiser la date en français : trouver une technique plus propre que [mon vieux bricolage](http://christopheducamp.com/2013/12/26/jekyll-localiser-la-date/)
* Ajouter un certificat SSL sur le sous-domaine avec pointage vers GitHub
* Premier pas vers l'[indiewebfication](https://indiewebify.me/) : installer une connexion web avec l'ajout d'un 'rel=me' dans le thème minima à retrouver... 

