---
layout: post
title:  Blogging on GitHub Pages
date:   2012-07-06 15:26:29 +0800
tags: [technote, living]
---

After spending a whole day to review & test the most popular static blogging platforms, I finally chose Ruhoh to start my first static blog. And since I don't wanna mess with those generated files, I decided to segregate the sources from GitHub Pages by setting up another private repository on bitbucket.org.

* Setup your ruhoh-based repository

Create your private repository on bitbucket.org, then setup the skeleton as below.

```bash
git clone git://github.com/ruhoh/blog.git <repos>
cd <repos>
git remote set-url origin https://bitbucket.org/<username>/<repos>.git
git push origin master
```

* Setup corresponding GitHub Pages with your domain

Create a public repository for Pages, **NOTE** that this repository will be serving your blog, so it has to be public, let's say we use "blog" as its name,.

```bash
git clone https://github.com/<username>/blog.git
cd blog && git checkout --orphan gh-pages
echo "" > CNAME && echo "Hello World" > index.html
git add . && git commit -a -m 'init import'
git push origin gh-pages
```

You should get a "Page build successful" notice from github.com in a few minutes, you can then access the goddamn "Hello World" page via your domain. **NOTE** Don't forget to point your domain name (A record) to github.com, you can find the latest IP address on this page.
