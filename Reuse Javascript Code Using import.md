---
tags: [Code Snippets, ES6, Javascript]
title: Reuse Javascript Code Using import
created: '2019-12-08T05:00:09.948Z'
modified: '2019-12-08T05:00:49.626Z'
---

Reuse Javascript Code Using import
==================================

import allows you to choose which parts of a file or module to load. In the previous lesson, the examples exported add from the math_functions.js file. Here's how you can import it to use in another file:
``` javascript
import { add } from './math_functions.js';

```
Here, import will find add in math_functions.js, import just that function for you to use, and ignore the rest. The ./ tells the import to look for the math_functions.js file in the same folder as the current file. The relative file path (./) and file extension (.js) are required when using import in this way.

You can import more than one item from the file by adding them in the import statement like this:
``` javascript
import { add, subtract } from './math_functions.js';

```
