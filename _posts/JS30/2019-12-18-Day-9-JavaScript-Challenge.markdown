---
layout: post
title:  "Day 9: JavaScript Challenge"
date:   2019-12-18 17:31:00 +0000
categories: JS30
---

I didn't realise there were so many console object methods!

Very interesting exercise!

Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](http://ml-js30.epizy.com/day09.html).

JS code snippet below:
{% highlight javascript %}

    const dogs = [{ name: 'Snickers', age: 2 }, { name: 'hugo', age: 8 }];

    function makeGreen() {
      const p = document.querySelector('p');
      p.style.color = '#BADA55';
      p.style.fontSize = '50px';
    }

    // Regular
    console.log('hello');

    // Interpolated
    console.log('Hello I am a %s string!', 'cheeky');

    // Styled
    // console.log('%c I am some great text', 'font-size: 50px; background: red; text-shadow: 10px 10px 0 blue');

    // warning!
    console.warn('OH NOOO');

    // Error :|
    console.error('Shit!');

    // Info
    console.info('Crocodiles eat 3-4 people per year');

    // Testing
    const p = document.querySelector('p');
    console.assert(p.classList.contains('ouch'), 'That is wrong!');

    // clearing
    console.clear();

    // Viewing DOM Elements
    console.log(p);
    console.dir(p);

    // Grouping together
    dogs.forEach(dog => {
      console.groupCollapsed(`${dog.name}`);
      console.log(`This is ${dog.name}`);
      console.log(`${dog.name} is ${dog.age} years old`);
      console.log(`${dog.name} is ${dog.age * 7} dog years old`);
      console.groupEnd(`${dog.name}`);
    });

    // counting
    console.count('Mil');
    console.count('Mil');
    console.count('Amu');
    console.count('Amu');
    console.count('Mil');
    console.count('Amu');
    console.count('Mil');
    console.count('Amu');
    console.count('Amu');
    console.count('Amu');
    console.count('Amu');
    console.count('Amu');

    // timing
    console.time('fetching data');
    fetch('https://api.github.com/users/mlatif01')
      .then(data => data.json())
      .then(data => {
        console.timeEnd('fetching data');
        console.log(data);
      });

    console.table(dogs);

{% endhighlight %}











