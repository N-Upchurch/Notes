---
tags: [Code Snippets, Javascript]
title: Example Fetch Request
created: '2020-11-10T03:15:55.797Z'
modified: '2020-11-10T03:16:30.271Z'
---

Example Fetch Request
=====================
``` javascript
const sendHttpRequest = (method, url, data) => {
  // Return fetch promise so that it can be used in promise chains
  return fetch(url, {
    method: method,
    // Convert send data into string
    body: JSON.stringify(data),
    // If (data) add headers to POST request
    headers: data ? { 'Content-Type': 'application/json' } : {}
  }).then(response => {
    // Return error for http responses >= 400
    if (response.status >= 400) {
      // Error data must be accessed via nested promise
      return response.json().then(errResData => {
        const error = new Error('Something went wrong!');
        error.data = errResData;
        throw error;
      });
    }
    // Return response in JSON to fetch promise
    return response.json();
  });
};

const getData = () => {
  // Send fetch request via sendHttpRequest helper function
  sendHttpRequest('GET', 'https://reqres.in/api/users')
  // Do something with the data
    .then(responseData => {
    console.log(responseData)
  });
};


const sendData = () => {
  // Send fetch request via sendHttpRequest helper function
  sendHttpRequest('POST', 'https://reqres.in/api/register', {
    email: 'eve.holt@reqres.in',
    password: 'pistol'
  // Do something with the data
  }).then(responseData => {
    console.log(responseData);
  // Log API errors
  }).catch(err => {
    console.log(err, err.data);
  });
};

// getData();
sendData();
```
