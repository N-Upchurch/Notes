---
tags: [Code Snippets, Javascript, Regex]
title: 'Regular Expressions: Match Single Character with Multiple Possibilities'
created: '2019-12-09T05:59:57.695Z'
modified: '2019-12-09T06:01:35.030Z'
---

Regular Expressions: Match Single Character with Multiple Possibilities
=======================================================================

You can search for a literal pattern with some flexibility with character classes. Character classes allow you to define a group of characters you wish to match by placing them inside square (```[``` and ```]```) brackets.

For example, you want to match "bag", "big", and "bug" but not "bog". You can create the regex ```/b[aiu]g/``` to do this. The ```[aiu]``` is the character class that will only match the characters "a", "i", or "u".
``` javascript
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex); // Returns ["big"]
bagStr.match(bgRegex); // Returns ["bag"]
bugStr.match(bgRegex); // Returns ["bug"]
bogStr.match(bgRegex); // Returns null

```
