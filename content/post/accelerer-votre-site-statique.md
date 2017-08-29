---
title: "GoHugo : Accélerer Votre Site Statique"
date: 2017-08-27T09:09:58+02:00
draft: true
lastmod: 2017-08-29
---

Ce post est une adaptation de la série **[Hugo Power User](https://matjaz.it/tags/hugo-power-user/)**. L'idée est de faire que votre site web Hugo soit même encore plus rapide qu'un site statique par défaut. Vitesse, vitesse, vitesse !

## Préface : personnaliser un thème existant

Comme je l'ai déjà écrit dans la [3ème partie de #HugoPowerUser](https://matjaz.it/hugo-power-user-make-it-web-friendly-1/), choisissez un thème existant et personnalisez-le pour qu'il corresponde à vos besoins. Une fois terminé, commencez à lire ce qui suit, parce que nous allons modifier et tordre aussi le thème.

## La Vitesse c'est Important 

La vitesse d'affichage est un facteur majeur d'importance pour votre site Web, et ce pour deux raisons principales :

- Les visiteurs : ils ne veulent pas attendre
- Les moteurs de recherche : ils préfèrent les sites web plus rapides car les utilisateurs préfèrent

La taille du site est étroitement corrélée à la vitesse du site web ; plus les pages web et les ressources sont importantes (plus de MB à charger pour le voir), plus le site web est lent. Un site web plus petit est une chose étonnante pour les réseaux à vitesse lente que vos lecteurs peuvent avoir à leur domicile, car tout le monde n'a pas une connexion de 100 Mbps, ou sur un réseau cellulaire. Avez-vous testé votre site Web sur une connexion EDGE (a.k.a. 2.5G) ?

## Suivez ces étapes pour accroître la vitesse

Il existe plein d'outils pour tester la vitesse de votre site web. Ceux que j'utilise sont : 

  * [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
  * [Varvy](https://varvy.com/), which includes 3 (!) tools
  * [Pingdom Tools](https://tools.pingdom.com/)
  * [GTMetrix](https://gtmetrix.com/)
  
Ce sont des outils étonnants, non seulement pour montrer les résultats d'une manière soignée, mais parce qu'**ils suggèrent les façons d'améliorer**.

Le processus d'optimisation du site Web que j'ai effectué sur ce site était essentiellement le suivant :

1. prendre un outil de mesure de vitesse et le lancer
1. prendre un problème pointé par l'outil et le réparer avec la solution proposée et un peu de recherche google
2. répéter la même chose pour chaque problème
4. répéter pour chaque outil

Quelques tests de vitesse sur ma page d'accueil montraient une accélération incroyable du site web en passant simplement d'un blog WordPress dynamique à un site statique avec Hugo.

## Améliorations potentielles sur un site web statique

Migrer vers un générateur statique comme Hugo me fait réfléchir aux métriques, mais il y a encore quelques points à nettoyer ici et là.

### Éliminer les codes JavaScript et CSS qui bloquent l'affichage du contenu au-dessus de la ligne de flottaison

Solution : déplacer la balise `<link>` appelant le fichier CSS de la section head du HTML vers la fin de la `<body>`.

Conséquence : cela produit un rendu du site web sans-CSS qui apparaît à l'écran une seconde avant que la CSS ne soit chargée. Ceci règle le problème de la section mobile des [outils de pagespeed Google](https://developers.google.com/speed/pagespeed/insights/).

Remarque : l'avertissement continue à s'afficher pour l'analyse du desktop et sur d'autres métriques comme _“Éliminer les codes JavaScript et CSS qui bloquent l'affichage du contenu au-dessus de la ligne de flottaison_ parce que le site web a besoin de charger le fichier CSS externe pour pouvoir afficher le style du contenu.

Une solution à cela peut être de mettre tout le CSS dans le HTML. Par souci de simplicité, j'ai décidé de continuer à utiliser le fichier CSS externe même s'il bloque le rendu. C'est juste un fichier de 12 kB une fois minifié. C'est assez petit par rapport à la majorité des sites Web et peut être gzipé par le serveur web. En outre, l'entrée du serveur HTTP/2 peut être suffisante pour ignorer ce problème.

La même chose s'applique aux fichiers Javascript.

### Unifer et minifier tous les fichiers Javascript et CSS

Comme le déclare clairement Varvy.com, **[combiner](https://varvy.com/pagespeed/combine-external-css.html) et [minifier](https://varvy.com/pagespeed/minify-css.html) les CSS & Javascript s'avère vraiment utile**.

J'ai unifié les 3 fichiers CSS provenant 
1. du thème [Hugo Zen](https://themes.gohugo.io/hugo-zen/) que j'ai utilisé pour ce site web, 
2. puis ajouté la CSS pour la mise en surbrillance du code provenant de [Highlight.js](https://highlightjs.org/) 
3. et pour finir, ajouté la CSS pour les fontes que j'avais précédemment téléchargée à partir de Google Fonts en utilisant [Localfont](http://www.localfont.com/).

Ce [fichier CSS unifié](https://matjaz.it/css/style.css) fait 28 kB. **Voici comment minifier !** J'ai utilisé [CSS Compressor](http://csscompressor.com/), un simple outil en ligne pour parvenir à la [version minifiée](https://matjaz.it/css/style.min.css) qui fait 14 kB ; soit 1⁄2 de la précédente !

Une fois la compression activée côté serveur (voir plus tard), cette CSS sera même encore plus petite : 3.5 kB et votre site web sera beaucoup plus rapide ! Merveilleux ! 

## Compresser les images et utiliser des vignettes 

Tout d'abord, **vérifiez le niveau de compression des images** que vous publiez avec vos outils de manipulation d'image préférés. J'utilise GIMP et les outils de ligne de commande ImageMagick. Réglez les niveaux de compression de vos fichiers PNG sur 9 (sur 9) et pour vos fichiers JPG quelque chose de 70 à 90 (sur 100). Le niveau dépend du contenu de l'image, alors assurez-vous de le vérifier après la compression.

Ensuite, **créez des vignettes de vos images à la largeur exacte de votre colonne de texte**. Il n'est pas nécessaire d'insérer une image 2000x1000 dans votre publication lorsque votre colonne est de 600px de largeur, n'est-ce pas ? Pour ce faire, j'utilise la commande ImageMagick pour créer des versions réduites des images dans un sous-dossier.

```bash
    # Cree le sous-dossier s'il n'existe pas.
    mkdir -p thumbnails
    
    # Créer des versions mises à l'échelle des images dans ce dossier dans le dossier thumbnails.
    # Les images réduites portent le meme nom mais font 600px de large.
    find . -maxdepth 1 \( -iname \*.png -o -iname \*.jpg \) -exec convert "{}" -scale 600x "thumbnails/{}" \;
```     

Une fois que c'est fait, **utilisez le shortcode `figure`** fourni par Hugo pour insérer les images d'une meilleure manière que le Markdown pur. Les images seront affichées en miniatures et seront liées à la version pleine-taille une fois qu'on clique dessus. Un exemple provenant d'un de mes posts : 

```go    
    {{< figure 
        src="/images/ring-distance/thumbnails/Circular_buffer.png" 
        link="/images/ring-distance/Circular_buffer.png"
    >}}
```    

Le shortcode `figure` est très puissant et peut ajouter des titles, captions et plus encore. Juste un exemple ici, mais [regardez la documentation](https://gohugo.io/extras/shortcodes#figure) pour une liste complète.

```go    
    {{< figure 
        src="/images/ring-distance/thumbnails/Circular_buffer.png" 
        link="/images/ring-distance/Circular_buffer.png"
        alt="Circular ring" 
        title="Image 1"
        caption="Circular ring-like buffer."
        attr="Source: Wikipedia"
        attrlink="https://en.wikipedia.org/wiki/File:Circular_buffer.svg"
    >}}
```    

## Configurations .htaccess : cache, compression, keep-alive

OK, commençons maintenant la partie effrayante mais aussi la plus puissante : la configuration du serveur web. Comme je vous l'ai déjà dit, j'utilise Apache (sur de l'hébergement mutualisé), donc je dois manipuler un fichier `.htaccess` dans le répertoire racine de mon site Web pour configurer le serveur d'une certaine manière. Si nécessaire, veuillez envisager d'autres configurations pour votre cas et pour votre serveur web.

Pour la configuration complète que j'utilise pour mon site web, regardez mon [fichier .htaccess](https://github.com/TheMatjaz/matjaz.it/blob/master/static/.htaccess).

### Compression

J'ai essayé la compression Gzip mais j'ai découvert que la méthode Deflate fonctionne mieux dans mon cas. Ajoutez simplement les lignes suivantes à votre `.htaccess` pour permettre la compression des fichiers texte (ish). Les images n'ont pas besoin d'être compressées, car elles le sont déjà, ainsi que les fichiers de police Woff2.


    
    ## Enable compression for common file types
    ## --------------------------------------------------------
    <IfModule mod_deflate.c>
      <IfModule mod_filter.c>
        # Plaintext, HTML, JavaScript, CSS, XML and fonts
        AddOutputFilterByType DEFLATE application/javascript
        AddOutputFilterByType DEFLATE application/rss+xml
        AddOutputFilterByType DEFLATE application/vnd.ms-fontobject
        AddOutputFilterByType DEFLATE application/x-font
        AddOutputFilterByType DEFLATE application/x-font-opentype
        AddOutputFilterByType DEFLATE application/x-font-otf
        AddOutputFilterByType DEFLATE application/x-font-truetype
        AddOutputFilterByType DEFLATE application/x-font-ttf
        AddOutputFilterByType DEFLATE application/x-javascript
        AddOutputFilterByType DEFLATE application/xhtml+xml
        AddOutputFilterByType DEFLATE application/xml
        AddOutputFilterByType DEFLATE font/opentype
        AddOutputFilterByType DEFLATE font/otf
        AddOutputFilterByType DEFLATE font/ttf
        AddOutputFilterByType DEFLATE image/svg+xml
        AddOutputFilterByType DEFLATE image/x-icon
        AddOutputFilterByType DEFLATE text/css
        AddOutputFilterByType DEFLATE text/html
        AddOutputFilterByType DEFLATE text/javascript
        AddOutputFilterByType DEFLATE text/plain
        AddOutputFilterByType DEFLATE text/xml
    
        # Remove browser bugs
        BrowserMatch ^Mozilla/4 gzip-only-text/html
        BrowserMatch ^Mozilla/4\.0[678] no-gzip
        BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
        Header append Vary User-Agent
      </IfModule>
    </IfModule>
    

### Keep-Alive header

Beaucoup de serveurs Web hébergés partagés ferment la connexion après que chaque fichier ait été téléchargé, ce qui crée évidemment beaucoup de surcharge pour le rouvrir et télécharger le fichier suivant.

Ajoutez ces lignes au fichier `.htaccess` pour laisser la connexion ouverte même après le premier transfert.

    
    ## Enable Keep-Alive connections
    ## --------------------------------------------------------
    <ifModule mod_headers.c>
        Header set Connection keep-alive
    </ifModule>
    

### Header Cache-Control

Finally the browser cache, a great tool to make your website fast. I use the`Cache-Control` header to add to each resource a time to live in the browser cache, so the browser does not even ask the server for validation. It just serves the user the cached content.

    
    ## Set browser cache time to live
    ## --------------------------------------------------------
    # 1 YEAR - fonts
    <FilesMatch "\.(woff2|woff|eot|ttf)$">
        Header set Cache-Control "max-age=31536000, public"
    </FilesMatch>
    
    # 3 MONTHS - images don't change except in strange cases
    <FilesMatch "\.(png|svg|ico|jpg|jpeg|gif|pdf)$">
        Header set Cache-Control "max-age=7884000, public"
    </FilesMatch>
    <FilesMatch "^manifest\.json$">
        # Manifest file used for Favicons by RealFaviconGenerator
        Header set Cache-Control "max-age=7884000, public"
    </FilesMatch>
    
    # 2 WEEKS - possible to be changed
    <FilesMatch "\.(css|txt|js)$">
        Header set Cache-Control "max-age=1209600, public"
    </FilesMatch>
    
    # NEVER CACHE - notice the extra directives
    <FilesMatch "\.(php|py|cgi|pl)$">
        Header set Cache-Control "max-age=0, private, no-store, no-cache, must-revalidate"
    </FilesMatch>
    

## Chargement des Ressources Uniquement si Besoin 

Il s'agit d'une suggestion très large, mais permettez-moi de vous donner un exemple pour expliquer : j'utilise la bibliothèque `highlight.js` pour ajouter la mise en surbrillance de la syntaxe pour afficher les extraits de code.

Le point est de savoir si j'ai besoin de la mise en surbrillance de syntaxe sur chaque page et sur chaque post ? Même sur la page d'accueil ?

Évidemment non. J'ai donc ajouté une simple ligne dans le front-matter de mes fichiers de contenu : `highlight = true`. Lorsque cette variable est `true`, une ligne est ajoutée au pied de page nécessitant l'appel de la bibliothèque de mise en surbrillance. Dans le cas inverse, la bibliothèque n'est pas chargée et nous disposons d'un site web plus rapide, car il s'agit d'une ressource en moins.

Le chargement conditionnel est obtenu avec ces lignes simples dans le fichier partiel du pied de page:

    
    {{ if eq .Params.highlight true }}
    <script src="/css/highlight.pack.js"></script>
    <script>hljs.initHighlightingOnLoad();</script>
    {{ end }}
    

## Note Finale : Wordpress vs Hugo optimisé 

Quelques résultats pour cette version optimisée de mon site web Hugo comparés à ma version précédente basée sur Wordpress

#### Google PageSpeed Insights

CriteriaWordpressHugo

Desktop
73
100

Mobile speed
63
97

Mobile UX
99
100

#### Outils Pingdom

The measurements were performed from the same location.

CriteriaWordpressHugo

Performance grade
81
**100**

Page size
646.6 kB [1]
**22.9 kB**

Load time
1.38 s
**184 ms**

Faster than
83%
**100%**

Requests
35
3 [2]

[1]: I removed all featured images that were displayed for each post. I also removed the full content of the posts to make the home page show just the titles, metadata and excerpts of the posts.

[2]: for the home page.

#### GTmetrix and YSlow

Both give the optimized Hugo website an **A (99%) rating**.

* * *

This post is part of the series **[Hugo Power User](https://matjaz.it/tags/hugo-power-user/)**. Check the other ones:

  1. [#HugoPowerUser: reasons to choose Hugo](https://matjaz.it/hugo-power-user-reasons-to-choose-hugo/) – 09 July 2016
  2. [#HugoPowerUser: content organization](https://matjaz.it/hugo-power-user-organization/) – 10 July 2016
  3. [#HugoPowerUser: make it web friendly pt. 1](https://matjaz.it/hugo-power-user-make-it-web-friendly-1/) – 13 July 2016
  4. [#HugoPowerUser: make it web friendly pt. 2](https://matjaz.it/hugo-power-user-make-it-web-friendly-2/) – 19 July 2016
  5. [#HugoPowerUser: make your static website even faster](https://matjaz.it/hugo-power-user-make-your-static-website-even-faster/) – 27 July 2016

**Categories**: [Blog](https://matjaz.it/categories/blog/)  
**Tags**: [Hugo power user](https://matjaz.it/tags/hugo-power-user/) // [Hugo](https://matjaz.it/tags/hugo/) // [Design](https://matjaz.it/tags/design/) // [Blog](https://matjaz.it/tags/blog/) // [Optimization](https://matjaz.it/tags/optimization/) // [Website](https://matjaz.it/tags/website/) // [Performance](https://matjaz.it/tags/performance/)
