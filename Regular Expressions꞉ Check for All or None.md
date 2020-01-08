---
tags: [Code Snippets, Javascript, Regex]
title: 'Regular Expressions: Check for All or None'
created: '2019-12-10T03:25:47.814Z'
modified: '2019-12-10T03:26:12.497Z'
---

Regular Expressions: Check for All or None
==========================================

Sometimes the patterns you want to search for may have parts of it that may or may not exist. However, it may be important to check for them nonetheless.

You can specify the possible existence of an element with a question mark, ?. This checks for zero or one of the preceding element. You can think of this symbol as saying the previous element is optional.

For example, there are slight differences in American and British English and you can use the question mark to match both spellings.
``` javascript
let american = "color";
let british = "colour";
let rainbowRegex= /colou?r/;
rainbowRegex.test(american); // Returns true
rainbowRegex.test(british); // Returns true

```
