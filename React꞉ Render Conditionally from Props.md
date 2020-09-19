---
tags: [Code Snippets, React]
title: 'React: Render Conditionally from Props'
created: '2020-09-19T01:17:45.451Z'
modified: '2020-09-19T01:18:51.522Z'
---

React: Render Conditionally from Props
======================================

``` js
class Results extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h1>{
      this.props.fiftyFifty ? "You Win!"
        : "You Lose!"
    }</h1>;
  }
}

class GameOfChance extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 1
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      counter: this.state.counter += 1
    });
  }
  render() {
    const expression = Math.random() >= .5;
    return (
      <div>
        <button onClick={this.handleClick}>Play Again</button>
        <Results fiftyFifty={expression} />
        <p>{'Turn: ' + this.state.counter}</p>
      </div>
    );
  }
}

```
