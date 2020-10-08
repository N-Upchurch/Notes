---
tags: [Code Snippets, Redux]
title: 'Redux: Never Mutate State'
created: '2020-10-08T02:41:11.906Z'
modified: '2020-10-08T02:43:13.236Z'
---

Redux: Never Mutate State
=========================

Immutable state means that you never modify state directly, instead, you return a new copy of state.

If you took a snapshot of the state of a Redux app over time, you would see something like `state 1`, `state 2`, `state 3`,`state 4`, `...` and so on where each state may be similar to the last, but each is a distinct piece of data. This immutability, in fact, is what provides such features as time-travel debugging that you may have heard about.

Redux does not actively enforce state immutability in its store or reducers, that responsibility falls on the programmer. Fortunately, JavaScript (especially ES6) provides several useful tools you can use to enforce the immutability of your state, whether it is a `string`, `number`, `array`, or `object`. Note that strings and numbers are primitive values and are immutable by nature. In other words, 3 is always 3. You cannot change the value of the number 3. An `array` or `object`, however, is mutable. In practice, your state will probably consist of an `array` or `object`, as these are useful data structures for representing many types of information.

``` javascript
const ADD_TO_DO = 'ADD_TO_DO';

// A list of strings representing tasks to do:
const todos = [
  'Go to the store',
  'Clean the house',
  'Cook dinner',
  'Learn to code',
];

// The concat() method returns a new array:
const immutableReducer = (state = todos, action) => {
  switch(action.type) {
    case ADD_TO_DO:
      return state.concat(action.todo);
    default:
      return state;
  }
};

// an example todo argument would be 'Learn React',
const addToDo = (todo) => {
  return {
    type: ADD_TO_DO,
    todo
  }
}

const store = Redux.createStore(immutableReducer);

```
