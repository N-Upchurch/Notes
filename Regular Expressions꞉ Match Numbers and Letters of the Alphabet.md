---
tags: [Javascript, JS Regex]
title: 'Regular Expressions: Match Numbers and Letters of the Alphabet'
created: '2019-12-09T06:11:02.558Z'
modified: '2021-02-09T20:00:23.262Z'
---

Regular Expressions: Match Numbers and Letters of the Alphabet
==============================================================

Using the hyphen (```-```) to match a range of characters is not limited to letters. It also works to match a range of numbers.

For example, ```/[0-5]/``` matches any number between 0 and 5, including the 0 and 5.

Also, it is possible to combine a range of letters and numbers in a single character set.
``` javascript
let jennyStr = "Jenny8675309";
let myRegex = /[a-z0-9]/ig;
// matches all letters and numbers in jennyStr
jennyStr.match(myRegex);

```
