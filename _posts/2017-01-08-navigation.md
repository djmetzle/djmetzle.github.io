---
layout: post
title: Navigation
---

I'd like to add some navigation to my little blog site.
By default, the page layout's are set up in such a way that do not have links or footers. 

Let's fix that.

### Jekyll
By default, Jekyll has it's own internal definition of what the default page looks like.
I have a custom defined `post` layout that looks like this:

```
---
layout: default
---

<article class="post">
  <h1>{{ page.title }}</h1>

  <div class="entry">
    {{ content }}
  </div>

  <div class="date">
    Written on {{ page.date | date: "%B %e, %Y" }}
  </div>
</article>
```

Kind of interesting right? There is some sort of YAML templating going on here.


### Default.html
There is a Jekyll page bootstrap repo available at [/barryclark/jekyll-now](https://github.com/barryclark/jekyll-now).

His `default.html` can be found [within /_layouts](https://github.com/barryclark/jekyll-now/blob/master/_layouts/default.html).
This repo contains a `page.html` [as well](https://github.com/barryclark/jekyll-now/blob/master/_layouts/page.html).

So using these as templates, with some careful modifications, we get [these](https://github.com/djmetzle/djmetzle.github.io/blob/master/_layouts/default.html) [files](https://github.com/djmetzle/djmetzle.github.io/blob/master/_layouts/page.html).

### Thoughts
They're ugly. We have a "Blog" link in the `nav`, so let's not `a` the title.
Also, i think the `article` class needs some padding, so add that in styles as well.


