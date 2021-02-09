---
tags: [React]
title: 'React: Create a Component with Composition'
created: '2020-05-10T23:36:17.721Z'
modified: '2021-02-09T19:58:31.481Z'
---

React: Create a Component with Composition
==========================================

Now we will look at how we can compose multiple React components together. Imagine you are building an App and have created three components, a ```Navbar```, ```Dashboard```, and ```Footer```.

To compose these components together, you could create an ```App``` *parent* component which renders each of these three components as children. To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX. For example, in the ```render``` method you could write:
``` javascript
return (
 <App>
  <Navbar />
  <Dashboard />
  <Footer />
 </App>
)
```
When React encounters a custom HTML tag that references another component (a component name wrapped in ```< />``` like in this example), it renders the markup for that component in the location of the tag. This should illustrate the parent/child relationship between the ```App``` component and the ```Navbar```, ```Dashboard```, and ```Footer```.

