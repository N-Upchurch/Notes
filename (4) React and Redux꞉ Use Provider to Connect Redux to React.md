---
tags: [Redux]
title: '(4) React and Redux: Use Provider to Connect Redux to React'
created: '2020-10-10T01:39:20.850Z'
modified: '2020-10-10T01:47:38.587Z'
---

(4) React and Redux: Use Provider to Connect Redux to React
===========================================================

In the last challenge, you created a Redux store to handle the messages array and created an action for adding new messages. The next step is to provide React access to the Redux store and the actions it needs to dispatch updates. React Redux provides its `react-redux` package to help accomplish these tasks.

React Redux provides a small API with two key features: `Provider` and `connect`. Another challenge covers `connect`. The `Provider` is a wrapper component from React Redux that wraps your React app. This wrapper then allows you to access the Redux `store` and `dispatch` functions throughout your component tree. `Provider` takes two props, the Redux store and the child components of your app. Defining the `Provider` for an App component might look like this:

``` javascript
<Provider store={store}>
  <App/>
</Provider>
```

``` javascript
// Redux:
const ADD = 'ADD';

const addMessage = (message) => {
  return {
    type: ADD,
    message
  }
};

const messageReducer = (state = [], action) => {
  switch (action.type) {
    case ADD:
      return [
        ...state,
        action.message
      ];
    default:
      return state;
  }
};



const store = Redux.createStore(messageReducer);

// React:

class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
    this.handleChange = this.handleChange.bind(this);
    this.submitMessage = this.submitMessage.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  submitMessage() {  
    this.setState((state) => {
      const currentMessage = state.input;
      return {
        input: '',
        messages: state.messages.concat(currentMessage)
      };
    });
  }
  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        <input
          value={this.state.input}
          onChange={this.handleChange}/><br/>
        <button onClick={this.submitMessage}>Submit</button>
        <ul>
          {this.state.messages.map( (message, idx) => {
              return (
                 <li key={idx}>{message}</li>
              )
            })
          }
        </ul>
      </div>
    );
  }
};

const Provider = ReactRedux.Provider;

class AppWrapper extends React.Component {
  render() {
    return (
      <Provider store={store}>
        <DisplayMessages />
      </Provider>
    )
  }
};

```
