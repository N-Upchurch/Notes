---
tags: [Javascript]
title: 'Object Oriented Programming: Define a Constructor Function'
created: '2019-12-13T05:48:17.488Z'
modified: '2021-02-09T19:58:31.163Z'
---

Object Oriented Programming: Define a Constructor Function
==========================================================

Constructors are functions that create new objects. They define properties and behaviors that will belong to the new object. Think of them as a blueprint for the creation of new objects.

Here is an example of a constructor:
``` javascript
function Bird() {
  this.name = "Albert";
  this.color = "blue";
  this.numLegs = 2;
}

```
This constructor defines a Bird object with properties name, color, and numLegs set to Albert, blue, and 2, respectively. Constructors follow a few conventions:

* Constructors are defined with a capitalized name to distinguish them from other functions that are not ```constructors```.
* Constructors use the keyword ```this``` to set properties of the object they will create. Inside the constructor, ```this``` refers to the new object it will create.
* Constructors define properties and behaviors instead of returning a value as other functions might.

Use a Constructor to Create Objects
------------------------------------

Here's the Bird constructor from above:
``` javascript
function Bird() {
  this.name = "Albert";
  this.color  = "blue";
  this.numLegs = 2;
  // "this" inside the constructor always refers to the object being created
}

let blueBird = new Bird();

```
Notice that the ```new``` operator is used when calling a constructor. This tells JavaScript to create a new instance of Bird called blueBird. Without the ```new``` operator, ```this``` inside the constructor would not point to the newly created object, giving unexpected results. Now blueBird has all the properties defined inside the Bird constructor:
``` javascript
blueBird.name; // => Albert
blueBird.color; // => blue
blueBird.numLegs; // => 2

```
Just like any other object, its properties can be accessed and modified:
``` javascript
blueBird.name = 'Elvira';
blueBird.name; // => Elvira

```

Using Parameters
----------------
``` javascript
function Bird(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}

```



