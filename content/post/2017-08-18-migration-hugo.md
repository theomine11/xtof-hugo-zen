---
title: r1d27 Migration Jekyll vers Hugo - 1ere partie
date: 2017-08-20T08:21:00Z
tags: [100daysofcode, gohugo, jekyll]
lastmod: 2017-08-20T08:25:00+02:00
draft: false
---


## Jekyll vs Hugo ?

Jekyll est un générateur de site statique incroyable et je ne voudrais en aucun cas le dénigrer dans ce post. Bertrand Keller mon *mentor* statique vous en parlera mieux que moi sur son dernier post ["Jekyll et Hugo sont dans un bateau"](https://bertrandkeller.info/2017/07/03/jekyll-hugo-sont-bateau/). 

![Jekyll build et version Ruby](https://monosnap.com/file/kXoJF1LsSSFVsjamdrTw37klKqc7C4.png)

Mais comme bien d'autres [utilisateurs plus ou moins néophytes](https://jamstatic.fr/2017/06/07/migration-de-jekyll-a-hugo/), j'ai rencontré ces derniers mois quelques soucis lors des mises à jour de version Jekyll. Les erreurs de build devenaient fréquentes et rebutantes pour revenir sur un flow d'écriture dans l'éditeur sans s'éterniser dans la fenêtre de terminal.

L'appel du pied Hugo me démange depuis quelques semaines avec quelques [premiers pas enthousiasmants sur Hugo](https://100daysofcode.christopheducamp.com/page/thanks) effectués sur un sous-domaine pour mon défi personnel #100daysofcode.

Je continuerai ailleurs à utiliser Jekyll. Tests prévus sur des  sous-domaines personnels de famille pour effectuer des tests. Et je prévois d'accompagner Barbara à la rentrée dans la prise en main de son nouveau site professionnel où Bertrand [nous invite à jongler avec des milliers de photos](http://jekyll-for-craftman.netlify.com/) pour organiser des collections de photos.


## Migration vers hugo-zen

Ce qui suit est une expérience personnelle de non développeur. Si vous êtes développeur web, vous aurez sûrement de meilleures astuces. Mais ce qui me fascine dans Hugo -outre la vitesse de "build"- c'est la visualisation live en local du rendu d'affichage durant les modifications de code. Ne pas avoir à rafraîchir la page s'avère à l'usage plus que pratique et fonctionnel pour l'apprentissage et les essais/erreurs.

[](https://matjaz.it/tags/hugo-power-user/) et repartir sur des bases simples à itérer.

Travaux sur **GoHugo** : retour sur un thème minimaliste. Le thème "Beautiful Hugo" est en effet magnifique mais à mon goût  surchargé de javascript et CSS. Difficile à aborder pour l'apprentissage, l'indiewebification.

Sur les conseils de [matjaz](https://matjaz.it/) dans son post "[Hugo Power User : make it web friendly part 1](https://matjaz.it/hugo-power-user-make-it-web-friendly-1/)", je migre aujourd'hui sur [hugo-zen](https://github.com/rakuishi/hugo-zen).


![terminal : hugo serve](/img/migration-gohugo/hugo-zen-hugo-serve.png)

Si vous êtes un développeur web, vous aurez sûrement  de meilleures astuces que moi. 

Ma ligne d'apprentissage indieweb ? choisir un thème et parvenir à le personnaliser. Le thème "hugo-zen" a été développé par quelqu'un avec plus d'expérience et sera probablement réactif, élégant et disposera de certaines lignes directrices de conception. Changer et peaufiner quelque chose déjà stable est plus facile que d'écrire à partir de zéro. Après cela, vous pouvez partager vos modifications avec l'auteur du thème ! Gardons-le open source!

[Trouvé dans les archives de rakuishi](https://rakuishi.com/archives/hugo-zen/) : 

> Hugo Zen : toujours motorisé par le même générateur de site statique Hugo, 

> Hugo Zen est un thème minimaliste basé sur le framewok Skeleton avec une `custom.css` de moins de 100 lignes. Il devrait me convenir pour apprendre à concevoir un thème personnalisé.

![screenshot hugo-zen](https://github.com/rakuishi/hugo-zen/blob/master/images/screenshot.png) 

## Travaux

###  Fait 

Utilisé la [commande import](https://gohugo.io/commands/hugo_import_jekyll/) `hugo import jekyll` éclairé par [les astuces de Joe Watkins](https://joe-watkins.io/webdev/migrate-from-jekyll-to-hugo/).

1. Nettoyé tous les posts et photos 
2. `permalinks` paramétrés dans le fichier de `config.toml` pour retrouver la structure des URLs réglée sur jekyll AAAA/MM/JJ.
2. localisation de la date en français dans les templates 


### attaquer le `config.tom

- encodage UTF-8 `<meta charset="utf-8"/>` dans la section `<head>`
- personnalisation fichier '.htaccess` 
    #Set HTTP headers for Charset
    AddDefaultCharset UTF-8
- + à finaliser avec [ça](https://matjaz.it/hugo-power-user-make-it-web-friendly-1/)




----

[source](https://joe-watkins.io/webdev/migrate-from-jekyll-to-hugo/)

## Gérer Templates

J'ai choisi de partir du thème Hugo-zen que je hackerai ces prochains jours. Hugo recomande de [personnaliser les thèmes](https://gohugo.io/themes/customizing/) en ajoutant de nouveaux partiels de template au dossier `/layouts`.

J'ai copié tous mes fichiers images provenant de Jekyll dans le dossier `/static` de Hugo. When Hugo builds it will copy all the contents of that folder over to the `/public`folder which you would then deploy.

I prefer to stick my images, Sass, JavaScript, package.json, and Gulpfile etc. in the `/static`folder as well.

Les templates en sortie de boîte sont plutôt aisés à comprendre. Ils tirent partie de la syntaxe [Go](https://golang.org/) et on peut aisément porter la [syntaxe liquidde Jekyll](https://jekyllrb.com/docs/templates/) en Go. par ex. `{{ ma_page.title }}` vers `{{ .Title }}`

You will want to integrate the template structure from your Jekyll `/_layouts` and `/_partials`folders site to the Hugo theme `/layouts` folder or the theme’s `/themes/theme-name/layouts`.

## Pages Statiques 

Some Jekyll sites have static pages that are not posts. You may need to create these manually with `$ hugo new page-name-here.md` which will stick the static page in the `/content` folder. You can define the url of those pages in the [front matter](https://gohugo.io/content/organization/) of that page.

## Gérer votre site Hugo sur GitHub Pages

If you want to host your Hugo site on GitHub you will want to deploy the `/public` folder to your GitHub pages repo. Be sure to include a `.nojekyll` file in your `/static` before doing this. [Learn more about the .nojekyll file](https://github.com/blog/572-bypassing-jekyll-on-github-pages).

## Yay!

So far I have really enjoyed the speed and and how easy it is to use Hugo. Now when I have an idea for a post I don’t have to wonder if it will make it up to the web! [Go get Hugo now](https://gohugo.io/)!

  





