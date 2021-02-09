---
tags: [React]
title: 'React: Create a Controlled Input'
created: '2020-06-12T03:44:45.073Z'
modified: '2021-02-09T19:58:31.572Z'
---

React: Create a Controlled Input
================================

Your application may have more complex interactions between ```state``` and the rendered UI. For example, form control elements for text input, such as ```input``` and ```textarea```, maintain their own state in the DOM as the user types. With React, you can move this mutable state into a React component's ```state```. The user's input becomes part of the application ```state```, so React controls the value of that input field. Typically, if you have React components with input fields the user can type into, it will be a controlled input form.

**Example:**

``` javascript
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
     this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  render() {
    return (
      <div>
        <input type="text" value={this.state.input} onChange={this.handleChange}></input>
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```
* Bind ```this``` in object constructor
* ```handleChange()``` takes ```event``` value and assigns to input ```state```
* Input value set to component input state
* ```onChange``` event handler calls ```handleChange```
* Component ```state``` is single source of truth regarding input data
