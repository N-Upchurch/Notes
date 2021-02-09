---
tags: [Javascript, JS Regex]
title: 'Regular Expressions: Match Characters that Occur Zero or More Times'
created: '2019-12-09T06:20:57.783Z'
modified: '2021-02-09T20:00:22.999Z'
---

Regular Expressions: Match Characters that Occur Zero or More Times
===================================================================

There's also an option that matches characters that occur zero or more times.

The character to do this is the asterisk or star: ```*```.
``` javascript
let soccerWord = "gooooooooal!";
let gPhrase = "gut feeling";
let oPhrase = "over the moon";
let goRegex = /go*/;
soccerWord.match(goRegex); // Returns ["goooooooo"]
gPhrase.match(goRegex); // Returns ["g"]
oPhrase.match(goRegex); // Returns null


```
