
## Day 92, R2
### 7/11/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ## `catchAPIrequest(request)` Trace

  I logged the trace to see when `catchAPIrequest(request)` is called.

  ```javascript
  // line 405, api.js
  static catchAPIrequest(request) {
    console.log("catchAPIrequest");
    console.trace();
    ...
  /*  catchAPIrequest
      Trace
          at Function.catchAPIrequest (/Users/dashiellbark-huss/Documents/100daysofcode/node-master/module/api/api.js:407:15)
          at ReadFileContext.callback (/Users/dashiellbark-huss/Documents/100daysofcode/node-master/index.js:34:25)
          at FSReqCallback.readFileAfterOpen [as oncomplete] (fs.js:230:13)
  */
  ```

  Some `fs` function calls `fs.readFile()`, which calls `catchAPIrequest(request)`.
  ```javascript
  //line 31, index.js
  fs.readFile(filename, function (error, content) {
      if (error) {
          if (error.code == 'ENOENT') {
              if (API.catchAPIrequest( request.url ))
                  API.exec(request, response);
  ...
  ```

  ## `http.createServer(requestListener);`
  `fs.readFile()` gets called in the `http.createServer()` callback. This callback is called the requestListener function.
  >The HTTP Server object can listen to ports on your computer and execute a function, a requestListener, each time a request is made.


  -*[Node.js http.createServer() Method](https://www.w3schools.com/nodejs/met_http_createserver.asp)*

  ### requestListener:
  >Specifies a function to be executed every time the server gets a request. This function is called a requestListener, and handles request from the user, as well as response back to the user.
  
  -*[Node.js http.createServer() Method](https://www.w3schools.com/nodejs/met_http_createserver.asp)*

  So every time the server gets a request, these functions are executed: the requestListener, `fs.readFile()`, and then conditionally `API.catchAPIrequest( request.url )`.

  ## Chain Of Events: Login
  Now I understand the chain of events. Here is how it works with logging in for example.

  ### UI Calls User.Login
  ```html
  <!--line 161, index.html-->
  <input type="button" onclick="User.login({username:'felix',password:'password'})"
  value="log in as user felix / password (check session)" /><br />
  ```
  **The function call in the above button:** `User.login({username:'felix',password:'password'})`

  ### User.login Makes A Fetch Request
  ```javascript
  // line 70, index.html
  /* Login and create user session (if credentials match)
    payload = {
    username: "username",
    password: "password" } */
  User.login = function(payload) {
      fetch("/api/user/login", make(payload)).then(promise => promise.json()).then(json => {
          console.log(json);
      });
  }
  ```

  Fetch makes a request using the relative path `"/api/user/login"`. 
  
  *I'm not totally sure about this part but I think*: This isn't an actually path so we have to use this info to conditionally call different parts of the API. We'll look at that later.

  ### The HTTP server object hears the request
  The HTTP server object, created by http.createServer(), listens to ports on your computer. When a request is made it executes the requestListener callback:

  **Syntax**:
  ```javascript
  http.createServer(requestListener)
  ```

  ### requestListener is executed

  ```javascript
  http.createServer(function(request, response) { //the requestListener
    // skipping code here ...
    fs.readFile(filename, function (error, content) { 
    // skipping code here ... 
      if (API.catchAPIrequest( request.url ))
                      API.exec(request, response);
      // ...
  ```
  From here we get to `API.catchAPIrequest( request.url )`.

  ### `API.catchAPIrequest( request.url )` is executed

  >Static function API.catchAPIrequest will return true if the request.url matches our API pattern. We will cancel serving the file as usual in this case.
  >
  >The static API.parts property stores the parts of the API call in an array. For example localhost:3000/api/user/get becomes: ["api", "user", "get"]. Based on these values we can tell our server what to do (execute MySQL query, etc.)

  -*[Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).*

  ```javascript
  // line 405, api.js
  static catchAPIrequest(request) {
    request[0] == "/" ? request = request.substring(1, request.length) : null;
    if (request.constructor === String)
        if (request.split("/")[0] == "api") {
            API.parts = request.split("/");
            return true;
        }
    return false;
  }
  ```
  `catchAPIrequest(request)` does two things:
  - Stores the parts of the request in API.parts
  - returns true if the first part of the fetch resource is `api`

  If `catchAPIrequest(request)` returns true, `API.exec(request, response)` gets executed.

  ### `API.exec(request, response)` is executed

  ```javascript
  // line 348, api.js
  static exec( request, response ) {
    ...
  ```
  Inside `exec` we start reading the POST data chunks:

  ```Javascript
  //line 358, api.js
  // Start reading POST data chunks
  request.on('data', segment => {
      if (segment.length > 1e6) // 413 = "Request Entity Too Large"
          response.writeHead(413, {'Content-Type': 'text/plain'}).end();
      else
          request.chunks.push(segment);
  });
  ```

  Then we finish reading the POST data:
  ```javascript
  // line 366, api,js
  // Finish reading POST data chunks
  request.on('end', () => { // POST data fully received

      API.parts = request.parts;

      if (identify("user", "register")) // Register (create) user
          Action.register_user( request, json( request.chunks ) )
          .then( content => respond(response, content) );
                      
      if (identify("user", "login")) // Log in
          Action.login( request, json( request.chunks ) )
          .then( content => respond(response, content) );
      // ...
  ```
  ### `identify("user", "login")` returns true
  `request.on('end')` check to see if `identify()` returns true for a bunch of different values. Here's `identify`:

    ```javascript
  //line 310, api.js
  function identify(a, b) { 
  console.log("identify");
    return API.parts[0] == "api" && API.parts[1] == a && API.parts[2] == b;
    }
  ```

  We're logging in, so `identify()` will return true in the if-statement with the params `identify("user", "login")`.

  ```javascript
  // line 375, api,js
  if (identify("user", "login")) // Log in
      Action.login( request, json( request.chunks ) )
      .then( content => respond(response, content) );
  ```
  Then `Action.login` is executed.


  ### `Action.login( request, json( request.chunks ) )` is executed
  Action.login is action_login:
  ```javascript
  // line 333, api.js
  Action.login = action_login;
  ```

  ```javascript
  // line 196, api.js
  function action_login ( request, payload ) {
    return new Promise((resolve, reject) => {
        // First, get the user from database by payload.id
        let query = `SELECT * FROM \`user\` WHERE \`username\` = '${payload.username}'`;
        console.log(query);
        // ...
  ```
  This function makes the necessary query.

  ## Creating A Session

  Now that we know the chain of events, we can figure out hot to link up `action_create_session` to the chain.


  ```javascript
  // line 233, api.js
  function action_create_session( request, payload ) {
    // Create unique authentication token
    function create_auth_token() {
      let token = md5( timestamp( true ) + "");
        return token;
    } 
    //... more code
  ```
  ## Session Path
  From looking at the code, I can see that the path to create a session needs to be `api/create/session`



  ```javascript
  //  line 392, api.js
  if (identify("session", "create")) // Create session
      Action.create_session( request, json( request.chunks ) )
      .then( content => respond(response, content) );
  ```

  ### However, in the frontend API *(index.html, on line 10)* there is no function that makes this fetch request.

  This is where the problem is!

  Tomorrow, I will make this function.