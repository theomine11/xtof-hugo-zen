---
title: "GoHugo : Accélerer Votre Site Statique"
date: 2017-08-27T09:09:58+02:00
draft: true
---

Ce post est une adaptation de la série **[Hugo Power User](https://matjaz.it/tags/hugo-power-user/)**. L'idée est de faire que votre site web Hugo soit même encore plus rapide qu'un site statique par défaut. Vitesse, vitesse, vitesse !

## Préface : personnaliser un thème existant

Comme je l'ai déjà écrit dans la [3ème partie de #HugoPowerUser](https://matjaz.it/hugo-power-user-make-it-web-friendly-1/), choisissez un thème existant et personnalisez-le pour qu'il corresponde à vos besoins. Une fois terminé, commencez à lire ce qui suit, parce que nous modifierons et tordrons aussi le thème.

## La Vitesse c'est Important 

La vitesse du site Web est un facteur majeur d'importance pour votre site Web, et ce pour deux raisons principales :

- Les visiteurs : ils ne veulent pas attendre
- Les moteurs de recherche : ils préfèrent les sites Web plus rapides car les utilisateurs préfèrent

La taille du site est étroitement corrélée à la vitesse du site web ; plus les pages Web et les ressources sont importantes (plus de MB à charger pour le voir), plus le site web est lent. Un site web plus petit est une chose étonnante pour les réseaux à vitesse lente que vos lecteurs peuvent avoir à leur domicile, car tout le monde n'a pas une connexion de 100 Mbps, ou sur un réseau cellulaire. Avez-vous testé votre site Web sur une connexion EDGE (a.k.a. 2.5G) ?

## Suivez ces étapes pour accroître la vitesse

Il existe de nombreux outils pour tester la vitesse de votre site web. Ceux que j'utilise sont : 

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

### Render-blocking JS and CSS in above-the-fold content

Solution : move the `<link>` tag calling the CSS file from the head section of the HTML to the end of the `<body>`.

Consequence: it makes a CSS-less rendering of the website appear on screen a second before the CSS is loaded. This fixes the problem in the mobile section of Google’s PageSpeed Insights.

Note: the warning still pops up for the desktop analysis and on other metrics as_“render blocking CSS”_ because the website needs to load the external CSS file to be able to render the content’s style

A solution to this may be inline the whole CSS in the HTML. For simplicity’s sake I decided to keep using the external CSS file even if it’s render blocking. It’s just one file of 12 kB once minified. It’s pretty small compared to the majority of the websites and can be further gzipped by the webserver. Also the incoming of HTTP/2’s server push may be just enough to ignore this issue.

The same applies to Javascript files.

### Unifer et minifier tous les fichiers Javascript et CSS

As clearly stated on Varvy.com, **[combining](https://varvy.com/pagespeed/combine-external-css.html) and [minifying](https://varvy.com/pagespeed/minify-css.html) CSS and Javascript is really useful**.

I unified the 3 CSS files from the [Hugo Zen](https://themes.gohugo.io/hugo-zen/) theme I used for this website, then added the CSS for the code highlighting from [Highlight.js](https://highlightjs.org/) and the CSS for the fonts I previously downloaded from Google Fonts using [Localfont](http://www.localfont.com/).

This [unified CSS file](https://matjaz.it/css/style.css) has 28 kB. **Here comes the minifying!** I used [CSS Compressor](http://csscompressor.com/), a simple online tool to achieve the [minified version](https://matjaz.it/css/style.min.css) which has 14 kB; that’s 1⁄2 of the previous one!

Once the server-side compression is enabled (see later), this CSS will be even smaller: 3.5 kB and your website will be much faster! Awesome!

## Compresser les images et utiliser des vignettes 

First of all, **check the compression level of the images** you are posting with your favorite image manipulation tools. Mine are GIMP and the ImageMagick command line tools. Set the compression levels of your PNG files to 9 (out of 9) and of your JPG files to something from 70 to 90 (out of 100). The level depends on the image content, so be sure to check it after the compression.

After that, **create thumbnails of your images the exact width as your text column**. There is no need to insert a 2000x1000 image in your post when your column is 600 px wide, right? To achieve that, I use the ImageMagick command to create reduced versions of the images in a subfolder.
    
    # Create subfolder if does not exists.
    mkdir -p thumbnails
    
    # Create scaled versions of the images in this folder in the thumbnails 
    # subfolder. The reduced images bear the same name but are 600px wide.
    find . -maxdepth 1 \( -iname \*.png -o -iname \*.jpg \) -exec convert "{}" -scale 600x "thumbnails/{}" \;
    

When this is done, **use the `figure` shortcode** provided by Hugo to insert the images in a better way than pure Markdown. The images will be shown as thumbnails and will link to the full-sized version when clicked on. An example from one of my posts:
    
    {{< figure 
        src="/images/ring-distance/thumbnails/Circular_buffer.png" 
        link="/images/ring-distance/Circular_buffer.png"
    >}}
    

The `figure` shortcode is very powerful and can add titles, captions and more. Just an example here, but [check the documentation](https://gohugo.io/extras/shortcodes#figure) for the full list.
    
    {{< figure 
        src="/images/ring-distance/thumbnails/Circular_buffer.png" 
        link="/images/ring-distance/Circular_buffer.png"
        alt="Circular ring" 
        title="Image 1"
        caption="Circular ring-like buffer."
        attr="Source: Wikipedia"
        attrlink="https://en.wikipedia.org/wiki/File:Circular_buffer.svg"
    >}}
    

## Configurations .htaccess : cache, compression, keep-alive

OK, now begins the scary part bu also the most powerful one: web server configuration. As I told you before, I’m using Apache (on shared hosting), so I have to manipulate an `.htaccess` file in my website’s root directory to configure the server in a certain way. Please consider other configurations for your case and for your webserver, if needed.

For the full configuration I’m using on my website, check my [.htaccess file](https://github.com/TheMatjaz/matjaz.it/blob/master/static/.htaccess).

### Compression

I tried the Gzip compression but found out that the Deflate method works better in my case. Just add the following lines to your `.htaccess` to enable compression of text(ish) files. Images don’t need to be compressed, since they already are, as well as Woff2 font files.
    
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

Many shared hosting web servers close the connection after each file has been downloaded, which obviously creates lots of overhead to reopening it and download the next file.

Add this lines to the `.htaccess` file to let the connection be open even after the first transfer.
    
    ## Enable Keep-Alive connections
    ## --------------------------------------------------------
    <ifModule mod_headers.c>
        Header set Connection keep-alive
    </ifModule>
    

### Cache-Control header

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
    

## Load resources only when needed

This is a very broad suggestion but let me give you an example to explain: I’m using the Highlight.js library to add syntax highlighting to the code snippets on my website.

The point is: do I need syntax highlighting on every page and post? Even on the homepage?

Obviously no, so what I did is add a simple line to the frontmatter of my content files: `highlight = true`. When this variable is `true`, then a line is added to the page footer requiring the highlighting library, otherwise the library is not loaded and we have a faster website, since its a resource less.

The conditional loading is obtained with this simple lines in the footer partial file:
    
    {{ if eq .Params.highlight true }}
    <script src="/css/highlight.pack.js"></script>
    <script>hljs.initHighlightingOnLoad();</script>
    {{ end }}
    

## Final note: Wordpress vs optimized Hugo

Just a few rating results for this optimized version of my Hugo website compared to my previous version based on Wordpress

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

#### Pingdom Tools

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
