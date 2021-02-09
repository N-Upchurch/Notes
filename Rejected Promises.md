---
tags: [Javascript, JS ES6]
title: Handle Fulfilled / Rejected Promises
created: '2019-12-09T05:25:28.362Z'
modified: '2021-02-09T20:02:36.019Z'
---

Handle Fulfilled  / Rejected Promises
=====================================

then()
------
Promises are most useful when you have a process that takes an unknown amount of time in your code (i.e. something asynchronous), often a server request. When you make a server request it takes some amount of time, and after it completes you usually want to do something with the response from the server. This can be achieved by using the then method. The then method is executed immediately after your promise is fulfilled with resolve. Here’s an example:
``` javascript
myPromise.then(result => {
  // do something with the result.
});

```
result comes from the argument given to the resolve method.

catch()
-------
catch is the method used when your promise has been rejected. It is executed immediately after a promise's reject method is called. Here’s the syntax:
``` javascript
myPromise.catch(error => {
  // do something with the error.
});

```
error is the argument passed in to the reject method.

**Note:** 
The then and catch methods can be chained to the promise declaration if you choose.
