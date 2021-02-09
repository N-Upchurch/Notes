---
tags: [Javascript, JS ES6]
title: Create an Export Fallback with export default
created: '2019-12-09T04:58:59.549Z'
modified: '2021-02-09T20:02:35.760Z'
---

Create an Export Fallback with export default
=============================================

There is another export syntax you need to know, known as export default. Usually you will use this syntax if only one value is being exported from a file. It is also used to create a fallback value for a file or module.

Below are examples using export default:
``` javascript
// named function
export default function add(x, y) {
  return x + y;
}

// anonymous function
export default function(x, y) {
  return x + y;
}
```
Since export default is used to declare a fallback value for a module or file, you can only have one value be a default export in each module or file. Additionally, you cannot use export default with var, let, or const
Create an Export Fallback with export default
