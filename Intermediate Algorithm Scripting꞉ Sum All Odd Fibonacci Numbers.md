---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Sum All Odd Fibonacci Numbers'
created: '2020-01-17T04:37:43.475Z'
modified: '2021-02-09T20:01:38.057Z'
---

Intermediate Algorithm Scripting: Sum All Odd Fibonacci Numbers
===============================================================

Given a positive integer ```num```, return the sum of all odd Fibonacci numbers that are less than or equal to ```num```.

The first two numbers in the Fibonacci sequence are 1 and 1. Every additional number in the sequence is the sum of the two previous numbers. The first six numbers of the Fibonacci sequence are 1, 1, 2, 3, 5 and 8.

For example, ```sumFibs(10)``` should return ```10``` because all odd Fibonacci numbers less than or equal to ```10``` are 1, 1, 3, and 5.

My Solution:
------------
``` javascript
const sumFibs = (n) => {
    let fibs = [1];
    let next = 1, 
        first = 0, 
        second = 1;
    if (n == 1) {return 1} else if (n < 1) {return -1}
    while (next <= n) {
        fibs.unshift(next = first + second);
        first = second;
        second = next;
    }
    return fibs.filter(x => (x <= n) && (x % 2 != 0)).reduce((x, y) => {
        return x + y;
        })
}

```

Given Solution 1
----------------
``` javascript
function sumFibs(num) {
  var prevNumber = 0;
  var currNumber = 1;
  var result = 0;
  while (currNumber <= num) {
    if (currNumber % 2 !== 0) {
      result += currNumber;
    }

    currNumber += prevNumber;
    prevNumber = currNumber - prevNumber;
  }

  return result;
}
```

### Code Explanation:
* Create a variable to keep record of the current and previous numbers along with the result that will be returned.
* Use a while loop to make sure we do not go over the number given as parameter.
* We use the modulo operand to check if the current number is odd or even. If it is odd, add it to the result.
* Complete the Fibonacci circle by rotating getting the next number and swapping values after.
* Return the result.

Given Solution 2
----------------
``` javascript
function sumFibs(num) {
  // Perform checks for the validity of the input
  if (num < 0) return -1;
  if (num === 0 || num === 1) return 1;

  // Create an array of fib numbers till num
  const arrFib = [1, 1];
  let nextFib = 0;

  // We put the new Fibonacci numbers to the front so we
  // don't need to calculate the length of the array on each
  // iteration
  while ((nextFib = arrFib[0] + arrFib[1]) <= num) {
    arrFib.unshift(nextFib);
  }

  // We filter the array to get the odd numbers and reduce them to get their sum.
  return arrFib.filter(x => x % 2 != 0).reduce((a, b) => a + b);
}
```

### Code Explanation:
* Create an array of fibonacci numbers till num.
* Use ```filter()``` method to filter out even numbers.
* Use ```reduce()``` method to sum the remaining (odd) values.
* Return the sum.

