+++
date = '2026-06-21T01:39:54+10:00'
draft = false
title = 'Documentation – Or how did you make this accessible?'
author = 'William'
+++

## Introduction

A good accessibility advocate should follow what they preach. 

While I'm no preacher, I've certainly done some things above choosing the right template to make this website and its documents accessible to all:

### 1. Website

#### Hugo and Zen
I used [Hugo](https://gohugo.io/), an open-source static website generator, to create this website. It's command line–based software. I chose it because earlier in 2026, I took the time to learn how to use Hugo so that I could create websites unfettered by subscription fees. Static websites have identical contentf for every user, which was not an issue for being the website for *Can That Be Accessible?*

There are a wide assortment of themes made by the Hugo community. Themes help define the layout of the site, and usually includes a lot of custom CSS. In other words, themes make sure you don't have to code a website from scratch. If you know a bit of HTML and CSS, you can customise themes to your liking, going beyond the parameters set by the theme creators.

I went with [Zen by frjo](https://github.com/frjo/hugo-theme-zen), which is licensed under the GPL-2.0 licence. I'll quote frjo because they said it best:

> [Zen] uses HTML5 with a modern CSS grid and flex layout. Care has been taken to produce semantic and accessible code.

While other Hugo themes might not think about accessibility, Zen was built with accessibility in mind. I found Zen thanks to [a forum post made by another accessibility-interested Hugo user](https://discourse.gohugo.io/t/which-theme-has-very-good-accessability-or-is-even-wcag-compliant/46960). As suggested in that thread, I ran the Zen demo site through [WAVE web accessibility evaluation tool](https://wave.webaim.org/). With an AIM Score of 10 out of 10—and with no red flags on closer look—Zen was the perfect theme for me to use.

However, I found that I could go further with accessibility.

#### Making an accessible theme more accessible

Zen does not have a "Skip to main content" link that would benefit keyboard and screen reader users. So, I made one myself. With the help of ChatGPT as my coding companion, I added a skip link in the base HTML file (baseof.html).

```
<a class="skip-link" href="#main-content">
  Skip to main content
</a>
```

This also required changing the body for all pages to have the tag "main-content". I did this by modifying taxonomy.html to be:
```
<main id="main-content" class="main layout__main" tabindex="-1">
<header>
<h1 class="title">{{ .Title }}</h1>
</header>

{{ .Content }}

{{ range .Pages.ByTitle -}}
{{ .Render "taxonomy-summary" }}
{{ end -}}
</main>
```

That likely isn't good indenting hygiene, but it works. 

Now on every page, there's a "Skip to main content" button that only appears when you go though the tab order.

### 2. YouTube

### 3. Website Documents (PDF and DOCX)

