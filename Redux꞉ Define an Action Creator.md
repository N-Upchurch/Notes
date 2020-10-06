---
tags: [Code Snippets, Redux]
title: 'Redux: Define an Action Creator'
created: '2020-10-06T02:56:59.420Z'
modified: '2020-10-06T02:57:23.980Z'
---

Redux: Define an Action Creator
===============================

After creating an action, the next step is sending the action to the Redux store so it can update its state. In Redux, you define action creators to accomplish this. An action creator is simply a JavaScript function that returns an action. In other words, action creators create objects that represent action events.

``` javascript
const action = {
  type: 'LOGIN'
}
// Define an action creator here:
const actionCreator = () => action;
```
