## Day 14, R3
### 8/2/19

- ## Chrome Extensions
  Yesterday, in my spare time, I started working on making chrome extensions.

  I found this repo of a bunch of chrome extension examples: [All Chrome Extension examples collected into one repository](https://github.com/orbitbot/chrome-extensions-examples)

  I played with this example: [A browser action with a popup that changes the page color](https://github.com/orbitbot/chrome-extensions-examples/tree/master/set_page_color)

- ## Node
 
  ### Where I left off:
  I added the session table and started adding the code for `action_session_create`. I'll continue that today.

  ## Sessions Question
  ***Do you create a new session for each device?*** If I log in a on a phone and then want to log in on a computer, should my app create two sessions?

  I think not, because here it says that you check if the session exists and then get it:

  ![](log_imgs/session_8-2.PNG)

  -*from [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087)*

  So then the way I logged out last time in [this project](https://github.com/DashBarkHuss/node_book/tree/5e8a6f8a9c93dab3264bab80b176986cdbaddba0) I think I did it wrong. I just deleted the session. But that would log every device out that's using that token.

  ## Promise Error
  I wondered how do I exit a long promise chain?

  I found this answer in [Early Returns out of a long promise chain](https://github.com/petkaantonov/bluebird/issues/581):

  > An answer on stackoverflow suggests throwing and error and then catching it.

  Info on errors: [JavaScript Errors - Throw and Try to Catch](https://www.w3schools.com/js/js_errors.asp)

  I added a throw statement and a catch statement:
  ```javascript
  fetch('http://127.0.0.1:3000/api/user/login', 
  payload)
  .then(promise=>promise.json()
  ).then(content=> {
      console.log("content:",content)
      if(content.success==true){
          return fetch("http://127.0.0.1:3000/api/session/create", payload)
      }
      throw content.message; //throw error
  }).then(promise=>promise.json()
  ).then(json=> console.log(json)
  ).catch((error) => { console.log("err:", error) }); //catch error
  ```
  ## Sessions & Login
  Now the sessions are managed and the login works. But I still need to move the login code to the UI and then save the token to local storage.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/f15b0b658ddad027ee37915bf392963e27cca682)

  ## Login UI
  I started to add the login UI but it's not working yet. I'll continue tomorrow.

