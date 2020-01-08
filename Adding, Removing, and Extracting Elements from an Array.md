---
tags: [Code Snippets, Javascript]
title: 'Adding, Removing, and Extracting Elements from an Array'
created: '2019-12-11T05:00:48.778Z'
modified: '2019-12-11T05:25:33.915Z'
---

Adding, Removing, and Extracting Elements from an Array
=======================================================

Adding Elements
---------------
* Add elements to the beginning of an array with ```unshift()```.
* Add elements to the end of an array with ```push()```.

Removing Elements
-----------------
* Remove elements from the beginning of an array with ```shift()```.
* Remove elements from the end of an array with ```pop()```.

We can also return the value of the removed element with either method like this:
``` javascript
let popped = greetings.pop();
// returns 'hello'
// greetings now equals []


```
* ```splice()``` can remove elements in any position of an array. 

The first two parameters of ```splice()``` are integers which represent indexes, or positions, of the array that ```splice()``` is being called upon. And remember, arrays are zero-indexed, so to indicate the first element of an array, we would use 0. ```splice()```'s first parameter represents the index on the array from which to begin removing elements, while the second parameter indicates the number of elements to delete. For example:
``` javascript
let array = ['today', 'was', 'not', 'so', 'great'];

array.splice(2, 2);
// remove 2 elements beginning with the 3rd element
// array now equals ['today', 'was', 'great']

```
```splice()``` not only modifies the array it's being called on, but it also returns a new array containing the value of the removed elements:
``` javascript
let array = ['I', 'am', 'feeling', 'really', 'happy'];

let newArray = array.splice(3, 2);
// newArray equals ['really', 'happy']

```

You can use the third parameter, comprised of one or more element(s), to add to the array. This can be incredibly useful for quickly switching out an element, or a set of elements, for another.
``` javascript
const numbers = [10, 11, 12, 12, 15];
const startIndex = 3;
const amountToDelete = 1;

numbers.splice(startIndex, amountToDelete, 13, 14);
// the second entry of 12 is removed, and we add 13 and 14 at the same index
console.log(numbers);
// returns [ 10, 11, 12, 13, 14, 15 ]

```
Here we begin with an array of numbers. We then pass the following to ```splice()```. The index at which to begin deleting elements (3), the number of elements to be deleted (1), and the elements (13, 14) to be inserted at that same index. Note that there can be any number of elements (separated by commas) following ```amountToDelete```, each of which gets inserted.

Extracting Elements
-------------------

```slice()```, rather than modifying an array, copies, or extracts, a given number of elements to a new array, leaving the array it is called upon untouched. ```slice()``` takes only 2 parameters — the first is the index at which to begin extraction, and the second is the index at which to stop extraction (extraction will occur up to, but not including the element at this index). Consider this:
``` javascript
let weatherConditions = ['rain', 'snow', 'sleet', 'hail', 'clear'];

let todaysWeather = weatherConditions.slice(1, 3);
// todaysWeather equals ['snow', 'sleet'];
// weatherConditions still equals ['rain', 'snow', 'sleet', 'hail', 'clear']

```
In effect, we have created a new array by extracting elements from an existing array.

