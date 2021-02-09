---
tags: [Javascript, JS Algorithms]
title: 'JavaScript Algorithms and Data Structures Projects: Roman Numeral Converter'
created: '2020-02-20T04:59:12.646Z'
modified: '2021-02-09T20:01:38.294Z'
---

JavaScript Algorithms and Data Structures Projects: Roman Numeral Converter
===========================================================================

Convert the given number into a roman numeral.

All roman numerals answers should be provided in upper-case.

My Solution:
------------
``` Javascript
const convertToRoman = (num) => {
  let numerals = "";
  let mapRomans = ['M','CM','D','CD','C','XC','L','XL','X','IX','V','IV','I'];
  let mapDigits = [1000,900,500,400,100,90,50,40,10,9,5,4,1] ;

    for (let i = 0; i<mapDigits.length; i++) {
      while(mapDigits[i] <= num) {
        numerals += mapRomans[i];
        num -= mapDigits[i];
      }
    }
  return numerals;
 }
```

Given Solution 1:
-----------------
``` Javascript
var convertToRoman = function(num) {
  var decimalValue = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1];
  var romanNumeral = [
    "M",
    "CM",
    "D",
    "CD",
    "C",
    "XC",
    "L",
    "XL",
    "X",
    "IX",
    "V",
    "IV",
    "I"
  ];

  var romanized = "";

  for (var index = 0; index < decimalValue.length; index++) {
    while (decimalValue[index] <= num) {
      romanized += romanNumeral[index];
      num -= decimalValue[index];
    }
  }

  return romanized;
};
```

### Code Explanation
* We start off by creating two arrays with default conversion with matching indices. These are called ```decimalValue``` and ```romanNumeral```. We also create an empty string variable, ```romanized```, which will house the final roman number.
* Using a for loop, we loop through the indicies of the ```decimalValue``` array. We continue to loop until while the value at the current ```index``` will fit into ```num```.
* Next, we add the roman numeral and decrease ```num``` by the decimal equivalent.
* Finally, we return the value of ```romanized```.


Given Solution 2:
-----------------
``` Javascript
function convertToRoman(num) {
  var romans = ["I", "V", "X", "L", "C", "D", "M"],
    ints = [],
    romanNumber = [],
    numeral = "",
    i;
  while (num) {
    ints.push(num % 10);
    num = Math.floor(num / 10);
  }
  for (i = 0; i < ints.length; i++) {
    units(ints[i]);
  }
  function units() {
    numeral = romans[i * 2];
    switch (ints[i]) {
      case 1:
        romanNumber.push(numeral);
        break;
      case 2:
        romanNumber.push(numeral.concat(numeral));
        break;
      case 3:
        romanNumber.push(numeral.concat(numeral).concat(numeral));
        break;
      case 4:
        romanNumber.push(numeral.concat(romans[i * 2 + 1]));
        break;
      case 5:
        romanNumber.push(romans[i * 2 + 1]);
        break;
      case 6:
        romanNumber.push(romans[i * 2 + 1].concat(numeral));
        break;
      case 7:
        romanNumber.push(romans[i * 2 + 1].concat(numeral).concat(numeral));
        break;
      case 8:
        romanNumber.push(
          romans[i * 2 + 1]
            .concat(numeral)
            .concat(numeral)
            .concat(numeral)
        );
        break;
      case 9:
        romanNumber.push(romans[i * 2].concat(romans[i * 2 + 2]));
    }
  }
  return romanNumber
    .reverse()
    .join("")
    .toString();
}
```

### Code Explanation
* Create an array of Roman Numerals (```romans```).
* Use a for loop to create an array of the digits (```ints```) in the number.
* Loop through the array of digits (base 10) and as you do, increment the Roman Numeral (base 5) index by 2 (```numeral = romans[i*2]```).
* Within the loop, use Switch Case to push the proper Roman Numerals (backwards) onto that array.
* Reverse the Roman Numerals array and turn it into a string.

Given Solution 3:
-----------------
``` Javascript
function convertToRoman(num) {
  var romans = [
      // 10^i 10^i*5
      ["I", "V"], // 10^0
      ["X", "L"], // 10^1
      ["C", "D"], // 10^2
      ["M"] // 10^3
    ],
    digits = num
      .toString()
      .split("")
      .reverse()
      .map(function(item, index) {
        return parseInt(item);
      }),
    numeral = "";

  // Loop through each digit, starting with the ones place
  for (var i = 0; i < digits.length; i++) {
    // Make a Roman numeral that ignores 5-multiples and shortening rules
    numeral = romans[i][0].repeat(digits[i]) + numeral;
    // Check for a Roman numeral 5-multiple version
    if (romans[i][1]) {
      numeral = numeral
        // Change occurrences of 5 * 10^i to the corresponding 5-multiple Roman numeral
        .replace(romans[i][0].repeat(5), romans[i][1])
        // Shorten occurrences of 9 * 10^i
        .replace(
          romans[i][1] + romans[i][0].repeat(4),
          romans[i][0] + romans[i + 1][0]
        )
        // Shorten occurrences of 4 * 10^i
        .replace(romans[i][0].repeat(4), romans[i][0] + romans[i][1]);
    }
  }

  return numeral;
}
```

### Code Explanation
* Use an array (```romans```) to create a matrix containing the Roman numeral for a given power of 10 and, if available, the Roman numeral for that power of 10 times 5.
* Convert the input number (```num```) to a reversed array of digits (```digits```) so that we can loop through those digits starting with the ones position and going up.
* Loop through each digit, starting with the ones place, and create a Roman numeral string by adding each higher-power Roman numeral to the start of the ```numeral``` string a number of times equal to ```digit```. This initial string ignores the Roman numerals that are a power of 10 times 5 and also ignores shortening rules.
* If the relevant power of 10 has a 5-multiple Roman numeral, in ```numeral```, replace 5-in-a-row occurrences with the relevant 5-multiple Roman numeral (i.e., V, L, or D) and shorten occurrences of 9 * 10^i (e.g., VIIII to VIX) and 4 * 10^i (e.g., XXXX to XL). Order is important here!
* Finally, return ```numeral```.

