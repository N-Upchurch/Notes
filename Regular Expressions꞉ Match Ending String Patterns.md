---
tags: [Javascript, JS Regex]
title: 'Regular Expressions: Match Ending String Patterns'
created: '2019-12-09T06:33:09.889Z'
modified: '2021-02-09T20:00:23.104Z'
---

Regular Expressions: Match Ending String Patterns
=================================================

You can search the end of strings using the dollar sign character $ at the end of the regex.
``` javascript
let theEnding = "This is a never ending story";
let storyRegex = /story$/;
storyRegex.test(theEnding);
// Returns true
let noEnding = "Sometimes a story will have to end";
storyRegex.test(noEnding);
// Returns false

```
