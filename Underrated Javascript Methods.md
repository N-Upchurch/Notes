---
tags: [Code Snippets, Javascript]
title: Underrated Javascript Methods
created: '2020-11-29T02:38:13.823Z'
modified: '2020-11-29T03:08:31.782Z'
---

Underrated Javascript Methods
=============================

copyWithin()
------------

The copyWithin() method shallow copies part of an array to another location in the same array and returns it without modifying its length. Here is an example of this method in action

Syntax – arr.copyWithin(target, start?, end?)

target: the index position at which to copy the sequence to.
The start and end argument is optional.

The start index defaults to zero, while the end index defaults to array.length.

``` javascript
const hearts = ['💜', '🧡', '💙', '🤍', ' 💚'];

// copy to index 0 the element at index 3
console.log(hearts.copyWithin(0, 3, 4));
// expected output: ["🤍", "🧡", "💙", "🤍", "💚"]

// copy to index 1 all elements from index 3 to the end
console.log(hearts.copyWithin(1, 3));
// expected output: ["💜", "🤍", "💚", "🤍", "💚"]

// copy to index 0 the element at index 4
console.log(hearts.copyWithin(0, 4));
// expected output: ["💚", "🧡", "💙", "🤍", "💚"]

```
Entries()
---------

Entries() is applied on an Object to return a new Array iterator object that allows you to iterate through the key/value pairs in the array. One could say Entries() converts an object to a nested array.

``` javascript
//Imagine a user fills a form that returns the object below
const allergies = {
  'milk': true,
  'eggs': false,
  'peanuts': false
}

const allergiesArray = allergies.entries();

console.log(allergiesArray);
// expected output: 
 [
    ['milk', true],
    ['eggs', false],
    ['peanuts', true]
];

```
Fill()
------

Fill() method changes all elements in an array to a static value, from a start index to an end index. It returns the modified array.

Syntax – array.fill(value, start?, end?)

Start and end are optional. The start index defaults to zero, while the end index defaults to array.length.

``` javascript
const hearts = ['💜', '🧡', '💙', '🤍', ' 💚'];

// fill with 💖 from position 2
console.log(hearts.fill('💖', 2));
// expected output: ['💜', '🧡', '💖', '💖', ' 💖']

//fill the whole array
console.log(hearts.fill(💖));
// expected output: ['💖', '💖', '💖', '💖', ' 💖']

```

some()
------
Returns true is some matches are found in an array.

``` javascript
var socials = ["Twitter", "Facebook", "YouTube", "Instagram"];

function checkSocial(social) {
  return social == "Twitter";
}

console.log(socials.some(checkSocial))
// Output: true
```

freeze()
--------
Converts an object into an immutable object.
``` javascript
var json = {
  key: "value"
}

Object.freeze(json);

json.key = "Another value";

console.log(json)
// Output: "Value"
```



