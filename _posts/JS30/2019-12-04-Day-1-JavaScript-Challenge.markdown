---
layout: post
title:  "Day 1: JavaScript Challenge"
date:   2019-12-04 12:30:44 +0000
categories: JS30
---
So this is day 1 of the [30 day JavaScript challenge](https://javascript30.com/).

For this challenge I have to build a JavaScript drum kit!

When you hit a corresponding key, it will play the sound associated with that key and it will 
perform a short animation to signify that the button is pressed.

I'm building a javascript drum kit for this challenge. I have decided to use Visual Studio Code as the editor as I'm pretty used to it now. 
The blog may be a bit of a brain dump, but I will read through here if I am bored or if I feel the need to recap on some of the things I have 
learnt throughout this course. Apologies for poor writing in advance, but who knows, this may help me improve my writing skills!
The challenge is to create a drum kit which plays the drum sound associated with the key that is pressed and it will do a short animation where 
it pops the button up to be a little bigger. Also it will apply some colouring to the button.

First below are code snippets of my JS and an important part of the CSS. Also you can find the repo [here](https://github.com/mlatif01/js30/tree/master/01%20-%20JS%20Drum%20Kit), 
and demo is [here](https://ml-js30.netlify.com/).

{% highlight javascript %}

  function playSound(e) {
    const audio = document.querySelector(`audio[data-key='${e.keyCode}']`); // selects audio element of data-key
    const key = document.querySelector(`.key[data-key='${e.keyCode}']`)      // selects class key of data-key
    if (!audio) return; // stop the function from running all together
    audio.currentTime = 0; // rewind to the start so we can press button many times
    audio.play();
    key.classList.add('playing'); // pops the button up and adds colour when key is pressed by adding playing as a class to the div
  }

  // function to remove transition effect
  function removeTransition(e) {
    if (e.propertyName !== 'transform') return; // skip if it is not a transform
    this.classList.remove('playing');
  }

  // rather than setting a timer we use a transitionend event that will fire when the button has stopped animating, so we start
  // by selecting elements with a class of key
  const keys = document.querySelectorAll('.key');

  // listen for event transitionend and call removeTransition to get rid off colour and scaling.
  // each key gets event listener added and when transition ends we remove it
  keys.forEach(key => key.addEventListener('transitionend', removeTransition));

  // here we listen to the key down event
  window.addEventListener('keydown', playSound);

{% endhighlight %}

{% highlight css %}

.keys {
  display: flex;
  flex: 1;
  min-height: 100vh;
  align-items: center;
  justify-content: center;
}

.key {
  border: .4rem solid black;
  border-radius: .5rem;
  margin: 1rem;
  font-size: 1.5rem;
  padding: 1rem .5rem;
  transition: all .07s ease;
  width: 10rem;
  text-align: center;
  color: white;
  background: rgba(0,0,0,0.4);
  text-shadow: 0 0 .5rem black;
}

.playing {
  transform: scale(1.1);
  border-color: #ffc600;
  box-shadow: 0 0 1rem #ffc600;
}
{% endhighlight %}

First new thing I came across was the data attribute. Data attributes are custom attributes which are used when we want to make up something 
like a key. Data attributes here are being used to hook up for e.g. data-key="65" along with the data key audio.
For instance, we need to hook up the data-key div to the data-key audio. So, that when someone hits a key on the keyboard, 
the audio element will be played, and a class of 'playing' which is specified in the CSS file, will be added to the data-key div. 
This will then animate the button being pressed.

A reminder worth mentioning. In CSS you can define your own selectors in the form of the class selector, which is a name preceded by a full stop "." 
The other method is using an ID selector which is a name preceded by a hash character "#". The difference between ID and class is that, an ID can be used 
to identify one element and a class can be used to identify more than one.

Furthermore, a benefit of the Class and ID selectors over using plain html selector (where you target the tag itself) is that you can have the same HTML element 
but present it differently depending on the class or ID. This ensures that the styling isn't tightly coupled with the DOM.

Keys gives us a node list of every single element that is matched. This happens when we define the key variable and assign document.querySelectorAll('.key') to it. Also we use 
keys.forEach(key => ...) as opposed to keys.addEventListener('transitionend'). This is because when we have a node list of elements we cannot listen to all of them. You must explicitly 
loop over every single element and attach an event listener.

To briefly summarise in the form of a brain dump... An Event listener was added to keydown. Query selector was used to target attribute data-key and class key. I realised that there are many 
more events that can be triggered in the DOM such as transitionend which was used in this project. Audio can be played using custom attribute data-key and src attribute and then targeting using 
query selector to target the class. We then call audio.play() to play the sound.

Describing the code:  
We create playSound function which uses a query selector to target the audio attribute of data-key and the key class of the data-key attribute. We use template expression to define argument for 
query selector function. We pass in e.KeyCode which represents the key code of the key board button being pressed.#

The if condition checks when the audio is not playing and returns from the playSound function when the sound has been played.
We rewind the time to the start so we can press the button many times so we don't have to wait every time the button is pressed. We then play and add a class of 'playing' to the class list so that the 
animation effect is performed. The removeTransition function is defined which removes the effect of the transition.

We define keys variable and use the query selector to target all classes with class of key. Listen for an event transitionend and call removeTransition to get rid of animation. 

Finally we listen to the key down event and call playSound which was mentioned above.
That's it! And we have built our drum kit. 

That was a pretty fun exercise and I am looking forward to the second one. I will aim to make the next blog post more organised!

