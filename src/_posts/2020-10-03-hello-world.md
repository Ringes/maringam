---
category: hello
tags:
  - Azure
date: 2020-10-03
title: Hello, world!
vssue: false
---

Setting up a simple blog using VuePress, Azure Static Web Apps and GitHub Actions.

<!-- more -->

## Hello, world!

I've been using [Vue.JS](https://vuejs.org/) for a couple of projects and, as far as Javascript frameworks, found it pretty awesome. It has an easy to use static site generator, [VuePress](https://vuepress.vuejs.org/), that this blog uses. The site is hosted using [Azure Static Web Apps](https://docs.microsoft.com/en-us/azure/static-web-apps/overview), which is currently in preview, so not costing any money...yet.

Getting started on the hosting was pretty straightforward as it has a very helpful guide for [VuePress](https://docs.microsoft.com/en-us/azure/static-web-apps/publish-vuepress).
::: tip
When creating the .gitignore file using

```bash
echo 'node_modules' > .gitignore
```

make sure the created file uses utf-8 encoding. I spent way too much time trying to figure out why git was ignoring my .gitignore file :neutral_face: and adding node_modules to the repo, yikes!
:::

If all goes well, when you commit any updates, or new posts to your static site repo hosted on github, a GitHub Actions workflow will kick in and build and deploy it.

### Spruce it up

The blog uses a pretty cool theme, [vuepress-theme-meteorlxy](https://vuepress-theme-meteorlxy.meteorlxy.cn/). There are plenty of other VuePress themes available, but I liked this one the most, probably mostly because the guide was well written.

### Custom Domain

The Preview also allows you to map a [custom domain](https://docs.microsoft.com/en-us/azure/static-web-apps/custom-domain) should you have one. Did I mention you also get a free SSL certificate? Yay!

### Costs

So far the only costs incurred have been on getting a domain, but when it does come out of preview, there will be some costs. Hosting low traffic static sites using an Azure storage account can be really cheap however, so hopefully this will remain so.
