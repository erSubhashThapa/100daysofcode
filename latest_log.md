## Day 39, R3
### 8/27/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.


  ### Where I Left Off
  I found a few ways to get a child module to access a variable from the main module. I didn't do much with my app but I did a lot of sandbox learning by playing with node in the debugger. Tomorrow, I'll try to get back to the app.

  ## Changing identify()
  api.js `require`s helpers.js. But I also need helpers.js to `require` api.js so it has access to `API.parts` which `helpers.identify` uses. 

  This circular requiring is causing issues. I haven't figured out when exactly to export the api module so that it doesn't export an empty object.
  
  I could just rewrite `identify` so that you pass `API.parts` as an argument. I didn't think this was as clean, but now I'm thinking it will be cleaner code than what I'm doing now.

  I decided  to go with changing `identify` so that the last argument is `Api.parts`.

  ```javascript
  // line 40, helpers.js
  helpers.identify= function(){ 
          const arr = [];
          for (i = 0; i<arguments.length-1; i++){arr.push(arguments[i])};
          const parts = arguments[arguments.length-1];
          return JSON.stringify(arr) == JSON.stringify(parts.slice(1, 3));
  }

  // line 103, api.js
  if(identify('user', 'register', API.parts)){
      ...
  ```

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/a64ce9128162d23ad0554a4123ac62e742bd6bb6)

  ## database.js Mess
  I had made all these database helper functions but I need to rewrite them so they can be used more generally. That's causing issues. This is where I left off.