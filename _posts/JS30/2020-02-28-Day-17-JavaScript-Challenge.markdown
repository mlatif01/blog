---
layout: post
title:  "Day 17: JavaScript Challenge"
date:   2020-02-28 14:30:00 +0000
categories: JS30
---

For this exercise we are working with JS Array.sort() method.

We will sort band names without the articles so that the band names are still in alphabetical order after 
stripping the articles 'a', 'the', 'an'.

I took Kyle Simpson's advice and used a named function expression as an argument in the sort() method, 
as opposed to using an anonymous function expression.

According to Kyle named function expressions are more descriptive and they highlight to the reader, 
the purpose of the function. In this case instead of using a fat arrow function, I have used the name compareBandNames 
as the function name to describe the work that it is doing.

Code snippets shown below:

{% highlight javascript %}
      const bands = [
        'The Plot in You',
        'The Devil Wears Prada',
        'Pierce the Veil',
        'Norma Jean',
        'The Bled',
        'Say Anything',
        'The Midway State',
        'We Came as Romans',
        'Counterparts',
        'Oh, Sleeper',
        'A Skylit Drive',
        'Anywhere But Here',
        'An Old Dog'
      ];

      function strip(bandName) {
        return bandName.replace(/^(a |the |an )/i, '').trim();
      }

      const sortedBands = bands.sort(function compareBandNames(a, b) {
        return strip(a) > strip(b) ? 1 : -1;
      });

      console.log(sortedBands);

{% endhighlight %}


Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](http://ml-js30.epizy.com/day17.html).









