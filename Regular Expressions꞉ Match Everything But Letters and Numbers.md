---
tags: [Javascript, JS Regex]
title: 'Regular Expressions: Match Everything But Letters and Numbers'
created: '2019-12-09T14:50:33.347Z'
modified: '2021-02-09T20:00:23.158Z'
---

Regular Expressions: Match Everything But Letters and Numbers
=============================================================

You've learned that you can use a shortcut to match alphanumerics [A-Za-z0-9_] using \w. A natural pattern you might want to search for is the opposite of alphanumerics.

You can search for the opposite of the \w with \W. Note, the opposite pattern uses a capital letter. This shortcut is the same as ```[^A-Za-z0-9_]```.
``` javascript
let shortHand = /\W/;
let numbers = "42%";
let sentence = "Coding!";
numbers.match(shortHand); // Returns ["%"]
sentence.match(shortHand); // Returns ["!"]

```
