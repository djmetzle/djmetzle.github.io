---
layout: post
title: Microblogging
---

[Microblogging](http://en.wikipedia.org/wiki/Microblogging) is the new buzzword topic in content creation. 

Lets give it a try with GitHub pages!

## GitHub Pages
Everyone with a GitHub account can create a statically hosted website. 

**Free Web Hosting for all!**

And that's *free* as in *beer*.

## Enter Jekyll
Jekyll is a static website generator written in Ruby. 
You can checkout their main site here: [JekyllRb.com](https://jekyllrb.com/).

This means it should be relatively easy to hack up quick blog posts in MarkDown. Well, GitHub markdown at least, but that's what we're familiar with already, isn't it?

### Oh what fun

Turns out Jekyll is kind of headache to set up. 
I'm running Fedora on my computers. 
Ruby by default (especially gem and bundler) seem to want to handle all their own dependencies.

#### Solution?

Cryptic errors abound. If you stumble onto the same issues, give 

```
dnf install ruby-devel
``` 

a try.

### References:
https://guides.github.com/features/pages/
https://help.github.com/categories/customizing-github-pages/
