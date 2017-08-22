---
title: Skeleton
subtitle: découverte du boilerplate intégré dans hugo-zen
slug:
date: "2017-08-21T02:51:30+02:00"
lastmod: "2017-08-21T02:52:30+02:00"
draft: false
tags: [100daysofcode, boilerplate, hugo-zen, skeleton, typo]
bigimg: [{src: "/img/path.jpg", desc: "Sur la Route"}]
comments: false
---




Avant de partir en *pensée design css* pour construire une page d'accueil "[above-the-fold](/2017/08/11/r1d19-above-the-fold/)" avec un menu personnalisé et d'autres layouts fondamentaux, je découvre avec enchantement les  potentiels de mise en forme du [Skeleton](http://getskeleton.com/#intro), le boilerplate intégré dans le thème [hugo-zen](https://github.com/rakuishi/hugo-zen).

## Typographie 

La typo est définie avec les `rems`, de sorte que les tailles de police et les relations spatiales peuvent être évaluées en fonction d'une propriété `<html>` unique `font-size`. En sortie de boîte, Skeleton ne change jamais la taille de police `<html>`, mais il reste là dans le cas où vous en avez besoin pour votre projet. Toutes les mesures sont toujours de base 10, un `<h1>` avec une `font-size` de `5.0rem` signifie simplement `50px`.

- La **typographie de base** est [Raleway](http://www.google.com/fonts/specimen/Raleway) servie par Google, définie à 15rem (15px) sur une hauteur de 1.6 lignes (24px). D'autres types de base comme les [ancres](http://getskeleton.com/#), le **gras**, l'_emphase_ et le _souligné_ sont tous évidemment inclus.
- **En-têtes** : créez une famille de tailles distinctes chacune avec des `letter-spacing`, `line-height` et `margins` spécifiques.

<!-- Titres standards -->

# Titre1
## Titre2
### Titre3
#### Titre4
##### Titre5
###### Titre6

<!-- Base taille typo -->
<p>La typo de base est de 15px sur une hauteur de ligne de 1.6  (24px)</p>

<!-- Autres tags pour styler le texte -->
<strong>Gras</strong>
<em>Italique</em>
<a>Coloré</a>
<u>Souligné</u>

## Boutons 

<!-- boutons standards -->
<a class="button" href="#">Bouton Ancre</a>
<button>Bouton Élément</button>
<input type="submit" value="submit input">
<input type="button" value="button input">

<!-- boutons primaires -->
<a class="button button-primary" href="#">Bouton Ancre</a>
<button class="button-primary">Bouton Élément</button>
<input class="button-primary" type="submit" value="submit input">
<input class="button-primary" type="button" value="button input">

## Formulaire 

<!-- Le formulaire ressemble à cela  -->
<form>
  <div class="row">
    <div class="six columns">
      <label for="exampleEmailInput">Votre e-mail</label>
      <input class="u-full-width" type="email" placeholder="test@mailbox.com" id="exampleEmailInput">
    </div>
    <div class="six columns">
      <label for="exampleRecipientInput">Raison pour me contacter</label>
      <select class="u-full-width" id="exampleRecipientInput">
        <option value="Option 1">Questions</option>
        <option value="Option 2">Admiration</option>
        <option value="Option 3">Puis-je avoir votre numéro de téléphone ?</option>
      </select>
    </div>
  </div>
  <label for="exampleMessage">Message</label>
  <textarea class="u-full-width" placeholder="Salut David …" id="exampleMessage"></textarea>
  <label class="example-send-yourself-copy">
    <input type="checkbox">
    <span class="label-body">Envoyer une copie à vous-même</span>
  </label>
  <input class="button-primary" type="submit" value="Envoyer">
</form>

<!-- Always wrap checkbox and radio inputs in a label and use a <span class="label-body"> inside of it -->

<!-- Note: The class .u-full-width is just a utility class shorthand for width: 100% -->

## Listes 

<div class="row docs-example">
    <div class="six columns">
        <ul>
            <li>Les listes non ordonnées ont des styles basiques</li>
            <li>
                Elles utilisent le style de liste circle
              <ul>
                <li>Les listes encapsulées peuvent être gérées</li>
                <li>Elles peuvent imbriquer n'importe quel type de liste l'une dans l'autre</li>
              </ul>
            </li>
            <li>Juste plus d'items de liste lorem ipsum</li>
          </ul>
    </div>
    <div class="six columns">
        <ol>
            <li>Les listes ordonnées ont aussi des styles basiques</li>
            <li>
                Elles utilisent le style de liste décimal
                  <ul>
                      <li>Les listes ordonnées et non ordonnées peuvent être imbriquées</li>
                      <li>Tout type de liste rentre l'une dans l'autre</li>
                   </ul>
            </li>
            <li>Dernier item de liste juste pour rire</li>
        </ol>
    </div>
</div>    
        
        
     


<!-- Substituez facilement toute <ul> ou un <ol> pour avoir des listes ou sous-listes numérotées. Skeleton ne supporte pas les listes imbriquées à plus de 2 niveaux -->

## Tableau

<table class="u-full-width">
  <thead>
    <tr>
      <th>Nom</th>
      <th>Age</th>
      <th>Sexe</th>
      <th>Ville</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Dave Gamache</td>
      <td>26</td>
      <td>Homme</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <td>Dwayne Johnson</td>
      <td>42</td>
      <td>Homme</td>
      <td>Hayward</td>
    </tr>
  </tbody>
</table>

```html
<table class="u-full-width">
  <thead>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Location</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Dave Gamache</td>
      <td>26</td>
      <td>Male</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <td>Dwayne Johnson</td>
      <td>42</td>
      <td>Male</td>
      <td>Hayward</td>
    </tr>
  </tbody>
</table>
```

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