---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Diff Two Arrays'
created: '2020-01-03T05:37:50.894Z'
modified: '2021-02-09T20:01:37.539Z'
---

Intermediate Algorithm Scripting: Diff Two Arrays
=================================================
Compare two arrays and return a new array with any items only found in one of the two given arrays, but not both. In other words, return the symmetric difference of the two arrays.

My Solution:
------------
``` javascript
function diffArray(arr1, arr2) {
  let newArr = arr1.concat(arr2).filter((x) => {
    if ((arr1.indexOf(x) == -1 && arr2.indexOf(x) > -1) || (arr1.indexOf(x) > -1 && arr2.indexOf(x) == -1)) {
      return x;
    }
  })
  // Same, same; but different.
  console.log(newArr);
  return newArr;
}
 
diffArray(["dog", "cat"],["dog", "caterpillar"]);

```

Given Solution 1
----------------
``` Javascript
function diffArray(arr1, arr2) {
  return arr1
    .concat(arr2)
    .filter(item => !arr1.includes(item) || !arr2.includes(item));
}

diffArray([1, 2, 3, 5], [1, 2, 3, 4, 5]);
```

Given Solution 2
----------------
``` Javascript
function diffArray(arr1, arr2) {
  return [...diff(arr1, arr2), ...diff(arr2, arr1)];

  function diff(a, b) {
    return a.filter(item => b.indexOf(item) === -1);
  }
}

```
