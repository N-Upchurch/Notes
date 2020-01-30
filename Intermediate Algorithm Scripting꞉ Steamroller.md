---
tags: [Algorithm Solutions]
title: 'Intermediate Algorithm Scripting: Steamroller'
created: '2020-01-30T04:49:02.678Z'
modified: '2020-01-30T04:58:53.659Z'
---

Intermediate Algorithm Scripting: Steamroller
=============================================

Flatten a nested array. You must account for varying levels of nesting.

My Solution:
------------
``` javascript
const steamrollArray = (arr) => arr.flat(Infinity);
```

Given Solution 1
----------------
``` javascript
function steamrollArray(arr) {
  var flattenedArray = [];

  // Create function that adds an element if it is not an array.
  // If it is an array, then loops through it and uses recursion on that array.
  var flatten = function(arg) {
    if (!Array.isArray(arg)) {
      flattenedArray.push(arg);
    } else {
      for (var a in arg) {
        flatten(arg[a]);
      }
    }
  };

  // Call the function for each element in the array
  arr.forEach(flatten);
  return flattenedArray;
}
```
### Code Explanation:
* Create a new variable to keep flattened arrays.
* Create a function that will add non-array elements to the new variable, and for the ones that are array, loop through them to get the element.
* It does that by using recursion, if the element is an array then call the function again with a layer of array deeper to check if it is an array or not. If it is not then push that non-array element to the variable that gets returned. Otherwise, keep going deeper.
* Invoke the function, the first time you will always pass it an array, so it always falls into the isArray branch
* Return the flattened array.

Given Solution 2
----------------
``` javascript
function steamrollArray(arr) {
  let flat = [].concat(...arr);
  return flat.some(Array.isArray) ? steamrollArray(flat) : flat;
}
```
### Code Explanation:
* Use spread operator to concatenate each element of ```arr``` with an empty array
* Use ```Array.some()``` method to find out if the new array contains an array still
* If it does, use recursion to call ```steamrollArray``` again, passing in the new array to repeat the process on the arrays that were deeply nested
* If it does not, return the flattened array

Given Solution 3
----------------
``` javascript
function steamrollArray(arr) {
  while (arr.some(element => Array.isArray(element))) {
    arr = arr.flat();
  }
  return arr;
}
```
### Code Explanation:
* Use ```Array.some()``` method to find out if the new array contains an array still, if it does flatten the array
* Repeats until there are no more arrays inside ```arr```.


Given Solution 4
----------------
``` javascript
function steamrollArray(arr) {
  return arr
    .toString()
    .replace(",,", ",") // "1,2,,3" => "1,2,3"
    .split(",") // ['1','2','3']
    .map(function(v) {
      if (v == "[object Object]") {
        // bring back empty objects
        return {};
      } else if (isNaN(v)) {
        // if not a number (string)
        return v;
      } else {
        return parseInt(v); // if a number in a string, convert it
      }
    });
}
```
### Code Explanation:
* First we turn the array to a string, which will give us a string of numbers separated by a comma, double comma if there was an empty array and literal object text if there was an object, which we can fix later in our if statement.
* We replace the double comma with one, then split it back into an array.
* map through the array and fix object values and convert string numbers to regular numbers.

Given Solution 5
----------------
``` javascript
function steamrollArray(val,flatArr=[]) {
  val.forEach(item => {
    if (Array.isArray(item)) steamrollArray(item, flatArr);
    else flatArr.push(item);
  });
  return flatArr;
}
```
Given Solution 6
----------------
``` javascript
function steamrollArray(arr, flatArr = []) {
  const elem = arr.pop();
  return elem
    ? !Array.isArray(elem)
      ? steamrollArray(arr, [elem, ...flatArr])
      : steamrollArray(arr.concat(elem), flatArr)
    : flatArr;
}
```
