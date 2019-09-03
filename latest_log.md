## Day 46, R3
### 9/4/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I left off
  I refactored and worked on `action_sessions_get`.

  ## Passing Environment Variables Command Line

  ```bash
  commandline$ USER_ID=239482 USER_KEY=foobar node app.js
  ```

  ```javascript
  // app.js
  console.log(process.env.USER_ID) //239482
  ````

  [Setting Environment Variables for Node to retrieve Ask Question](https://stackoverflow.com/questions/22312671/setting-environment-variables-for-node-to-retrieve)

  ## Log Out
  I finished all the code dealing with logging in and out.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/8d5ac1738ad6085f1b63f68e33df491a5629b914)

  ## Statically Typed Languages
  While working with my own helper functions I thought, *"Wouldn't it be nice if I could tell Javascript what data types a function expects for its parameters?"*

  <img src="log_imgs/type_9-3.PNG" width=500>

  This way, I wouldn't have to go back to the function to check the parameter data types. I'd see them in the info popup pictured above. 

  But you can't do this in Javascript. [Javascript is not statically typed.](https://stackoverflow.com/questions/8407622/set-type-for-function-parameters) But **Typescript** is ES6 plus type hinting.

  ## Where I Left Off
  I started working on crud.

- ## Thoughts and Feelings:
  Some of my functions are counterintuitive. It's hard to remember what they take and what they return.  Good naming and design can help me remember what the function takes and returns. Good function design will speed up the coding process.
