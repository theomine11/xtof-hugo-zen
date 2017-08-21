---
title: Skeleton
subtitle: La Grille 
slug:
date: "2017-08-21T02:51:30+02:00"
lastmod: "2017-08-21T02:52:30+02:00"
draft: false
tags: [100daysofcode, gohugo, git]
bigimg: [{src: "/img/path.jpg", desc: "Sur la Route"}]
comments: false
---

## Typographie 


La typo est définie avec le `rems`, de sorte que les tailles de police et les relations spatiales peuvent être évaluées en fonction d'une propriété `<html>` unique `font-size`. En sortie de boîte, Skeleton ne change jamais la taille de police `<html>`, mais il reste là dans le cas où vous en avez besoin pour votre projet. Toutes les mesures sont toujours de base 10, un `<h1>` avec `5.0rem` de font-size signifie simplement `50px`.

- La **typographie de base** est [Raleway](http://www.google.com/fonts/specimen/Raleway) servie par Google, définie à 15rem (15px) sur une hauteur de 1.6 lignes (24px). D'autres types de base comme les [ancres](http://getskeleton.com/#), le **gras**, l'_emphase_ et le _souligné_ sont tous évidemment inclus.
- **En-têtes** créez une famille de tailles distinctes chacune avec des `letter-spacing`, `line-height` et `margins` spécifiques.

<!-- Titres standards -->
<h1>Titre</h1>
<h2>Titre</h2>
<h3>Titre</h3>
<h4>Titre</h4>
<h5>Titre</h5>
<h6>Titre</h6>

<!-- Base taille typo -->
<p>La typo de base est de 15px sur une hauteur de ligne de 1.6  (24px)</p>

<!-- Autres tags pour styler le texte -->
<strong>Gras</strong>
<em>Italique</em>
<a>Coloré</a>
<u>Souligné</u>


## La Grille Skeleton 

La grille est une _grille fluide de 12 colonnes avec une largeur max de 960px_, qui rétrécit avec le navigateur/terminal pour les plus petites tailles. La largeur maximale peut être modifiée avec une ligne de CSS et toutes les colonnes se retailleront. La syntaxe reste simple et facilite un code responsive. Retaillez le navigateur.

<div class="example-grid docs-example">
        <div class="row">
          <div class="one column">Un</div>
          <div class="eleven columns">Onze</div>
        </div>
        <div class="row">
          <div class="two columns">Deux</div>
          <div class="ten columns">Dix</div>
        </div>
        <div class="row">
          <div class="three columns">Three</div>
          <div class="nine columns">Neuf</div>
        </div>
        <div class="row">
          <div class="four columns">Quatre</div>
          <div class="eight columns">Huit</div>
        </div>
        <div class="row">
          <div class="five columns">Cinq</div>
          <div class="seven columns">Sept</div>
        </div>
        <div class="row">
          <div class="six columns">Six</div>
          <div class="six columns">Six</div>
        </div>
        <div class="row">
          <div class="seven columns">Sept</div>
          <div class="five columns">Cinq</div>
        </div>
        <div class="row">
          <div class="eight columns">Huit</div>
          <div class="four  columns">Quatre</div>
        </div>
        <div class="row">
          <div class="nine columns">Neuf</div>
          <div class="three columns">Trois</div>
        </div>
        <div class="row">
          <div class="ten columns">Dix</div>
          <div class="two columns">Deux</div>
        </div>
        <div class="row">
          <div class="eleven columns">Onze</div>
          <div class="one column">Un</div>
        </div>
      </div>



<!-- .container is main centered wrapper -->
<div class="container">

  <!-- les colonnes devraient être l'enfant immédiat d'une .row -->
  <div class="row">
    <div class="one column">Un</div>
    <div class="eleven columns">Onze</div>
  </div>

  <!-- just use a number and class 'column' or 'columns' -->
  <div class="row">
    <div class="two columns">Deux</div>
    <div class="ten columns">Dix</div>
  </div>

  <!-- there are a few shorthand columns widths as well -->
  <div class="row">
    <div class="one-third column">1/3</div>
    <div class="two-thirds column">2/3</div>
  </div>
  <div class="row">
    <div class="one-half column">1/2</div>
    <div class="one-half column">1/2</div>
  </div>

</div>

<!-- Note: columns can be nested, but it's not recommended since Skeleton's grid has %-based gutters, meaning a nested grid results in variable with gutters (which can end up being *really* small on certain browser/device sizes) -->