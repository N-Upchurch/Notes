---
tags: [Code Snippets, scss]
title: 'Sass: Apply a Style Until a Condition is Met with @while'
created: '2020-05-09T22:27:03.363Z'
modified: '2020-05-09T22:27:50.881Z'
---

Sass: Apply a Style Until a Condition is Met with @while
========================================================

The ```@while``` directive is an option with similar functionality to the JavaScript while loop. It creates CSS rules until a condition is met.

The ```@for``` challenge gave an example to create a simple grid system. This can also work with ```@while```.
```scss
$x: 1;
@while $x < 13 {
  .col-#{$x} { width: 100%/12 * $x;}
  $x: $x + 1;
}
```
First, define a variable ```$x``` and set it to 1. Next, use the ```@while``` directive to create the grid system while ```$x``` is less than 13. After setting the CSS rule for ```width```, ```$x``` is incremented by 1 to avoid an infinite loop.

