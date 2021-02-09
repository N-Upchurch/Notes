---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: DNA Pairing'
created: '2020-01-09T07:14:21.797Z'
modified: '2021-02-09T20:01:37.583Z'
---

Intermediate Algorithm Scripting: DNA Pairing
=============================================

The DNA strand is missing the pairing element. Take each character, get its pair, and return the results as a 2d array.

Base pairs are a pair of AT and CG. Match the missing element to the provided character.

Return the provided character as the first element in each array.

For example, for the input GCG, return ```[["G", "C"], ["C","G"],["G", "C"]]```

The character and its pair are paired up in an array, and all the arrays are grouped into one encapsulating array.

My Solution:
------------
``` javascript
let pairElement = (str) => {
    let arr = str.split('');
    let mdArr = arr.map(x => [x]);
    mdArr.forEach( x => {
      switch(x[0]) {
        case 'A' :
        x.push('T');
        break;
  
        case 'T' :
        x.push('A');
        break;
  
        case 'C' :
        x.push('G');
        break;
  
        case 'G' :
        x.push('C');
        break;
      }
    });
    return mdArr
  }
  
```

Given Solution 1:
-----------------
``` javascript
function pairElement(str) {
  // Return each strand as an array of two elements, the original and the pair.
  var paired = [];

  // Function to check with strand to pair.
  var search = function(char) {
    switch (char) {
      case "A":
        paired.push(["A", "T"]);
        break;
      case "T":
        paired.push(["T", "A"]);
        break;
      case "C":
        paired.push(["C", "G"]);
        break;
      case "G":
        paired.push(["G", "C"]);
        break;
    }
  };

  // Loops through the input and pair.
  for (var i = 0; i < str.length; i++) {
    search(str[i]);
  }

  return paired;
}
```

### Code Explanation
* The program is very simple, the best solution that I have come up with is to use a switch to catch all the possible four elements. Using if statements would take too much code. You could also use Regular Expressions.
* Since we have to the original and the pair, I decided to take all four cases instead of the base two.
* Create an empty array and use the ```search``` function to push the right values to the array and return them.


Given Solution 2:
-----------------
``` javascript
function pairElement(str) {
  //create object for pair lookup
  var pairs = {
    A: "T",
    T: "A",
    C: "G",
    G: "C"
  };
  //split string into array of characters
  var arr = str.split("");
  //map character to array of character and matching pair
  return arr.map(x => [x, pairs[x]]);
}
```

### Code Explanation
* First define an object with all pair possibilities, this allows us to easily find by key or value.
* Split ```str``` into a characters array so we can use each letter to find its pair.
* Use the map function to map each character in the array to an array with the character and its matching pair, creating a 2D array.


