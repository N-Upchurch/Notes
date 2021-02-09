---
tags: [Javascript, JS ES6]
title: Import a Default Export
created: '2019-12-09T05:04:15.506Z'
modified: '2021-02-09T20:02:36.144Z'
---

Import a Default Export
=======================

To import a default export, you need to use a different import syntax. In the following example, add is the default export of the math_functions.js file. Here is how to import it:
``` javascript
import add from "./math_functions.js";

```
The syntax differs in one key place. The imported value, add, is not surrounded by curly braces ({}). add here is simply a variable name for whatever the default export of the math_functions.js file is. You can use any name here when importing a default.
