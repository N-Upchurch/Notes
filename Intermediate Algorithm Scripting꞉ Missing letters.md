---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Missing letters'
created: '2020-01-09T20:04:56.106Z'
modified: '2021-02-09T20:01:37.766Z'
---

Intermediate Algorithm Scripting: Missing letters
=================================================

Find the missing letter in the passed letter range and return it.
If all letters are present in the range, return undefined.

My Solution:
------------
``` javascript
let fearNotLetter = (str) => {
  let inc = str.charCodeAt(0);
  for (let i = 0; i < str.length; i++) {
    if (str.charCodeAt(i) === inc) {inc +=1} else {
      return String.fromCharCode(inc)};
  }
  return undefined
}
```

Given Solution 1
----------------
``` javascript
function fearNotLetter(str) {
  for (var i = 0; i < str.length; i++) {
    /* code of current character */
    var code = str.charCodeAt(i);

    /* if code of current character is not equal to first character + no of iteration
        hence character has been escaped */
    if (code !== str.charCodeAt(0) + i) {
      /* if current character has escaped one character find previous char and return */
      return String.fromCharCode(code - 1);
    }
  }
  return undefined;
}
```
### Code Explanation:
* This solutions makes use of a ```for``` loop.
* Code of encountered character is stored in ```code```.
* It is checked if code of current character is the expected one (no characters are skipped) by using the logic - ```code of current character = code of first character + number of iterations```.
* If a character is missing, the missing character is found and the final string is returned.
* ```undefined``` is returned if there is no missing character in the string.

Given Solution 2
----------------
``` javascript
function fearNotLetter(str) {
  var compare = str.charCodeAt(0),
    missing;

  str.split("").map(function(letter, index) {
    if (str.charCodeAt(index) == compare) {
      ++compare;
    } else {
      missing = String.fromCharCode(compare);
    }
  });

  return missing;
}
```
### Code Explanation:

* First we define variables to store the character code for the first letter in the string, and to store whatever missing letters we may find.
* We turn the string to an array in order to map through it instead of using ```for``` and ```while``` loops.
* As we ```map``` through our letters’ character codes, we go comparing with the one that should be in that position.
* If the current letter matches, we move the comparison variable to its next position so we can compare on the next cycle.
* If not, the missing letter will be assigned to the ```missing``` variable, which will be returned after the map is finished.
* If there are no missing characters, return ```undefined```.


Given Solution 3
----------------
``` javascript
function fearNotLetter(str) {
  for (let i = 1; i < str.length; ++i) {
    if (str.charCodeAt(i) - str.charCodeAt(i - 1) > 1) {
      return String.fromCharCode(str.charCodeAt(i - 1) + 1);
    }
  }
}
```
### Code Explanation:

* Loop over the string
* Check if the difference in char codes between adjacent characters in the string is more than 1 (check ASCII table)
* Return the missing character ( +1 from where the gap was detected)


Given Solution 4
----------------
``` javascript
function fearNotLetter(str) {
  var allChars = "";
  var notChars = new RegExp("[^" + str + "]", "g");

  for (var i = 0; allChars[allChars.length - 1] !== str[str.length - 1]; i++)
    allChars += String.fromCharCode(str[0].charCodeAt(0) + i);

  return allChars.match(notChars)
    ? allChars.match(notChars).join("")
    : undefined;
}
```
### Code Explanation:
* A new string allChars is created.
* Create a regular expression notChars which selects everything except str.
* The ```for``` loop is used to add all the letters in the range to allChars.
* ```match()``` is used to strip off the str letters from the newly created string and it is returned.
* If there are no missing characters, return ```undefined```.


