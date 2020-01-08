---
tags: [Cheat Sheet, Code Snippets, Javascript]
title: Arrow Notation Cheat Sheet
created: '2019-12-19T20:37:18.842Z'
modified: '2019-12-19T20:41:45.630Z'
---

Arrow Notation Cheat Sheet
==========================

Normal
------

```(parameters) => { statements }```

When you have no parameters:
----------------------------

```() => { statements }```

When you have only one parameter (parenthesis optional)
-------------------------------------------------------

```parameters => { statements }```

When returning an expression
----------------------------
```
parameters => expression

// is equivalent to:

function (parameters){
  return expression;
}
```
