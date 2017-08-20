---
title: "r1d21 SVG"
subtitle: "Extraction d'une icône Font-Awesome"
slug: "r1d21-svg"
date: "2017-08-13T21:05:42+02:00"
lastmod: "2017-08-13T21:05:42+02:00"
draft: false
tags: [100daysofcode,svg]
bigimg: [{src: "/img/path.jpg", desc: "Sur la Route"}]
---

## Statut : 

Après l'[étude des couleurs](/2017/08/12/r1d20-couleurs/), je reste toujours motivé par l'excellente section "graphisme" dans le cours en ligne de Todd McLeod : "[How to Create A Website: An HTML Tutorial and CSS Tutorial](https://www.greatercommons.com/learn/6708511014649856)". 

Mon intention à cette heure :

- explorer la *personnalisation* d'icônes SVG en HTML et CSS pour intégration dans les menus de sites web responsive,
- mesurer les *gains de performance* en évitant de charger des librairies complètes d'icônes.

## Premier gribouillage...

Cette figure est constituée d'un chemin (le coeur), d'un rectangle, d'un segment de droite et d'un cercle.

<svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="600" height="200">
<title>Exemple simple de figure SVG</title>
<desc>Cette figure est constituée d'un chemin, d'un rectangle, d'un segment de droite et d'un cercle.</desc>
<rect width="100" height="80" x="0" y="70" fill="pink" />
<line x1="5" y1="5" x2="250" y2="95" stroke="red" />
<circle cx="70" cy="80" r="50" fill="hotpink" />
<text x="180" y="60">chemin, rectangle, segment et cercle.</text>
<path d="M80.2,55.9L52.3,83.3c-0.5,0.5-1.3,0.8-2,0.8s-1.4-0.3-2-0.8L20.5,55.8c-0.4-0.3-10.2-9.5-10.2-20.5 c0-13.4,8-21.4,21.4-21.4c7.8,0,15.2,6.3,18.7,9.9c3.5-3.6,10.9-9.9,18.7-9.9c13.4,0,21.4,8,21.4,21.4 C90.5,46.3,80.7,55.5,80.2,55.9z M69.1,19.8c-6.7,0-14.2,7.4-16.5,10.2c-1.1,1.3-3.3,1.3-4.4,0c-2.3-2.8-9.9-10.2-16.5-10.2 	c-7.2,0-15.7,2.7-15.7,15.5c0,8.4,8.3,16.1,8.4,16.2l26,25.6l26-25.5c0.1-0.1,8.4-7.9,8.4-16.3C84.8,22.5,76.3,19.8,69.1,19.8z"/>	
</svg>

## C'est quoi SVG 

Le *SVG* (*[graphique vectoriel adaptable](https://fr.wikipedia.org/wiki/Scalable_Vector_Graphics#cite_ref-1)*) est un format de données conçu pour décrire des ensembles de graphiques vectoriels. Basé sur XML, ce format utilise des polygones pour représenter les images dans les graphiques informatiques. Les graphiques vectoriels sont basés sur des vecteurs, qui conduisent à des emplacements appelés points de contrôle ou nœuds. Chacun de ces points a une position définie sur les axes x et y du plan de travail et détermine la direction du chemin. En outre, chaque chemin peut recevoir différents attributs, y compris des valeurs telles que *la couleur, la forme, la courbe, l'épaisseur et le remplissage des traits*.

## Les trucs à savoir sur SVG 

Source [outline de Todd McLeod](https://github.com/GoesToEleven/html-css-bootcamp/blob/master/044_svg/06_about-svg/index.html)

- SVG c'est du XML
	- SVG est du  XML décrivant une image
	- le XML est sensible à la casse
	- vous devez fermer tous les tags
	- les valeurs d'attribut doivent être entre guillemets
	- les premières lignes du header ("prologue") 
		- exemple :
			- <?xml version="1.0" encoding="utf-8"?>
			- **devraient être retirées** quand vous embarquez  un SVG dans une page HTML ou un autre SVG. Voir [ceci](http://www.w3schools.com/xml/xml_syntax.asp) et [ça](http://www.w3.org/TR/2008/REC-xml-20081126/#dt-wellformed) pour plus d'infos
- l'élément `<svg>` est un élément racine.
- le "Doctype Declaration" (DTD) devrait être évité - génère plus de problèmes qu'il n'en résout.
	- Ne pas utiliser 
		- `<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
    "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">`
	- **Utiliser ça :**
		- `<svg version="1.1"
         xmlns="http://www.w3.org/2000/svg"
         viewBox="0 0 100 100">`
     - **ou ça :**
	     - `<svg version="1.1"
         baseProfile="full"
         xmlns="http://www.w3.org/2000/svg"
         xmlns:xlink="http://www.w3.org/1999/xlink"
         xmlns:ev="http://www.w3.org/2001/xml-events">`
         - "version" et "baseProfile" identifient la  version du SVG et devraient toujours être utilisés au lieu du DTD
     - L'odre du rendu des éléments compte
 - CSS
	 - **Evitez l'attribut 'style' dans la ligne** si possible
		 - **Pas ça**
			 - `<circle style="fill:red; stroke:blue;" ... />`                  
      - **Mais ça**
	      - `<circle fill="red" stroke="blue" ... />`
  - **Spécifiez les unités au moment d'assigner des longueurs aux propriétés**
	  - Le seul moyen d'éviter les problèmes est de toujours spécifier une unité au moment d'assigner des longueurs aux propriétés.
	  - Heureusement, dans SVG, les unités px sont définies pour être équivalentes aux unités d'utilisateur.
	  - En d'autres termes, partout où vous auriez autrement omis l'unité d'une longueur attribuée à une propriété, utilisez l'unité px à la place.
		  - **Pas ça** :
			  - `<text stroke-width="2" style="font-size:20;" ...>`
		  - **Mais ça :**
			  - `<text stroke-width="2px" style="font-size:20px;" ...>`
			  - Selon SVG 1.1 Property Index, **seules 8 propriétés SVG 1.1 acceptent une valeur de longueur** :
				  - stroke-width
				  - stroke-dashoffset
				  - font
				  - font-size
				  - baseline-shift
				  - kerning
				  - letter-spacing
				  - word-spacing

### à lire : 
- [SVG Introduction](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Introduction)   
- [Premiers pas](https://developer.mozilla.org/fr/docs/Web/SVG/Tutoriel/Premiers_pas)   
- [la grille et le positionnement](https://developer.mozilla.org/fr/docs/Web/SVG/Tutoriel/Positionnement)   
[SVG Authoring Guidelines](https://jwatt.org/svg/authoring/)


## Formes de base

> Il existe tout un ensemble de formes de bases utilisées pour faire du dessin avec SVG. Le but de ces formes est assez transparent, si on regarde attentivement les noms de chaque élément. Des attributs permettent de configurer leur position et leur taille, mais vous pourrez retrouver les détails de chaque élément avec tous ses attributs à [la page des références SVG](https://developer.mozilla.org/fr/SVG/Element). (...) -- [mdn](https://developer.mozilla.org/fr/docs/Web/SVG/Tutoriel/Formes_de_base)


<svg version="1.1"
     xmlns="http://www.w3.org/2000/svg"
     width="200"
     height="250">
<rect x="10" y="10" width="30" height="30" stroke="red" fill="black" stroke-width="5"/>
<rect x="60" y="10" rx="10" ry="10" width="30" height="30" stroke="black" fill="yellow" stroke-width="5" />
<circle cx="25" cy="75" r="20" stroke="red" fill="transparent" stroke-width="5"/>
<ellipse cx="75" cy="75" rx="20" ry="5" stroke="red" fill="transparent" stroke-width="5"/>
<line x1="10" y1="110" x2="190" y2="250" stroke="purple" fill="transparent" stroke-width="5"/>
<polyline points="60 110 65 120 70 115 75 130 80 125 85 140 90 135 95 150 100 145"
              stroke="hotpink" fill="transparent" stroke-width="5"/>
<polygon points="50 160 55 180 70 180 60 190 65 205 50 195 35 205 40 190 30 180 45 180"
             stroke="green" fill="transparent" stroke-width="5"/>
<path d="M20,230 Q40,205 50,230 T90,230" fill="none" stroke="blue" stroke-width="5"/>
</svg>

## Exemple de chevron
<svg version="1.1"
     baseProfile="full"
     xmlns="http://www.w3.org/2000/svg"
     width="160"
     height="280">
<polyline points="40 60 80 20 120 60" stroke="black" stroke-width="20" stroke-linecap="butt" fill="none" stroke-linejoin="miter"/>
<polyline points="40 140 80 100 120 140" stroke="black" stroke-width="20" stroke-linecap="round" fill="none" stroke-linejoin="round"/>
<polyline points="40 220 80 180 120 220" stroke="black" stroke-width="20" stroke-linecap="square" fill="none" stroke-linejoin="bevel"/>
</svg>
<svg version="1.1"
     baseProfile="full"
     xmlns="http://www.w3.org/2000/svg"
     width="200"
     height="150">
<path d="M 10 75 Q 50 10 100 75 T 190 75" stroke="black" stroke-linecap="round" stroke-dasharray="5,10,5" fill="none"/>
<path d="M 10 75 L 190 75" stroke="red" stroke-linecap="round" stroke-width="1" stroke-dasharray="5,5" fill="none"/>
</svg>


## Font Awesome et extraction d'icônes SVG

[Font Awesome](http://fontawesome.io/) est une boîte à outils de polices et d'icônes. Avec une part de marché de 20% parmi les sites Web qui utilisent des scripts de police tiers, elle se classe en deuxième place après Google Fonts. 

Premiers pas sur le [mode d'emploi de Todd McLeod pour extraire une icône font-awesome et la transformer en un fichier svg](https://github.com/GoesToEleven/html-css-bootcamp/tree/master/044_svg/01_illustrator) pouvant s'insérer dans une page.

<svg version="1.1"
     xmlns="http://www.w3.org/2000/svg">
    viewBox="0 0 10 10">
        <path d="M80.2,55.9L52.3,83.3c-0.5,0.5-1.3,0.8-2,0.8s-1.4-0.3-2-0.8L20.5,55.8c-0.4-0.3-10.2-9.5-10.2-20.5 c0-13.4,8-21.4,21.4-21.4c7.8,0,15.2,6.3,18.7,9.9c3.5-3.6,10.9-9.9,18.7-9.9c13.4,0,21.4,8,21.4,21.4 C90.5,46.3,80.7,55.5,80.2,55.9z M69.1,19.8c-6.7,0-14.2,7.4-16.5,10.2c-1.1,1.3-3.3,1.3-4.4,0c-2.3-2.8-9.9-10.2-16.5-10.2 	c-7.2,0-15.7,2.7-15.7,15.5c0,8.4,8.3,16.1,8.4,16.2l26,25.6l26-25.5c0.1-0.1,8.4-7.9,8.4-16.3C84.8,22.5,76.3,19.8,69.1,19.8z"/>	
</svg>

code source : 

```svg
<svg version="1.1"
     xmlns="http://www.w3.org/2000/svg">
    viewBox="0 0 10 10">
        <path d="M80.2,55.9L52.3,83.3c-0.5,0.5-1.3,0.8-2,0.8s-1.4-0.3-2-0.8L20.5,55.8c-0.4-0.3-10.2-9.5-10.2-20.5
		c0-13.4,8-21.4,21.4-21.4c7.8,0,15.2,6.3,18.7,9.9c3.5-3.6,10.9-9.9,18.7-9.9c13.4,0,21.4,8,21.4,21.4
		C90.5,46.3,80.7,55.5,80.2,55.9z M69.1,19.8c-6.7,0-14.2,7.4-16.5,10.2c-1.1,1.3-3.3,1.3-4.4,0c-2.3-2.8-9.9-10.2-16.5-10.2
		c-7.2,0-15.7,2.7-15.7,15.5c0,8.4,8.3,16.1,8.4,16.2l26,25.6l26-25.5c0.1-0.1,8.4-7.9,8.4-16.3C84.8,22.5,76.3,19.8,69.1,19.8z"/>
</svg>
```


**Note** : [Iconic](https://useiconic.com/icons/) et [https://feather.netlify.com/](https://feather.netlify.com/) sont des alternatives à Font-Awesome avec une belle gamme d'icônes à télécharger en SVG.

## Pour aller plus loin 

Si vous comptez utiliser les icônes SVG en production (avec le support IE9), lisez [cet article](https://fvsch.com/code/svg-icons/how-to/#section-preparing) ou sa traduction : [Comment travailler avec des icônes en SVG](https://la-cascade.io/comment-travailler-avec-des-icones-en-svg/).

Pour conclure, je prévois d'étudier l'article "[Styling And Animating SVGs With CSS](https://www.smashingmagazine.com/2014/11/styling-and-animating-svgs-with-css/)", une transcription adaptée d'une conférence de Sara Soueidan pour travailler les SVGs avec CSS.

<iframe src="//slides.com/sarasoueidan/styling-animating-svgs-with-css--2/embed" width="576" height="420" scrolling="no" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>