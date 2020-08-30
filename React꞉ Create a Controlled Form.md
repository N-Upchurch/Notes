---
tags: [Code Snippets, React]
title: 'React: Create a Controlled Form'
created: '2020-08-23T01:32:04.938Z'
modified: '2020-08-23T01:33:23.228Z'
---

React: Create a Controlled Form
===============================
React can control the internal state for certain elements like ```input``` and ```textarea```, which makes them controlled components. This applies to other form elements as well, including the regular HTML ```form``` element.
``` javascript
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: ''
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  handleSubmit(event) {
    // Prevents normal submit behavior (page reload)
    event.preventDefault()
    this.setState({
      submit: this.state.input
    });
  }
  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          <input value={this.state.input} onChange={this.handleChange} />
          <button type='submit'>Submit!</button>
        </form>
        <h1>{this.state.submit}</h1>
      </div>
    );
  }
};

```
