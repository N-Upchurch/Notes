---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Seek and Destroy'
created: '2020-01-06T02:41:04.598Z'
modified: '2021-02-09T20:01:37.904Z'
---

Intermediate Algorithm Scripting: Seek and Destroy
==================================================
You will be provided with an initial array (the first argument in the destroyer function), followed by one or more arguments. Remove all elements from the initial array that are of the same value as these arguments.

My Solution:
------------
``` javascript
function destroyer(arr, ...values) {
  let argArray = [];
  return argArray = Array.prototype.slice.call(arr).filter(x => values.includes(x) == false)
}

destroyer(["tree", "hamburger", 53], "tree", 53);
```

Given Solution 1
----------------
``` javascript
function destroyer(arr) {
  var args = Array.from(arguments).slice(1);
  return arr.filter(function(val) {
    return !args.includes(val);
  });
}

```
### Code Explanation

Declare a variable named args and set it equal to a new Array object from() the arguments passed into the function. On the same or next line, use the slice()method on args starting from the second index, 1. This separates the arguments used for filtering into their own array of args.

Return the filtered array, using includes() in the callback function to check if val is not in args; returning true to keep the value in the original array or false to remove it.

Given Solution 2
----------------
``` javascript
const destroyer = (arr, ...valsToRemove) => arr.filter(elem => !valuesToRemove.includes(elem));
```
### Code Explanation

Code using ES6 syntax to declare function using arrow functions.
Using spread operator to retrieve the arguments.
Return the filtered array, using includes().
