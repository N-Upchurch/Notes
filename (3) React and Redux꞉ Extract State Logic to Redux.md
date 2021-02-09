---
tags: [React, Redux]
title: '(3) React and Redux: Extract State Logic to Redux'
created: '2020-10-10T01:05:44.922Z'
modified: '2021-02-09T19:58:28.687Z'
---

(3) React and Redux: Extract State Logic to Redux
=================================================

Now that you finished the React component, you need to move the logic it's performing locally in its `state` into Redux. This is the first step to connect the simple React app to Redux. The only functionality your app has is to add new messages from the user to an unordered list. The example is simple in order to demonstrate how React and Redux work together.

``` javascript 
// Action type
const ADD = 'ADD';

// Action Creator
const addMessage = (message) => {return {type: ADD, message}};

// Reducer
const messageReducer = (state = [], action) => {
    switch(action.type) {
        case ADD:
            return [...state, action.message];
        default:
            return state;
    }
}

// Redux Store
const store = Redux.createStore(messageReducer);
```
