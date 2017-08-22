---
title: CSS Tufte
subtitle: des outils pour mettre en forme les articles
comments: false
date: 2017-08-20
lastmod: 2017-08-20
hidefromhome: true
---

*Une première ébauche de traduction pour étude d'un nouveau thème Hugo, extraite de la [source](https://edwardtufte.github.io/tufte-css/) originale, seul lien de référence.*

Tufte CSS fournit des outils pour mette en forme des articles sur Internet en utilisant les idées démontrées par les livres et les documents d'Edward Tufte. Le style de Tufte est connu pour sa simplicité, son utilisation intensive des notes dans les pages, une intégration étroite des graphiques avec du texte et une typographie soigneusement choisie.

Tufte CSS a été créé par [Dave Liepmann](http://www.daveliepmann.com/) et fait désormais partie du projet Edward Tufte. L'idée originale provient de [Tufte-LATEX](https://tufte-latex.github.io/tufte-latex/) et des [formats de documents de Tufte en R Markdown](http://rmarkdown.rstudio.com/tufte_handout_format.html). Nous remercions chaleureusement toutes les personnes qui ont contribué à ces projets.

Si vous voyez quelque chose que Tufte CSS pourrait améliorer, nous nous réjouissons de votre contribution sous la forme d'une issue ou pull request sur le projet GitHub: [tufte-css](https://github.com/edwardtufte/tufte-css). Veuillez noter les [consignes de contribution](https://github.com/edwardtufte/tufte-css#contributing).

Enfin, un rappel sur l'objectif de ce projet. Le Web n'est pas imprimé. Les pages Web ne sont pas des livres. Par conséquent, l'objectif de "Tufte CSS" n'est pas de dire que "les sites Web devraient ressembler à cette interprétation des livres de Tufte", mais plutôt "voici quelques techniques développées par Tufte que nous avons trouvé utiles dans l'impression ; peut-être que vous pouvez trouver un moyen de les rendre utiles sur le Web". Tufte CSS est simplement un croquis d'une manière de mettre en œuvre cet ensemble d'idées. Ce devrait être un point de départ, pas un objectif de design, car tout projet doit présenter ses informations selon les meilleures conditions.

## Démarrage 

Pour utiliser Tufte CSS, copiez `tufte.css` et le répertoire `et-book` des fichiers de police dans votre dossier de projet, puis ajoutez ce qui suit au bloc `head` de votre document HTML :

```html
<link rel="stylesheet" href="tufte.css" />
```

Maintenant, il vous suffit d'utiliser les règles CSS fournies et les conventions Tufte CSS décrites dans ce document. Pour obtenir de meilleurs résultats, consultez la Source et inspectez l'élément fréquemment.

(...)


## Tufte CSS et Thème Hugo 

- <https://github.com/ChristopherA/LifeWithAlacrityBlog/tree/master/blog/themes/indie-tufte> - par Kevin Marks
