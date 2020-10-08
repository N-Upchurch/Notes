---
tags: [Code Snippets, Redux]
title: 'Redux: Write a Counter with Redux'
created: '2020-10-08T02:31:56.455Z'
modified: '2020-10-08T02:32:31.231Z'
---

Redux: Write a Counter with Redux
=================================

``` javascript
// define constants for increment action types
const INCREMENT = 'INCREMENT'; 
const DECREMENT = 'DECREMENT';

// define the counter reducer which will increment or decrement the state based on the action it receives
const counterReducer = (state = 0, action) => {
  switch(action.type) {
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
};

// define an action creator for incrementing
const incAction = () => {return {type: INCREMENT}};

// define an action creator for decrementing
const decAction = () => {return {type: DECREMENT}}; 

// define the Redux store here, passing in your reducers
const store = Redux.createStore(counterReducer); 

```
