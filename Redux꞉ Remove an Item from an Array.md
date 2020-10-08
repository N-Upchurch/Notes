---
tags: [Code Snippets, Redux]
title: 'Redux: Remove an Item from an Array'
created: '2020-10-08T02:57:34.102Z'
modified: '2020-10-08T02:58:20.613Z'
---

Redux: Remove an Item from an Array
==================================

``` javascript
const immutableReducer = (state = [0,1,2,3,4,5], action) => {
  switch(action.type) {
    case 'REMOVE_ITEM':
      // filter() will return a new array
      return state.filter(x => x != state[action.index])
    default:
      return state;
  }
};

const removeItem = (index) => {
  return {
    type: 'REMOVE_ITEM',
    index
  }
}

const store = Redux.createStore(immutableReducer);
```
