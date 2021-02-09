---
tags: [React, Redux]
title: '(2) React and Redux: Manage State Locally First'
created: '2020-10-08T23:53:33.612Z'
modified: '2021-02-09T19:58:28.603Z'
---

(2) React and Redux: Manage State Locally First
===============================================

Here you'll finish creating the DisplayMessages component.

First, in the `render()` method, have the component render an `input` element, `button` element, and `ul` element. When the `input` element changes, it should trigger a `handleChange()` method. Also, the `input` element should render the value of `input` that's in the component's state. The `button` element should trigger a `submitMessage()` method when it's clicked.

Second, write these two methods. The `handleChange()` method should update the input with what the user is typing. The `submitMessage()` method should concatenate the current message (stored in `input`) to the `messages` array in local state, and clear the value of the `input`.

Finally, use the `ul` to map over the array of `messages` and render it to the screen as a list of `li` elements.

``` javascript
class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
  }

  handleChange(event) {
    this.setState({
      input: event.target.value,
      messages: this.state.messages
    });
  }

  submitMessage() {
    this.setState({
      input: '',
      messages: [...this.state.messages,this.state.input]
    });
  }
  
  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        <input value={this.state.input} onChange={this.handleChange.bind(this)} />
        <button onClick={this.submitMessage.bind(this)}>Add message</button>
        <ul>{this.state.messages.map((x)=>{
          return <li key={x+1}>{x}</li>})}</ul>
      </div>
    );
  }
};
```
