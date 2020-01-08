---
tags: [Code Snippets, ES6, Javascript]
title: Use getters and setters to Control Access to an Object
created: '2019-12-08T03:37:49.451Z'
modified: '2019-12-08T04:19:08.543Z'
---

Use getters and setters to Control Access to an Object
======================================================

You can obtain values from an object and set the value of a property within an object.

These are classically called getters and setters.

Getter functions are meant to simply return (get) the value of an object's private variable to the user without the user directly accessing the private variable.

Setter functions are meant to modify (set) the value of an object's private variable based on the value passed into the setter function. This change could involve calculations, or even overwriting the previous value completely.
``` Javascript
class Book {
  constructor(author) {
    this._author = author;
  }
  // getter
  get writer() {
    return this._author;
  }
  // setter
  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}
const lol = new Book('anonymous');
console.log(lol.writer);  // anonymous
lol.writer = 'wut';
console.log(lol.writer);  // wut

```
Notice the syntax used to invoke the getter and setter. They do not even look like functions. Getters and setters are important because they hide internal implementation details. Note: It is convention to precede the name of a private variable with an underscore (_). However, the practice itself does not make a variable private.
``` javascript
class Thermostat {
    constructor(fahrenheit) {
        this.fahrenheit = fahrenheit;
    }
    get temperature() {
        return (this.fahrenheit-32)*(5/9);
    }
    set temperature(celsius) {
        this.fahrenheit = (celsius*(9/5))+32;
    }
}

const thermos = new Thermostat(76); // setting in Fahrenheit scale
let temp = thermos.temperature; // 24.44 in C
thermos.temperature = 26;
temp = thermos.temperature; // 26 in C
```
