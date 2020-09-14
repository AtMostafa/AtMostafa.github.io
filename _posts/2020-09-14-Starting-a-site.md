---
layout: post
title: "Starting a site"
author: Mostafa
tags: site Jekyll github
---

First things first.
Let's talk about how I started this [_website_]({{site.url}}) without any knowledge of HTML and web programming.
{{site.url}} is hosted on [GitHub Pages](https://pages.github.com/).
It is very easy and **free**:
1. I created a **public** repository following the [instructions](https://pages.github.com/): it will turn into a simple website available at [http://YourUsername.github.io]().
2. GitHub uses Jekyll to build the website.
Every time I push something to the repository, GitHub runs Jekyll on it and in a few minutes, the changes will be published online.
I found a Jekyll theme I liked from the many freely available ones—for example, check this out: [https://jekyllthemes.io/](https://jekyllthemes.io/).
Don't worry about the exact material in the theme.
You will be able to change everything.
Just choose one that has the general design elements you need, because that would need more effort to change later on.
3. I replaced my entire repository (which was pretty empty at this point), with the contents of the theme's repository. After that, my site looked exactly like the theme.
4. So far, I didn't do any coding myself. At this point, I started learning about the syntax of Jekyll to be able to modify the theme to my liking and add my content.
I read the "step-by-step tutorial" available on: Jekyll website > Docs > Tutorial ([here](https://jekyllrb.com/docs/step-by-step/01-setup/), start from the second section).
5. I started modifying the placeholders in the theme (still in progress as of publishing this post).
The "find and replace" tool in my editor was my best friend at this stage.
I looked for the parameters I didn't really know to figure out where they are defined and I changed their values.
I started adding my information instead of the theme's author's and re-arranged the menus.
For instance, the 'Blog' button at the top used to be called 'Services'.

At this point, and only after 4 days since I decided to start this up, I can pretty much do whatever I like on my website and I plan to eventually add more materials.


---
There is this great tutorial that covers this process in more details [_here_](http://jmcglone.com/guides/github-pages/).