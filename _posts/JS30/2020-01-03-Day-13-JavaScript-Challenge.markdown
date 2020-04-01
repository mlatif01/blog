---
layout: post
title:  "Day 13: JavaScript Challenge"
date:   2020-01-03 12:30:00 +0000
categories: JS30
---

This exercise involved creating a 'slide in on scroll' effect. When the user scrolls down the page, 
images will scroll into the body of the page.

Two key learning aspects were the window ['scroll'](https://developer.mozilla.org/en-US/docs/Web/API/Document/scroll_event) 
event and the [debounce](https://john-dugan.com/javascript-debounce/) function.

Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](https://ml-js30.netlify.com/).

{% highlight javascript %}

	function debounce(func, wait = 20, immediate = true) {
      var timeout;
      return function() {
        var context = this, args = arguments;
        var later = function() {
          timeout = null;
          if (!immediate) func.apply(context, args);
        };
        var callNow = immediate && !timeout;
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
        if (callNow) func.apply(context, args);
      };
    };

    const sliderImages = document.querySelectorAll('.slide-in');

    function checkSlide(e) {
      sliderImages.forEach(sliderImage => {
        // half way through the image
        const slideInAt = (window.scrollY + window.innerHeight)
          - sliderImage.height / 2;
          // bottom of the image
        const imageBottom = sliderImage.offsetTop + sliderImage.height;
        const isHalfShown = slideInAt > sliderImage.offsetTop;
        const isNotScrolledPast = window.scrollY < imageBottom;
        if (isHalfShown && isNotScrolledPast) {
          sliderImage.classList.add('active');
        } else {
          sliderImage.classList.remove('active');
        }
      });
    }

    window.addEventListener('scroll', debounce(checkSlide));

{% endhighlight %}










