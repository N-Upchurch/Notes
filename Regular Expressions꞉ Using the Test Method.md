---
tags: [Javascript, JS Regex]
title: 'Regular Expressions: Using the Test Method'
created: '2019-12-09T05:38:46.908Z'
modified: '2021-02-09T20:00:23.568Z'
---

Regular Expressions: Using the Test Method
==========================================

Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

If you want to find the word "the" in the string "The dog chased the cat", you could use the following regular expression: /the/. Notice that quote marks are not required within the regular expression.

JavaScript has multiple ways to use regexes. One way to test a regex is using the .test() method. The .test() method takes the regex, applies it to a string (which is placed inside the parentheses), and returns true or false if your pattern finds something or not.
``` test
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr);
// Returns true

```
