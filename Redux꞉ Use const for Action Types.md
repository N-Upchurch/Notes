---
tags: [Redux]
title: 'Redux: Use const for Action Types'
created: '2020-10-07T00:21:25.757Z'
modified: '2021-02-09T19:58:33.282Z'
---

Redux: Use const for Action Types
=================================

A common practice when working with Redux is to assign action types as read-only constants, then reference these constants wherever they are used. You can refactor the code you're working with to write the action types as `const` declarations.

``` javascript 
const LOGIN = 'LOGIN';
const LOGOUT = 'LOGOUT'

const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {
  switch (action.type) {
    case LOGIN:
      return {
        authenticated: true
      }
    case LOGOUT:
      return {
        authenticated: false
      }
    default:
      return state
  }
};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: LOGIN
  }
};

const logoutUser = () => {
  return {
    type: LOGOUT
  }
};

```
