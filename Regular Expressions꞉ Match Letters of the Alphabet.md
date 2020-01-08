---
tags: [Code Snippets, Javascript, Regex]
title: 'Regular Expressions: Match Letters of the Alphabet'
created: '2019-12-09T06:03:44.945Z'
modified: '2019-12-09T06:04:22.657Z'
---

Regular Expressions: Match Letters of the Alphabet
==================================================

You saw how you can use character sets to specify a group of characters to match, but that's a lot of typing when you need to match a large range of characters (for example, every letter in the alphabet). Fortunately, there is a built-in feature that makes this short and simple.

Inside a character set, you can define a range of characters to match using a hyphen character: ```-```.

For example, to match lowercase letters a through e you would use ```[a-e]```.
``` javascript
let catStr = "cat";
let batStr = "bat";
let matStr = "mat";
let bgRegex = /[a-e]at/;
catStr.match(bgRegex); // Returns ["cat"]
batStr.match(bgRegex); // Returns ["bat"]
matStr.match(bgRegex); // Returns null

```
