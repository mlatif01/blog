---
layout: post
title:  "Day 21: JavaScript Challenge"
date:   2020-04-07 16:36:00 +0000
categories: JS30
---

In this exercise we create a geolocation based speedometer and compass.

The exercise requires us to install an IOS simulator that unfortunately only works on Mac computers.

For the challenge we have to use the geolocation API to rotate an image in the form of a compass. The image will be altered based 
on the position, speed and heading of the device it is running on.

In case you have a Mac the code is below!

{% highlight javascript %}

      const arrow = document.querySelector('.arrow');
      const speed = document.querySelector('.speed-value');

      navigator.geolocation.watchPosition(
        (data) => {
          console.log(data);
          speed.textContent = data.coords.speed;
          arrow.style.transform = `rotate(${data.coords.heading}deg)`;
        },
        (err) => {
          console.error(err);
        }
      );

{% endhighlight %}

Furthermore, since this exercise could not be done on windows. I created a JS Calculator instead for fun, and have added that to the 
demo page for day 21.

Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](https://ml-js30.netlify.com/).









