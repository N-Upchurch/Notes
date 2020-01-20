---
tags: [Algorithm Solutions]
title: 'Intermediate Algorithm Scripting: Sum All Primes'
created: '2020-01-20T05:36:21.428Z'
modified: '2020-01-20T05:42:41.754Z'
---

Intermediate Algorithm Scripting: Sum All Primes
================================================

A prime number is a whole number greater than 1 with exactly two divisors: 1 and itself. For example, 2 is a prime number because it is only divisible by 1 and 2. In contrast, 4 is not prime since it is divisible by 1, 2 and 4.

Rewrite ```sumPrimes``` so it returns the sum of all prime numbers that are less than or equal to num.

My Solution:
------------
``` javascript
// Returns sum of all prime numbers up to a given limit, n (inclusive).
const sumPrimes = (n) => {
    // Create array of booleans from 2 - n 
    let arr = [], limit = Math.sqrt(n), output = [];
    for (let i = 0; i <= n; i++) {
        arr.push(true);
    }
    // Change all multiples of numbers up to square 
    // root of n to false in arr
    for (let i = 2; i < limit; i++) {
        if (arr[i]) {
            for (let j = i * i; j <= n; j += i) {
                arr[j] = false;
            }
        }
    }
    // Push index of all true booleans to output
    for (let i = 2; i <= n; i++) {
        if (arr[i]) {
            output.push(i)
        }
    }
    // Return sum of output
    return output.reduce((x, y) => x + y);
};
```

Given Solution 1
-----------------
``` javascript
function sumPrimes(num) {
  var res = 0;

  // Function to get the primes up to max in an array
  function getPrimes(max) {
    var sieve = [];
    var i;
    var j;
    var primes = [];
    for (i = 2; i <= max; ++i) {
      if (!sieve[i]) {
        // i has not been marked -- it is prime
        primes.push(i);
        for (j = i << 1; j <= max; j += i) {
          sieve[j] = true;
        }
      }
    }

    return primes;
  }

  // Add the primes
  var primes = getPrimes(num);
  for (var p = 0; p < primes.length; p++) {
    res += primes[p];
  }

  return res;
}
```
### Code Explanation:
* Create a function that generates the numbers from 1 to ```num``` and check if they are prime along the way.
* Declare the variables that will be needed.
* Start with 2, if it has not been marked and added to the sieve array then it is a prime and we add it to the prime array.
* Add the others to the sieve array.
* Return the primes
* Loop through the returned array and add all the elements to then return the final value.

Given Solution 2
-----------------
``` javascript
function sumPrimes(num) {
  let i = 1;
  let sum = 0;
  while (i <= num) {
    if (isPrime(i)) {
      sum += i;
    }
    i++;
  }
  return sum;
}
//function to check if a number is prime or not
function isPrime(x) {
  for (let i = 2; i < x; i++) {
    if (x % i === 0) return false;
  }
  return x !== 1 && x !== 0;
}
//test here
sumPrimes(10);
```
### Code Explanation:
* Create a function to check if a number is prime or not.
* Declare two variables. One to keep us within the limit of the given number and the other to store the sum of numbers to be returned.
* Create a loop to check all numbers lesser than or equal to the given number.
* Check if a number is prime and add it to the value of sum.
* Return the value of sum once the loop exits.

Given Solution 3
-----------------
``` javascript
function sumPrimes(num) {
  // function to check if the number presented is prime
  function isPrime(number) {
    for (i = 2; i <= number; i++) {
      if (number % i === 0 && number != i) {
        // return true if it is divisible by any number that is not itself.
        return false;
      }
    }
    // if it passes the for loops conditions it is a prime
    return true;
  }
  // 1 is not a prime, so return nothing, also stops the recursive calls.
  if (num === 1) {
    return 0;
  }
  // Check if your number is not prime
  if (isPrime(num) === false) {
    // for non primes check the next number down from your maximum number, do not add anything to your answer
    return sumPrimes(num - 1);
  }

  // Check if your number is prime
  if (isPrime(num) === true) {
    // for primes add that number to the next number in the sequence through a recursive call to our sumPrimes function.
    return num + sumPrimes(num - 1);
  }
}
```
### Code Explanation:
* The function ```isPrime``` checks if a particular number is prime or not.
* If ```num``` is 1, return 0 since 1 is not a prime number.
* If ```num``` is not prime, check next number down from maximum number.
* If ```num``` is prime, add it to next number in the sequence through recursion to ```sumPrimes``` function.

Given Solution 4
-----------------
``` javascript
function sumPrimes(num) {
  let nums = Array.from({ length: num + 1 })
    .map((_, i) => i)
    .slice(2);
  for (let n in nums) {
    nums = nums.filter(val => val == nums[n] || val % nums[n] != 0);
  }
  return nums.reduce((prevSum, cur) => prevSum + cur);
}
// test here
sumPrimes(13);
```
### Code Explanation:
* Use ```Array.from()``` to generate a sequence of numbers up to and including ```num```. Combine with ```.slice()``` to slice off first two indices ```[0, 1]``` since all prime numbers must be greater than 1.
* If a number is not prime, it is divided by number > 1 other smaller than himself.

Given Solution 5
-----------------
``` javascript
function sumPrimes(num) {
  // step 1
  let arr = Array.from({ length: num + 1 }, (v, k) => k).slice(2);
  // step 2
  let onlyPrimes = arr.filter(n => {
    let m = n - 1;
    while (m > 1 && m >= Math.sqrt(n)) {
      if (n % m === 0) return false;
      m--;
    }
    return true;
  });
  // step 3
  return onlyPrimes.reduce((a, b) => a + b);
}
// test here
sumPrimes(977);
```
### Code Explanation:
* Step 1: Use ```Array.from()``` to generate a sequence of numbers up to and including num. Combine with ```.slice()``` to slice off first two indices ```[0, 1]``` since all prime numbers must be greater than 1.
* Step 2: Filter all numbers off of ```arr``` that are not prime by subjecting each element to the “trial division test” which “consists of dividing n by each integer m that is greater than 1 and less than or equal to the square root of n”. This test returns ```false``` if any number less than the element being operated on (m) produces no remainder when said element (n) is divided by it. See link below for more on this.
* Step 3: Return the sum of all remaining elements of arr using ```.reduce()```.


