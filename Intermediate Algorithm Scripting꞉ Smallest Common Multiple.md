---
tags: [Algorithm Solutions, Code Snippets, Javascript]
title: 'Intermediate Algorithm Scripting: Smallest Common Multiple'
created: '2020-01-20T19:59:54.749Z'
modified: '2020-01-21T06:28:46.874Z'
---

Intermediate Algorithm Scripting: Smallest Common Multiple
==========================================================

Find the smallest common multiple of the provided parameters that can be evenly divided by both, 
as well as by all sequential numbers in the range between these parameters. 
The range will be an array of two numbers that will not necessarily be in numerical order.
For example, if given 1 and 3, find the smallest common multiple of both 1 and 3 that is 
also evenly divisible by all numbers between 1 and 3. 
The answer here would be 6.

My Solution:
------------
``` javascript
// Generates all integers in a range (inclusive) https://www.calculator.net/lcm-calculator.html & https://www.calculator.net/gcf-calculator.html
const numRange = (arr) => {
    let numbers = [], range = [...arr.sort((a, b) => a-b)];
    for (let i = range[1]; i >= range[0]; i--) numbers.push(i);
    return numbers;
}
console.log(numRange([1, 5]))
 
const GCD = (arr) => {
    let len = arr.length;
    for (let i = 0; i < len; i++) {
        while (arr[i] - arr[i-1] >= arr[i+1]) {
            arr[i] -= arr[i+1]
        }
    } return arr;
}
console.log(GCD([5, 4, 3, 2, 1]))
console.log(GCD([155,15]))
```

