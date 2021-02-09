---
tags: [Javascript, JS Algorithms]
title: 'JavaScript Algorithms and Data Structures Projects: Cash Register'
created: '2020-04-05T17:45:02.435Z'
modified: '2021-02-09T20:01:38.246Z'
---

JavaScript Algorithms and Data Structures Projects: Cash Register
=================================================================

Design a cash register drawer function ```checkCashRegister()``` that accepts purchase price as the first argument (```price```), payment as the second argument (```cash```), and cash-in-drawer (```cid```) as the third argument.

cid is a 2D array listing available currency.

The ```checkCashRegister()``` function should always return an object with a ```status``` key and a ```change``` key.

Return ```{status: "INSUFFICIENT_FUNDS", change: []}``` if cash-in-drawer is less than the change due, or if you cannot return the exact change.

Return ```{status: "CLOSED", change: [...]}``` with cash-in-drawer as the value for the key ```change``` if it is equal to the change due.

Otherwise, return ```{status: "OPEN", change: [...]}```, with the change due in coins and bills, sorted in highest to lowest order, as the value of the ```change``` key.

My Solution:
------------
``` javascript
const currencyValues = [
    ["PENNY", 1], 
    ["NICKEL", 5], 
    ["DIME", 10], 
    ["QUARTER", 25], 
    ["ONE", 100], 
    ["FIVE", 500], 
    ["TEN", 1000], 
    ["TWENTY", 2000], 
    ["ONE HUNDRED", 10000]
];

// Helper Functions
const   convertPennies = (value) => Math.round(value * 100);
const   getChange = (price, cash) => convertPennies(cash) - convertPennies(price);
const   adequateCash = (cid, change) => getDrawerTotal(cid) >= change ? true : false;
const   getDrawerTotal = (cid) => {
            let values = [];
            cid.forEach(x => values.push(convertPennies(x[1])));
            return values.reduce((x, y) => x + y);
        };
const   makeChange = (cid, change) => {
            let changeDue = change;
            let madeChange = [
                    ["PENNY", 0], 
                    ["NICKEL", 0], 
                    ["DIME", 0], 
                    ["QUARTER", 0], 
                    ["ONE", 0], 
                    ["FIVE", 0], 
                    ["TEN", 0], 
                    ["TWENTY", 0], 
                    ["ONE HUNDRED", 0]
                ];
            for (let i=8; i>=0; i--) {
                let denomTotal = convertPennies(cid[i][1]);
                let currencyValue = currencyValues[i][1];
                while (denomTotal >= currencyValue && currencyValue <= changeDue) {
                    madeChange[i][1] += currencyValue;
                    changeDue -= currencyValue;
                    denomTotal -= currencyValue;
                };
            }
            madeChange.forEach(x => x[1] = x[1]/100);
            return madeChange;
        };
const   changePossible = (madeChange, change) => getDrawerTotal(madeChange) >= change ? true : false;

// Main Function
const checkCashRegister = (price, cash, cid) => {
    let change = getChange(price, cash);
    let adequate = adequateCash(cid, change);
    let madeChange = makeChange(cid, change);
    let drawerTotal = getDrawerTotal(cid);
    let possible = changePossible(madeChange, change);
        console.log(getDrawerTotal(madeChange));
        console.log(change);
        console.log(possible);
    if (adequate == false || possible == false) {
        return {status: "INSUFFICIENT_FUNDS", change: []}
    } else if (change == drawerTotal) {
        return {status: "CLOSED", change: cid}
    } else {
        return {status: "OPEN", change: madeChange.reverse().filter(x => x[1] > 0)}
    }
}

```

Given Solution 1:
-----------------
``` javascript
// Create an array of objects which hold the denominations and their values
var denom = [
  { name: "ONE HUNDRED", val: 100.0 },
  { name: "TWENTY", val: 20.0 },
  { name: "TEN", val: 10.0 },
  { name: "FIVE", val: 5.0 },
  { name: "ONE", val: 1.0 },
  { name: "QUARTER", val: 0.25 },
  { name: "DIME", val: 0.1 },
  { name: "NICKEL", val: 0.05 },
  { name: "PENNY", val: 0.01 }
];

function checkCashRegister(price, cash, cid) {
  var output = { status: null, change: [] };
  var change = cash - price;

  // Transform CID array into drawer object
  var register = cid.reduce(
    function(acc, curr) {
      acc.total += curr[1];
      acc[curr[0]] = curr[1];
      return acc;
    },
    { total: 0 }
  );

  // Handle exact change
  if (register.total === change) {
    output.status = "CLOSED";
    output.change = cid;
    return output;
  }

  // Handle obvious insufficient funds
  if (register.total < change) {
    output.status = "INSUFFICIENT_FUNDS";
    return output;
  }

  // Loop through the denomination array
  var change_arr = denom.reduce(function(acc, curr) {
    var value = 0;
    // While there is still money of this type in the drawer
    // And while the denomination is larger than the change remaining
    while (register[curr.name] > 0 && change >= curr.val) {
      change -= curr.val;
      register[curr.name] -= curr.val;
      value += curr.val;

      // Round change to the nearest hundreth deals with precision errors
      change = Math.round(change * 100) / 100;
    }
    // Add this denomination to the output only if any was used.
    if (value > 0) {
      acc.push([curr.name, value]);
    }
    return acc; // Return the current change_arr
  }, []); // Initial value of empty array for reduce

  // If there are no elements in change_arr or we have leftover change, return
  // the string "Insufficient Funds"
  if (change_arr.length < 1 || change > 0) {
    output.status = "INSUFFICIENT_FUNDS";
    return output;
  }

  // Here is your change, ma'am.
  output.status = "OPEN";
  output.change = change_arr;
  return output;
}
```
### Code Explanation:
First, create an array of objects with the value of each denomination of bill or coin, along with an output object with the status and change keys. Next, transform the ```CID``` array into a drawer object. Then, handle the conditions of exact change and insufficient funds. Loop through the ```denom``` array and update the change and values while there is still money of each type in the drawer and while the denomination is larger than the change remaining. Add this denomination to the accumulator of ```change_arr``` if any of this type was used. After the loop, ```change_arr``` is a 2D array of the change due, sorted from highest to lowest denomination. If there are no elements in ```change_arr``` or you still owe change, return the output object with a status of ```INSUFFICIENT_FUNDS```. Finally you can give the correct change. Return the output object with a status of ```OPEN``` and ```change_arr``` as the value of change.
