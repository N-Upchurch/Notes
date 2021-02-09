---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Smallest Common Multiple'
created: '2020-01-20T19:59:54.749Z'
modified: '2021-02-09T20:01:07.400Z'
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
const smallestCommons = (arr) => {
    let sorted = arr.sort((a, b) => a-b);
    let multiple = sorted[0];
    const RANGE = (arr) => {
        let numbers = [];
        for (let i = arr[1]; i >= arr[0]; i--) numbers.unshift(i);
        return numbers;
    }
    const GCD = (a, b) => !b ? a : GCD(b, a % b);
    const LCM = (a, b) => (a * b) / GCD(a, b);
    RANGE(sorted).forEach(x => multiple = LCM(multiple, x));
    return multiple;
}

```

Given Solution 1:
-----------------
``` javascript
function smallestCommons(arr) {
  // Sort array from greater to lowest
  // This line of code was from Adam Doyle (http://github.com/Adoyle2014)
  arr.sort(function(a, b) {
    return b - a;
  });

  // Create new array and add all values from greater to smaller from the
  // original array.
  var newArr = [];
  for (var i = arr[0]; i >= arr[1]; i--) {
    newArr.push(i);
  }

  // Variables needed declared outside the loops.
  var quot = 0;
  var loop = 1;
  var n;

  // Run code while n is not the same as the array length.
  do {
    quot = newArr[0] * loop * newArr[1];
    for (n = 2; n < newArr.length; n++) {
      if (quot % newArr[n] !== 0) {
        break;
      }
    }

    loop++;
  } while (n !== newArr.length);

  return quot;
}

```

### Code Explanation:

* Because of the possibility of the smallest common denominator being among the two biggest numbers, it makes sense to check those first, so sort the array.
* Create a new array to sort all the numbers, ```newArr```.
* Use a descending ```for``` loop (```var i = arr[0]; i >= arr[1]; i--```) to add the numbers from the biggest to the smallest in the new array.
* Declare the variables for the quotient so we can access them outside the loop:
    * the quotient that’ll be our smallest common multiple (```quot```)
    * the loop number we’re checking (```loop```)
    * the index of the array of numbers (```n```)
* Use a ```do while``` loop to check what we need whilen is not the same length as the new array.
* In the ```do``` part, we are going to multiply the very first number, times the number of loops, times the second number (```quot = newArr[0] * loop * newArr[1];```).
* The ```loop``` part will allows us to increase the number we’re checking beyond the greatest number we have without having to change the algorithm.
* We enter a ```for``` loop that will go from n being 2 and going up by one (```loop++```) while it is smaller than the array with all the numbers (```n < newArr.length```).
* If the quotient does not divide evenly (```quot % newArr[n] !== 0```), then stop the loop (```break;```). If it is even, then check for the next elements (```n++```) in the array until it is not even or we find our answer.
* Outside the loop, increase the value of loop (```loop++```).
* At the end of the loop return the quotient (```return quot;```).

Note: If the array only has two elements, then the ```for``` loop never gets used and the return value is the product of said numbers.

Given Solution 2:
-----------------
``` javascript
function smallestCommons(arr) {
  var range = [];
  for (var i = Math.max(arr[0], arr[1]); i >= Math.min(arr[0], arr[1]); i--) {
    range.push(i);
  }

  // can use reduce() in place of this block
  var lcm = range[0];
  for (i = 1; i < range.length; i++) {
    var GCD = gcd(lcm, range[i]);
    lcm = (lcm * range[i]) / GCD;
  }
  return lcm;

  function gcd(x, y) {
    // Implements the Euclidean Algorithm
    if (y === 0) return x;
    else return gcd(y, x % y);
  }
}
```

### Code Explanation:
* The first, basic solution requires over 2,000 loops to calculate the test case ```smallestCommons([1,13])```, and over 4 million loops to calculate ```smallestCommons([1,25])```. This solution evaluates ```smallestCommons([1,13])``` in around 20 loops and ```smallestCommons([1,25])``` in 40, by using a more efficient algorithm.
* Make an empty array range.
* All numbers between the given range are pushed to range using a ```for``` loop.
* The next block of code implements the Euclidean algorithm, which is used for finding smallest common multiples.


Given Solution 3:
-----------------
``` javascript
function smallestCommons(arr) {
  // Euclidean algorithm for the greatest common divisor.
  // ref: https://en.wikipedia.org/wiki/Euclidean_algorithm
  const gcd = (a, b) => (b === 0 ? a : gcd(b, a % b));

  // Least Common Multiple for two numbers based on GCD
  const lcm = (a, b) => (a * b) / gcd(a, b);

  // range
  let [min, max] = arr.sort((a, b) => a - b);
  let currentLCM = min;

  while (min < max) {
    currentLCM = lcm(currentLCM, ++min);
  }

  return currentLCM;
}
```

### Code Explanation:
* Extract minimum and maximum from provided ```arr``` by sorting and grabbing the first and last values.
* Initialise ```smallestCommon``` with the LCM of first two numbers.
* Loop through range computing LCM of current LCM and next number in range ```lcm(a, b, c) = lcm(lcm(a, b), c)```.


Given Solution 4:
-----------------
``` javascript
const smallestCommons = arr => {
  let max = Math.max(...arr);
  let min = Math.min(...arr);
  // Initially the solution is assigned to the highest value of the array
  let sol = max;

  for (let i = max - 1; i >= min; i--) {
    // Each time the solution checks (i.e. sol%i===0) it won't be necessary
    // to increment 'max' to our solution and restart the loop
    if (sol % i) {
      sol += max;
      i = max;
    }
  }
  return sol;
};
```

### Code Explanation:
* Extract ```min``` and ```max``` from arr using ```Math.min()``` and ```Math.max()```, respectively. As the arguments to these functions are integers, it is necessary to spread ```...``` the array.
* As a first guess, let’s say that the solution is ```max```. (we will increment this value later on if it is not the solution)
* Confirm that our solution is a multiple of all the values between ```max``` and ```min``` using a ```for``` loop.
* In case it isn’t a solution, increment ```max``` to our solution (i.e. get the next multiple of the ```arr``` highest value) and restart the loop ```i = max```. Note that it isn’t ```i = max - 1``` since the ```for``` loop hasn’t finished yet. Once it is finished, the loop itself will execute ```i--```. It is also worth mentioning now that we started the loop at ```i = max``` and decremented ```i``` throughout instead of starting at ```i = min``` and then increment it in order to minimize the number of iterations.
* The ```if``` statement never being true means that all numbers between ```min``` and ```max``` are divisible by our solution


