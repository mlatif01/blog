---
layout: post
title:  "Day 3: JavaScript Challenge"
date:   2019-12-06 09:45:44 +0000
categories: JS30
---

For day 3 we are experimenting with CSS variables and JS. Code is [here](https://github.com/mlatif01/js30/tree/master/03%20-%20CSS%20Variables) 
and demo is [here](http://ml-js30.epizy.com/day03.html).

CSS variables are declared on an element. We use the var() CSS function to insert the value of a custom property.
They allow you to reuse and apply changes to repeatedly occurring CSS properties.

The CSS variable is declared using a double dash before the name of the var.

We can declare our CSS vars in the :root pseudo-class (which represents the entire document) so that all selectors can gain access 
to these variables. 

The below code snippets show the CSS variables that are declared and the JS that interacts with it.

A reminder that came up in this task is when using the querySelectorAll function. A NodeList is returned and
not an array. The difference is that an Array has all kinds of methods for dealing with an array like map and reduce.
However, the NodeList has far less methods, which includes entries, forEach, item, keys, values.

Also an interesting fact about CSS variables is that when a variable is changed, the elements which reference it will change also.
The CSS variable behaves the same as regular CSS features in the sense that it cascades.

Code Snippets:

{% highlight javascript %}

    const inputs = document.querySelectorAll('.controls input');

    function handleUpdate() {
      const suffix = this.dataset.sizing || '';
      document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
    }

    inputs.forEach(input => input.addEventListener('change', handleUpdate));
    inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));


{% endhighlight %}

{% highlight css %}

    :root {
      --base: #ffc600;
      --spacing: 10px;
      --blur: 10px;
    }

    img {
      padding: var(--spacing);
      background: var(--base);
      filter: blur(var(--blur));
    }

    .hl {
      color: var(--base);
    }


{% endhighlight %}











