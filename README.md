# How to maintain Hooberman HEP Group site

Stored here is the source code for [Hooberman HEP Group Site](http://research.physics.illinois.edu/hooberman). The basic tool for compiling and testing is called [Jekyll](http://jekyllrb.com/), which is supported on all the platforms, Windows, Mac OS and linux.

This guide was written by Goten Cao. If you need any help, feel free to contact me at ycao31@illinois.edu. I got the idea of the site after successfully creating some Twiki pages and I found it useful to have a place to show our great group members and put what we have done and what we are doing. The design was from [Kwiat QI Group Page](http://research.physics.illinois.edu/QI/Photonics/) but I somewhat changed most of it and added new stuff. During the process of making the website, I received huge support and help from the maintainer of their site, Rebecca Holmes.

## Table of Contents

* [Don't edit those HTML files on the server!](#dont-edit-those-html-files-on-the-server)
* [What you are supposed to do.](#what-you-are-supposed-to-do)
* [Setup](#setup)
  * [Github](#github)
  * [Jekyll Installation](#jekyll-installation)
* [Make changes](#make-changes)
  * [Change your About Me paragraph and Publications](#change-your-about-me-paragraph-and-publications)
  * [Change your head shot or the photo in your own page](#change-your-head-shot-or-the-photo-in-your-own-page)
  * [Add News](#add-news)
  * [Add publications for Ben](#add-publications-for-ben)
* [Test locally](#test-locally)
* [Build and upload](#build-and-upload)
  * [Get access to the remote server](#get-access-to-the-remote-server)
* [Sync your change to github](#sync-your-change-to-github)
* [What if what you want to do are not listed above?](#what-if-what-you-wnat-to-do-are-not-listed-above)
  * [More about Jekyll](#more-about-jekyll)
  * [Bootstrap](#bootstrap)

## Don't edit those HTML files on the server!

People may find it easy to simply change the html files on the server, but one thing to tell them is that all their changes will be gone after other people make changes using Jekyll. If you find it difficult to make changes yourself, simply send me the stuff you want to add.

### Why is this?

All Hooberman HEP group members are supposed to know how to do coding. So I'll put it directly here. After we make changes to the code, the compilation process is also required in order to see the changes in the software. Jekyll is the same case. Html files are the output files of Jekyll. Thus, if your changes are not done in the source code of Jekyll, they will be gone.

### Why bother using Jekyll?

Although html is equal to the plain text plus descriptive tags, which is much more human-readable than the machine code generated by C++ compiler, there are lots of sub-parts of the website that are used multiple times. Without Jekyll, you have to copy/paste each time you create a page. With Jekyll, you can just use layouts and variables with the help of Liquid language. And Jekyll will do all the rest of work for you. In other words, Jekyll reduces the time cost and complexity, and it somewhat makes a static site dynamic. 

## What you are supposed to do.

1. Download the files in this repository.
2. Make changes to the files locally.
3. Test locally (by command `jekyll serve`).
4. Compile using Jekyll (by command `jekyll build`).
5. Copy the files generated by Jekyll (under the folder `_site`) to the server that hosts the website.
6. Sync your changes to the GitHub repository.

## Setup

You need Github and Jekyll to do the work.

### Github

1. Get a GitHub account and contact one of the administrators of the organization (HoobermanHEP) to get added to the organization.

2. Install and set up [GitHub Desktop](https://help.github.com/articles/set-up-git/).

3. From GitHub web page, find the repository Hooberman-Group-Site-jekyll, and click "Clone in Desktop" on the bottom right and get the files on your local computer.

### Jekyll Installation

Jekyll is based on the programming language Ruby, which you must install in order to run Jekyll. (You don't need to know how to use Ruby.) Once Ruby is installed, you can easily install Jekyll and a few other necessary programs.

1. If you are not using windows, skip to step 3. Otherwise, you have to install Ruby using [RubyInstaller](http://rubyinstaller.org/downloads/). Also, in the same page, download development kit.

2. After extracting the DevKit package, use the command prompt (type `cmd` in the Windows search bar) to `cd` to the directory where you extracted it. Run the following commands:

    ```
    ruby dk.rb init
    ruby dk.rb install
    ```

3. Install the RubyGem Jekyll by typing:

    ```
    gem install jekyll
    ```
    
4. Install the RubyGem RDiscount (a processor for Markdown, which we will use for simple text formatting):

    ```
    gem install rdiscount
    ```

## Make changes

Now that you have both the source code and Jekyll, you can start to make changes. This is the directory structure of the source code:

```
.
├── _data
|   ├── group_members.yml
|   └── longjond_work.yml
├── _includes
|   ├── footer.html
|   └── navbar.html
|   └── poster.html
├── _layouts
|   ├── default.html
|   └── home.html
├── _plugin
|   └── markdown-tag.rb
├── _posts
|   └── 2015-06-23-USATLAS-Workshop.md
├── _site
├── changelog
├── css
├── group_member_photo
|   ├── full
|   └── headshot
├── img
├── js
├── news
├── people
|   ├── index.html
|   └── longjond.html
├── publications
├── research
├── _config.yml
├── index.html
└── README.md
```
### Change your About Me paragraph and Publications

Go to `people/your_netid.html`. Make changes according to the format.

### Change your head shot or the photo in your own page

Go to `group_member_photo`. `/headshot` is for the headshot in the people main page and `/full` is the one in your own page. Make sure that the photo you submit have the same width as height and please try to get the size of the photo to its minimum under the condition that it doesn't reduce the quality when viewed on the website.

### Add News

Go to `_post` and follow the format there.

### Add publications for Ben

Go to `publications` and change the stuff in index.html according to the format.

## Test locally

You've made the changes! But please test locally to make sure it works fine before upload it to the server. Go to the directory of the site in your terminal and do the command
```
jekyll serve
```
Then inside the terminal window, there will be an address provided. For me, it's 127.0.0.1:4000. And I just go to 127.0.0.1:4000/hooberman in the browser. This way you are able to have a look at your changes.

## Build and upload

Now that you've tested locally, you can move to build and upload. Building(compiling) is simply by the command
```
jekyll build
```
After this, the generated site will be stored in the folder `_site`

### Get access to the remote server

I've asked the webmaster to grant all of our members the access to the server. But if there are new comers, please email engrit-help@illinois.edu to get added.

The server locates at `\\engr-web-02.engr.illinois.edu\research.physics.illinois.edu\hooberman`.

You may access to it either by using a campus Windows computer (remote access is also fine) or using the [vpn](https://www.cites.illinois.edu/vpn/download-install.html).

Once you reach there, simply copy the files in the `_site` folder to the server. If you know which file you've changed, it's always better if you only replace that file.

## Sync your change to github

At last, don't forget to sync your changes to github. And please delete all the files in the folder `_site` before you commit.

## What if what you want to do are not listed above?

Here are some more details about jekyll and other stuff.

### More about Jekyll

Please read [Jekyll documentations](http://jekyllrb.com/docs/home/). And I'll explain how Jekyll works.

You may spot that some folders in the directory start with `_`. These folders are used by Jekyll to make our lifes easier. Stored in these folders are the sub-parts of the page and also texts in other formats like markdown. As a result, these folders will not be copied to the generated site. And the folders starting without `_` or `.` will be 100% copied to the generated site folder.

You may also find things like this at the front of the html file.

```
---
layout: people
title: People
---

```
These are called YAML frontmatter, which you can find documentation about in Jekyll documentation page. What this does is to use the layout people.html in _layout.

Also, you can see things like 
```
{% for category in site.data.group_members %}
```

They don't seem to be html... You are right. They are not. This is [Liquid Templating language](http://liquidmarkup.org/) which is used to save efforts for webdesign.

And, for things like
```
{% include navbar.html %}
```
This means to include navbar.html in the _include folder.

### Bootstrap

You may also noticed that we have an css file which is very big compared to others and that many divs have strange class names. It's because we are using [bootstrap](http://getbootstrap.com/) here. It offers great style templates that we can use by simply copy/paste and I used lots of it in our site. If you are also interested in applying some styles of it, go to [this page](http://getbootstrap.com/getting-started/) and find examples. Get into any of them you like and download the html. Then copy/paste the ones you like.
