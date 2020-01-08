---
tags: [Algorithm Solutions, Code Snippets, Javascript, Regex]
title: 'Intermediate Algorithm Scripting: Pig Latin'
created: '2020-01-06T20:25:34.910Z'
modified: '2020-01-08T02:27:32.811Z'
---

Intermediate Algorithm Scripting: Pig Latin
===========================================

Translate the provided string to pig latin.

* Pig Latin takes the first consonant (or consonant cluster) of an English word, moves it to the end of the word and suffixes an "ay".
* If a word begins with a vowel you just add "way" to the end.
* If a word does not contain a vowel, just add "ay" to the end.
* Input strings are guaranteed to be English words in all lowercase.

My Solution:
------------
``` javascript
function translatePigLatin(str) {

  let beginVowel = /^[aeiou]/,
      beginConsonant = /^[^aeiou]+/g,
      contVowels = /(?=[aeiou]+)/,
      findFirstVowel = /[aeiou]/
 
  if (beginVowel.test(str)) { 
    return str.concat("way")
  } else if (!contVowels.test(str)){ 
    return str.concat("ay")
  } else if (beginConsonant.test(str)) { 
    let firstVowel = str.match(findFirstVowel)
    let end = str.indexOf(firstVowel[0])
    return str.slice(str.indexOf(firstVowel[0]), str.length) + (str.slice(0, str.indexOf(firstVowel[0])) )+ "ay"
  } 
}

```

Given Solution 1
----------------
``` javascript
function translatePigLatin(str) {
  let consonantRegex = /^[^aeiou]+/;
  let myConsonants = str.match(consonantRegex);
  return myConsonants !== null
    ? str
        .replace(consonantRegex, "")
        .concat(myConsonants)
        .concat("ay")
    : str.concat("way");
}

translatePigLatin("consonant");
```
### Code Explanation:
* Start at beginning and get longest match of everything not a vowel (consonants)
* If regex pattern found, it saves the match; else, it returns null
* If regex pattern found (starts with consonants), it deletes match, adds the match to the end, and adds “ay” to the end
* If regex pattern not found (starts with vowels), it just adds “way” to the ending


Given Solution 2
----------------
``` javascript
function translatePigLatin(str) {
  // Create variables to be used
  var pigLatin = "";
  var regex = /[aeiou]/gi;

  // Check if the first character is a vowel
  if (str[0].match(regex)) {
    pigLatin = str + "way";
  } else if (str.match(regex) === null) {
    // Check if the string contains only consonants
    pigLatin = str + "ay";
  } else {
    // Find how many consonants before the first vowel.
    var vowelIndice = str.indexOf(str.match(regex)[0]);

    // Take the string from the first vowel to the last char
    // then add the consonants that were previously omitted and add the ending.
    pigLatin = str.substr(vowelIndice) + str.substr(0, vowelIndice) + "ay";
  }

  return pigLatin;
}
```
### Code Explanation:
* Make an empty string to hold your Pig Latin word.
* Assign your appropriate regular expression to a variable.
* If the first character is a vowel, just add way to end of string and return it.
* If the first character is not a vowel:
   * Find number of consonants before first vowel with help of ```indexOf()```, ```match()``` and regex.
   * Start Pig Latin string with first vowel till the end.
   * Add letters before first vowel to end of string.
   * ```substr()``` is used for string manipulation here.
   * Add "ay" to end of string and return it.


Given Solution 3
----------------
``` javascript
function translatePigLatin(str) {
  if (str.match(/^[aeiou]/)) return str + "way";

  const consonantCluster = str.match(/^[^aeiou]+/)[0];
  return str.substring(consonantCluster.length) + consonantCluster + "ay";
}
```
### Code Explanation:

* First, check to see if the string begins with a vowel.
  * The regex looks at the beginning of the string ```^``` for one of the specified characters ```[aeiou]```
  * If it does, you only need to return the original string with “way” appended on the end.
* If the string does not start with a vowel, we want to build a string which contains every consonant before the first vowel in the provided string.
  * To do this, look at the beginning of a string ```^``` for one or more characters + NOT specified ```[^aeiou]```.
  * If there is a match (and in this case, there always will be), ```match()``` returns an Array with the matched string as the first element, which is all we want. Grab it with ```[0]```.
* Now, we can start building our Pig Latin string to return. This can be built in three parts:
  * The first part contains all of the characters in the original string, starting from the first vowel. We can easily get these characters by creating a substring of the original string, with its starting index being the first vowel.
  * The second part contains the consonant string we just built. (If you add the second and first parts of this string together, you will get the original string.)
  * The final part contains “ay”.


Given Solution 4
----------------
``` javascript
function translatePigLatin(str) {
  return str
    .replace(/^[aeiou]\w*/, "$&way")
    .replace(/(^[^aeiou]+)(\w*)/, "$2$1ay");
}
```
### Code Explanation:

* Use ```replace()``` on the string, using a regular expression to check if the first letter is a consonant and adding "way" at the end in this case. If the first letter is a consonant nothing will happen at this point.
* Use ```replace()``` again to check for consonants at the beginning of the word and to move it or them to the end of the word and add "ay" at the end.


