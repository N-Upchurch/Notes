---
tags: [Code Snippets, Javascript, Regex]
title: 'Regular Expressions: Match Anything with Wildcard Period'
created: '2019-12-09T05:54:18.537Z'
modified: '2019-12-09T05:55:41.513Z'
---

Regular Expressions: Match Anything with Wildcard Period
========================================================

Sometimes you won't (or don't need to) know the exact characters in your patterns. Thinking of all words that match, say, a misspelling would take a long time. Luckily, you can save time using the wildcard character: ```.```

The wildcard character . will match any one character. The wildcard is also called dot and period. You can use the wildcard character just like any other character in the regex. For example, if you wanted to match "hug", "huh", "hut", and "hum", you can use the regex ```/hu./``` to match all four words.
``` javascript
let humStr = "I'll hum a song";
let hugStr = "Bear hug";
let huRegex = /hu./;
huRegex.test(humStr); // Returns true
huRegex.test(hugStr); // Returns true

```
