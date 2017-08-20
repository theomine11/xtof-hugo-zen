---
title: Exemple de Grande Image
subtitle: Utiliser Plusieurs Images
date: 2017-07-27
tags: ["exemple", "bigimg"]
bigimg: [{src: "/img/triangle.jpg", desc: "Triangle"}, {src: "/img/sphere.jpg", desc: "Sphère"}, {src: "/img/hexagon.jpg", desc: "Hexagon"}]
---

Les bannières d'images en haut de la page font référence à `bigimg` dans ce thème. Elles sont facultatives, et une image ou plus peuvent être spécifiées. Si plus d'une image est spécifée, [ce qui n'est pas recommandé](https://conversionxl.com/dont-use-automatic-image-sliders-or-carousels/), les images tournent toutes les 10 secondes. Dans le front matter, les bigimgs sont spécifiées en utilisant une array de hashes.

<!--more-->

Une bigimg peut être spécifiée dans le front matter avec le front-matter YAML suivant :
```yaml
bigimg: [{src: "/img/triangle.jpg", desc: "Triangle"}]
```

Plusieurs bigimgs peuvent être spécifiées dans le front matter avec le YAML suivant :
```yaml
bigimg: [{src: "/img/triangle.jpg", desc: "Triangle"}, 
         {src: "/img/sphere.jpg", desc: "Sphere"}, 
         {src: "/img/hexagon.jpg", desc: "Hexagon"}]
```

Notez également que le champ de description est facultatif, et les images peuvent plutôt être spécifiées par :

```yaml
bigimg: [{src: "/img/triangle.jpg"}, 
         {src: "/img/sphere.jpg"}, 
         {src: "/img/hexagon.jpg"}]
```

Le tableau de hashes YAML ci-dessus a été écrit en style "flow". Cependant, lors de la génération d'une nouvelle page ou d'une publication avec `hugo new post/monpost.md`, hugo peut interpréter l'archétype pour `bigimg` dans le style YAML par défaut. La définition de multiples `bigimg` complets avec des descriptions dans ce style serait spécifié par 

```yaml
bigimg: 
- {src: "/img/triangle.jpg", desc: "Triangle"}
- {src: "/img/sphere.jpg", desc: "Sphere"}
- {src: "/img/hexagon.jpg", desc: "Hexagon"}
```

De plus amples informations peuvent être trouvées  [dans ce tutoriel YAML](https://rhnh.net/2011/01/31/yaml-tutorial/).