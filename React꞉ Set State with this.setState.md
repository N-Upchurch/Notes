---
tags: [React]
title: 'React: Set State with this.setState'
created: '2020-05-12T18:59:30.774Z'
modified: '2021-02-09T19:58:32.112Z'
---

React: Set State with this.setState
===================================

There is also a way to change the component's ```state```. React provides a method for updating component ```state``` called ```setState```. You call the ```setState``` method within your component class like so: ```this.setState()```, passing in an object with key-value pairs. The keys are your state properties and the values are the updated state data. For instance, if we were storing a ```username``` in state and wanted to update it, it would look like this:
``` javascript
this.setState({
  username: 'Lewis'
});

```
React expects you to never modify ```state``` directly, instead always use ```this.setState()``` when state changes occur. Also, you should note that React may batch multiple state updates in order to improve performance. What this means is that state updates through the ```setState``` method can be asynchronous. There is an alternative syntax for the ```setState``` method which provides a way around this problem. This is rarely needed but it's good to keep it in mind! Please consult the React documentation for further details.

### Another Example: 
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
