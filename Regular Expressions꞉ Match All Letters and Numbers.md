---
tags: [Javascript]
title: 'Regular Expressions: Match All Letters and Numbers'
created: '2019-12-09T14:47:39.398Z'
modified: '2021-02-09T20:00:08.264Z'
---

Regular Expressions: Match All Letters and Numbers
==================================================

Using character classes, you were able to search for all letters of the alphabet with [a-z]. This kind of character class is common enough that there is a shortcut for it, although it includes a few extra characters as well.

The closest character class in JavaScript to match the alphabet is ```\w```. This shortcut is equal to ```[A-Za-z0-9_]```. This character class matches upper and lowercase letters plus numbers. Note, this character class also includes the underscore character (```_```).
``` javascript
let longHand = /[A-Za-z0-9_]+/;
let shortHand = /\w+/;
let numbers = "42";
let varNames = "important_var";
longHand.test(numbers); // Returns true
shortHand.test(numbers); // Returns true
longHand.test(varNames); // Returns true
shortHand.test(varNames); // Returns true

```
These shortcut character classes are also known as shorthand character classes.

