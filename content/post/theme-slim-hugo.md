---
title: "Minimaliste : le Thème Slim pour Hugo"
date: 2017-07-20T16:20:32+02:00
lastmod: 2017-08-27
draft: true
---

**Contexte** : Étude de ce  [tutoriel](https://code.tutsplus.com/tutorials/make-creating-websites-fun-again-with-hugo-the-static-website-generator-written-in-go--cms-27319) pour envisager de produire une vidéo de production Hugo en moins <!--more-->de x minutes.


# Slim

Slim est le thème que j'ai retenu pour décorer mon bazar minimal sur le générateur de site [Hugo](http://gohugo.io/).

![Slim screenshot](https://github.com/zhe/hugo-theme-slim/blob/master/images/screenshot.png)

[Demo](http://themes.gohugo.io/theme/slim).

## Installation Hugo 

```bash
brew install hugo
```

à écrire vite et faire un article

## Installation du thème

```bash
mkdir themes
cd themes
git clone https://github.com/zhe/hugo-theme-slim slim
```

Pour plus d'informations regardez les [docs](http://gohugo.io/themes/installing) .

## Configuration

Vous pouvez ajouter `params` à l'intérieur du fichier de configuration `config.toml` de votre site :

```toml
[params]
  Subtitle = "Sous titre de votre site ou tagline"
  GithubID = "Votre ID Github"
  TwitterID = "Votre ID Twitter"
  AnalyticsID = "Your Google Analytics tracking code"
  DisqusShortname = "Votre pseudo disqus"
  Summary = true  # true or false
  Content = true  # true or false
  # si les deux sont sur true, le résumé est affiché.
  # FooterMsg = "Copyright tof 2017. Motorisé par Hugo."
```

si vous utilisez `config.yaml`, cela pourrait ressembler à ce qui suit :

```
params:
  Subtitle: "Your site's subtitle/tagline"
  GithubID: "Your Github ID"
  TwitterID: "Your Twitter ID"
  AnalyticsID: "Your Google Analytics tracking code"
  DisqusShortname: "Your Disqus shortname"
  Summary: true # takes true or false
  Content: false # takes true or false
  # if both are set to true, summary is shown
  # FooterMsg: "Custom footer message. Powered by Hugo."
```

### Activer les commentaires Disqus sur votre post

1. Ajoutez votre pseudo Disqus Shortname au fichier de configuration du site ;
2. Vous pouvez activer Disqus par-post, en ajoutant `comments: true` (YAML) ou `comments = true` (TOML) dans le front matter de votre post. Pour les désactiver, vous pouvez soit changer la valeur sur `false` ou plus simplement inclure la variable `comments` et sa valeur à all. 

## Construire votre site

```bash
hugo server -t slim
```


## Licence

Open sourcé sous [Licence MIT](https://github.com/zhe/hugo-theme-slim/blob/master/LICENSE.md).
