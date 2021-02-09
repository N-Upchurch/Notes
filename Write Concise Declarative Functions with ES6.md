---
tags: [Javascript, JS ES6]
title: Write Concise Declarative Functions with ES6
created: '2019-12-08T02:42:58.702Z'
modified: '2021-02-09T20:02:36.819Z'
---

Write Concise Declarative Functions with ES6
============================================

When defining functions within objects in ES5, we have to use the keyword function as follows:
``` javascript
const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};
```
With ES6, You can remove the function keyword and colon altogether when defining functions in objects. Here's an example of this syntax:
``` javascript
const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};
```
