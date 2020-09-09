---
tags: [Code Snippets, React]
title: 'React: Add Event Listeners'
<<<<<<< HEAD
created: '2020-09-09T04:02:16.899Z'
modified: '2020-09-09T04:05:20.323Z'
---

React: Add Event Listeners
================================
=======
created: '2020-09-04T05:21:41.809Z'
modified: '2020-09-04T05:24:37.308Z'
---

React: Add Event Listeners
==========================
>>>>>>> 8e619261639157f040c478e299c124c47716f65d

The ```componentDidMount()``` method is also the best place to attach any event listeners you need to add for specific functionality. React provides a synthetic event system which wraps the native event system present in browsers. This means that the synthetic event system behaves exactly the same regardless of the user's browser - even if the native events may behave differently between different browsers.

You've already been using some of these synthetic event handlers such as ```onClick()```. React's synthetic event system is great to use for most interactions you'll manage on DOM elements. However, if you want to attach an event handler to the document or window objects, you have to do this directly.

<<<<<<< HEAD
``` javascript
=======
``` Javascript
>>>>>>> 8e619261639157f040c478e299c124c47716f65d
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
<<<<<<< HEAD
      message: ""
=======
      message: ''
>>>>>>> 8e619261639157f040c478e299c124c47716f65d
    };
    this.handleEnter = this.handleEnter.bind(this);
    this.handleKeyPress = this.handleKeyPress.bind(this);
  }
  componentDidMount() {
<<<<<<< HEAD
    document.addEventListener("keydown", this.handleKeyPress);
  }
  componentWillUnmount() {
    document.removeEventListener("keydown", this.handleKeyPress);
  }
  handleEnter() {
    this.setState({
      message: this.state.message + "You pressed the enter key! "
    });
=======
    document.addEventListener("keydown",this.handleKeyPress);
  }
  componentWillUnmount() {
  /* It's good practice to use this to clean up React components before they are unmounted. for example: removing event listeners. */

    document.removeEventListener("keydown",this.handleKeyPress);
  }
  handleEnter() {
    this.setState((state) => ({
      message: state.message + 'You pressed the enter key! '
    }));
>>>>>>> 8e619261639157f040c478e299c124c47716f65d
  }
  handleKeyPress(event) {
    if (event.keyCode === 13) {
      this.handleEnter();
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.message}</h1>
      </div>
    );
  }
<<<<<<< HEAD
}
=======
};

>>>>>>> 8e619261639157f040c478e299c124c47716f65d
```
