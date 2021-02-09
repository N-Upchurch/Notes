---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Arguments Optional'
created: '2020-02-18T19:26:43.710Z'
modified: '2021-02-09T20:01:37.383Z'
---

Intermediate Algorithm Scripting: Arguments Optional
====================================================

Create a function that sums two arguments together. If only one argument is provided, then return a function that expects one argument and returns the sum.

For example, ```addTogether(2, 3)``` should return ```5```, and ```addTogether(2)``` should return a function.

Calling this returned function with a single argument will then return the sum:

```var sumTwoAnd = addTogether(2);```

```sumTwoAnd(3)``` returns ```5```.

If either argument isn't a valid number, return undefined.

My Solution: 
------------
``` Javascript
const addTogether = (...nums) => {
    if ([...nums].every(x => typeof x == "number")) {
        console.log("Arguments are numbers")
    } else {
        return undefined;
    }
    if ([...nums].length >= 2) {
        return [...nums].every(x => typeof x == "number") ? [...nums].reduce((x, y) => x + y): undefined;
    } else {
        return x => addTogether(...nums,x);
    }
  }
```

Given Solution 1:
-----------------
``` Javascript
function addTogether() {
  // Function to check if a number is actually a number
  // and return undefined otherwise.
  var checkNum = function(num) {
    if (typeof num !== "number") {
      return undefined;
    } else return num;
  };

  // Check if we have two parameters, check if they are numbers
  // handle the case where one is not
  // returns the addition.
  if (arguments.length > 1) {
    var a = checkNum(arguments[0]);
    var b = checkNum(arguments[1]);
    if (a === undefined || b === undefined) {
      return undefined;
    } else {
      return a + b;
    }
  } else {
    // If only one parameter was found, returns a new function that expects two
    // Store first argument before entering the new function scope
    var c = arguments[0];

    // Check the number again, must be outside the function to about returning an object
    // instead of undefined.
    if (checkNum(c)) {
      // Return function that expect a second argument.
      return function(arg2) {
        // Check for non-numbers
        if (c === undefined || checkNum(arg2) === undefined) {
          return undefined;
        } else {
          // if numbers then add them.
          return c + arg2;
        }
      };
    }
  }
}
```

### Code Explanation:
* First, I create a function with the sole purpose of checking if a number is actually a number and returns undefined if it is not. It uses ```typeof``` to check.
* Check if we have two parameters, if so, then check if they are numbers or not using the ```checkNum``` function I created.
* If they are not ```undefined``` then add them and return the addition. If they any of them is undefined then return undefined.
* In the case that we only have one argument, then we return a new function that expects two parameters. For this we store the first argument before going into a new scope to avoid our arguments being overwritten.
* Still inside the big else, we need to check the argument we saved, if it is a number then we return the function expecting a second argument.
* Now inside the function we are returning, we have to check for non numbers again just as at the beginning using ```checkNum``` if undefined then return that, otherwise if numbers add them and return the addition.

Given Solution 2:
-----------------
``` Javascript
function addTogether(first, second) {
  if (typeof first !== "number") {
    return undefined;
  }
  const sum = second =>
    typeof second === "number" ? first + second : undefined;
  return typeof second === "undefined" ? second => sum(second) : sum(second);
}
```

### Code Explanation:
* Return ```undefined``` if first argument is not a ```number``` or second argument is defined, but not a ```number```.
* Return sum of the arguments if both are provided otherwise return a sum function.

Given Solution 3:
-----------------
``` Javascript
function addTogether() {
  var args = Array.from(arguments);
  return args.some(n => typeof n !== "number")
    ? undefined
    : args.length > 1
    ? args.reduce((acc, n) => (acc += n), 0)
    : n => (typeof n === "number" ? n + args[0] : undefined);
}
```

### Code Explanation:
* First I iterate through the arguments and check for arguments that are not a number and return ```undefined```
* If it’s not I then check if the arguments length is above 1, if it is I sum the arguments using ```Array.prototype.reduce```
* Else I return a function that checks if the passed in argument is a number and sum it, if not return ```undefined```

