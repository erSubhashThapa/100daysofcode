## Day 13, R3
### 8/1/19

- ## Node
  New month! I looked back at my  posts from a month ago. It feels like progress is so slow, but looking back, I can see I accomplished a lot. I hadn't even connected my database to any Node app yet. Since then, I've connected databases to apps multiple times. I've also figured out so much about creating a node app on my own, soldiering through many issues that the book tutorial hadn't addressed.
  
  ### Where I left off:
  Yesterday, I continued my Node app that will have CRUD *and* sessions/logins so I can get more practice with sessions.

  I started to add the database query. I'll continue that today.

  ## Database Query
  I got `action_user_login` to query the database to see if the username passed into the payload exists.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/92889e68b0ba588a44ffe299227199bd6ac8d12c)

  ## MD5
  I added the md5 package with --save-dev:
  ```bash
  npm install md5 --save-dev
  ```
  And required it in api.js:
  ```javascript
  const md5 = require('md5');
  ```

  ## `action_user_register`
  I added action_user_register. Now users can register with just a username and password. MD5 encrypts the password.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/212e3f9fd91cc07ae36ce2f72c4e0e93fb762869)

  ## Login Checks Password
  `action_user_login` only outputs a message that the user logged in if the passwords match. No session is created yet.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/801b6518d5dc246780beb1c8f9336ac516bf805d)

  ## `action_session_create`
  I added the session table and started adding the code for `action_session_create`. I'll continue that tomorrow.
