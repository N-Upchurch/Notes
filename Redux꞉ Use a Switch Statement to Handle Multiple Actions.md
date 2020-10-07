---
tags: [Code Snippets, Redux]
title: 'Redux: Use a Switch Statement to Handle Multiple Actions'
created: '2020-10-07T00:04:03.709Z'
modified: '2020-10-07T00:10:50.059Z'
---

Redux: Use a Switch Statement to Handle Multiple Actions
========================================================

You can tell the Redux store how to handle multiple action types. Say you are managing user authentication in your Redux store. You want to have a state representation for when users are logged in and when they are logged out. You represent this with a single state object with the property `authenticated`. You also need action creators that create actions corresponding to user login and user logout, along with the action objects themselves.

``` javascript
const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {
  switch(action.type){
    case 'LOGIN':
      return {authenticated: true};
      break;
    case 'LOGOUT':
      return {authenticated: false};
      break;
    default: 
      return state;
  }
};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: 'LOGIN'
  }
};

const logoutUser = () => {
  return {
    type: 'LOGOUT'
  }
};
```
