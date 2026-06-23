+++
date = '2026-06-23T01:39:54+10:00'
draft = false
title = 'Documentation – How did you make this accessible?'
author = 'William'
+++

<div class="alternative-formats">
	This blog post is also available in multiple formats:<br>
	<ul>
		<li><a href="/downloads/posts/Documentation - How did you make this accessible.pdf">PDF version</a> (PDF, 108 KB)</li>
		<li><a href="/downloads/posts/Documentation - How did you make this accessible</a> (DOCX, 243 KB)</li>
	</ul>
</div>

## Introduction

A good accessibility advocate should follow what they preach. 

While I'm no preacher, I've certainly done some things above choosing the right template to make this website and its documents accessible to all.

### 1. Website

#### Hugo and Zen
I used [Hugo](https://gohugo.io/), an open-source static website generator, to create this website. It's command line–based software. I chose it because earlier in 2026, I took the time to learn how to use Hugo so that I could create websites unfettered by subscription fees. Static websites have identical content for every user, which was not an issue for being the website for *Can That Be Accessible?*

There is a wide assortment of themes made by the Hugo community. Themes help define the layout of the site and usually includes a lot of custom CSS. In other words, themes make sure you don't have to code a website from scratch. If you know a bit of HTML and CSS, you can customise themes to your liking, going beyond the parameters set by the theme creators.

I went with [Zen by frjo](https://github.com/frjo/hugo-theme-zen), which is licensed under the GPL-2.0 licence. I'll quote frjo because they said it best:

> [Zen] uses HTML5 with a modern CSS grid and flex layout. Care has been taken to produce semantic and accessible code.

While other Hugo themes might not think about accessibility, Zen was built with accessibility in mind. I found Zen thanks to [a forum post made by another accessibility-interested Hugo user](https://discourse.gohugo.io/t/which-theme-has-very-good-accessability-or-is-even-wcag-compliant/46960). As suggested in that thread, I ran the Zen demo site through [WAVE web accessibility evaluation tool](https://wave.webaim.org/). With an AIM Score of 10 out of 10—and no red flags on my manual inspection—Zen was the perfect theme for me to use.

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

That likely isn't good indenting hygiene, but it works. Now every page has a "main-content" that we can skip to using the "Skip to main content" button that only appears when you go though the tab order.

### Other elements

#### Responsiveness
I can only take credit for selecting Zen as my theme. Zen features a responsive design that scales well for mobile devices. I tested my website using my iPhone 16e. On my phone, the website uses a hamburger menu rather than the row of headers on desktop. I was satisfied that it was still usable and easy to navigate.

#### Colour palette
I outline [how I chose my colour palette in a separate post](/posts/colour-palette/). When choosing the colours, I made sure that they were all WCAG AAA compliant when acting as a background black or white.

#### Font 
I chose Franklin Gothic as the typeface of choice. It san-serif and seemed easy to read. It is also a widely available font, meaning most devices (and their browsers) would be able to load it. Nevertheless, in the website's CSS, there are contingency fonts.

```
--ff-body: "Franklin Gothic Book", "ITC Franklin Gothic", Arial, system-ui, sans-serif;
--ff-headings: "Franklin Gothic Demi", "Franklin Gothic Medium", Arial, system-ui, sans-serif;
```

## 2. YouTube

The YouTube video, <a href="https://www.youtube.com/watch?v=p_RIlw-MekE"><i>Can a Medieval Fayre be accessible?</i></a>, was made from scratch, combining my skills as a video editor and as someone interested in accessibility.

While it is possible to set an audio description track as an alternative track on a YouTube video, I did not have access to this feature. According to the [YouTube Help page about multi-langauge features](https://support.google.com/youtube/answer/13338784?hl=en), multi-language audio was only available to a "subset of creators with access to Advanced features as we are expanding access gradually."

Therefore, I went with the weaker approach of uploading a [separate audio-described version](https://www.youtube.com/watch?v=SPIc47fLIwc). This separates the audio-described track from the original video, which is not as clean as being an audio track. However, I was limited by YouTube, and the opaque way it allocates features.

Recording an audio description was an interesting experience. Since the YouTube audio description track must be the same length as the original video, I could only speak in the pauses. I chose to read Dr Stephen Stone's quote verbatim rather than using my identity-first re-phrasing so that I was true to what was on screen. Similarly, I continued reading the credits even after it disappeared from the video.

Other features of the main video include:
- Closed captioning – which also includes descriptions of the music (that I wrote myself). 
- Ensuring any text on screen remains static for at least one second.
- Ensuring clear audio – I used my best lapel mic and cleaned up the audio so that it was crisp and clear. There is background noise I added in post, but I kept it at a low volume and cut out distracting elements (however, you might catch the distant police siren I left in!).
- Ensuring text on screen has sufficient contrast against background elements.
- Providing alternative formats – this includes the HTML, PDF, and DOCX transcripts as well as the audio-described version.
- Using an embedded YouTube video – when testing my website, I confirmed that a keyboard user could tab to the video and select play.

As a small note, I mainly stuck to [Pexels](https://www.pexels.com/) stock images and videos. I made sure to feature a diverse cast, including showing people who do not have any visible disability.

## 3. Website Documents (PDF and DOCX)

I took the approach of having website documents (mainly PDF and DOCX files) be alternative versions of content. This was because I made sure the HTML webpages were generally accessible. However, this did not mean I neglected the downloadable files.

The Word docs are very simple in format. I was careful to make use of correct semantic structure, mainly that there is only one H1-level heading, which is the title of the document. I also set the title of the document in the metadata.

When you set up a Word doc well, you can easily make an accessible PDF. This was the case. I did not perform any major remediation of the PDFs aside from turning some blank space into artefacts. I used Adobe Acrobat to check the accessibility of the PDFs. I manually checked the reading order. 

As you will find in the DOCX and PDF versions of my [blog post about de-linking disability from accessibility](/posts/should-accessibility-ever-be-delinked-from-disability/), I made sure the caption text was at least 12 pt. By default, Word has the caption style as 9 pt, which can be more difficult to read. 

## Reflections

Having created a website with accessibility in mind, I will honestly say that accessibility is not that hard when you plan ahead. I chose an accessible Hugo theme that was 95% of the way there. When I made sure the Word docs were accessible, the PDFs had the right reading order and was tagged.

However, accessibility was genuinely time-consuming when making the video. A lot more care was needed in writing the audio description and then recording the audio description narration. I think this came more from my inexperience in writing audio description. 

At my workplace, I make heavy use of GenAI to help me write alt text—then I refine the output. I think it would be a smoother process if I could share excerpts of the video for the GenAI to come up with a description. I would then record it.

This process really showed me that when you plan for accessibility, you'll have an easier time than retrofitting accessibility onto a product. 

When I first started my work at an unnamed government agency, I thought cramming everything into one complex table was the way to go—it displayed everything on one page. However, I wouldn't dare try remediating those tables. Sometimes, it's easier to just have three simple tables that can the same story across.