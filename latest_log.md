## Day 37, R3
### 8/25/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I Left Off
  I spent the day yesterday trying to understand promises instead of working on my app. Today, I'll really finish that verify endpoint!

  ## module.exports All The Things!
  I'm refactoring my code and put my helpers into one file. I wanted to module.export all the functions so I followed this tutorial: [module.exports All The Things!](https://vancelucas.com/blog/module-exports-all-the-things/).

  >The way I have come up with to solve this in my own code is to create a single empty object literal at the top of the file named ns (for namespace). I then create functions on the ns object as I go, and export all the properties on the ns object at the end of the file.

  ```javascript
  var ns = {};
  // ...
  // Platform detection helpers
  var osname = Ti.Platform.osname;
  ns.isiPhone = function() {   return ('iphone' == osname); };
  ns.isiPad = function() {   return ('ipad' == osname); };
  ns.isiOS = function() {   return (ns.isiPhone() || ns.isiPad() || 'ios' == osname); };
  ns.isAndroid = function() {   return ('android' == osname); };
  // ...

  // Export all the things! *\('o')|
  for(prop in ns) {
     if(ns.hasOwnProperty(prop)) {
       module.exports[prop] = ns[prop];
     }
  }
  ```

  ## Arrow Functions: No Arguments Object
  >**Arguments object**
  >
  >Arrow functions don’t have the local variable arguments as do other functions. The arguments object is an array-like object that allows developers to dynamically discover and access a function’s arguments. This is helpful because JavaScript functions can take an unlimited number of arguments. Arrow functions do not have this object.
  
  *-[sitepoint.com](https://www.sitepoint.com/es6-arrow-functions-new-fat-concise-syntax-javascript/)*

  ## Where I Left Off
  I left off working on a helper function. It's being `require`d by `api.js`. But it cannot access a global variable of `api.js` anymore since it's in another file. I'm trying to figure out a way to access global variables of the main javascript file from required functions. I thought I could use a closure but that didn't work or I didn't do it the right way. I did finish the verify endpoint though!

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/506758e036bd7122c122462a500364cb66325a51)

