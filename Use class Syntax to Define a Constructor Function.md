---
tags: [Javascript, JS ES6]
title: Use class Syntax to Define a Constructor Function
created: '2019-12-08T02:57:03.080Z'
modified: '2021-02-09T20:02:36.435Z'
---

Use class Syntax to Define a Constructor Function
=================================================

ES6 provides a new syntax to create objects, using the class keyword.

It should be noted that the class syntax is just syntax, and not a full-fledged class-based implementation of an object-oriented paradigm, unlike in languages such as Java, Python, Ruby, etc.

In ES5, we usually define a constructor function and use the new keyword to instantiate an object.
``` Javascript
var SpaceShuttle = function(targetPlanet){
  this.targetPlanet = targetPlanet;
}
var zeus = new SpaceShuttle('Jupiter');
```

The class syntax simply replaces the constructor function creation:

``` Javascript
class SpaceShuttle {
  constructor(targetPlanet) {
    this.targetPlanet = targetPlanet;
  }
}
const zeus = new SpaceShuttle('Jupiter');
```

It should be noted that the class keyword declares a new function, to which a constructor is added. This constructor is invoked when new is called to create a new object.

**Notes:**
* UpperCamelCase should be used by convention for ES6 class names, as in SpaceShuttle used above.
* The constructor method is a special method for creating and initializing an object created with a class.
