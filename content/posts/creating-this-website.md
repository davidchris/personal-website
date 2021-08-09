---
title: Creating This Website
date: 2020-05-25T09:10:55.000Z
draft: false
---

This is the start of my personal website. And instead of writing some generic, somewhat empty first post saying 'Hello World!'. I instead want to write about how I created this website. Foremost as a tutorial for myself.

## Static Site Generation

I went with Hugo, after some research online:

- You could all build it by yourself
- Jekyll, generates html with themes from markdown, runs locally, well integrated with GitHub, written in Ruby (I think)
- Hugo, fast, works everywhere, easy to use, written in Go

And yes, it's fast and easy to use. I rebuild my website from scratch several times one day and there was no hustle. Utilizing one of the many themes available ([Hugo Themes](https://themes.gohugo.io)) is also straight forward.

For this site I used the [hello-friend-ng theme](https://themes.gohugo.io/themes/hugo-theme-hello-friend-ng/) from [Djordje Atlialp](https://atlialp.com).

## Domain

I probably didn't do it properly here, let's see:

I bought or rented a domain, actually for another project, with GoDaddy. It seemed straight forward for me. Then, for some reason, I decided to create a dynamic domain name server (DDNS) not with GoDaddy, but with dnyu.com.

Though I forgot why I did that, it turns out that this was the easier choice for me. Managing my DNS from dnyu is more convenient. The UI looks older, but reacts faster and everything is more easily accessible.

## Hosting

It was a rough ride here.

First I could not decide for several days whether to host it at home, on a VM in the cloud or via GitHub/Gitlab. I figured that I want it somewhat in my own hands while not doing everything by myself.

For now I went with hosting over GitHub pages. After testing GitLab pages and not wanting to go through setting up a VM myself for now it seemed like the best choice.

## Publishing

Publishing goes as easy as described here: [Deploy Hugo as a GitHub Pages project](https://gohugo.io/hosting-and-deployment/hosting-on-github/).

**Edit 2021-08-09**: Something I forgot to add here which confused me a lot in the last few days is to have my `public/` directory as a git sub-module.
This sub-module has the GitHub Page as its remote.
The 'rest' of the code, the repository, is the source to generate the page, which goes into another git repository.

Thanks to: [Create and host a blog with Hugo and GitHub Pages in less than 30 minutes](https://www.mytechramblings.com/posts/create-a-website-with-hugo-and-gh/)
