---
tags: [Javascript, JS Regex]
title: 'Regular Expressions: Match Single Characters Not Specified'
created: '2019-12-09T06:14:27.143Z'
modified: '2021-02-09T20:00:23.348Z'
---

Regular Expressions: Match Single Characters Not Specified
==========================================================

You can also create a set of characters that you do not want to match. These types of character sets are called negated character sets.

To create a negated character set, you place a caret character (```^```) after the opening bracket and before the characters you do not want to match.

For example, ```/[^aeiou]/gi``` matches all characters that are not a vowel. Note that characters like ```.```, ```!```, ```[```, ```@```, ```/``` and white space are matched - the negated vowel character set only excludes the vowel characters.
