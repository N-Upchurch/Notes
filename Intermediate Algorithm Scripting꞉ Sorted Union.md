---
tags: [Algorithm Solutions]
title: 'Intermediate Algorithm Scripting: Sorted Union'
created: '2020-01-13T06:01:42.123Z'
modified: '2020-01-13T06:10:52.788Z'
---

Intermediate Algorithm Scripting: Sorted Union
==============================================

Write a function that takes two or more arrays and returns a new array of unique values in the order of the original provided arrays.

In other words, all values present from all arrays should be included in their original order, but with no duplicates in the final array.

The unique numbers should be sorted by their original order, but the final array should not be sorted in numerical order.

My Solution:
------------
``` javascript
const uniteUnique = (arr, ...arrs) => ([...new Set(arr.concat(...arrs))]);
```

Given Solution 1
----------------
``` javascript
function uniteUnique(arr1, arr2, arr3) {
  // Creates an empty array to store our final result.
  var finalArray = [];

  // Loop through the arguments object to truly make the program work with two or more arrays
  // instead of 3.
  for (var i = 0; i < arguments.length; i++) {
    var arrayArguments = arguments[i];

    // Loops through the array at hand
    for (var j = 0; j < arrayArguments.length; j++) {
      var indexValue = arrayArguments[j];

      // Checks if the value is already on the final array.
      if (finalArray.indexOf(indexValue) < 0) {
        finalArray.push(indexValue);
      }
    }
  }

  return finalArray;
}
```
### Code Explanation
* Create empty array ```finalResult``` to store the final result.
* Loop through the arguments object in the outer loop and store it in ```arrayArguments```.
* The inner loop is used to loop through individual array elements.
* If the element doesn’t already exist in ```finalArray```, add it.
* Return ```finalArray```.

Given Solution 2
----------------
``` javascript
function uniteUnique(arr) {
  var args = [...arguments];
  var result = [];
  for (var i = 0; i < args.length; i++) {
    for (var j = 0; j < args[i].length; j++) {
      if (!result.includes(args[i][j])) {
        result.push(args[i][j]);
      }
    }
  }
  return result;
}
```
Given Solution 3
----------------
``` javascript
function uniteUnique(arr1, arr2, arr3) {
  var newArr;
  //Convert the arguments object into an array
  var args = Array.prototype.slice.call(arguments);
  //Use reduce function to flatten the array
  newArr = args.reduce(function(arrA, arrB) {
    //Apply filter to remove the duplicate elements in the array
    return arrA.concat(
      arrB.filter(function(i) {
        return arrA.indexOf(i) === -1;
      })
    );
  });

  return newArr;
}
```
### Code Explanation
* arguments object is converted into an array using ```slice()```.
* ```reduce()``` function is used to flatten the array i.e., for every element that is in the array (or nested arrays), extract it’s elements into one-dimensional array.
* After flattening the array, ```filter()``` is used to remove duplicate elements from ```newArr```.

Given Solution 4
----------------
``` javascript
function uniteUnique() {
  var concatArr = [];
  var i = 0;
  while (arguments[i]) {
    concatArr = concatArr.concat(arguments[i]);
    i++;
  }
  uniqueArray = concatArr.filter(function(item, pos) {
    return concatArr.indexOf(item) == pos;
  });
  return uniqueArray;
}
```
### Code Explanation
* Number of arguments can change dynamically, so we don’t need to bother providing our function ```uniteUnique()``` with arguments at all.
* We use a while loop to concatenate all the arguments into one array called ```concatArr```.
* We use ```filter()``` to remove the duplicate elements by checking the index of each element and removing same elements with different positions.
* Ordering will be preserved here.

Given Solution 5
----------------
``` javascript
function uniteUnique(...arrays) {
  const flatArray = [].concat(...arrays);
  return [...new Set(flatArray)];
}
```
### Code Explanation
* We first use ```concat()``` with an empty array as a starting point and the spread operator ```...``` to create an array out of the Arguments object and to flatten it at the same time
* then we use the new ES2015 ```Set``` object to store only unique values

