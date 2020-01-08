---
tags: [Code Snippets, ES6, Javascript]
title: Copy an Array with the Spread Operator
created: '2019-12-11T05:32:16.620Z'
modified: '2019-12-11T05:32:45.085Z'
---

Copy an Array with the Spread Operator
======================================

While ```slice()``` allows us to be selective about what elements of an array to copy, among several other useful tasks, ES6's new spread operator allows us to easily copy all of an array's elements, in order, with a simple and highly readable syntax. The spread syntax simply looks like this: ```...```

In practice, we can use the spread operator to copy an array like so:
``` javascript
let thisArray = [true, true, undefined, false, null];
let thatArray = [...thisArray];
// thatArray equals [true, true, undefined, false, null]
// thisArray remains unchanged, and is identical to thatArray

```
