
## Day 90, R2
### 7/9/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ## API Instance Of Class?
  Yesterday when I logged `API`, I wonder if the result was the API call or an instance of a class?
  
  I think it's the class. Because it's called 'API' and it logs `class API{...`. What confuses me is that `API.parts`changes. So it seems like it should be different instances of the API class.

  I looked over some things. It is logging the class. Inside the class, API.parts changes on line 369 with every new request.

  ```javascript
  // api.js line:369
  API.parts = request.parts;
  ```

  ## Clarify Questions
  I need to clarify what I'm trying to figure out so I know what to do next:

  ### Where does or where *should* `action_create_session` get called?
  - `request.on('end')`*(line 367, api.js)* conditionally calls `action_create_session`*(233)* if `identify("session", "create")`*(395, 310)* returns `true`
  
  ### So when is `request.on('end')` called and `identify("session", "create")` `true`?
  - ### `identify("session", "create")` is `true`
    - `identify("session", "create")` is `true` when the `API.parts` array is `["api", "session", "create"]`
  
      ```javascript
      // line 314 api.js
      return API.parts[0] == "api" && API.parts[1] == a && API.parts[2] == b;
      ```

    - `API.parts` is the same as `request.parts`
      ```javascript
      // line 369 api.js
      API.parts = request.parts;
      ```
  - ## `request.on('end')` gets called
    - I'm pretty sure it gets called when the http request gets sent back. I'm not totally sure how that works.
    - `request` is actually a parameter of  `exec()`
      ```javascript
      // line 348, api.js
      static exec( request, response ) {
      ```
  ### Where is `exec()` called and what is the argument for `request`?

  - `exec()` is called inside the `http.createServer` callback:

  - ```javascript
    // line 32, index.js
    API.exec(request, response);
    ```
    `createServer` and the `callback` are here:
    ```javascript
    //line 1 index.js
    let http = require('http');
    // line 16,index.js
    http.createServer(function(request, response) {
    ...
    ```
    The argument for request is the http request.

  ### Still not sure: when does `request.on('end')` get called?

  ## `request.on()`

  >The on method binds an event to a object.
  >
  >It is a way to express your intent if there is something happening (data sent or error in your case) , then execute the function added as a parameter.

  -*[In node.js “request.on” what is it this “.on”](https://stackoverflow.com/questions/12892717/in-node-js-request-on-what-is-it-this-on)*

  More about `.on` here: [emitter.on(eventName, listener)](https://nodejs.org/api/events.html#events_emitter_on_eventname_listener)

  ## EventEmitter

  >Much of the Node.js core API is built around an idiomatic asynchronous event-driven architecture in which certain kinds of objects (called "emitters") emit named events that cause Function objects ("listeners") to be called.

  >All objects that emit events are instances of the EventEmitter class. These objects expose an eventEmitter.on() function that allows one or more functions to be attached to named events emitted by the object. 

  -*[Events](https://nodejs.org/api/events.html#events_events)*



  Is `request` a kind of EventEmitter? Can I log it to find out?

  ## IncomingMessage Object
  `request` is an IncomingMessage object.

  >The IncomingMessage object is passed as the first argument in the requestListener function:

  -*[Node.js IncomingMessage Object](https://www.w3schools.com/nodejs/obj_http_incomingmessage.asp)*

  Is the IncomingMessage object  a kind of EventEmitter?

  According to [this page](http://www.acuriousanimal.com/2015/08/31/how-to-read-from-a-writable-stream-httpserverresponse-in-node.html), http.IncomingMessage is a readable stream. I'm not sure if it still can't inherit from EventEmitter though.

  ## Prototype Of An Object In Node?
  In DevTools I can `console.dir()` to find out an object's prototype. But in node when I `console.dir(http.IncomingMessage);` I just get `[Function: IncomingMessage]`.

    
    

  