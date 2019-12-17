---
layout: post
title:  "Day 8: JavaScript Challenge"
date:   2019-12-17 09:31:00 +0000
categories: JS30
---

Here we learn about the fundamentals of the canvas element and some other DOM manipulation tricks.

Canvas on the web is similar to microsoft paint where you get a block of actual pixels and you need to
then draw on that. You don't draw directly on the canvas element on HTML, you draw on the 'context'.

Play around with the demo! This is pretty cool!

Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](http://ml-js30.epizy.com/day08.html).

JS code snippet below:
{% highlight javascript %}

  // grab canvas and context
  const canvas = document.querySelector('#draw');
  const context = canvas.getContext('2d');

  // resize the window
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  // base settings
  context.strokeStyle = '#BADA55';
  context.lineJoin = 'round';
  context.lineCap = 'round';
  context.lineWidth = 0;
  // context.globalCompositeOperation = 'multiply';

  // initial vars
  let isDrawing = false;
  let lastX = 0;
  let lastY = 0;
  let hue = 0;
  let direction = true;

  function draw(e) {
    if (!isDrawing) return; // from the fun from running when mouse is not down
    context.strokeStyle = `hsl(${hue}, 100%, 50%)`;
    context.beginPath();
    // start from
    context.moveTo(lastX, lastY);
    // go to
    context.lineTo(e.offsetX, e.offsetY);
    context.stroke();
    [lastX, lastY] = [e.offsetX, e.offsetY];

    hue++;
    if(hue >= 360 ) {
      hue = 0;
    }

    if (context.lineWidth >= 100 || context.lineWidth <= 1) {
      direction = !direction;
    }
    if (direction) {
      context.lineWidth++;
    } else {
      context.lineWidth--;
    }
  }

  canvas.addEventListener('mousedown', (e) => {
    isDrawing = true;
    [lastX, lastY] = [e.offsetX, e.offsetY];
  });

  canvas.addEventListener('mousemove', draw);
  canvas.addEventListener('mouseup', () => isDrawing = false);
  canvas.addEventListener('mouseout', () => isDrawing = false);

{% endhighlight %}











