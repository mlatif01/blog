---
layout: post
title:  "Day 2: JavaScript Challenge"
date:   2019-12-05 15:58:44 +0000
categories: JS30
---

Let's build a CSS and JS Clock!

Code snippets are below. Also you can find the repo [here](https://github.com/mlatif01/js30/tree/master/02%20-%20CSS%20%2B%20JS%20Clock), 
and demo is [here](https://ml-js30.netlify.com/).

Code Snippets:

{% highlight javascript %}

    const secondHand = document.querySelector('.second-hand');
    const minuteHand = document.querySelector('.min-hand');
    const hourHand = document.querySelector('.hour-hand');

    function setDate() {
      const now = new Date();
      const seconds = now.getSeconds();
      const secondsDegrees = ((seconds / 60) * 360) + 90;
      secondHand.style.transform = `rotate(${secondsDegrees}deg)`;

      const minutes = now.getMinutes();
      const minutesDegrees = ((minutes / 60) * 360) + ((seconds/60)*6) + 90;
      minuteHand.style.transform = `rotate(${minutesDegrees}deg)`;

      const hour = now.getHours();
      const hoursDegrees = ((hour / 12) * 360) + ((minutes/60)*30) + 90;
      hourHand.style.transform = `rotate(${hoursDegrees}deg)`;
    }

    setInterval(setDate, 1000);

{% endhighlight %}

The hand class property
{% highlight css %}
    .hand {
      width: 50%;
      height: 6px;
      background: black;
      position: absolute;
      top: 50%;
      transform-origin: 100%;
      transform: rotate(90deg);
      transition: all 0.05s;
      transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
    }

{% endhighlight %}

This will take in the current time from JavaScript and will update the clock hands based on correct
hour, minute and second.

I realised there are many interesting CSS properties:
transform: rotate();
transform-origin;
transition;
transition-timing-function;

first we update the CSS styles for elements which have a class of .hand by adding the above properties. We then select the corresponding
div elements using the selector (i.e. .second-hand) representing the second, minute and hour hands.

The setDate function does the following:
We create a new instance of the Date class and get the current time, and degrees by which our hands should transform.
Then we add the transformation to the corresponding div elements which represent the hands.

Finally we use setInterval to call the setDate function every 1 second.

