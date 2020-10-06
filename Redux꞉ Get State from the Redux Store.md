---
tags: [Code Snippets, Redux]
title: 'Redux: Get State from the Redux Store'
created: '2020-10-06T02:50:12.514Z'
modified: '2020-10-06T02:51:00.078Z'
---

Redux: Get State from the Redux Store
=====================================

The Redux store object provides several methods that allow you to interact with it. For example, you can retrieve the current `state` held in the Redux store object with the `getState()` method.

``` javascript
const store = Redux.createStore(
  (state = 5) => state
);

let currentState = store.getState();
```
