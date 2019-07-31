## Day 12, R3
### 7/31/19

- ## Node
  
  ### Where I left off:
  Yesterday, I continued my Node app that will have CRUD *and* sessions/logins so I can get more practice with sessions.

  I started the login API endpoint and I'm continuing that.

  ## Promise Syntax
  I had a really weird error where my a promise constructor executor was catching an error but the error was the resolve value. It was because I had switched the order of the parameters for the executor. I did `(reject, resolve)` but it should be `(resolve, reject)`.

  [Promise Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
  ### No:
  ```javascript
  return new Promise((reject, resolve)=>{ //wrong order
      if (!payload){
          reject("Oops no payload")
      };
      resolve(`{"success": true}`); 
  }).catch((error) => { console.log("err:", error) });
  ```
  ### Yes: 
  ```javascript
  return new Promise((resolve, reject)=>{
      if (!payload){
          reject("Oops no payload")
      };
      resolve(`{"success": true}`); 
  }).catch((error) => { console.log("err:", error) });
  ```

  ## `action_user_login` Returns Promise
  Now `action_user_login` returns a promise.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/10414a907e0f55ee02e5c9c6a3198a222455e180)

  ## `request.on('data')`
  I added the callback function for `request.on('data')` and added a payload to my test fetch call.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/0cb8e2aa5b26a5327f26f227f0ab5c711f7f34b6)

  ## Database Class
  I added the database class and created a connection to the database.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/a79461e580773cffec62d1d13a8ddc9efc309dd9)

  ## Database Connection Query
  I started to add the database query. I'll continue that tomorrow.