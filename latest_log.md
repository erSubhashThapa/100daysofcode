
## Day 91, R2
### 7/10/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ## Is `http.IncomingMessage` An Instance Of `EventEmitter`?

  Yesterday, I wanted to know if `request` was an instance of `EventEmitter` because It had the `.on()` method.

  >The on method binds an event to a object.

  -*[In node.js “request.on” what is it this “.on”](https://stackoverflow.com/questions/12892717/in-node-js-request-on-what-is-it-this-on)*

  >All objects that emit events are instances of the `EventEmitter` class.

  -*[Events](https://nodejs.org/api/events.html#events_events)*

  `request` is the identifier for an `http.IncomingMessage` object. So we need to know if `http.IncomingMessage` is an instance of `EventEmitter`.

  ## Tracing The Prototype Chain
  I used `Object.getPrototypeOf()` and `.__proto__` to trace the prototype chain of `http.IncomingMessage`. More on that here: [Tracing Javascript’s Prototype Chain](https://alanstorm.com/tracing-javascripts-prototype-chain/)

  The first object that `http.IncomingMessage` inherits from is `Readable`:
  ```javascript
  console.log('proto', Object.getPrototypeOf(http.IncomingMessage));
  /*  proto [Function: Readable] {
      ReadableState: [Function: ReadableState],
      _fromList: [Function: fromList],
      from: [Function]
    }  */
  ```

  If you trace back the inheritance chain, you find that yes, **`http.IncomingMessage` does inherit from `EventEmitter`.**

  ```javascript
  console.log('proto', Object.getPrototypeOf(http.IncomingMessage).__proto__.__proto__);
  /*  proto [Function: EventEmitter] {
      once: [Function: once],
      EventEmitter: [Circular],
      usingDomains: false,
      defaultMaxListeners: [Getter/Setter],
      init: [Function],
      listenerCount: [Function]
    }  */
  ```

  ## `http.IncomingMessage` inherits from `EventEmitter`
  This also means `request`, which is an `http.IncomingMessage` object, is an instance of `EventEmitter`.

  So now I know that `request.on()` is the `emitter.on()` method and not some other "on" method.

  ## Clarify Questions
  I looked back at my questions from yesterday to get back to what I was trying to figure out. I now wonder:

  ## How is the UI making requests?
  Let's look at the login button:

  ```html
  <!--line 161, index.html-->
  <input type="button" onclick="User.login({username:'felix',password:'password'})"
  value="log in as user felix / password (check session)" /><br />
  ```

  **The function call in the above button:** `User.login({username:'felix',password:'password'})`

  ### User.login:
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

  I'm totally sure how the URL `"/api/user/login"` works.

  I think it has something to do with this method in the API class:
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
  When is `catchAPIrequest(request)` called?

  I logged the trace to see.

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

    

  