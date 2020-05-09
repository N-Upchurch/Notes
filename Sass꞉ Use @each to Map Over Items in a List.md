---
tags: [Code Snippets, scss]
title: 'Sass: Use @each to Map Over Items in a List'
created: '2020-05-09T22:18:11.790Z'
modified: '2020-05-09T22:19:30.883Z'
---

Sass: Use @each to Map Over Items in a List
===========================================

Sass offers the ```@each``` directive which loops over each item in a list or map. On each iteration, the variable gets assigned to the current value from the list or map.
``` scss
@each $color in blue, red, green {
  .#{$color}-text {color: $color;}
}
```

A map has slightly different syntax. Here's an example:
```scss
$colors: (color1: blue, color2: red, color3: green);

@each $key, $color in $colors {
  .#{$color}-text {color: $color;}
}
``````
Note that the ```$key``` variable is needed to reference the keys in the map. Otherwise, the compiled CSS would have ```color1```, ```color2```... in it. Both of the above code examples are converted into the following CSS:
``` scss
.blue-text {
  color: blue;
}

.red-text {
  color: red;
}

.green-text {
  color: green;
}
```
