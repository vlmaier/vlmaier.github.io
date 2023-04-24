---
layout: post
title: Tech stack visualization
author: Vladas Maier
tags: badges css html jekyll
---

There are many ways you can show off your technical skills on your resume. Some of the options can be pretty simple like
visualizing the skills as bullet points. Another option is a single column with skills as rows and a "progress bar"-like
visualization to show how advanced your skills are compared to others. It can also be a table of skill ratings on a D to
S scale (but honestly, if I have a D-rated skill I'd just skip it).

Each option is useful in its way and is perfect for a PDF resume. However, if you have a website where you can
put your resume online and just share a link to it, you have the freedom to design your resume the way you want. Of
course, you can do the same for a PDF resume, but I haven't heard anyone say that he/she wrote his/her resume by
creating a webpage and then exporting it to a PDF.

### First attempts

What I want to show you is how I found a cool way to present your tech stack by visualizing it as an actual stack.
There's nothing magical about it, just plain HTML and CSS. When I first tried to represent technical skills with
badges, it used to look like this:

<div class="tech-stack left margin2" style="width: 100%;">
{% capture badges %}
{% include_relative assets/badges/_blog-badges.md %}
{% endcapture %}
{{ badges | markdownify }}
</div>

<p>&nbsp;</p>

I use <a href="https://home.aveek.io/GitHub-Profile-Badges/">home.aveek.io</a> website which provides great prefab
badges. It uses <a href="https://shields.io/">shields.io</a> under the hood. So s/o to both (I have starred both GitHub
repositories, of course).

On my first try, I didn't like the spacing between each badge. So I changed it. It's looking sticky now, but what if you
have a bigger stack? I didn't like the second row of badges
presented this way. In the worst case, you have a badge that is placed all by itself on its own row. Not satisfying.

<div class="tech-stack left" style="width: 100%;">
{% capture badges %}
{% include_relative assets/badges/_taski-badges.md %}
{% endcapture %}
{{ badges | markdownify }}
</div>

<p>&nbsp;</p>

Then I added more badges and thought about the visualization style of them. Honestly, with more badges, it
kind of looks neat. But "kind of" isn't good enough.

<div class="tech-stack left" style="width: 100%;">
{% capture badges %}
{% include_relative assets/badges/_sse-dracoon-badges.md %}
{% endcapture %}
{{ badges | markdownify }}
</div>

<p>&nbsp;</p>

I started to play with responsive design. I want to make sure it also looks good on a mobile device then according
to <a href="https://www.statista.com/topics/779/mobile-internet/#topicOverview">statista</a>

> Mobile internet traffic as share of total global online traffic is 59.72%
>
> Published on Jan 23, 2023

and that's a lot. So, I definitely don't want my website to look ugly on mobile phones.

### What the Stack?

After seeing my squashed badges in a mobile preview I got an idea. What if I make my badges look like a
real stack so the badges stack on top of each other to form a stack? Like Jenga tower, you know.

I tried it and I loved it.

<div class="tech-stack left">
{% capture badges %}
{% include_relative assets/badges/_blog-badges.md %}
{% endcapture %}
{{ badges | markdownify }}
</div>

<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

I played around with different CSS settings and ended up getting what pleased my eyes. I am now sharing this result code
with you.

### <a name="code"></a>Code

Plain HTML and CSS below:

#### HTML

~~~ html
<div class="tech-stack left">
  <p><img src="https://img.shields.io/badge/css3-1572B6.svg?style=for-the-badge&amp;logo=CSS3&amp;logoColor=white"></p>
  <p><img src="https://img.shields.io/badge/git-F05032.svg?style=for-the-badge&amp;logo=Git&amp;logoColor=white"></p>
  <p><img src="https://img.shields.io/badge/github%20actions-2671E5.svg?style=for-the-badge&amp;logo=githubactions&amp;logoColor=white"></p>
  <p><img src="https://img.shields.io/badge/github%20pages-121013.svg?style=for-the-badge&amp;logo=github&amp;logoColor=white"></p>
  <p><img src="https://img.shields.io/badge/html5-E34F26.svg?style=for-the-badge&amp;logo=HTML5&amp;logoColor=white"></p>
  <p><img src="https://img.shields.io/badge/markdown-000000.svg?style=for-the-badge&amp;logo=markdown&amp;logoColor=white"></p>
  <div class="tech-stack-footer"></div>
</div>
~~~

#### CSS

~~~ css
.left {
    float: left;
}
.tech-stack {
    margin: 0;
    min-width: 25%;
    width: 25%;
}
.tech-stack p {
    margin: 0;
}
.tech-stack.left p img {
    float: left;
}
.tech-stack-footer {
    clear: both;
}
@media only screen and (max-width: 600px) {
    .tech-stack {
        width: 47%;
    }
}
~~~

#### Jekyll

Since Jekyll uses <a href="https://jekyllrb.com/docs/liquid/">Liquid</a> to process templates, you can insert one
markdown file into another using the following snippet:

~~~ liquid
{% raw %}<div class="tech-stack left">
{% capture badges %}
{% include_relative assets/badges/_blog-badges.md %}
{% endcapture %}
{{ badges | markdownify }}
</div>{% endraw %}
~~~

This way you don't lose track of your text while writing the actual content of your resume, and you can reuse the
badges. Example: You have two positions where you have developed in Java, then you need a Java badge for both
positions. But you don't want to repeat yourself by using the same badge multiple times (because DRY you know).
Therefore, you can create a markdown file
for each tech stack you add. Like this:

##### assets/badges/_blog-badges.md

~~~ liquid
{% raw %}{% capture badges %}
{% include_relative assets/badges/css.md %}
{% include_relative assets/badges/git.md %}
{% include_relative assets/badges/github-actions.md %}
{% include_relative assets/badges/github-pages.md %}
{% include_relative assets/badges/html.md %}
{% include_relative assets/badges/markdown.md %}
{% endcapture %}
{{ badges | markdownify }}
<div class="tech-stack-footer"></div>{% endraw %}
~~~

##### assets/badges/_taski-badges.md

~~~ liquid
{% raw %}{% capture badges %}
{% include_relative assets/badges/android.md %}
{% include_relative assets/badges/android-studio.md %}
{% include_relative assets/badges/git.md %}
{% include_relative assets/badges/google-play.md %}
{% include_relative assets/badges/gradle.md %}
{% include_relative assets/badges/kotlin.md %}
{% include_relative assets/badges/sqlite.md %}
{% endcapture %}
{{ badges | markdownify }}
<div class="tech-stack-footer"></div>{% endraw %}
~~~

As you can see both of the tech stacks reuse the `assets/badges/git.md` badge. For completeness, this
is the content of a badge markdown file:

##### assets/badges/git.md

~~~ html
<img src="https://img.shields.io/badge/git-F05032.svg?style=for-the-badge&logo=Git&logoColor=white">
~~~

It's just an `img` tag with a link to the actual badge. You can change the `style` of the badge if you like.
Visit <a href="https://shields.io/">shields.io</a> for available badge styles.

There is definitely room for improvement here, e.g. extract the badge
style as a variable. I'll do that one day (it's on my TODO list) but for now I'm happy with the <code>
for-the-badge</code> badge style.

Check out my tech stacks on my [About](/about) page.

Cheers, happy coding :)
