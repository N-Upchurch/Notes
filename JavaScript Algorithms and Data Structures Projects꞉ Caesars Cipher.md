---
tags: [Algorithm Solutions, Code Snippets, Javascript]
title: 'JavaScript Algorithms and Data Structures Projects: Caesars Cipher'
created: '2020-04-01T20:52:18.741Z'
modified: '2020-04-01T20:59:02.014Z'
---

JavaScript Algorithms and Data Structures Projects: Caesars Cipher
==================================================================
One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the ROT13 cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

Write a function which takes a ROT13 encoded string as input and returns a decoded string.

My Solution:
------------
``` javascript
const rot13 = (str) => {
    const AZ = /[A-Z]/;
    let characters = str.split(""),
        plaintext = [];
    const getPlain = (char) => {
        let product = char.charCodeAt(0) - 13;
        if (product < 65) {
            const distance = 65 - product - 1;
            return String.fromCharCode(90 - distance);
        } return String.fromCharCode(product);
    }
    characters.forEach(x => {
        x.match(AZ) ? plaintext.push(x.replace(AZ, getPlain(x))) : plaintext.push(x);
    })
    return plaintext.join("");
}
```
Given Solution 1
----------------
``` javascript
function rot13(str) {
  // Split str into a character array
  return (
    str
      .split("")
      // Iterate over each character in the array
      .map.call(str, function(char) {
        // Convert char to a character code
        var x = char.charCodeAt(0);
        // Checks if character lies between A-Z
        if (x < 65 || x > 90) {
          return String.fromCharCode(x); // Return un-converted character
        }
        //N = ASCII 78, if the character code is less than 78, shift forward 13 places
        else if (x < 78) {
          return String.fromCharCode(x + 13);
        }
        // Otherwise shift the character 13 places backward
        return String.fromCharCode(x - 13);
      })
      .join("")
  ); // Rejoin the array into a string
}
```
### Code Explanation:
* A string variable ```nstr``` is declared and initialized to store the decoded string.
* The for loop is used to loop through each character of the input string.
* If the character is not uppercase English alphabets(i.e. its ascii doesn’t lie between 65 and 91 ), we’ll leave it as it is and continue 73 with next iteration.
* If it’s the uppercase English alphabet, we’ll subtract 13 from its ascii code.
* If the ascii code is less than 78, it’ll get out of range when subtracted by 13 so we’ll add 26 (number of letters in English alphabets) to it so that after A it’ll go back to Z. e.g. M(77) <==> 77-13 = 64(Not an English alphabet) +26 = 90 <==> Z(90).

Given Solution 2
----------------
``` javascript
// Solution with Regular expression and Array of ASCII character codes
function rot13(str) {
  var rotCharArray = [];
  var regEx = /[A-Z]/;
  str = str.split("");
  for (var x in str) {
    if (regEx.test(str[x])) {
      // A more general approach
      // possible because of modular arithmetic
      // and cyclic nature of rot13 transform
      rotCharArray.push(((str[x].charCodeAt() - 65 + 13) % 26) + 65);
    } else {
      rotCharArray.push(str[x].charCodeAt());
    }
  }
  str = String.fromCharCode.apply(String, rotCharArray);
  return str;
}
```
### Code Explanation:
* An empty array is created in a variable called ```rotCharArray``` to store the character codes.
* The ```regEx``` variable stores a regular expression for all uppercase letters from A to Z.
* We split ```str``` into a character array and then use a for loop to loop through each character in the array.
* Using an if statement, we test to see if the string only contains uppercase letters from A to Z.
* If it returns true, we use the ```charCodeAt()``` function and rot13 transformation to return the correct value, otherwise we return the initial value.
* We then return the string with the character codes from the ```rotCharArray``` variable.

Given Solution 3
----------------
``` javascript
function rot13(str) {
  return str.replace(/[A-Z]/g, L =>
    String.fromCharCode((L.charCodeAt(0) % 26) + 65)
  );
}
```
### Code Explanation:
* ```String.prototype.replace``` function 47 lets you transform a ```String``` based on some pattern match (defined by a regular expression), and the transformation function 64 (which is applied to each of the pattern matches).
* Arrow function 161 syntax is used to write the function parameter to ```replace()```.
* L represents a single unit, from every pattern match with ```/[A-Z]/g``` - which is every uppercase letter in the alphabet, from ```A``` to ```Z```, present in the string.
* The arrow function applies the ```rot13``` transform on every uppercase letter from English alphabet present in the given string.

Given Solution 4
----------------
``` javascript
function rot13(str) {
    const alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    return str
      .split('')
      .map(char => {  
        const pos = alphabet.indexOf(char);      
        return pos >= 0 ? alphabet[(pos + 13) % 26] : char;
      })
      .join('');
}
```
