---
layout: post
title:  "Day 6: JavaScript Challenge"
date:   2019-12-12 21:39:44 +0000
categories: JS30
---

Today we create a 'Type Ahead' feature. When you type something in the search bar, it will show all
the matched states/cities with the corresponding population.

The data is coming in from an external json file from a URL. The data (which is a huge array) needs 
to be fetched and when someone types in the search box, it will show a subset of the cities/states.

In this task we learn about AJAX (Asynchronous JavaScript and XML). It is a web development technique used to communicate with 
a server, without reloading the page.

The data is fetched using the browser's Fetch API, which is an interface for fetching resources. According to 
Mozilla's [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API). The method takes one mandatory argument, 
the path to the resource you want to fetch. It returns a Promise, which is an obejct used to handle asynchronous 
operations in JS.

I enjoyed this excercise!
  
Repo [here](https://github.com/mlatif01/js30) 
and demo is [here](http://ml-js30.epizy.com/day06.html).

JS code snippet below:
{% highlight javascript %}

const endpoint = 'https://gist.githubusercontent.com/Miserlou/c5cd8364bf9b2420bb29/raw/2bf258763cdddd704f8ffd3ea9a3e81d25e2c6f6/cities.json';

const cities = [];

// fetch api from the browser is used, and it returns a promise object
fetch(endpoint)
  .then(blob => blob.json())
  // Spread into the push method and that will give us the cities array we need
  .then(data => cities.push(...data));

function findMatches(wordToMatch, cities) {
  // find subset of the array required
  return cities.filter(place => {
    // this is where we check if the city or state matches what was searched
    const regex = new RegExp(wordToMatch, 'gi'); // Flags: g = global, i = insensitive
    return place.city.match(regex) || place.state.match(regex);
  });
}

// puts in commas
function numberWithCommas(x) {
  return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
}

// When we type into the search box, it should call this method, and then call findMatches
// to find the cities/states that match the input in the box
function displayMatches() {
  // displays filtered array to the list
  const matchArray = findMatches(this.value, cities);
  const html = matchArray.map(place => {
    const regex = new RegExp(this.value, 'gi');
    const cityName = place.city.replace(regex, `<span class="hl">${this.value}</span>`);
    const stateName = place.state.replace(regex, `<span class="hl">${this.value}</span>`);
    return `
      <li>
        <span class="name">${cityName}, ${stateName}</span>
        <span class="population">${numberWithCommas(place.population)}</span>
      </li>
    `;
  }).join('');
  suggestions.innerHTML = html;
}

// select the search bar and the suggestions list
const searchInput = document.querySelector('.search');
const suggestions = document.querySelector('.suggestions');

searchInput.addEventListener('change', displayMatches);
searchInput.addEventListener('keyup', displayMatches);

{% endhighlight %}











