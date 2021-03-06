---
title: Forker un Repo sur GitHub
date: 2013-12-16 15:36:00 +01:00
categories:
- github
- git
- repo
- fork
- howto
- tutoriel
slug: forker-un-repo-github
subtitle: Un fork (bifurcation) est une copie d'un repository. Ce peut être une bonne base pour démarrer.
author: Christophe Ducamp
---

Lien de référence : <span class="h-cite"><cite class="p-name u-url">[Fork A Repo](https://help.github.com/articles/fork-a-repo/)</cite></span>

Si vous vous trouvez sur cette page, je peux supposer que vous [débutez sur Git et GitHub](/2013/12/15/github-pour-nuls-partie-1/). Ce petit guide vous fera réviser quelques fondamentaux et vous aidera à faire vos premiers pas sur GitHub.

## Forker un Repo

Un *fork* est une copie d'un dépôt. Forker un dépôt vous permet d'expérimenter librement des modifications sans toucher au projet original.

Plus communément, les forks sont utilisés soit pour proposer des modifications sur le projet de quelqu'un d'autre ou pour utiliser le projet de quelqu'un d'autre comme point de départ pour une nouvelle idée.

####  Proposer des modifications sur le projet de quelqu'un d'autre

Un exemple génial d'utilisation des forks est de proposer des modifications pour la correction de bugs. Plutôt que de signaler un problème que vous trouvez, vous pouvez : 

- Forker le repository
- Réparer le bug
- Proposer une *pull request* au propriétaire du projet.

Si le propriétaire du projet aime votre travail, il pourrait prendre votre réparation pour la ramener dans le dépôt original !

#### Utiliser le projet de quelqu'un d'autre comme point de départ d'une nouvelle idée. 

Au [coeur de l'open source](http://opensource.org/about) il y a l'idée qu'en partageant du code, nous pouvons produire un logiciel meilleur et de confiance.

Au moment de créer un dépôt public à partir d'un fork du projet de quelqu'un d'autre, assurez-vous d'inclure un [fichier de licence](http://choosealicense.com/) qui détermine comment vous voulez que votre projet soit partagé avec d'autres.

Pour plus d'information sur l'open source, spécifiquement sur la façon de créer et faire grandir un projet open source, nous avons créé les [Guides Open Source](https://opensource.guide/) qui  vous aideront à Qui vous aideront à développer une communauté open source saine en recommandant les meilleures pratiques pour la création et l'entretien de dépôts pour votre projet open source.

## Forkez un repository d'exemple 

Forker un repository est un processus très simple en deux étapes. Nous avons créé un repository pour vous entraîner. 

1. Sur GitHub, naviguez vers le dépôt [spoon-knife](https://github.com/octocat/Spoon-Knife)
2. Dans le coin en haut et à droite de la page, cliquez sur **Fork**

Voilà, c'est fait ! Vous disposez désormais d'un *fork* du dépôt   original `octocat/Spoon-Knife repository`

## Maintenez votre fork synchronisé 

Vous pourriez avoir forké un projet afin de proposer des modifications vers l'*upstream*, ou le dépôt original. Dans ce cas, c'est une bonne pratique de synchroniser régulièrement votre fork avec le repository original. Pour faire ça, vous devrez utiliser Git à la ligne de commande. Vous pouvez pratiquer le réglage du dépôt upstream en utilisant le même repository `octocat/Spoon-Knife que vous venez de forker. 

### Étape 1 : Installer et Paramétrer Git 

Si ce n'est déjà fait, vous devez d'abord [installer et régler Git](/2013/12/10/installer-git/). N'oubliez pas non plus de [régler l'authentification vers GitHub à partir de Git](https://help.github.com/articles/set-up-git#next-steps-authenticating-with-github-from-git).


### Étape 2 : Créer un clone local de votre fork

À ce stade, vous avez un fork du repository Spoon-Knife, mais vous n'avez pas les fichiers dans ce repository sur votre ordinateur. Créons localement un *clone* de votre fork sur votre ordinateur.

1. Sur GitHub, naviguez vers **votre fork** du dépôt Spoon-Knife.
2. Sous le nom du dépôt, cliquez sur **Clone or download** 
3. Dans le Clone avec la section HTTPs, cliquez sur l'icône fléchée pour copiez l'URL de clone du dépôt. <img src="https://help.github.com/assets/images/help/repository/https-url-clone.png" />
4. Ouvrez la fenêtre de Terminal
5. Tapez `git clone`, et collez ensuite l'URL que vous avez copiée à l'étape 2. Cela ressemblera à cela, avec votre nom d'utilisateur GitHub au lieu de `VOTRE-NOMUTILISATEUR`:
```git clone https://github.com/VOTRE-NOMUTILISATEUR/Spoon-Knife```
6. Pressez la touche **Retour**. Votre clone local sera créé.

```bash
git clone https://github.com/YOUR-USERNAME/Spoon-Knife
Cloning into `Spoon-Knife`...
remote: Counting objects: 10, done.
remote: Compressing objects: 100% (8/8), done.
remove: Total 10 (delta 1), reused 10 (delta 1)
Unpacking objects: 100% (10/10), done.
```

Vous avez désormais une copie locale de votre fork du repository Spoon-Knife !

### Étape 3 : Configurer Git pour synchroniser votre fork avec le dépôt original Spoon-Knife

Quand vous forkez un projet afin de proposer des modifications sur le repository original, vous pouvez configurer Git pour tirer les modifications à partir du dépôt original (encore appelé *upstream*) à l'intérieur du clone local de votre fork. 

1. Sur GitHub, naviguez vers le dépôt [octocat/Spoon-Knife](https://github.com/octocat/Spoon-Knife).
2. Sous le nom de votre dépôt, cliquez **Clone or download** 
3. Dans le Clone avec la section HTTPs, cliquez sur l'icône fléchée "copy to clipboard" pour copier l'URL clone du repository. 
4. Ouvrez le Terminal.
5. "Change directories" (`cd`) allez à l'endroit du fork que vous avez cloné à l'étape 2
	1. Allez en haut de votre répertoire, tapez juste `cd` sans autre texte.
	2. Pour lister les fichiers et répertoires dans votre répertoire actuel, tapez `ls`.
	3. Pour aller dans l'un de vos répertoires listés, tapez `cd votre_liste_repertoire`.
	4. Pour remonter d'un répertoire, tapez `cd ..`
6. Tapez `git remote -v`et pressez la touche **Retour**. Vous verrez le dépôt distant actuel configuré pour votre fork.
```bash
git remote -v
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
```
7. Tapez `git remote add upstream`, puis collez l'URL que vous avez copiée à l'étape 2 et pressez **Retour**. Cela ressemblera à ça : 
```bash
git remote add upstream https://github.com/octocat/Spoon-Knife.git
```
8. Pour vérifier le nouveau dépôt "upstream" que vous avez spécifié pour votre fork, tapez de nouveau `git remote -v`. Vous devriez voir l'URL de votre fork sous `origin`, et l'URL pour le dépôt  original sous `upstream`.

```bash
git remote -v
origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
``` 

Maintenant, vous pouvez maintenir votre fork synchronisé avec le dépôt upstream à l'aide de quelques commandes Git. Pour plus d'information, voir "[Syncing a fork](https://help.github.com/articles/syncing-a-fork)."

## Prochaines étapes

Le ciel est la limite avec les modifications vous pouvez produire un fork, incluant :

- la **Création de Branches** : les branches vous permettent de construire de nouvelles fonctionnalités ou tester des idées sans mettre votre projet principal en péril.
- **Ouvrir des pull requests** : Si vous espérez contribuer en retour sur le dépôt original, vous pouvez envoyer une demande à l'auteur original de tirer votre fork dans son dépôt en lui proposant une *[pull request](https://help.github.com/articles/about-pull-requests)*.

## Trouver un autre repository à forker 

Chaque repository public peut être forké, aussi à vous de trouver un autre projet qui vous intéresse et de le forker ! 

[Explore Github](https://github.com/explore) est un endroit merveilleux pour trouver des sujets qui vont piquer votre intérêt. Visitez cette page de temps en temps pour trouver ce qu'il y a de nouveau. 

<img src="https://help.github.com/assets/images/help/repository/fork-repo-explore.png" alt="explore github" />

### Célébrez 

Vous avez désormais forké un dépôt, mis en pratique le clonage de votre fork, et configuré un repository upstream. Que voulez-vous faire ensuite ?

* [Installer Git](/2013/12/10/installer-git/)
* [Créer un Repo](/2013/12/16/creer_un_repo_GitHub/)
* **Forker un Repo**
* [Etre Social](/2013/12/16/github-etre-social/)

---
À Nettoyer …

Faites tourner le code qui suit :

```
git clone https://github.com/username/Spoon-Knife.git
# Clone votre fork du dépôt à l'intérieur du répertoire en cours dans le terminal
```  
  
### Étape 3 : Configurer les remotes

Quand un dépôt est cloné, il a un *remote* par défaut appelé `origin` qui pointe vers votre fork sur GitHub, et non pas le dépôt original à partir duquel il a été forké. Pour garder une trace du dépôt original, vous devez ajouter un autre remote appelé `upstream` :

#### Plus sur les remotes

Un *remote* est un dépôt stocké sur un autre ordinateur, dans ce cas sur le serveur de GitHub. C'est une pratique standard (et aussi le défaut quand vous clonez un dépôt) de donner le nom `origin` au remote qui pointe vers votre dépôt principal hors du site (par exemple, votre dépôt GitHub).

Git supporte plusieurs remotes. Ceci s'utilise communément au moment de forker un dépôt.

```
cd Spoon-Knife
# Change le répertoire actif dans le terminal vers le nouveau répertoire fraîchement cloné "Spoon-Knife"
git remote add upstream https://github.com/octocat/Spoon-Knife.git
# Assigne le dépôt original à un remote nommé "upstream"
git fetch upstream
# Rapatrie les modifications non présentes dans votre dépôt local, sans modifier vos fichiers
```
  


## Plein de Trucs Restent À Faire !

Vous avez forké avec succès un dépôt, mais vous avez maintenant plein d'autres choses cools à faire : 

### Pousser des commits

Une fois que vous avez produit quelques commits vers un dépôt forké et que vous voulez les pousser vers votre dépôt forké, vous faites ça de la même façon que vous le feriez avec un dépôt normal : 

```
git push origin master
# Pousse les commits vers votre dépôt remote (distant) stocké sur GitHub
```
  
  
#### Plus sur les commits

Pensez à un *commit* comme un instantané de votre projet - code, fichiers, tout - à un instant t. Après votre premier commit, git ne sauvegardera que les fichiers qui ont été modifiés, d'où le gain d'espace.

**Attention :** git fera de son mieux pour compresser vos fichiers, mais les gros fichiers et les binaires peuvent amener un dépôt à devenir obèse et peu maniable. Essayez d'éviter de committer des choses comme des ficihers compressés (zips, rars, jars), du code compilé (fichiers object, bibliothèques, exécutables), sauvegardes de database et fichiers média (flv, psd, musique, films)


### Rentrer des modifications upstream

Si le dépôt original que vous avez forké pour votre projet est mis à jour, vous pouvez ajouter ces mises à jour à votre fork en faisant tourner la commande suivante : 

```
git fetch upstream
# Rapatrie toutes les nouvelles modifications provenant du dépôt original
git merge upstream/master
# Fusionne toutes les modifications rapatriées à l'intérieur de vos fichiers de travail
```

#### Quelle est la différence entre fetch et  pull ?

Il y a deux moyens de recevoir des commits provenant d'un dépôt distant ou d'une branche : `git fetch` et `git pull`. Bien que ces deux commandes puissent sembler similaires, il existe des différences que vous devriez comprendre :

##### Pull

```
git pull upstream master
# Tire les commits provenant de 'upstream' et les stocke dans le dépôt local
```

Quand vous utilisez `git pull`, git essaye automatiquement de faire le travail à votre place. C'est sensible au contexte, ainsi git fusionnera tous les les commits tirés (pull) à l'intérieur de la branche dans laquelle vous êtes en train de travailler. Une chose à garder à l'esprit, est que `git pull` fusionne automatiquement les commits sans vous laisser d'abord les réviser. Si vous ne gérez pas vos branches de très près, vous pourriez rencontrer des conflits fréquents.

##### Fetch & Merge

```
git fetch upstream
# Rapatrie tous les nouveaux commits provenant du dépôt original
git merge upstream/master
# Fusionne tous les commits rapatriés à l'intérieur de vos fichiers de travail
```

Quand vous lancez `git fetch`, git retrouve tous les nouveaux commits provenant du `remote` cible que vous n'avez pas et les stocke dans votre dépôt local. Néanmoins, il ne les fusionne pas dans votre branche actuelle. Ceci est tout particulièrement utile si vous avez besoin de conserver votre dépôt à jour mais travaillez sur quelque chose qui pourrait se casser si vous mettiez vos fichiers à jour. Pour intégrer les commits à l'intérieur de votre branche locale, vous utilisez `git merge`. Ceci combine les branches spécifiées et vous alerte en cas de conflits.

### Créer des branches

Brancher vous permet de construire de nouvelles fonctionnalités ou de tester de nouvelles idées, sans mettre votre projet principal en péril. Dans git, `branch`er est une sorte de bookmark qui référence le dernier commit produit dans la branche. Ceci produit des branches très petites et faciles à travailler.

##### Comment j'utilise les branches ?

Les branches sont vraiment faciles à travailler et vous épargneront beaucoup de maux de têtes, tout spécialement quand vous travaillez avec beaucoup de gens. Pour créer une branche et commencer à travailler dedans, lancez ces commandes : 

```bash
    git branch *mabranche*
    # Crée une nouvelle branche nommée "mabranche"
    git checkout *mabranche*
    # Transforme "mabranche" en branche active
```

Alternativement, vous pouvez utiliser le raccourci :

```bash
    git checkout -b *mabranche*
    # Crée une nouvelle branche nommée "mabranche" et la transforme en branche active
```

Pour basculer entre les branches, utilisez `git checkout`.

```
git checkout master
# Transforme "master" en branche active
git checkout *mabranche*
# Transforme "mabranche" en branche active
```

Une fois que vous avez fini de travailler sur votre branche et quand vous êtes prêt à la combiner en retour à l'intérieur de la branche `master`, utilisez `merge`.

```
git checkout master
# Fait de "master" la branche active
git merge *mabranche*
# Fusionne les commits provenant de "mabranche" à l'intérieur de "master"
git branch -d *mabranche*
# Efface la branche "mabranche"
```

**Truc** : Quand vous switchez entre les branches, les fichiers sur lesquels vous travaillez (la "copie de travail") sont mis à jour pour renvoyer les modifications dans la nouvelles branche. Si vous avez des modifications que vous n'avez pas committées, git s'assurera que vous ne les perdez pas. Git fait aussi très attention durant les fusions et les pulls pour vous assurer que vous ne perdez pas de modifications. **En cas de doute, committez tôt et committez souvent**.

### Demandes de Pull

Si vous espérez contribuez en retour sur le fork original, vous pouvez envoyer à l'auteur original une [demande de pull](https://help.github.com/articles/using-pull-requests).

### Ne plus suivre le dépôt principal

Quand vous forkez un dépôt populaire, vous pouvez vous retrouver avec beaucoup de mises à jour non voulues. Pour vous désabonner des mises à jour sur le dépôt original, cliquez sur le bouton "Unwatch" sur le **dépôt principal** et sélectionnez "Not Watching".

![image](https://github-images.s3.amazonaws.com/help/Bootcamp-Not-Watching.png "Cliquez sur Unwatch")

### Effacer votre fork

À un certain stade, vous pouvez décider de vouloir effacer votre fork. Pour effacer un fork, suivez simplement les mêmes étapes comme vous [effaceriez un dépôt normal](https://help.github.com/articles/deleting-a-repository).






