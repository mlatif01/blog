---
layout: post
title:  "Day 10: JavaScript Challenge"
date:   2019-12-20 14:48:00 +0000
categories: JS30
---

This one is quite tricky! We have to implement functionality so that when a user holds shift and
then clicks another checkbox a few rows down, all the checkboxes inbetween those should be checked.

I got a little stuck and [this](https://medium.com/@yurikanamba/javascript30-hold-shift-to-check-multiple-checkboxes-42fe0db1d350
) article was very helpful! 

Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](http://ml-js30.epizy.com/day10.html).

JS code snippet below:
{% highlight javascript %}

  // selects all input elements with type checkbox
  const checkboxes = document.querySelectorAll('.inbox input[type="checkbox"]');
  // stores which element was checked
  let lastChecked;

  function handleCheck(e) {
    // Check if they had the shift key down
    // AND check that they are checking it
    let inBetween = false;
      // check if shift key was pressed and checkbox has been checked
      if (e.shiftKey && this.checked) {
        // loop through every single checkbox
        checkboxes.forEach(checkbox => {
          if (checkbox === this || checkbox === lastChecked) {
            inBetween = !inBetween;
            console.log('Checking them in between');
          }

          if (inBetween) {
            checkbox.checked = true;
          }
        });
      }
      
      lastChecked = this;
  }

  checkboxes.forEach(checkbox => checkbox.addEventListener('click', handleCheck));

{% endhighlight %}











