---
title: "Layout : les essentiels"
subtitle: Proposé par Todd McLeod
comments: false
date: 2017-08-09
lastmod: 2017-08-09
draft: false
---
<!--more-->
# Eléments essentiels de mise en page

[référence source](https://docs.google.com/document/d/1IjV1IlnEXKPu5IFdWtr9Fubl_RZEVJdmPgaBQOjomU0/edit#heading=h.xcv7ky5v8suo)

## Modèle de boîte
content → padding → border → margin

## box-sizing: border box

Au fur et à mesure que nous modifions les padding et border, cela ne modifie pas la taille de notre élément sur la page.

## margin: 0 auto

Centre le contenu

## Border-radius
Coins arrondis

- TRBL
- TB RL
- T R B L 

## Display
- inline
- block
- inline-block
- none
- flex

## Flexbox

### Propriétés conteneur
- display
	- flex
	- inline-flex 
- flex-direction
	- row (par défaut)
	- row-reverse
	- column
	- column-reverse 
- flex-wrap
	- no-wrap (par défaut)
	- wrap
	- wrap-reverse
- justify-content (axe principal)
	- flex-start (par défaut)
	- flex-end
	- center
	- space-between
	- space-around
- align-items (axe secondaire)
	- flex-start
	- flex-end
	- center
	- stretch (par défaut)
	- baseline
- align-content (axe secondaire)
	- flex-start
	- flex-end
	- center
	- stretch (par défaut)
	- space-between
	- space-around


### Propriétés des éléments
- align-self
	- auto
	- flex-start
	- flex-end
	- center
	- baseline
	- stretch
- order
	- valeur numérique
- flex-grow
	- valeur numérique
	- 0 (par défaut)
- flex-shrink
	- valeur numérique
	- 1 (par défaut)
- flex-basis
	- une valeur width
	- auto (par défaut)

## Media queries
```html
<link rel="stylesheet" media="(min-width: 900px)" href="mq_900-plus.css">

<link rel="stylesheet" media="(max-width: 900px)" href="mq_900-less.css">

<link rel="stylesheet" media="print" href="mq_print.css">

<link rel="stylesheet" media="screen and (min-width: 900px)" href="mq_screen_min-width.css">

<link rel="stylesheet" media="(min-width: 600px) and (max-width: 899px)" href="mq_600-899.css">
```

## Position

Différentes valeurs

- fixed
- relative 
- absolute

Utiliser ces propriétés pour ajuster la position

- top
- bottom
- right
- left

## Float

- left, right
- overflow: auto
- clear
- left, right, both

## Meta-viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```