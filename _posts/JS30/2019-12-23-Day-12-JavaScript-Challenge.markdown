---
layout: post
title:  "Day 12: JavaScript Challenge"
date:   2019-12-23 10:22:00 +0000
categories: JS30
---

This execise is all about key sequence detection. Basically when someone inputs a certain sequence of keys 
into a window or input, something should happen.
 
This is a.k.a the Konami Code. It is a cheat code that appears in many Konami video games and even 
[buzzfeed](https://buzzfeed.com) uses it on their website. If you press Up, Up, Down, Down, Left, Right, Left, Right, B, A, Enter.
It changes the background. A lot of websites have these types of easter eggs.

Haha, this is quite fun! Everytime you type the secret code 'milad'. Unicorns will be printed to the 
screen XD!

Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](http://ml-js30.epizy.com/day12.html).

{% highlight javascript %}

  const pressed = [];
  const code = 'milad';
  window.addEventListener('keyup', (e) => {
    pressed.push(e.key);
    pressed.splice(-code.length-1, pressed.length - code.length);
    
    if (pressed.join('').includes(code)) {
      console.log('DING DING');
      cornify_add();
    }
  });

{% endhighlight %}










