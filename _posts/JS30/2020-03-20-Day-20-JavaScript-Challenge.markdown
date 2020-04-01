---
layout: post
title:  "Day 20: JavaScript Challenge"
date:   2020-04-01 12:06:00 +0000
categories: JS30
---

This this exercise, we learnt about speech recognition in the browser. It is amazing that you can 
do this straight in the browser without any external libraries or API's.

We use a speech recognition object which lives on top of the window to implement this functionality.

Every time we start speaking we create a new paragraph on the DOM where we find the .words class.

Code snippets shown below:

{% highlight javascript %}

      window.SpeechRecognition =
        window.SpeechRecognition || window.webkitSpeechRecognition;

      const recognition = new SpeechRecognition();
      recognition.interimResults = true;
      recognition.lang = 'en-US';

      let p = document.createElement('p');
      const words = document.querySelector('.words');
      words.appendChild(p);

      recognition.addEventListener('result', e => {
        const transcript = Array.from(e.results)
          .map(result => result[0])
          .map(result => result.transcript)
          .join('');

        const poopScript = transcript.replace(/poop|poo|shit|dump/gi, '??');
        p.textContent = poopScript;

        if (e.results[0].isFinal) {
          p = document.createElement('p');
          words.appendChild(p);
        }
      });

      recognition.addEventListener('end', recognition.start);

      recognition.start();

{% endhighlight %}


Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](https://ml-js30.netlify.com/).









