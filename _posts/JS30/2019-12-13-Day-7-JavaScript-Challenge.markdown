---
layout: post
title:  "Day 7: JavaScript Challenge"
date:   2019-12-13 18:06:44 +0000
categories: JS30
---

This exercise focusses on the following Array methods: some(), every(), find() and findIndex().

Didn't break a sweat with this one :) but ended up learning some useful Array methods!
  
Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](https://ml-js30.netlify.com/).

JS code snippet below:
{% highlight javascript %}

    // ## Array Cardio Day 2

    const people = [
      { name: 'Wes', year: 1988 },
      { name: 'Kait', year: 1986 },
      { name: 'Irv', year: 1970 },
      { name: 'Lux', year: 2015 }
    ];

    const comments = [
      { text: 'Love this!', id: 523423 },
      { text: 'Super good', id: 823423 },
      { text: 'You are the best', id: 2039842 },
      { text: 'Ramen is my fav food ever', id: 123523 },
      { text: 'Nice Nice Nice!', id: 542328 }
    ];

    // Some and Every Checks
    // Array.prototype.some() // is at least one person 19 or older?

    // const isAdult = people.some(function(person) {
    //   const currentYear = (new Date()).getFullYear();
    //   if (currentYear - person.year >= 19) {
    //     return true;
    //   }
    // });

    // Better way of doing the above
    const isAdult = people.some(person => ( (new Date()).getFullYear())
    - person.year >= 19);
    console.log({isAdult});

    // Array.prototype.every() // is everyone 19 or older?
    const allAdults = people.every(person => ((new Date()).getFullYear)
    - person.year >= 19);
    console.log({allAdults});

    // Array.prototype.find()
    // Find is like filter, but instead returns just the one you are looking for
    // find the comment with the ID of 823423
    const findComment = comments.find(comment => comment.id === 823423);
    console.log({findComment});

    // Array.prototype.findIndex()
    // Find the comment with this ID
    // delete the comment with the ID of 823423
    const index = comments.findIndex(comment => comment.id === 823423);
    // commnts.splice(index, 1); // one way of doing it

    // another way - builds a new array of comments, using spread operator
    const newComments = [
      ...comments.slice(0, index),
      ...comments.slice(index + 1)
    ];

    console.log(newComments);

{% endhighlight %}











