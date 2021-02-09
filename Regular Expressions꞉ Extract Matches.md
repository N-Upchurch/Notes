---
tags: [Javascript]
title: 'Regular Expressions: Extract Matches'
created: '2019-12-09T05:47:30.979Z'
modified: '2021-02-09T20:00:07.988Z'
---

Regular Expressions: Extract Matches
====================================

So far, you have only been checking if a pattern exists or not within a string. You can also extract the actual matches you found with the .match() method.

To use the .match() method, apply the method on a string and pass in the regex inside the parentheses. Here's an example:
``` javascript
"Hello, World!".match(/Hello/);
// Returns ["Hello"]
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
// Returns ["expressions"]

```
