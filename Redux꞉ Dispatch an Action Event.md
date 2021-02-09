---
tags: [Redux]
title: 'Redux: Dispatch an Action Event'
created: '2020-10-06T23:46:09.165Z'
modified: '2021-02-09T19:58:32.810Z'
---

Redux: Dispatch an Action Event
===============================

`dispatch` method is what you use to dispatch actions to the Redux store. Calling `store.dispatch()` and passing the value returned from an action creator sends an action back to the store.

Recall that action creators return an object with a type property that specifies the action that has occurred. Then the method dispatches an action object to the Redux store. Based on the previous challenge's example, the following lines are equivalent, and both dispatch the action of type `LOGIN`:

``` javascript
store.dispatch(actionCreator());
store.dispatch({ type: 'LOGIN' });
```

``` javascript
const store = Redux.createStore(
  (state = {login: false}) => state
);

const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};

// Dispatch the action here:
store.dispatch(loginAction());
```

