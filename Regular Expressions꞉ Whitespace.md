---
tags: [Code Snippets, Javascript, Regex]
title: 'Regular Expressions: Whitespace'
created: '2019-12-10T01:56:08.416Z'
modified: '2019-12-10T03:12:39.617Z'
---

Regular Expressions: Whitespace
=====================================

Match Whitespace Characters
--------------------------------

You can search for whitespace using \s, which is a lowercase s. This pattern not only matches whitespace, but also carriage return, tab, form feed, and new line characters. You can think of it as similar to the character class ```[ \r\t\f\n\v]```.
``` javascript
let whiteSpace = "Whitespace. Whitespace everywhere!"
let spaceRegex = /\s/g;
whiteSpace.match(spaceRegex);
// Returns [" ", " "]

```

Match Non-Whitespace Characters
--------------------------------

Search for non-whitespace using ```\S```, which is an uppercase s. This pattern will not match whitespace, carriage return, tab, form feed, and new line characters. You can think of it being similar to the character class ```[^ \r\t\f\n\v]```.
``` javascript
let whiteSpace = "Whitespace. Whitespace everywhere!"
let nonSpaceRegex = /\S/g;
whiteSpace.match(nonSpaceRegex).length; // Returns 32

```
