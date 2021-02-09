---
tags: [Redux]
title: 'Redux: Send Action Data to the Store'
created: '2020-10-07T00:41:35.040Z'
modified: '2021-02-09T19:58:33.169Z'
---

Redux: Send Action Data to the Store
====================================

``` javascript
const ADD_NOTE = 'ADD_NOTE';

const notesReducer = (state = 'Initial State', action) => {
  switch(action.type) {
    case ADD_NOTE:
      return action.text;
    default:
      return state;
  }
};

const addNoteText = (note) => {
  return {
    type: ADD_NOTE,
    text: note
  }
};

const store = Redux.createStore(notesReducer);

console.log(store.getState());
store.dispatch(addNoteText('Hello!'));
console.log(store.getState());

```
