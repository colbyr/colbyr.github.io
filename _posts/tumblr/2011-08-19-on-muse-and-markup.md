---
layout: post
title: On Muse and Markup
tags:
- web design
- markup
- adobe
---
After Monday's [headlines](http://www.macrumors.com/2011/08/15/adobe-
introduces-muse-subscription-based-website-creation-tools/) on Adobe Muse, I
decided to check out the [free beta](http://muse.adobe.com/) for myself. For
those of you who may not know, Muse is a new tool from Adobe to "design and
publish HTML websites without writing code." The interface will be quite
familiar to those of you who have used Flash, Fireworks, Indesign, etc.

So let me make sure I got this right:

## design and publish HTML websites without writing code

Herein lies the problem with WYSIWYG editors of all shapes and sizes. The
rendered web page is just the tip of the iceberg. Without a rudimentary
understanding of the way the code works, it's harder to grasp the how, when
and why of the rendered HTML document.

Yes it's true that many print design principles are easily, and quite
effectively, applied to web design, but the differences lie in their
respective implementations. There's no scenario in which a newspaper column
would need to respond to a change in the size of the paper itself. Print
design is static. Web design is not…

There's a reason that fantastically talented individuals, like Harry Williams
of [CSS Wizardry](http://csswizardry.com/), spend time writing on the
intricacies of clean and semantic HTML:

## markup is important

Cleaner markup means faster load times and a readable document for humans
outside the confines of the browser window. I'm not saying a write perfect
HTML, not by a longshot, but I'm damn sure it looks better than this:

{% highlight python %}
<ul class="MenuBar widget_invisible colelem" id="n5"><!-- row -->
 <li class="MenuItemContainer grpelem" id="n6"><!-- vertical box -->
  <div class="pointer_cursor MenuItem MenuItemWithSubMenu MuseMenuActive colelem" id="n7"><!-- horizontal box -->
   <a class="block" href="index.html"></a>
   <div class="MenuItemLabel NoWrap grpelem" id="n8"><!-- content -->
    <p id="n10">Home</p>
    <div class="wrap"></div>
   </div>
   <div class="wrap"></div>
  </div>
 </li>
 <li class="MenuItemContainer grpelem" id="n12"><!-- vertical box -->
  <div class="pointer_cursor MenuItem MenuItemWithSubMenu colelem" id="n13"><!-- horizontal box -->
   <a class="block" href="portfolio.html"></a>
   <div class="MenuItemLabel NoWrap grpelem" id="n14"><!-- content -->
    <p id="n16">Portfolio</p>
    <div class="wrap"></div>
   </div>
   <div class="wrap"></div>
  </div>
 </li>
 <li class="MenuItemContainer grpelem" id="n18"><!-- vertical box -->
  <div class="pointer_cursor MenuItem MenuItemWithSubMenu colelem" id="n19"><!-- horizontal box -->
   <a class="block" href="contact.html"></a>
   <div class="MenuItemLabel NoWrap grpelem" id="n20"><!-- content -->
    <p id="n22">Contact</p>
    <div class="wrap"></div>
   </div>
   <div class="wrap"></div>
  </div>
 </li>
 <li class="MenuItemContainer grpelem" id="n24"><!-- vertical box -->
  <div class="pointer_cursor MenuItem MenuItemWithSubMenu colelem" id="n25"><!-- horizontal box -->
   <a class="block" href="blog.html"></a>
   <div class="MenuItemLabel NoWrap grpelem" id="n26"><!-- content -->
    <p id="n28">Blog</p>
    <div class="wrap"></div>
   </div>
   <div class="wrap"></div>
  </div>
 </li>
 <li class="wrap"></li>
</ul>
{% endhighlight %}

That's Muse output of a simple, 4-item navigation menu. Sure it works… but I
can accomplish the same thing with a fraction of the code:

{% highlight python %}
<ul class="MenuBar">
  <li><a href="#home">Home</a></li>
  <li><a href="#portfolio">Portfolio</a></li>
  <li><a href="#contact">Contact</a></li>
  <li><a href="#blog">Blog</a></li>
</ul>
{% endhighlight %}

It took Muse 43 lines to do 6 lines of work. I think the result speaks for
itself. If your objective is a professional HTML websites, you will not reach
it without writing markup. No matter how simple the site.

Desktop programs don't make good websites, us web folk make good websites.
