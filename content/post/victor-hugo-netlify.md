---
aliases: "victor-hugo-netlify"
title: "Victor-Hugo sur Netlify : Un Guide Étape par Étape"
subtitle: ""
slug: ""
date: "2017-08-23T11:17:10+02:00"
lastmod: "2017-08-23T12:18:10+02:00"
draft: false
categories: [jamstack]
tags: [100daysofcode, gohugo, boilerplate, netlify, déploiement, github]
---

Jetons un oeil sur la façon d’héberger un site web statique utilisant [Hugo][1] sur Netlify, en n’oubliant pas d’installer un déploiement continu.

Dans ce tutoriel, nous utiliserons [Victor Hugo][2] (un modèle Hugo continuellement maintenu) pour construire notre site statique.

Pour commencer, nous allons nous assurer que vous disposez de tous les outils dont vous aurez besoin. 
Allez-y et téléchargez Victor Hugo [ici][2].

Si vous avez déjà installé un site Hugo, vous pouvez passer directement à la section [Connexion à Netlify][3].

## Construire votre Site

Hugo construit et organise un squelette pour votre site, qui mettra en place un répertoire principal ; pour simplifier, nous appellerons ça `hugo`. En outre, il configure des sous-répertoires dans ce répertoire `hugo` comme décrit ci-dessous. Voici une ventilation basique de la structure que Victor Hugo construit pour vous :
    
```    
    |--site                // Tout ce qui est dedans sera construit avec hugo
    |  |--content          // Pages et collections. demande si pages supplémentaires
    |  |--data             // Fichiers data YAML avec toute data à utiliser dans les exemples
    |  |--layouts          // C’est l’endroit où vont les templates
    |  |  |--partials      // C’est là où vivent les includes
    |  |  |--index.html    // La page index
    |  |--static           // Les fichiers placés ici terminent dans le répertoire public
    |  |--config.toml      // L’endroit où vous réglez/stockez vos réglages de configuration
    |--src                 // Les fichiers qui passeront à travers le pipeline asset
    |  |--css              // Les fichiers CSS à la racine de ce répertoire atterrissent dans /css/...
    |  |--js               // Les app.js seront compilées dans /js/app.js avec babel
```    

Pour démarrer ouvrez le terminal, naviguer à l’endroit où réside votre répertoire Victor Hugo :
    
```bash    
    $ cd /PATH/TO/hugo
``` 

Puis installez les dépendances nécessaires en saisissant : 
```bash
    $ npm install
```    
Pour démarrer le serveur, saisissez : 
```bash
    $ npm start
```    

## Créer une page À Propos.

Dans le terminal, naviguez vers le répertoire `site` ce qui peut être fait à partir du terminal avec la ligne de commande : 
```
    $ cd site
```    

Désormais, dirigez-vous directement et initialisez la page about en utilisant la commande Hugo suivante : 

```
    $ hugo new a-propos.md
```    

Si vous ouvrez le répertoire `hugo` dans votre gestionnaire de fichiers, vous verrez une liste de sous-répertoires. Ouvrez `site/content/a-propos.md` pour visualiser ce que vous venez de créer. Vous devriez voir quelque chose comme suit : 

```yaml
---
title: "À Propos"
date: 2017-08-23T11:23:09+02:00
draft: true
---
```

Placez un peu de contenu en format Markdown sous le front-matter yaml (la section marquée entre les signes `---` avant et après) et sauvegardez.

## Maintenant, ajoutons un nouveau post.

Pour faire ainsi, entrez ce qui suit : 
```bash    
    $ hugo new post/premier.md
```    

Le nouveau fichier est situé sur `content/post/premier.md`. Il vous appartien de l'épicer :

```yaml
    ---
    title: "Mon Premier Post"
    date: 2017-08-23T11:25:34+02:00
    draft: true
    ---
    «La paix de l'esprit produit des valeurs justes, les valeurs justes produisent des pensées droites. Les bonnes pensées produisent des actions justes et les actions justes produisent un travail qui sera une réflexion matérielle pour que les autres puissent voir la sérénité au centre de tout cela.
    
    "Peace of mind produces right values, right values produce right thoughts. Right thoughts produce right actions and right actions produce work which will be a material reflection for others to see of the serenity at the center of it all."
    ― Robert M. Pirsig, Zen and the Art of Motorcycle Maintenance
```    

**Truc :** Créez quelques posts comme celui-ci pour avoir du contenu en place et voir la mise en page de plusieurs articles sous forme de listes.

Maintenant que vous avez du contenu, il est temps de l'afficher. Hugo a un [référentiel plein de thèmes][4] que vous pouvez utiliser (ou vous pouvez toujours créer un thème personnalisé). Pour les besoins de ce tutoriel, utilisons le thème [Strata][5].

Retrouvez le thème Strata dans la bibliothèque de thèmes Hugo (ou cliquez [ici][5]). Pour éviter les maux de tête et vous faciliter la vie sur la modification du thème, nous allons simplement télécharger le zip au lieu de cloner le repo du thème. Pour ce faire, cliquez sur le bouton **Clone or download**, puis cliquez sur le bouton **Download zip** situé à droite de la page. Dans le répertoire `hugo / site`, créez un nouveau dossier appelé `themes`, puis décompressez le fichier Strata dans `/PATH/TO/hugo/themes`. N'oubliez pas de renommer le dossier de `hugo-strata-theme-master` en un simple` hugo-strata-theme`.

## Régler votre premier thème

La plupart des thèmes documentent dans leur fichier `README.md` la façon de les paramétrer. Pour le thème Strata, il y a cinq choses à faire :

**1** - Pour éviter les conflits avec le thème, nous devons effacer quelques-uns des fichiers initiaux, aussi effacez tous les fichiers dans le répertoire `layouts` situé sur `site/layouts`. Un autre fichier de conflit est `src/css/main.css` \- effacez aussi ce fichier. (Si vous construisez votre propre thème, ne tenez pas compte de ces étapes.)

**2** - Puis nous devons copier les contenus du fichier exemple `config.toml` à partir de `themes/hugo-strata-theme` sur notre fichier du site `config.toml` situé sur `hugo/site`.

***NOTE : Assurez-vous de régler la variable `baseurl` dans le fichier config vers un chemin relatif comme ci-dessous.**

```bash
    baseurl = "/"
```    

**3** - Nous devons mettre à jour notre layout de landing page avec le layout template du thème sur `themes/hugo-strata-theme/index.html`. Pour plus de facilité, voici le code de ce thème (en date du 9/9/16) pour remplacer les contenus de votre fichier `index.html` situés dans `site/layouts/index.html`.

```    
        {{ define "main" }}
        {{ if not .Site.Params.about.hide }}
            {{ partial "about" . }}
        {{ end }}
    
        {{ if not .Site.Params.portfolio.hide }}
            {{ partial "portfolio" . }}
        {{ end }}
    
        {{ if not .Site.Params.recentposts.hide }}
            {{ partial "recent-posts" . }}
        {{ end }}
    
        {{ if not .Site.Params.contact.hide }}
            {{ partial "contact" . }}
        {{ end }}
    {{ end }}
```    

**4** - Pour inclure notre nouvelle page about dans cette navigation de thème, ouvrez le fichier `config.toml` que nous avons modifié précédemment et mettez à jour les variables du menu pour inclure la page about comme suit : 

```    
        [[menu.main]]
        name = "Home"
        url  = "/"
        weight = 0
    
    [[menu.main]]
        name = "About"
        url  = "about"
        weight = 5
    
    [[menu.main]]
        name = "Blog"
        url  = "post/"
        weight = 10
```    

Vous verrez maintenant le lien de page about restitué dans la barre latérale de navigation mais si vous cliquez dessus, elle affichera une erreur que la page about ne peut pas être trouvée. Ceci parce que nous n’avons jamais modifié le statut de la page de « draft » à « production-ready ». Tout ce que nous devons faire c’est modifier la valeur de `draft` de `true` vers `false` dans le front-matter. Votre fichier `about.md` que nous avons créé précédemment devrait désormais ressembler à quelque chose comme suit : 
    
```bash
    ---
    date = "2016-09-09T10:15:23-04:00"
    draft = false
    title = "about"
    ---
    
    ## Ceci est notre contenu échantillon Markdown.
```    

**5** - Répétez cette mise à jour de statut draft avec tous les fichiers post que nous avons créés plus tôt (faisant référence au `first.md` et autres contenus que vous pouvez avoir créé). Ceci vous permettra de voir ces articles listés sur la page d’accueil (dans la section "Recent Blog Posts") et sur la page "Blog" (accédée en cliquant "Blog" dans la navigation latérale).

## **Tester votre Site**

Maintenant que nous avons paramétré le site, jetons un oeil à ce que nous obtenons (si vous n’avez pas déjà fait un suivi en temps réel). Allumez le serveur dans le terminal avec la commande : 

```bash
    $ npm start
```    

Voilà ! Vous devriez voir votre landing page mise en forme pour ressembler à la photo d’écran ci-dessous : 

![Screenshot][6]

Même si vous êtes effrayé de voir votre nouvelle page de destination, allez-y et consultez aussi vos nouvelles pages "À propos" et "Blog".

Si tout vous semble bien, il est temps de pousser votre nouveau site hugo sur un compte Github (Netlify prend également en charge les liaisons vers BitBucket, GitLabs et les repos autonomes).

## **Créer votre Repo Git**

[Créez un nouveau repo sur GitHub][7]. Pour éviter les erreurs, n'initialisez  pas le nouveau repo avec les fichiers README, license, ou gitignore. Vous pouvez ajouter ces fichiers une fois que votre projet aura été poussé vers GitHub.

Ouvrez le terminal (ou votre outil de ligne de commande préféré) et assurez vous d'être que le répertoire de travail est réglé sur votre projet local. Si non, naviguez là comme suit : 
    
```bash    
    cd /PATH/TO/hugo
```    

Initialisez le répertoire local sous forme de repo Git : 

```bash
    git init
```    

Ajoutez les fichiers dans votre nouveau repo local. Ceci les présente pour le premier commit : 
```bash
    git add .
```    

Committez les fichiers que vous avez présentés dans votre repo local :
```bash
    git commit -m 'Premier commit'
```    

Tout en haut de votre page Quick Setup de repo GitHub, cliquez sur l'icône presse-papier pour copier l'URL du dépôt distant.

Dans le Terminal, ajoutez l'URL du repo distant où votre repo local sera poussé.

```bash
    git remote add origin YOUR_GITHUB_REPOSITORY_URL
```    

Vérifiez votre URL
```bash
    git remote -v
```    

Maintenant, il est temps de pousser les modifications dans votre repo local sur GitHub.
```bash
    git push origin master
```    

Maintenant que votre repo est sur GitHub, connectons-le à Netlify.

## Démarrer sur Netlify

Dans cette section, nous montrerons combien il est facile de lancer votre premier site Hugo sur Netlify. Si vous n'êtes pas déjà utilisateur Netlify, allez-y et enregistrez-vous d'abord [ici][8], c'est gratuit.

### Étape 1 : Ajouter Votre Nouveau Site

![étape 1 - ajouter][9]

La création d'un nouveau site sur Netlify est simple. Une fois que vous vous êtes connecté, vous serez amené sur <https://app.netlify.com>. Si vous venez de démarrer, il n'y a qu'une seule option, cliquez sur le bouton **Add A New Project** affiché au-dessus.

### Étape 2 : Relier à Votre GitHub

Cliquer sur "Add A New Project" vous amène à cet écran :

![étape 2 - lier][10]

Lorsque vous poussez sur GitHub, Netlify fait tout le travail. Fini le déploiement manuel des mises à jour ou modifications !

Puisque votre repo est déjà poussé sur GitHub, il suffit de lier Netlify à GitHub. Cliquez sur le bouton **GitHub** comme illustré dans la capture d'écran ci-dessus.

### Étape 3 : Autoriser Netlify

![étape 3 - autoriser][11]

Il est désormais temps d'autoriser Netlify et GitHub à se parler. En cliquant sur le bouton **Authorize Application**, cela fera exactement cela. Comme cela est indiqué dans l'image ci-dessous, Netlify ne stocke pas votre jeton d'accès GitHub sur nos serveurs. Si vous souhaitez en savoir plus sur les demandes d'autorisations Netlify et pourquoi nous en avons besoin, vous pouvez visiter <https://docs.netlify.com/github-permissions/>.

### Étape 4 : Sélectionner Votre Repo

![étape 4 - repo][12]

Maintenant que vous avez connecté Netlify et GitHub, vous pouvez voir une liste de vos repos Git. Il y a le repo "hugo" que nous venons de pousser à GitHub. Sélectionnez-le.

### Étape 5: Configurer Vos Paramétrages

![étape 5 - configurer][13]

Ici vous pouvez configurer vos options. Assurez-vous que votre répertoire est `dist/` et que votre commande de construction est `npm run build`. Ensuite, cliquez sur le bouton **Build your site** pour continuer.

### Étape 6 : Construire Votre Site

![step 6 - build][14]

Maintenant, il est temps de s'asseoir et de vous détendre. Vous avez fait votre part pour permettre à Netlify de prendre soin du reste - ça ne prendra qu'une minute.

### Étape 7 : Terminé

![étape 7 - terminé][15]

Netlify a avancé et a donné à votre site un nom temporaire. Mettons-le à jour rapidement pour que cela soit un peu plus joli :

![étape 8 - plus joli][16]

Là, c'est mieux. C'est beau, non ? N'était-ce pas si simple ? Avancez un peu plus loin et configurez votre domaine personnalisé (Apprenez comment faire cela [ici] [17]). Félicitations, et merci d'utiliser Netlify !

[Article original](https://www.netlify.com/blog/2016/09/21/a-step-by-step-guide-victor-hugo-on-netlify/ "Permalink to A Step-by-Step Guide: Victor-Hugo on Netlify")



---

[1]: https://gohugo.io/
[2]: https://github.com/netlify/victor-hugo
[3]: https://www.netlify.com#netlifystart
[4]: http://themes.gohugo.io/
[5]: https://github.com/digitalcraftsman/hugo-strata-theme
[6]: https://raw.githubusercontent.com/digitalcraftsman/hugo-strata-theme/dev/images/screenshot.png
[7]: https://help.github.com/articles/create-a-repo/
[8]: https://app.netlify.com/signup
[9]: https://cdn.netlify.com/ef2fd8809717bbf8c7a16ac2862c19bb12f717b5/ef6e8/img/blog/add-new-project.png
[10]: https://cdn.netlify.com/6ce8bf46dcc8bfc6d6ef982c7870eb86e32d2b8c/89152/img/blog/step-2-hugo.png
[11]: https://cloud.githubusercontent.com/assets/6520639/9803635/71760370-57d9-11e5-8bdb-850aa176a22c.png
[12]: https://cloud.githubusercontent.com/assets/6520639/9897552/b9ea7f7c-5bfe-11e5-94a0-f957a7d1986e.png
[13]: https://cdn.netlify.com/80976208deb6958b0fd438cb961a63d95a259f07/c1ae2/img/blog/config-your-repo.png
[14]: https://cdn.netlify.com/8f58588b14e3136d2885c3df9875b1b5b8e72f51/0a39b/img/blog/building-site.png
[15]: https://cdn.netlify.com/adbf91d6cdc41c8295b1162e7058b013d52e93f3/aa69f/img/blog/done-1.png
[16]: https://cdn.netlify.com/7af81cfe5062746090a0fd72b6cbea5961f02627/a165c/img/blog/done-2.png
[17]: https://www.netlify.com/blog/2016/03/14/setting-up-your-custom-domain/

