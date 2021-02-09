---
tags: [Javascript]
title: 'Regular Expressions: Match Beginning String Patterns'
created: '2019-12-09T06:30:33.407Z'
modified: '2021-02-09T20:00:08.510Z'
---

Regular Expressions: Match Beginning String Patterns
====================================================

Outside of a character set, the caret is used to search for patterns at the beginning of strings.
``` javascript
let firstString = "Ricky is first and can be found.";
let firstRegex = /^Ricky/;
firstRegex.test(firstString);
// Returns true
let notFirst = "You can't find Ricky now.";
firstRegex.test(notFirst);
// Returns false

```
