# Frontend Homework

This homework is designed to test knowledge of JavaScript, HTML & CSS. At Shadow, our front-end apps interact with RESTful APIs to send and retrieve data using modern JavaScript. You will be requesting data from an API, transforming this data, and displaying the data with HTML and CSS.

## Task

You will be provided with an API and endpoint.  In `api/users.js`, write a function named `getUsers` that requests data from the `/users` endpoint, transforms the result into the format outlined below, returns a promise that resolves with the transformed object, and displays the result. In addition to `getUsers`, you may add as many helper functions as you wish.

1. Get data from the `/users` endpoint. Fetch pages of 10 items at a time.

2. The `getUsers` function accepts an options object and should support the following keys:
  - `page` - Specifies which page to retrieve from the `/users` endpoint. If omitted, fetch page 1.
  - `role` - Specified which role to retrieve from the `/users` endpoint. If omitted, fetch all roles.

  As an example, to fetch the 2nd page of admins from the API, `getUsers` might be called like:  
  `getUsers({page: 2, role: 'admin'});`

3. You can assume standard HTTP status codes on the response. If a request is unsuccessful, log an error message and recover.

4. Upon a successful API response, transform the payload into an object containing the following keys:
  - **ids**: An array containing the ids of all items returned from the request.
  - **smsUsers**: The total number of users returned where smsUser is true.


5. Return a promise from `getUsers` that resolves with the transformed data.

6. In index.html, display the results of the following request to the API:

  `getUsers({page: 2, role: 'admin'})`

7. You may display the information however you like. However we will be looking for well-formed, responsive HTML and CSS.

8. At the top of the page, list the ids of the returned admins and the total number of SMS users

9. Design should be informed by https://groundbase.io/


### API

The `/users` API endpoint returns a JSON array of items in the following format:

```json
[{
    "id": 1,
    "email": "janedoe@example.com",
    "familyName": "Doe",
    "givenName": "Jane",
    "role": "admin",
    "smsUser": true
  },
  {
    "id": 2,
    "email": "johndoe@example.com",
    "familyName": "Doe",
    "givenName": "John",
    "role": "standard",
    "smsUser": false
  }]
```

Each item returned from the `/users` endpoint will have:
- **id**: a unique integer
- **email**: string
- **familyName**: string
- **givenName**: string
- **role**: string ("admin" or "standard")
- **smsUser**: boolean

Additionally, the `/users` endpoint accepts the following options, sent as query string parameters on the request URL:
- **limit**: The number of items to be returned
- **offset**: The index of the first item to be returned
- **role**: Which role to include. If omitted, all roles will be returned.

An example request URL might look like:

`/users?limit=20&offset=2&role=admin`

### Additional Requirements

- Write your solution using ES2015. You may use any methods or syntax supported by Babel.
- Use the Fetch API to interact with the records endpoint.
- Please delete the `node_modules` directory before submitting your completed homework.

### Setup

**Requirements:** NodeJS > 4, npm  
`npm install` in `/` and `/users` to install  
`node users/index.js` to start server
