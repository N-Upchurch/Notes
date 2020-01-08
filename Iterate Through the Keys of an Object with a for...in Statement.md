---
tags: [Code Snippets, Javascript]
title: Iterate Through the Keys of an Object with a for...in Statement
created: '2019-12-11T06:48:00.660Z'
modified: '2019-12-11T06:48:32.554Z'
---

Iterate Through the Keys of an Object with a for...in Statement
===============================================================

Sometimes you may need to iterate through all the keys within an object. This requires a specific syntax in JavaScript called a for...in statement. For our users object, this could look like:
``` javascript
for (let user in users) {
  console.log(user);
}

// logs:
Alan
Jeff
Sarah
Ryan

```
In this statement, we defined a variable user, and as you can see, this variable was reset during each iteration to each of the object's keys as the statement looped through the object, resulting in each user's name being printed to the console. NOTE: Objects do not maintain an ordering to stored keys like arrays do; thus a key's position on an object, or the relative order in which it appears, is irrelevant when referencing or accessing that key.

