---
layout: post
title:  "Day 5: JavaScript Challenge"
date:   2019-12-11 18:31:44 +0000
categories: JS30
---

Today we mess around with CSS Flexbox. Mozilla MDN explains this well, much better than I can be
bothered to right now ;) [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox).
This [YouTube video](https://www.youtube.com/watch?v=4GaHn08BXQw) is also really good at explaining it 

Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](https://ml-js30.netlify.com/).

JS code snippet below:
{% highlight javascript %}

    const panels = document.querySelectorAll('.panel');

    function toggleOpen() {
      this.classList.toggle('open');
    }

    function toggleActive(e) {
      if (e.propertyName.includes('flex')) {
        this.classList.toggle('open-active');
      }
    }

    panels.forEach(panel => panel.addEventListener('click', toggleOpen));
    panels.forEach(panel => panel.addEventListener('transitionend', toggleActive));


{% endhighlight %}











