---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Wherefore art thou'
created: '2020-01-06T05:34:19.220Z'
modified: '2021-02-09T20:01:38.157Z'
---

Intermediate Algorithm Scripting: Wherefore art thou
====================================================

Make a function that looks through an array of objects (first argument) and returns an array of all objects that have matching name and value pairs (second argument). Each name and value pair of the source object has to be present in the object from the collection if it is to be included in the returned array.

For example, if the first argument is ```[{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }]```, and the second argument is ```{ last: "Capulet" }```, then you must return the third object from the array (the first argument), because it contains the name and its value, that was passed on as the second argument.

My Solution:
------------
``` javascript
const whatIsInAName = (collection, source) => {
  let keys = Object.keys(source)
  return collection.filter(obj => keys.every(key => obj.hasOwnProperty(key) && obj[key] === source[key]))
}
```

Given Solution 1
----------------
``` Javascript
function whatIsInAName(collection, source) {
  var srcKeys = Object.keys(source);
  return collection.filter(function(obj) {
    for (var i = 0; i < srcKeys.length; i++) {
      if (
        !obj.hasOwnProperty(srcKeys[i]) ||
        obj[srcKeys[i]] !== source[srcKeys[i]]
      ) {
        return false;
      }
    }
    return true;
  });
}
```

Given Solution 2
----------------
``` Javascript
function whatIsInAName(collection, source) {
  var srcKeys = Object.keys(source);
  return collection.filter(function(obj) {
    return srcKeys.every(function(key) {
      return obj.hasOwnProperty(key) && obj[key] === source[key];
    });
  });
}
```
Given Solution 3
----------------
``` Javascript
function whatIsInAName(collection, source) {
  var srcKeys = Object.keys(source);
  // filter the collection
  return collection.filter(function(obj) {
    return srcKeys
      .map(function(key) {
        return obj.hasOwnProperty(key) && obj[key] === source[key];
      })
      .reduce(function(a, b) {
        return a && b;
      });
  });
}
```
