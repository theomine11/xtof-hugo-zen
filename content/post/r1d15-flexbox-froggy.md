---
title: "R1d15 : Flexbox"
subtitle: Dans le casse-tête de la "pensée conteneur"
date: 2017-08-07T09:46:52+02:00
lastmod: "2017-08-07T17:23:52+02:00"
draft: false
tags: [100daysofcode,flexbox,hugo]
bigimg: [{src: "/img/flex/flexbox-froggy.png", desc: "flexbox froggy"}]
---
<!--more-->

## Flexbox et la "Pensée conteneur" 

Achevé la "grosse section" Flexbox (toujours accompagné par l'excellent [tutoriel HTML/CSS](https://www.greatercommons.com/learn/6708511014649856) de Todd Mc Leod). Compris le concept et l'importance de l'axe principal et de l'axe secondaire. Certaines propriétés fonctionnent uniquement sur l'axe principal, ou l'axe secondaire. Un paquet de connaissance à assimiler et pratiquer. Le [guide CSS-tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/), le [fascicule de Joni Trythall](http://jonibologna.com/announcing-a-field-guide-to-flexbox/) et le jeu du [flexbox-froggy](http://flexboxfroggy.com/) m'accompagneront ces prochains jours pour pratiquer ces nouvelles propriétés :

1. **Propriétés du conteneur**
	2. Flex-direction
	3. Flex-wrap
	4. Justify-content (axe principal)
	5. Align-items (axe secondaire)
	6. Align-content (axe secondaire)  

7. **Propriétés des éléments**
	8. Align-self
	9. Order
	10. Flex-grow
	11. Flex-shrink
	12. Flex-basis
	13. Flex (0 1 auto)


### Ressources flex

Les ressources que je conserve à portée de main : 

- [A complete guide to flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) - Chris Coyier  
- [Mise en page avec flexbox](https://openclassrooms.com/courses/apprenez-a-creer-votre-site-web-avec-html5-et-css3/la-mise-en-page-avec-flexbox) - Openclassrooms
- et pour finir l'excellent ouvrage "[A field Guide To FlexBox](https://gumroad.com/l/UVuuf)" avec son [anti-sèche](http://jonibologna.com/flexbox-cheatsheet/) par Joni Trythall

![anti-sèche](/img/flex/flexboxsheet.png)

### Pen pour s'entraîner 

{{% codepen id="pAlei" tab="css" %}}

## r1d15-log 

### Flexbox

- [14 pages d'exercices par Todd McLeod](https://github.com/GoesToEleven/html-css-bootcamp/tree/master/031_flexbox/03_hands-on-exercises/01_challenges) 
- 24 pages du jeu [Flexbox Froggy](http://flexboxfroggy.com/#fr).

### Hugo 0.26

Mise à jour motorisation [Hugo 0.26.](https://gohugo.io/news/0.26-relnotes/). Modifié `config.toml` pour activer les "guillemets en français" 

```toml
angledQuotes = true
smartypantsQuotesNBSP = true
```
