---
tags: [Algorithm Solutions, Code Snippets, Javascript]
title: 'Intermediate Algorithm Scripting: Everything Be True'
created: '2020-02-18T04:41:42.984Z'
modified: '2020-02-18T04:57:04.692Z'
---

Intermediate Algorithm Scripting: Everything Be True
====================================================

Check if the predicate (second argument) is truthy on all elements of a collection (first argument).

In other words, you are given an array collection of objects. The predicate ```pre``` will be an object property and you need to return ```true``` if its value is ```truthy```. Otherwise, return ```false```.

In JavaScript, ```truthy``` values are values that translate to ```true``` when evaluated in a Boolean context.

Remember, you can access object properties through either dot notation or ```[]``` notation.

My Solution:
------------
``` Javascript
const truthCheck = (collection, pre) => {
    let isPre = [];
    collection.forEach(x => {
      x[pre] ? isPre.push(true) : isPre.push(false)
    })
    return isPre.includes(false) ? false : true;
  }
```

Given Solution 1
----------------
``` Javascript
function truthCheck(collection, pre) {
  // Create a counter to check how many are true.
  var counter = 0;
  // Check for each object
  for (var c in collection) {
    // If it is has property and value is truthy
    if (collection[c].hasOwnProperty(pre) && Boolean(collection[c][pre])) {
      counter++;
    }
  }
  // Outside the loop, check to see if we got true for all of them and return true or false
  return counter == collection.length;
}
```

### Code Explanation
* First I create a counter to check how many cases are actually true.
* Then check for each object if the value is truthy
* Outside the loop, I check to see if the counter variable has the same value as the length of collection, if true then return true, otherwise, return false

Given Solution 2
----------------
``` Javascript
function truthCheck(collection, pre) {
  return collection.every(function(element) {
    return element.hasOwnProperty(pre) && Boolean(element[pre]);
  });
}
```

### Code Explanation
* Uses the native “every” method to test whether all elements in the array pass the test.

Given Solution 3
----------------
``` Javascript
function truthCheck(collection, pre) {
  // Is everyone being true?
  return collection.every(obj => obj[pre]);
}
```
### Code Explanation
* For every object in the ```collection``` array, check the truthiness of object’s property passed in ```pre``` parameter
* ```Array#every``` method internally checks if the value returned from the callback is truthy.
* Return ```true``` if it passes for every object. Otherwise, return ```false```.
