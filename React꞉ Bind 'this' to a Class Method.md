---
tags: [React]
title: 'React: Bind ''this'' to a Class Method'
created: '2020-05-21T18:48:40.044Z'
modified: '2021-02-09T19:58:31.397Z'
---

React: Bind 'this' to a Class Method
====================================

In addition to setting and updating ```state```, you can also define methods for your component class. A class method typically needs to use the ```this``` keyword so it can access properties on the class (such as ```state``` and ```props```) inside the scope of the method. There are a few ways to allow your class methods to access ```this```.

One common way is to explicitly bind ```this``` in the constructor so ```this``` becomes bound to the class methods when the component is initialized. As an example, in the below code, ```this.handleClick = this.handleClick.bind(this)``` is used for the ``handleClick`` method in the constructor. By doing this, when you call a function like ```this.setState()``` within your class method, ```this``` refers to the class and will not be ```undefined```.

``` javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      name: "React Rocks!"
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};

```
