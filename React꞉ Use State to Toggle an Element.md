---
tags: [Code Snippets, React]
title: 'React: Use State to Toggle an Element'
created: '2020-05-22T18:21:06.097Z'
modified: '2020-05-22T19:01:13.582Z'
---

React: Use State to Toggle an Element
=====================================

Sometimes you might need to know the previous state when updating the state. However, state updates may be asynchronous - this means React may batch multiple ```setState()``` calls into a single update. This means you can't rely on the previous value of ```this.state``` or ```this.props``` when calculating the next value. So, you should not use code like this:

``` javascript
// Do NOT do this
this.setState({
  counter: this.state.counter + this.props.increment
});
```
Instead, you should pass ```setState``` a function that allows you to access state and props. Using a function with ```setState``` guarantees you are working with the most current values of state and props. This means that the above should be rewritten as:

``` javascript
// Do this
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```
You can also use a form without props if you need only the state:

``` javascript
this.setState(state => ({
  counter: state.counter + 1
}));
```
Note that you have to wrap the object literal in parentheses, otherwise JavaScript thinks it's a block of code.

**Example:**
``` javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    // Bind THIS to method constructor
    this.toggleVisibility = this.toggleVisibility.bind(this);
  }
  toggleVisibility (){
    // Use function to enable access to STATE
    this.setState(state => {
      // Ternary operator did not work here
      if (state.visibility === true) {
        return {visibility: false}
      } else {
        return {visibility: true}
      }
    });
  }
  render() {
    // if truthy
    if (this.state.visibility) {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
          <h1>Now you see me!</h1>
        </div>
      );
    // if falsy
    } else {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
        </div>
      );
    }
  }
};
```
Using These Principles to Create a Simple Counter
-------------------------------------------------
``` javascript
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    // Bind THIS to method constructor
  this.increment = this.increment.bind(this);
  this.decrement = this.decrement.bind(this);
  this.reset = this.reset.bind(this);
  }
  increment() {
    this.setState(state => {
      return state.count += 1;
    })
  }
  decrement() {
    this.setState(state => {
      return state.count -= 1;
    })
  }
  reset() {
    this.setState(state => {
      return state.count = 0;
    })
  }
  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```
