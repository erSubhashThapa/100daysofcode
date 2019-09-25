
## Day 68, R3
### 9/25/19
- ## Node
  ## Where I Left Off
  I started working on getting Socket IO to send data to localStorage when the database is updated.

  ## Socket IO And Database Changes
  I'm wondering, if the database updates, is there a way to trigger some action so socket io can update the client?
  The obvious way would be to emit an event when the code inserts successfully in the database. This seems like it would work mostly, but it would not work if I manually added data to the database.

  I looked into datbase triggers, but I'm not sure what they are, it just sounded right:

  - [What is a Database Trigger?](https://www.essentialsql.com/what-is-a-database-trigger/)
  - [Introduction on Triggers](https://www.w3resource.com/mysql/mysql-triggers.php)

  I think these only trigger SQL actions.

  ## To Fix
  In my app, the client fetches all the Rc's since the last rc. But it should only do that if the last Rc is from today. Otherwise it should clear all the RC's. So I need to fix that.

  ## Nodemon In Two Terminals?
  Can I run two different script in two different terminals using nodemon? I want to run my regular server and my socket server with Nodemon. Right now, I can't because they're on the same port. But can I have them on two different ports?

  Looking at this `package.json`:

  ```javascript
  {
    "name": "my-node-api",
    "version": "0.5.0",
    "description": "API for serving cannabis data",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "start": "PORT=4200 node server.js",
      "dev": "NODE_ENV=test PORT=4205 nodemon server.js"
    },
  }
  ```
  -from *[Make a NodeJS API with mySQL](http://stayregular.net/blog/make-a-nodejs-api-with-mysql)*

  Made me think I could control the port by running: `PORT=4205 nodemon somefile.js`. But the port didn't change.

  Now I see the port it's referring to is set in my app:
  ```javascript
  //index.js
  app.listen(3306, ()=>{console.log("listening")})
  ```
  I tested my other project- the Socket IO sample project: I was able to run two files using nodemon, so nodemon isn't the problem. It must be my express project.

  ## My App Can't Run Two Files on Nodemon
  My app can't run some two files at once on nodemon but for other given two files it works.

  - can: socket-server and timeHelper
  - can't: socket-server and index.js
  - can't: index.js and timeHelper

  When I can't run them at the same time, it's because I get this error: 
  ```bash
  Error: listen EADDRINUSE: address already in use :::3306
  ```
  That port is the port from:
   ```javascript
  //index.js
  app.listen(3306, ()=>{console.log("listening")})
  ```

  So I see now that when I run `nodemon timehelper`, index.js also runs. That calls `app.listen(3306...`. So if I also run `nodemon index.js`, they both run. Then `app.listen(3306...` runs twice.

  Ok so I found a weird solution. I changed the name of index.js to `indexo.js`. Now running timeHelper and socket-server doesn't also run `indexo.js`. So for some reason nodemon is always running whatever file is named index in the directory.

  
  After looking at this- [Nodemon index.js](https://stackoverflow.com/questions/42190362/nodemon-index-js), I think it's because nodemon runs whatever is in the `main` property in your package.json. In my case, `index.js` is in main.

  ## Socket IO update
  Now I got the socket to trigger an event on indexo.js when an RC is added to the database.

  But we want the event to be triggered on the client. So that's next.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/ef9f02e409a2c890633790d1dda518e6ef186916)

  ##  `http.Server(app)`
  I saw this weird line in the files for the video [Connect to Socket.io from the browser app](https://www.linkedin.com/learning/learning-node-js-2/connect-to-socket-io-from-the-browser-app):
  ```javascript
  const http = require('http').Server(app);
  ```
  I read about it a bit here: [http.createServer(app) v. http.Server(app)](https://stackoverflow.com/questions/26921117/http-createserverapp-v-http-serverapp)

  ## Where I Left Off
  I'm watching the LI Learning video [Connect to Socket.io from the browser app](https://www.linkedin.com/learning/learning-node-js-2/connect-to-socket-io-from-the-browser-app). I'm running into a weird error when I follow along:

  `Access to XMLHttpRequest at 'http://localhost:3000/messages' from origin 'http://127.0.0.1:3000' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.`

  Aren't these the same origin?:
    - 'http://localhost:3000/messages
    - 'http://127.0.0.1:3000'
  
  Localhost is the same as 127.0.0.1 and /messages isn't part of the origin, is it? So how are they not the same? What's going on?