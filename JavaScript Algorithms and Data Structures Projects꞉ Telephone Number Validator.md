---
title: 'JavaScript Algorithms and Data Structures Projects: Telephone Number Validator'
created: '2020-04-02T21:36:30.156Z'
modified: '2021-02-09T20:00:07.874Z'
---

JavaScript Algorithms and Data Structures Projects: Telephone Number Validator
==============================================================================
Return ```true``` if the passed string looks like a valid US phone number.

The user may fill out the form field any way they choose as long as it has the format of a valid US number. The following are examples of valid formats for US numbers (refer to the tests below for other variants):

    555-555-5555
    (555)555-5555
    (555) 555-5555
    555 555 5555
    5555555555
    1 555 555 5555

For this challenge you will be presented with a string such as 800-692-7753 or 8oo-six427676;laskdjf. Your job is to validate or reject the US phone number based on any combination of the formats provided above. The area code is required. If the country code is provided, you must confirm that the country code is 1. Return true if the string is a valid US phone number; otherwise return false.

My Solution:
------------
``` Javascript
function telephoneCheck(str) {
  return /^1{0,1}(\s{0,1}|-{0,1})((\(\d{3}\))|\d{3})(\s{0,1}|-{0,1})\d{3}(\s{0,1}|-{0,1})\d{4}$/.test(str);
}

telephoneCheck("1 555-555-5555");
```

Given Solution 1
----------------
``` Javascript
function telephoneCheck(str) {
  var regex = /^(1\s?)?(\(\d{3}\)|\d{3})[\s\-]?\d{3}[\s\-]?\d{4}$/;
  return regex.test(str);
}
telephoneCheck("555-555-5555");
```
### Code Explanation
* ```^``` denotes the beginning of the string.
* ```(1\s?)?``` allows for “1” or "1 " if there is one.
* ```\d{n}``` checks for exactly n number of digits so ```\d{3}``` checks for three digits.
* ```x|y``` checks for either x OR y so ```(\(\d{3}\)|\d{3})``` checks for either three digits surrounded by parentheses, or three digits by themselves with no parentheses.
* ```[\s\-]?``` checks for spaces or dashes between the groups of digits.
* ```$``` denotes the end of the string. In this case the beginning ```^``` and end of the string ```$``` are used in the regex to prevent it from matching any longer string that might contain a valid phone number (eg. “s 555 555 5555 3”).
* Lastly we use ```regex.test(str)``` to test if the string adheres to the regular expression, it returns ```true``` or ```false```.

Given Solution 2
----------------
``` Javascript
function telephoneCheck(str) {
  var re = /^([+]?1[\s]?)?((?:[(](?:[2-9]1[02-9]|[2-9][02-8][0-9])[)][\s]?)|(?:(?:[2-9]1[02-9]|[2-9][02-8][0-9])[\s.-]?)){1}([2-9]1[02-9]|[2-9][02-9]1|[2-9][02-9]{2}[\s.-]?){1}([0-9]{4}){1}$/;
  return re.test(str);
}
telephoneCheck("555-555-5555");
```
### Code Explanation
* This is an example of a very comprehensive and robust solution to validating US phone numbers client side. In such cases it might be much better and easier to implement this library: [libphonenumber](https://github.com/google/libphonenumber).

