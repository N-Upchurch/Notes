---
tags: [JSX, React]
title: 'React: Render HTML Elements to the DOM'
created: '2020-05-10T22:07:38.698Z'
modified: '2021-02-09T19:58:31.940Z'
---

React: Render HTML Elements to the DOM
======================================

So far, you've learned that JSX is a convenient tool to write readable HTML within JavaScript. With React, we can render this JSX directly to the HTML DOM using React's rendering API known as ReactDOM.

ReactDOM offers a simple method to render React elements to the DOM which looks like this: ```ReactDOM.render(componentToRender, targetNode)```, where the first argument is the React element or component that you want to render, and the second argument is the DOM node that you want to render the component to.

As you would expect, ```ReactDOM.render()``` must be called after the JSX element declarations, just like how you must declare variables before using them.

Example:
--------
``` javascript
// JSX
const JSX = (
  <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);

// Render to the DOM
ReactDOM.render(JSX, document.getElementById("node-id"))
```
