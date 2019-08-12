
## Day 24, R3
### 8/12/19
- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Today, I'll work on connecting the database and handling API requests.
  
  ## Database
  I linked the app to the database:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/28a3df025ff366d3b5d3604c84b3a287bcd364c3)

  ## `catchAPIrequest`
  I  made the `catchAPIrequest` function that determines if the request url is an API request.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/781aca305804f7cccdbae3f73765207cb1dfe48d)

  ## Identify
  I made an identify function that identifies any amount of api parts using the arguments object:

  ```javascript
  //api.js line 16
  function identify(){
      const arr = [];
      for (i = 0; i<arguments.length; i++){arr.push(arguments[i])};
      return JSON.stringify(arr) == JSON.stringify(API.parts.slice(1, API.parts.length));
  }
  ```
  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/8580bcfab56b6fbca9570a7548aa6b73a69b7c8c)

  ## Register
  I started the register user api:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commits/master)

- ## Thoughts and Feelings
  Two flies were distracting me. When I killed them I finally could concentrate. Lesson: Kill flies.
