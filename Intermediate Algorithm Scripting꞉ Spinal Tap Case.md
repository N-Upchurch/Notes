---
tags: [Javascript, JS Algorithms]
title: 'Intermediate Algorithm Scripting: Spinal Tap Case'
created: '2020-01-06T06:03:22.121Z'
modified: '2021-02-09T20:01:38.004Z'
---

Intermediate Algorithm Scripting: Spinal Tap Case
=================================================

Convert a string to spinal case. Spinal case is all-lowercase-words-joined-by-dashes.

My Solution:
------------
``` javascript
function spinalCase(str) {
  return str.replace(/([a-z])([A-Z])/g,'$1-$2').replace(/\W|_/g, "-").toLowerCase();
}
```

Given Solution 1
----------------
``` javascript
function spinalCase(str) {
  // Create a variable for the white space and underscores.
  var regex = /\s+|_+/g;

  // Replace low-upper case to low-space-uppercase
  str = str.replace(/([a-z])([A-Z])/g, "$1 $2");

  // Replace space and underscore with -
  return str.replace(regex, "-").toLowerCase();
}
```
Given Solution 2
----------------
``` javascript
function spinalCase(str) {
  // Replace low-upper case to low-space-uppercase
  str = str.replace(/([a-z])([A-Z])/g, "$1 $2");
  // Split on whitespace and underscores and join with dash
  return str
    .toLowerCase()
    .split(/(?:_| )+/)
    .join("-");
}
```
Given Solution 3
----------------
``` javascript
function spinalCase(str) {
  return str
    .split(/\s|_|(?=[A-Z])/)
    .join("-")
    .toLowerCase();
}
```
