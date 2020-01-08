---
tags: [Code Snippets, Javascript, Regex]
title: 'Regular Expressions: Use Capture Groups to Search and Replace'
created: '2019-12-11T03:58:45.730Z'
modified: '2019-12-11T04:00:33.494Z'
---

Regular Expressions: Use Capture Groups to Search and Replace
=============================================================

Searching is useful. However, you can make searching even more powerful when it also changes (or replaces) the text you match.

You can search and replace text in a string using ```.replace()``` on a string. The inputs for .replace() is first the regex pattern you want to search for. The second parameter is the string to replace the match or a function to do something.
``` javascript
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue");
// Returns "The sky is blue."

```
You can also access capture groups in the replacement string with dollar signs (```$```).
``` javascript
"Code Camp".replace(/(\w+)\s(\w+)/, '$2 $1');
// Returns "Camp Code"

```
