---
layout: post
title:  "Day 18: JavaScript Challenge"
date:   2020-03-20 18:30:00 +0000
categories: JS30
---

In this challenge we need to tally string times with reduce. We are going to add the total number of minutes, seconds and hours
from a list of timestamps from videos.

We need to pull the strings from all list items with the data-time attribute from the DOM, convert them into numbers and add everything up.
Finally we will log this to the console.

The main point of the exercise is to show how the reduce function is used.

Code snippets shown below:

{% highlight javascript %}
    <script>
      const timeNodes = Array.from(document.querySelectorAll('[data-time]'));

      const seconds = timeNodes
        .map(node => node.dataset.time)
        .map(timeCode => {
          const [mins, secs] = timeCode.split(':').map(parseFloat);
          return mins * 60 + secs;
        })
        .reduce((total, vidSeconds) => total + vidSeconds);

      let secondsLeft = seconds;
      const hours = Math.floor(secondsLeft / 3600);
      secondsLeft = secondsLeft % 3600;
      const mins = Math.floor(secondsLeft / 60);
      secondsLeft = secondsLeft % 60;
      console.log(`${hours}:${mins}:${secondsLeft}`);
    </script>
{% endhighlight %}


Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](https://ml-js30.netlify.com/).









