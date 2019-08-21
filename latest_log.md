## Day 33, R3
### 8/21/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I Left Off:
  I got bcrypt to recognize when a password matches a hashed password but I didn't put that function in the verify endpoint yet. That's what I'll do today.

  ## Debugging 
  Yesterday, I posted on twitter for help with debugging node. A lot of different tools were recommended: [Quokka](https://quokkajs.com/docs/index.html), [ndb](https://github.com/GoogleChromeLabs/ndb), and even the VSC debbuger. I tried them all. 
  
  It turns out VSC's debugger works for what I wanted, but I didn't know you had to pause the script to be able to call a function. In DevTools on the client side you don't have to pause a script unless the function is not in scope. I think scope works different in Node, so that's why I have to pause it.

  Quokka is interesting too. It works a bit differently. But the free version isn't helpful to me and I'm not sure if I want the paid version.

  ## Refactored handleContent

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/d650708888f1c1ac7cc520f0ab8f2383e3686b0c)

  ## Debugger Error
  I was getting this error when I tried to use the debugger in VSC:

  ```bash
  Error: connect ECONNREFUSED 127.0.0.1:3306
  ```

  It went away when I changed http.createServer to listen to port to 3306. I tried to figure out how to control what port the debugger uses but I couldn't find how.

  ## Where I Left Off
  I continued action user verify. I added a database method that returns a value from the database. Tomorrow, I'll continue to work on the verify endpoint.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/e70218f7463b7f34b964dd3d1a10f12691df3ec0)
