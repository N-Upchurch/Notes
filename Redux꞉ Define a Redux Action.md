---
tags: [Redux]
title: 'Redux: Define a Redux Action'
created: '2020-10-06T02:52:08.093Z'
modified: '2021-02-09T19:58:32.701Z'
---

Redux: Define a Redux Action
============================

Since Redux is a state management framework, updating state is one of its core tasks. In Redux, all state updates are triggered by dispatching actions. An action is simply a JavaScript object that contains information about an action event that has occurred. The Redux store receives these action objects, then updates its state accordingly. Sometimes a Redux action also carries some data. For example, the action carries a username after a user logs in. While the data is optional, actions must carry a `type` property that specifies the 'type' of action that occurred.

Think of Redux actions as messengers that deliver information about events happening in your app to the Redux store. The store then conducts the business of updating state based on the action that occurred.

``` javascript
const action = {type: 'LOGIN'};
```
