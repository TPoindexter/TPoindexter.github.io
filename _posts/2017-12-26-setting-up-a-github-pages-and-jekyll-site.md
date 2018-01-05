---
layout: post
title: "Setting Up My Github Pages/Jekyll Site"
date: 2017-12-26 
categories: technical 
---

# Setting Up My Git Hub Page/Jekyll Site
As a back end engineer, it’s rare that I mosey into the land of front end adventures, but I wanted to give it a whirl for this blog site. I wanted something relatively easy to maintain, so I decided to go with a [Github Pages](https://pages.github.com) / [Jekyll](https://jekyllrb.com) combo . After completing my site, I wanted to complete a guide to help you do the same. 

## Setup Your Blog Repository In Github 
1. Log into your Github account 
2. On your homepage, there will be a `New Repository` button, click it
3. For the repository name, input `username.github.io` where the username is your *__Github username__* 
    - It is very important for the username portion to match your username exactly. Otherwise, Github Pages will not work 
4. Fill out the remainder of the form as you’d like, and click `Create repository` 
5. Once created, your newly created repository will have a list of tabs (Code, Issues, Pull Requests, etc).Select the `Settings` tab
6. Navigate down to the Github Pages section, and click the `Change Theme` button
7. Select the theme that strikes your fancy, and commit 

## Locally Clone The Newly Created Repo
1. Within your browser, click into your new blog repo 
2. Along the right side, there will be a `Clone or download` button, click it
3. Make sure the the title of the pop-up is `Clone with HTTPS`. If it is not, click the `Use HTTPS` hyperlink in the upper right hand corner of the pop up 
4. Copy the URL, and go back to your terminal 
5. Navigate to the directory you’d like the repo to exist
6. Type `git clone https://github.com/…` (the full URL will be the one you just copied) 

## Add Jekyll dependencies on your local
1. Change directories into your recently cloned repo 
2. Check if you have a Gemfile within your directory by typing [`ls`](http://www.mediacollege.com/linux/command/ls.html) into your terminal  
3. Do the following: 
  * `vim Gemfile` (If the file already exists, this will simply open the file. If the file does not exist, it will create it, and also allow you to enter text)
  * Type a lowercase `i` to enter Vim’s insert mode
  * Copy the two lines into the file: 

  > source 'https://rubygems.org' 

  > gem 'github-pages', group: :jekyll_plugins

  * If normal CMD + V does not work, paste the text into VIM using the dropdown menu (Edit → Paste). 
  * Sometimes copying and pasting lines into VIM from an IDE or site will cause your quotes to be "smart quotes", and these smart quotes will cause isseues. To check this, after pasting, delete one of the quotes and type it back in. If it looks different than the other quotes, replace the remaining quotes in a similar fashion. 
  * Hit the ESC button on your keyboard, followed by `:wq` to save and exit the file

## Install Jekyll and its dependencies:  
1. `bundle install`
  - If you recently updated your Mac to High Sierra, and receive an error on any gem install (nokogiri, for example), try `xcode-select --install`
2. In the future, you can keep your bundle updated by running a simple `bundle update`
3. Run your site locally: `bundle exec jekyll serve`
4. View your site: `http://localhost:4000`

## Overall Words of Wisdom 
Directory structure is key within Jekyll, so you’ll have to be mindful of this as you make your changes. If you’re ever unsure, you can always reference the [Jekyll documentation](https://jekyllrb.com/docs/structure/). In my short time of working with Jekyll and Github Pages, the `_layouts` and `_posts` folders have been most useful for me. Within my `_layouts` folder, I have two html files: one that formats my welcome page and  the other that formats my posts. If you want a layout to be your site's default layout (say for your site’s initial page), simply name it default.html. The name will allow Jekyll to pick this layout up as your default layout. The `_posts` folder contains `markdown` files of my writings. If markdown confuses you, there is plenty of solid [documentation](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) on the web.

When writing a post, make sure that you follow [Jekyll’s rules](https://jekyllrb.com/docs/posts/) for naming your files and also include the `YAML Front Matter` at the start of every post. 

Any changes that you try to make within the folder that’s name equals your Jekyll theme (mine is Architect), it will be overwritten. Any modifications you’d like to make should be executed with either an index file, or by creating new layouts in the `_layout`s folder. 


## Execute your first push!
1. Once you’ve made your desired changes, type the following commands into your terminal: 

> git add -a 

> git commit -a -m “first push”

> git push

  * If the terminal prompts you for a username/password when you try to push, it is not asking for your Github password. You need to generate a key to use as your password. The steps are provided below. 
    * Within Github, click your user icon → Settings → Developer Settings → Personal Access Tokens → Generate new token 
    * Once you navigate away from this page, you won’t be able to see the token, so copy the newly created token, and use this for your password when the terminal prompts you 
