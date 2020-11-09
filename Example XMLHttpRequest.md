---
tags: [Code Snippets, Javascript]
title: Example XMLHttpRequest
created: '2020-11-09T05:18:49.299Z'
modified: '2020-11-09T05:20:14.796Z'
---

Example XMLHttpRequest
======================
``` javascript
const sendHttpRequest = (method, url, data) => {
  const promise = new Promise((resolve, reject) => {
    // Create new XMLHttpRequest object
      const xhr = new XMLHttpRequest();
    
    // Configure the request
      xhr.open(method, url);
    
    // Ensure JS data is returned in lieu of string
      xhr.responseType = 'json';
    
    // For POST, add headers
      if (data) {
        xhr.setRequestHeader('Content-Type', 'application/json');
      };
    
    // Called after response is received
      xhr.onload = () => {
        // Checks for HTTP status errors
        if (xhr.status >= 400) {
          reject(xhr.response);
        } else {
          resolve(xhr.response);
        }
      };
    
    // Checks for errors from API
      xhr.onerror = () => {
        reject('Something went wrong!');
      };
      xhr.send(JSON.stringify(data));
  });
  return promise;
};

// Use sendHttpRequest to receive data
// Data must be accessed here as the funciton is asynchronous
const getData = (method, url) => {
  sendHttpRequest(method, url).then(responseData => {
    listUsers(responseData);
    printAdText(responseData);
  }).catch(err => {
    console.log(err);
  })
};

// Use sendHttpRequest to send data
// Data must be accessed here as the funciton is asynchronous
const sendData = (method, url, data) => {
  sendHttpRequest(method, url, data).then(responseData => {
    return responseData;
  }).catch(err => {
    console.log(err);
  })
};

// Functions to work with response data
const listUsers = (response) => {
  response.data.forEach(i => console.log(`${i.last_name}, ${i.first_name}: ${i.email}`));
};

const printAdText = (response) => {
  console.log(response.ad.text);
};

getData('GET','https://reqres.in/api/users');

sendData('POST', 'https://reqres.in/api/register', {
  email: 'eve.holt@reqres.in',
  password: 'pistol'
});

```
