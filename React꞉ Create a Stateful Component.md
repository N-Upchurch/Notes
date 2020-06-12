---
tags: [Code Snippets, React]
title: 'React: Create a Stateful Component'
created: '2020-05-12T01:38:20.317Z'
modified: '2020-05-12T01:44:09.368Z'
---

React: Create a Stateful Component
==================================

One of the most important topics in React is ```state```. State consists of any data your application needs to know about, that can change over time. You want your apps to respond to state changes and present an updated UI when necessary. React offers a nice solution for the state management of modern web applications.

You create state in a React component by declaring a ```state``` property on the component class in its ```constructor```. This initializes the component with ```state``` when it is created. The ```state``` property must be set to a JavaScript object. Declaring it looks like this:
``` javascript
this.state = {
  // describe your state here
}
```
You have access to the ```state``` object throughout the life of your component. You can update it, render it in your UI, and pass it as props to child components. The ```state``` object can be as complex or as simple as you need it to be. Note that you must create a class component by extending ```React.Component``` in order to create ```state``` like this.

**Another Example:**
``` javascript
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    // initialize state here
    this.state = {
      name: "Nathan"
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```
