---
tags: [React]
title: 'React: Use the Lifecycle Method componentDidMount'
created: '2020-08-30T23:53:18.305Z'
modified: '2021-02-09T19:58:32.431Z'
---

React: Use the Lifecycle Method componentDidMount
=================================================

Most web developers, at some point, need to call an API endpoint to retrieve data. If you're working with React, it's important to know where to perform this action.

The best practice with React is to place API calls or any calls to your server in the lifecycle method ```componentDidMount()```. This method is called after a component is mounted to the DOM. Any calls to ```setState()``` here will trigger a re-rendering of your component. When you call an API in this method, and set your state with the data that the API returns, it will automatically trigger an update once you receive the data.

There is a mock API call in ```componentDidMount()``` below. It sets state after 2.5 seconds to simulate calling a server to retrieve data. This example requests the current total active users for a site. In the render method, the value of ```activeUsers``` is rendered in the ```h1```.

``` javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      activeUsers: null
    };
  }
  componentDidMount() {
    setTimeout( () => {
      this.setState({
        activeUsers: 1273
      });
    }, 2500);
  }
  render() {
    return (
      <div>
        <h1>Active Users: {this.state.activeUsers}</h1>
      </div>
    );
  }
};
```
