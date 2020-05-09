---
tags: [Code Snippets, scss]
title: 'Sass: Extend One Set of CSS Styles to Another Element'
created: '2020-05-09T22:48:19.330Z'
modified: '2020-05-09T22:49:55.123Z'
---

Sass: Extend One Set of CSS Styles to Another Element
=====================================================

Sass has a feature called extend that makes it easy to borrow the CSS rules from one element and build upon them in another.

For example, the below block of CSS rules style a ```.panel``` class. It has a ```background-color```, ```height``` and ```border```.
``` scss
.panel{
  background-color: red;
  height: 70px;
  border: 2px solid green;
}
```
Now you want another panel called ```.big-panel```. It has the same base properties as ```.panel```, but also needs a ```width``` and ```font-size```. It's possible to copy and paste the initial CSS rules from ```.panel```, but the code becomes repetitive as you add more types of panels. The ```extend``` directive is a simple way to reuse the rules written for one element, then add more for another:
``` scss
.big-panel{
  @extend .panel;
  width: 150px;
  font-size: 2em;
}
```
The ```.big-panel``` will have the same properties as ```.panel``` in addition to the new styles.

