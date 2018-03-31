---
title: Pourquoi j'embarque sur "micro.blog"
subtitle: "..."
slug: "microblog"
date: "2018-03-29T10:32:45+02:00"
categories: []
tags: [microblog]
bigimg: [{src: "/img/microblog.jpg", desc: "micro.blog"}]
draft: true
---

Image : interface conversationnelle

> Le problème est la domination d'un moteur de recherche, d'un grand réseau social et d'un pour le micro-blogging. Nous n'avons pas de problème technologique, nous avons un problème social (Berners-Lee, 2016)

Fondamentalement, le problème de l'écosystème du web est que le choix du consommateur est de plus en plus limité. Facebook, Twitter, Google et d'autres géants chinois "possèdent" une grande partie du graphe social. Tenir le graphe leur confère le pouvoir de tenir les connexions numérique : si vous voulez vous connecter aux personnes sur l'internet, vous devez suivre leurs règles du jeu.

and other tech giants "own" a large part of the social graph that both powers the core digital connection goodness and sustains the momentum that they will keep owning it, due to something called Metcalfe's law. If you want to connect to people on the internet, you have to play by their rules

Internet Un était un réseau ouvert, avec des protocoles ouverts et des systèmes ouverts. 
Internet Deux est constitué de plateformes fermés qui dominent de plus en plus le marché, possèdent nos contenus et conrôlent nos vies.   
Internet Trois selon indieweb pourrait être de reprendre le contrôle de nous-mêmes. Et c'est en train de se produire.(Inspiration Wilson, 2018) 

Micro.blog 
Un réseau social de microblogs indépendants. Un principe simple : Votre contenu, votre site. Vous publiez sur votre propre site, vous hébergez sur Micro.blog ou utilisez n'importe quel service pouvant éditer des flux RSS. Le texte de chaque message devrait être plutôt court (280 caractères à vérifier et sans titre) Puis ajoutez votre flux RSS à Micro.blog et tout le monde peut vous suivre. 

... une petite couche de glue qui assemble quelques éléments du web ouvert.
définition : 

D'après ce que j'ai compris, Micro.blog n'est pas un nouveau moteur de blog, mais bien un service de publication sociale. Le service n'est plus tout nouveau. Lancé en bêta le .... l'idée est que vous publiez des petits messages, ceux ci sont renvoyés via un flux RSS sur micro.blog/votrenomutilisateur. 

Vous pouvez alors soit choisir un blog hébergé sur micro.blog à une adresse du type votrenomutilisateur.micro.blog ou utiliser votre propre nom de domaine.

N'ayant pas d'iphone, je ne peux encore me prononcer sur l'application iOS faute de l'avoir essayée.

The micro.blog iOS app will post to your micro.blog blog or your own WordPress blog. Or you can use your own system. There is a microblog bot that will post your posts on to Twitter too.

The difference between the hosted blog and your micro.blog/username stream is a mite confusing at the moment. I wonder if a different domain name might have helped.

Both the hosted blog and the twitter bot are paid for options. The docs make it clear that you can host your own and point to IFTTT as an alternative to the bot.

The system follows the indieweb principle of controlling your own content and sending it on to other spaces.

Replies on micro.blog to your posts are sent as webmentions to your own blog and show up as comments if you have the webmention plugin installed. I had that already to get twitter replies as comments.
My setup

I’ve added a new category here, micro. I’ve edited the blog to not have posts with this category show on the home page, they show on micro instead.

I set the micro.blog app to create posts with the status format in the micro category.

I turned off the jetpack social posting to Twitter function. I’ll manually post normal posts. I’ve set up a micro.blog bot to post to Twitter.

The service is very much a work in progress, and I’ve not really read the docs but I’ve noticed a few interesting things.
titleless

On is that the posts on micro.blog consist of descriptions with no titles. When you post form the app, you get a post on your blog without a title. A post with a title on your blog is posted as a link to micro.blog. With a post without out a title the description becomes the content of the micro.blog post.

That means you get lots of posts listed in your dashboard as ‘no title’. Since I didn’t like this I tried to auto add titles to posts without titles with a little Google-fu and some WordPress coding.

This worked out fine, except the posts on micro.blog consist of a title and a link, the tweet posted by the twitter bot is the same.

I am now looking to create a custom RSS feed without title. More googling ahead.

Alternatively I could use the code from Tweaks for micro.blog that adds dates as titles, micro.blog ignore these.

Or just learn to live with ‘no title’ posts in the dashboard.

Me on Micro.blog

Preparing for the microblog is a lot more coherent than this post if you are looking for setup advice.

I’ll post the code I’ve mentioned above at some point, it is pretty simple stuff.


---

Il est probable que vous vous souveniez du temps Beaucoup d'entre vous se souviennent des premiers jours du web. Si vous vouliez écrire sur internet, vous avez créé un site web. Vous pouvez publier des essais, poster des photos, démarrer des weblogs. Parce que les sites Web étaient indépendants, souvent avec leur propre nom de domaine personnel, il n'y avait pas une entreprise qui pouvait dire aux auteurs quoi publier ou quels outils utiliser. Si un fournisseur d'hébergement a cessé ses activités ou a modifié ses prix ou ses règles, vous pouvez simplement déplacer votre site vers un autre hôte. C'était votre contenu et vous l'avez possédé.



Many of you remember the earlier days of the web. If you wanted to write on the internet, you created a web site. You could publish essays, post photos, start weblogs. Because web sites were independent, often with their own personal domain name, there was no one company who could tell authors what to post or which tools to use. If a hosting provider went out of business, or changed their prices or policies, you could simply move your site to another host. It was your content and you owned it.

Today, most writing instead goes into a small number of popular social networking sites. These sites became popular because they made it so easy to connect with friends and start publishing, and because they provided a timeline user experience that made everything easy and fast.

But this simplicity comes at a cost: it’s impossible to move content between these platform silos, ads are everywhere, and if a company goes out of business, all the writing hosted there vanishes from the internet.

I believe that even these short-form posts, no matter if they seem unimportant and fleeting at the time, still have an important place on the open web. That’s why I created Micro.blog.

Instead of yet another social network, Micro.blog is designed to work with the open web. It’s built on RSS and independent microblogs. It’s about pulling together short posts and making them more useful and easier to interact with. It prioritizes both a safe community of microblogs as well as the freedom to post to your own site.

Micro.blog encourages publishing at your own domain name, where you can control your own content, but it still integrates posts into a familiar timeline user interface, with centralized replies, favorites, and an open API based on JSON Feed and IndieWeb standards.

[You can register for free](https://micro.blog/register), bring your own weblog, or let Micro.blog host a microblog for you with a simple paid subscription. Map a custom domain to your site and get your content out whenever you want. I hope you like it.
