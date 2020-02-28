---
layout: post
title:  "Day 16: JavaScript Challenge"
date:   2020-02-06 14:30:00 +0000
categories: JS30
---

In this challenge we implement a CSS text shadow mouse move effect!

When you move your cursor around some text, the text shadow is dynamically changed.

We listen to a mouse event on 'hero' and then when that changes we will figure out where to place
the text shadow based on the offset. It looks really cool!

A wierd thing is when we listen to the mouse move on hero, if there are children elements inside the hero, 
the event.target will give us the x and y co ordinates of the actual element being hovered over.

To fix this, we need to do some normalisation to modify the x and y values. If the element we are hovering is the h1, then we 
modify the x and y values so it will be consistent across all of the elements.

In the final demo I decided to use an image instead of text and to dynamically change it's box shadow values.

Code snippets shown below:

{% highlight html %}
  <div class="hero">
    <article contenteditable>
      <img src="smash.png" alt="" class="smash">
    </article>
  </div>

  <embed src="smash.mp3" autoplay="true">
{% endhighlight %}

{% highlight javascript %}
  const hero = document.querySelector('.hero');
  const img = document.querySelector('.smash');
  const walk = 100; // 100px

  function shadow(e) {
    // get width and height of what we are hovering over
    const { offsetWidth: width, offsetHeight: height } = hero;
    let { offsetX: x, offsetY: y } = e;

    // normalisation
    if (this !== e.target) {
      x = x + e.target.offsetLeft;
      y = y + e.target.offsetTop;
    }

    // now we figure out how far the text shadow should go
    const xWalk = Math.round((x / width * walk) - (walk / 2));
    const yWalk = Math.round((y / height * walk) - (walk / 2));
    
    img.style.boxShadow = `
      ${xWalk}px ${yWalk}px 0 rgba(255,0,255,0.7),
      ${xWalk * -2}px ${yWalk}px 0 rgba(0,255,255,0.7),
      ${yWalk}px ${xWalk * -1}px 0 rgba(0,255,0,0.7),
      ${yWalk * -2}px ${xWalk}px 0 rgba(0,0,255,0.7)
    `;
  }

  hero.addEventListener('mousemove', shadow);
{% endhighlight %}


Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](http://ml-js30.epizy.com/day16.html).









