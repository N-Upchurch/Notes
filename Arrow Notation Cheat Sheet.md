---
tags: [Cheat Sheets, Javascript]
title: Arrow Notation Cheat Sheet
created: '2019-12-19T20:37:18.842Z'
modified: '2021-02-09T19:58:55.792Z'
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
