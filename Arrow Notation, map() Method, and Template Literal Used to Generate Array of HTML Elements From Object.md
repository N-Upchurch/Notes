---
tags: [Javascript, JS ES6]
title: 'Arrow Notation, map() Method, and Template Literal Used to Generate Array of HTML Elements From Object'
created: '2019-12-08T02:44:19.077Z'
modified: '2021-02-09T20:02:35.452Z'
---

Arrow Notation, map() Method, and Template Literal Used to Generate Array of HTML Elements From Object
=======================================================================================================

``` javascript
const result = {
  success: ["max-length", "no-amd", "prefer-arrow-functions"],
  failure: ["no-var", "var-on-top", "linebreak"],
  skipped: ["id-blacklist", "no-dup-keys"]
};

function makeList(arr) {
  "use strict";
  const resultDisplayArray = arr.map(element => { 
    return `<li class="text-warning">${element}</li>`;
  });

  return resultDisplayArray;
}

const resultDisplayArray = makeList(result.failure);

```
