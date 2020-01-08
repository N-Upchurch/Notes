---
tags: [Code Snippets, Javascript, Regex]
title: 'Regular Expressions: Find More Than the First Match'
created: '2019-12-09T05:50:04.495Z'
modified: '2019-12-09T05:50:59.080Z'
---

Regular Expressions: Find More Than the First Match
===================================================

So far, you have only been able to extract or search a pattern once.
``` javascript
let testStr = "Repeat, Repeat, Repeat";
let ourRegex = /Repeat/;
testStr.match(ourRegex);
// Returns ["Repeat"]

```
To search or extract a pattern more than once, you can use the g flag.
``` javascript
let repeatRegex = /Repeat/g;
testStr.match(repeatRegex);
// Returns ["Repeat", "Repeat", "Repeat"]

```
**Note:**
You can have multiple flags on your regex like /search/gi
