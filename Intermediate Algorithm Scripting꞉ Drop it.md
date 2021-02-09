---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Drop it'
created: '2020-01-27T02:29:17.957Z'
modified: '2021-02-09T20:01:37.632Z'
---

Intermediate Algorithm Scripting: Drop it
=========================================

Given the array ```arr```, iterate through and remove each element starting from the first element (the 0 index) until the function ```func``` returns ```true``` when the iterated element is passed through it.

Then return the rest of the array once the condition is satisfied, otherwise, ```arr``` should be returned as an empty array.

Remember to use Read-Search-Ask if you get stuck. Try to pair program. Write your own code.

My Solution:
------------
``` javascript
const dropElements = (arr, func) => {
  while (!func(arr[0])) arr.shift(); 
  return arr;
}
```

Given Solution 1
-----------------
``` javascript
function dropElements(arr, func) {
  // drop them elements.
  var times = arr.length;
  for (var i = 0; i < times; i++) {
    if (func(arr[0])) {
      break;
    } else {
      arr.shift();
    }
  }
  return arr;
}
```
### Code Explanation:
* Create a ```for``` loop to check each element.
* Then check for the function given if ```true``` then stop, otherwise remove that element.
* return the array.

Given Solution 2
-----------------
``` javascript
function dropElements(arr, func) {
  return arr.slice(arr.findIndex(func) >= 0 ? arr.findIndex(func) : arr.length);
}
```
### Code Explanation:
* Use ES6 ```findIndex()``` function to find the index of the element that passes the condition
* Slice the array from the found index until the end
* There is one edge case! if the condition is not met against any of the elements ‘findIndex’ will return ```-1``` which messes up the input to ```slice()```. In this case use a simple conditional operator to return false instead of ```-1```. And the ternary operator returns the found index of required elements when the condition is ```true```, and the length of the array otherwise so that the return value is an empty array as is instructed.



Given Solution 3
-----------------
``` javascript
function dropElements(arr, func) {
  while (arr.length > 0 && !func(arr[0])) {
    arr.shift();
  }
  return arr;
}
```
### Code Explanation:
* Use a while loop with Array.prototype.shift() to continue checking and dropping the first element of the array until the function returns true. It also makes sure the array is not empty first to avoid infinite loops.
* Return the filtered array.


Given Solution 4
-----------------
``` javascript
function dropElements(arr, func, i = 0) {
  return i < arr.length && !func(arr[i])
    ? (dropElements(arr.slice(i + 1), func, i))
    : arr;
}
```
### Code Explanation:
* Use recursion to solve the challenge



