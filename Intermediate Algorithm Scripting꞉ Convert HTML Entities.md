---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Convert HTML Entities'
created: '2020-01-13T19:27:21.316Z'
modified: '2021-02-09T20:01:37.482Z'
---

Intermediate Algorithm Scripting: Convert HTML Entities
=======================================================

Convert the characters ```&```, ```<```, ```>```, `````` (double quote), and `````` (apostrophe), in a string to their corresponding HTML entities.

My Solution:
------------
``` javascript
const convertHTML = (str) => {
    let pairs = {
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        "\"": "&quot;",
        "'": "&apos;"
    }
    return str.replace(/&|<|>|\"|\'/g, (match) =>  pairs[match])
  }
```
Given Solution 1
----------------
``` javascript
function convertHTML(str) {
  // Split by character to avoid problems.

  var temp = str.split("");

  // Since we are only checking for a few HTML elements, use a switch

  for (var i = 0; i < temp.length; i++) {
    switch (temp[i]) {
      case "<":
        temp[i] = "&lt;";
        break;
      case "&":
        temp[i] = "&amp;";
        break;
      case ">":
        temp[i] = "&gt;";
        break;
      case '"':
        temp[i] = "&quot;";
        break;
      case "'":
        temp[i] = "&apos;";
        break;
    }
  }

  temp = temp.join("");
  return temp;
}
```
### Code Explanation:
* Assign temp to ```str.split('')```, which creates an array containing each individual character in the passed in string.
* Pass each character in the newly created array into a ```switch()``` statement.
* Replace the HTML entities with their corresponding HTML entity string (i.e. ```&``` becomes ```&amp;``` in line 51)
* ```temp.join('')``` converts the array of characters into a string to be returned.

Given Solution 2
----------------
``` javascript
function convertHTML(str) {
  // Use Object Lookup to declare as many HTML entities as needed.
  const htmlEntities = {
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&apos;"
  };
  // Using a regex, replace characters with it's corresponding html entity
  return str.replace(/([&<>\"'])/g, match => htmlEntities[match]);
}
```
### Code Explanation:
* Create an object to use the Lookup functionality and easily find the characters.
* Use ```replace()``` to replace characters with regex.
* The first argument for ```replace()``` is a regex that catches all the target characters and puts them into a capturing group.
* The second arguments for ```replace()``` is a function with the matched character as a parameter. It returns the correspondant entity from htmlEntities.

Given Solution 3
----------------
``` javascript
function convertHTML(str) {
  // Use Object Lookup to declare as many HTML entities as needed.
  const htmlEntities = {
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&apos;"
  };
  //Use map function to return a filtered str with all entities changed automatically.
  return str
    .split("")
    .map(entity => htmlEntities[entity] || entity)
    .join("");
}
```
### Code Explanation:
* Create an object to use the Lookup functionality and easily find the characters.
* Split the original string by characters and use map to check for the changed html entity or use the same one.
* The a function is added which is what returns the converted entity or the original one if there is no conversion.
* Lastly we join all the characters once again.


