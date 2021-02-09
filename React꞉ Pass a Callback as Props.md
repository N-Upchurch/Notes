---
tags: [React]
title: 'React: Pass a Callback as Props'
created: '2020-08-30T03:09:53.471Z'
modified: '2021-02-09T19:58:31.780Z'
---

React: Pass a Callback as Props
===============================

You can pass ```state``` as props to child components, but you're not limited to passing data. You can also pass handler functions or any method that's defined on a React component to a child component. This is how you allow child components to interact with their parent components. You pass methods to a child just like a regular prop. It's assigned a name and you have access to that method name under ```this.props``` in the child component.

``` javascript
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        <GetInput input={this.state.inputValue} handleChange={this.handleChange} />
        <RenderInput input={this.state.inputValue} />
       </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input
          value={this.props.input}
          onChange={this.props.handleChange}/>
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```

*There are three components outlined above. The ```MyApp``` component is the parent that will render the ```GetInput``` and ```RenderInput``` child components. The ```GetInput``` component is added to the render method in ```MyApp```, then passed a prop called ```input``` assigned to ```inputValue``` from ```MyApp```'s state. A prop called ```handleChange``` is passed the input handler ```handleChange```.```RenderInput``` is added to the render method in ```MyApp```, then a prop called ```input``` is passed the ```inputValue``` from state. This enables you to type in the input field in the ```GetInput``` component, which then calls the handler method in its parent via ```props```. This updates the input in the state of the parent, which is passed as ```props``` to both children. Observe how the data flows between the components and how the single source of truth remains the state of the parent component. Admittedly, this example is a bit contrived, but should serve to illustrate how data and callbacks can be passed between React components.*
