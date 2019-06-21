---
title: "Setting up a blog in Hugo with Github and Netlify"
date: 2019-06-16T17:55:17+02:00
draft: true
---

## Setting up a Hugo blog with Github and Netlify

In this post I'll go over the general steps to take in setting up a [Hugo](https://gohugo.io/) blog with [Github](https://github.com/) and setting up the DNS and hosting with [Netlify](https://www.netlify.com/).
<!--more-->
### Hugo
Hugo is a **static site generator**. This means that Hugo builds a website based on two things, your posts and the theme you selected for your website.
With these two things, it generates a **static website**,  which means that the web pages you see are the exact ones that are stored on the server. Opposed to dynamic websites, which are generated the moment they are requested, static pages load much faster.
### Github
Github is a Git repository hosting service. This means that you can host your own project (code, wiki, issues tracker, ...) on their website with version control.
We will store the code for our website here.
### Netlify
With Netlify you can build, deploy and serve your sites and web apps. We are going to use Netlify to build the website from our Github repository using Hugo and serve it on our domain.


