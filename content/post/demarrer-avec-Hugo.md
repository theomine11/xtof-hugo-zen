---
title: "Demarrer Avec Hugo"
date: 2017-07-20T17:25:19+02:00
draft: true
---

J'abandonne [Jekyll](https://jekyllrb.com/) pour me lancer dans le grand bain de la JAMstack avec [Hugo](https://gohugo.io), le générateur de site statique écrit dans [Go](https://golang.org). Go est un langage de programmation rapide développé par Google.

Nouveau tournant : mon intention est de construire un nouveau portfolio plus en image, pratique et raffiner quelques compétences de développement Web avec **JavaScript**, **Go**, et **SCSS**.

## Objectifs

   * Créer un portfolio pour afficher le travail
   * Revenir sur un blog pour noter mes progrès et aider les autres en cours de route
   * Apprendre la conception SCSS
   * Apprendre à concevoir un thème Hugo

Lorsque ce post sera publié, les quatre principaux objectifs de mon nouveau site de portfolio de Hugo devraient être complets.

My new portfolio has officially been launched! This is my first static website built using Hugo. In my [previous post](https://tomanistor.com/blog/starting-with-hugo), I mapped out a few broad objectives for this project.

Let’s take a look at the completed goals from a short while ago and review.

## Objectives

  * <del>Create portfolio to display work</del>
  * <del>Create blog to jot down my progress and help others along the way</del>
  * <del>Implement design with SCSS</del>
  * <del>Design new Hugo theme and distribute for others to used</del>

## Create Portfolio

The portfolio has been created and published in place of my old portfolio site. Currently, projects are displayed under the “Work” section on the index page. The index page was constructed as a one-page template to display a hero header, gallery of web projects, a list of the 10 latest blog posts, and a contact form.

## Create Blog

The blog post links on the index page lead to their own individual pages. The majority of the blog was based off of the [Hugo Black and Light Theme](https://github.com/davidhampgonsalves/hugo-black-and-light-theme) by David Hamp-Gonsalves. Overall, it was a well-constructed, minimalist, text-only theme without any scripts or clutter. The blog has been slightly redesigned but there is a bit more customization work to be done.

## Use SCSS

My first major challenge was figuring out how to use [SCSS](http://sass-lang.com/) outside of a Ruby on Rails project, since my previous installations of SASS were as easy as typing `gem install sass` in the terminal. Luckily, I found a fantastically thorough tutorial by Dan Bahrami: [Building a production website with Hugo and GulpJS](http://danbahrami.io/articles/building-a-production-website-with-hugo-and-gulp-js/). This also marked my first exposure to [Node.js](https://nodejs.org/en/).

## Design & Distribute Hugo Theme

While the theme I’ve constructed is fine to publish now and use myself, there is a ways to go to clean it up and optimize it before distributing to the Hugo community. This will be the most challenging objective that I still need to complete and requires more studying of Hugo and the correct syntax. However, I’m very close to finishing the design portion of the theme!


# Workflow Hugo

The Hugo workflow is fairly simple and straightforward. This is the workflow I use to update and operate this blog and portfolio.

Inside of your Hugo project folder, the `public/` folder is generated with all of your static site files once `hugo` is run in the terminal.

## Purge and Serve

To generate a new `public/` folder, just remove the existing one and run the server. All updates you have made to your content and theme are now available in the new `public/` folder and visible on the live server.

Always make sure to remove the old `public/` folder otherwise Hugo will continue to update existing files and add new files without removed old unused files. You definitely don’t want the clutter and confusion.
    
    $ rm -rf public/
    $ hugo server --verbose
    

### LiveReload

One of my favorite features in Hugo so far? LiveReload. The Hugo server automatically watches your project folder for changes and refreshes your browser when any new changes are made while editing, creating, or deleting files.

This is great for development when you can make changes in your text editor and immediately see them occur in your browser window.

If you want to disable LiveReload:
    
    $ hugo server --disableLiveReload
    

## Gulp Pipeline

When making any styling changes or designing themes, I use a Gulp pipeline to compile my SCSS files into compressed CSS files that are then rendering into the `public/` folder appropriately. Besides compiling and compressing style files, my gulpfile also runs a task that minifies my JavaScript files. Dan Bahrami has a [great guide](http://danbahrami.io/articles/building-a-production-website-with-hugo-and-gulp-js/) that includes setting up a Gulp pipeline and assigning Gulp tasks to watch for changes in style folders.

To get the Gulp pipeline going after I start the Hugo server, I simply type:
    
    $ gulp
    

## New Content

Creating new content in the project folder is also very simple. For example, I created this page as a markdown file inside of `content/blog/`:
    
    $ hugo new blog/hugo-workflow.md
    

So far I’ve been enjoying writing blog posts in markdown.

## Hugo Deploy

For deploying Hugo, I currently use [hugodeploy](https://github.com/mindok/hugodeploy), a simple FTP/SFTP deployment tool built in Go. Content inside of `public/` is effortlessly uploaded to my website’s root folder on my shared webhost account with two simple commands:
    
    $ hugodeploy preview
    $ hugodeploy push
    

A neat extra feature of hugodeploy is the minification of CSS, HTML, JavaScript, JSON, and XML files upon deployment. While this option can be turned off, it does help with file size and site speed if you’re not already minifying your static files.

### Rsync Process

An alternative deployment method I was thinking about using and may try out down the line is using rsync. Andrew Codispoti detailed the steps to [setting up an rsync process](http://www.andrewcodispoti.com/deploy-process/) that can deploy updates when committing and pushing with git.

### Clear Cache

I use CloudFlare as my DNS to cache my static files and help serve them faster around the world. When deploying, I sometimes find that I’ll need to clear CloudFlare’s caches in order to serve up freshly update files. As a little shortcut to constantly going to the CloudFlare site and manually clearing the cache, I created a [shell script that clears the cache](https://tomanistor.com/blog/shell-script-to-clear-cloudflare-cache) after deployment when I call it in the terminal with: `cloudclear`.

## Conclusion

All in all, my Hugo workflow is short and sweet. A typical update and publication to the live site can look like this:
    
    $ rm -rf public
    $ hugo
    $ hugodeploy preview
    $ hugodeploy push
    




