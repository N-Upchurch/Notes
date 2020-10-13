---
tags: [Code Snippets, JSX, Notes, React]
title: React Notes
created: '2020-05-09T22:56:06.949Z'
modified: '2020-10-13T01:38:31.949Z'
---

React Notes
============
Vocabulary
----------
**Stateful Component**
A class component that maintains its own internal state. You may see stateful components referred to simply as components or React components.

**Stateless Component**
A class that extends React.Component, but does not use internal state.

**Stateless Functional Component**
Any function you write which accepts props and returns JSX. 

Components
----------
### Evaluating Prop Values as JavaScript
For prop values to be evaluated as JavaScript, they must be enclosed in curly brackets, for instance ```date={Date()}```

### Setting Default Props
``` javascript
MyComponent.defaultProps = { location: 'San Francisco' }
```
### Access Props in ES6 Class Components Using this.props

The ES6 class component uses a slightly different convention to access props.

Anytime you refer to a class component within itself, you use the ```this``` keyword. To access ```props``` within a class component, you preface the code that you use to access it with ```this```. For example, if an ES6 class component has a prop called ```data```, you write ```{this.props.data}``` in JSX.

ReactDOM
--------
### Rendering React Components
React components are passed into ```ReactDOM.render()``` a little differently than JSX elements. For JSX elements, you pass in the name of the element that you want to render. However, for React components, you need to use the same syntax as if you were rendering a nested component, for example: 
``` javascript
ReactDOM.render(<ComponentToRender />, targetNode)
```
You use this syntax for both ES6 class components and functional components. An example of creating and rendering a React component:
``` javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>My First React Component!</h1>
      </div>
    );
  }
}

/* 
In the below function, the first argument is the component to be rendered, and the second is where it is to be rendered. Thus, rendering a React app might look like this:

ReactDOM.render(<App />, document.getElementByID("root"));

*/
ReactDOM.render(<MyComponent />, document.getElementById("challenge-node"));
```

JSX
---
### JSX Must Return a Single Element

#### Valid
``` HTML
<div>
  <p>Paragraph One</p>
  <p>Paragraph Two</p>
  <p>Paragraph Three</p>
</div>
```
#### Invalid
``` HTML
<p>Paragraph One</p>
<p>Paragraph Two</p>
<p>Paragraph Three</p>
```
### Comments

To put comments inside JSX, use the syntax ```{/* */}``` to wrap around the comment text.

### Naming Convention for HTML Attributes

The naming convention for all HTML attributes and event references in JSX is camelCase. For example, a click event in JSX is onClick, instead of onclick. Likewise, onchange becomes onChange.

#### HTML Attribute Name Reference:
|HTML|JSX|
|----|---|
|class|className|

### Self-Closing JSX Tags
Any JSX element can be written with a self-closing tag, and *every element must be closed*. The line-break tag, for example, must always be written as ```<br />``` in order to be valid JSX that can be transpiled. A ```<div>```, on the other hand, can be written as ```<div />``` or ```<div></div>```. The difference is that in the first syntax version there is no way to include anything in the ```<div />```
