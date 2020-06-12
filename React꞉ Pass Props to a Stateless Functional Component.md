---
tags: [Code Snippets, React]
title: 'React: Pass Props to a Stateless Functional Component'
created: '2020-05-11T00:01:29.075Z'
modified: '2020-05-12T19:00:59.395Z'
---

React: Pass Props to a Stateless Functional Component
=====================================================

In React, you can pass props, or properties, to child components. Say you have an ```App``` component which renders a child component called ```Welcome``` which is a stateless functional component. You can pass ```Welcome``` a ```user``` property by writing:
``` javascript
<App>
  <Welcome user='Mark' />
</App>
```
You use *custom HTML attributes* created by you and supported by React to be passed to the component. In this case, the created property ```user``` is passed to the component ```Welcome```. Since ```Welcome``` is a stateless functional component, it has access to this value like so:
``` javascript
const Welcome = (props) => <h1>Hello, {props.user}!</h1>
```
It is standard to call this value ```props``` and when dealing with stateless functional components, you basically consider it as an argument to a function which returns JSX. You can access the value of the argument in the function body. With class components, you will see this is a little different.

