---
tags: [Javascript, JS ES6]
title: Destructuring Assignment
created: '2019-12-08T00:53:09.284Z'
modified: '2021-02-09T20:02:35.934Z'
---

Destructuring Assignment
=======================

### Assigning Variables From Objects With Data Destructuring
Destructuring assignment is special syntax introduced in ES6, for neatly assigning values taken directly from an object.

#### Example without destructuring assignment:
``` javascript
const user = { name: 'John Doe', age: 34 };

const name = user.name; // name = 'John Doe'
const age = user.age; // age = 34
```
#### Example using destructuring assignment:
``` javascript
const { name, age } = user;
// name = 'John Doe', age = 34
```

### Using Destructuring Assignment with the Rest Parameter to Reassign Array Elements
``` javascript
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b); // 1, 2
console.log(arr); // [3, 4, 5, 7]
```
Variables a and b take the first and second values from the array. After that, because of rest parameter's presence, arr gets the rest of the values in the form of an array. The rest element only works correctly as the last variable in the list. As in, you cannot use the rest parameter to catch a subarray that leaves out last element of the original array.




