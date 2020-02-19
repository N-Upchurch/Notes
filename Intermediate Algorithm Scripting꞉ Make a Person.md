---
tags: [Algorithm Solutions, Code Snippets, Javascript]
title: 'Intermediate Algorithm Scripting: Make a Person'
created: '2020-02-19T02:46:45.467Z'
modified: '2020-02-19T02:49:21.182Z'
---

Intermediate Algorithm Scripting: Make a Person
===============================================

Fill in the object constructor with the following methods below:
``` Javascript
getFirstName()
getLastName()
getFullName()
setFirstName(first)
setLastName(last)
setFullName(firstAndLast)
```

Run the tests to see the expected output for each method. The methods that take an argument must accept only one argument and it has to be a string. These methods must be the only available means of interacting with the object.

My Solution:
------------
``` Javascript
function Person(firstAndLast) {
    let fullName = firstAndLast.split(" ");
    this.getFirstName = () => {
        return fullName[0];
    };
    this.getLastName = () => {
        return fullName[1];
    };
    this.getFullName = () => {
        return fullName.join(" ");
    };
    this.setFirstName = (first) => {
        return fullName[0] = first;
    };
    this.setLastName = (last) => {
        return fullName[1] = last;
    };
    this.setFullName = (firstAndLast) => {
        return fullName = firstAndLast.split(" ");
    };
};
```

Given Solution 1
----------------
``` Javascript
var Person = function(firstAndLast) {
  var fullName = firstAndLast;

  this.getFirstName = function() {
    return fullName.split(" ")[0];
  };

  this.getLastName = function() {
    return fullName.split(" ")[1];
  };

  this.getFullName = function() {
    return fullName;
  };

  this.setFirstName = function(name) {
    fullName = name + " " + fullName.split(" ")[1];
  };

  this.setLastName = function(name) {
    fullName = fullName.split(" ")[0] + " " + name;
  };

  this.setFullName = function(name) {
    fullName = name;
  };
};
```

### Code Explanation
* Create a variable that will make a copy of the full name that was passed as a parameter.
* Then we can proceed to create the six methods needed and return what is asked for.
* For the individual setters, we can use the split to turn the fullname into an array of first and last names and concatenate the unchanged portion of the name with what was passed as a parameter.

