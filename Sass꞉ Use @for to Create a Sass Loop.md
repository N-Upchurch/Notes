---
tags: [Code Snippets, scss]
title: 'Sass: Use @for to Create a Sass Loop'
created: '2020-05-09T22:15:03.426Z'
modified: '2020-05-09T22:17:10.675Z'
---

Sass: Use @for to Create a Sass Loop
====================================

The ```@for``` directive adds styles in a loop, very similar to a ```for``` loop in JavaScript.

```@for``` is used in two ways: "start through end" or "start to end". The main difference is that the "start to end" excludes the end number as part of the count, and "start through end" includes the end number as part of the count.

Here's a start through end example:

``` scss
@for $i from 1 through 12 {
  .col-#{$i} { width: 100%/12 * $i; }
}
```

The ```#{$i}``` part is the syntax to combine a variable (```i```) with text to make a string. When the Sass file is converted to CSS, it looks like this:

``` scss
.col-1 {
  width: 8.33333%;
}

.col-2 {
  width: 16.66667%;
}

...

.col-12 {
  width: 100%;
}
```

This is a powerful way to create a grid layout. Now you have twelve options for column widths available as CSS classes.

