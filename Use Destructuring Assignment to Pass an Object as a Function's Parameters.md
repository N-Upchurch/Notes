---
tags: [Javascript, JS ES6]
title: Use Destructuring Assignment to Pass an Object as a Function's Parameters
created: '2019-12-08T02:45:59.035Z'
modified: '2021-02-09T20:02:36.515Z'
---

Use Destructuring Assignment to Pass an Object as a Function's Parameters
============================================================================

In some cases, you can destructure the object in a function argument itself.

Consider the code below:
``` javascript
const profileUpdate = (profileData) => {
  const { name, age, nationality, location } = profileData;
  // do something with these variables
}
```
This effectively destructures the object sent into the function. This can also be done in-place:
``` javascript
const profileUpdate = ({ name, age, nationality, location }) => {
  /* do something with these fields */
}
```
This removes some extra lines and makes our code look neat. This has the added benefit of not having to manipulate an entire object in a function — only the fields that are needed are copied inside the function.

