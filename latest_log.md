## Day 17, R3
### 8/5/19


- ## Node
 
  ### Where I left off:
  I started to make the logout endpoint. It's not working. The session is still in the table. 

  ## Logout Deleting Session
  I got the logout to delete the session. I had the syntax wrong for the ip and the user-agent. Here's how it should be:

  ```javascript
  // api.js
  const q = `Delete from session where ip = '${request.connection.remoteAddress}' AND useragent='${request.headers['user-agent']}'`;
  ```
  ## Logout UI Working
  The logout is working on the UI.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/7a349c37fec8a014063470d919e8354585c8e434)

  ## Register UI
  I added a UI for register. But register doesn't log you in on the new account yet.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/f6e343c75db923d2493e7d2c00f59bb2b9c17988)

  ## Create Session On Frontend?
  Right now I have `action_create_session` being called from the frontend if the password and username match and the success property returns true.

  ```javascript
  // index.html
  const login = (payload) => {
      payload = makePayload(payload);
      fetch('api/user/login', payload
          ).then(promise=>promise.json()
          ).then(content=> {
              console.log("content:",content)
              if(content.success==true){
                  return fetch("api/session/create", payload)
              }
              throw content.message;
          }).then(promise=>promise.json()
          ).then(json=> {
              console.log(json)
              localStorage.setItem('token', json.token);

          }).catch((error) => { console.log("err:", error) });
  }
  ```
  I'm not sure if this is secure enough. I think I should add that the passwords need to match in the `action_create_session` function on the backend. Or I need to call `action_create_session` from the `action_user_login` function instead of from the frontend.

  ## Create Session On Backend
  I moved `fetch("api/session/create", payload)` out of the frontend:
  ```javascript
  // index.html
  const login = (payload) => {
    payload = makePayload(payload);
    fetch('api/user/login', payload
        ).then(promise=>promise.json()
        ).then(json=> {
            localStorage.setItem('token', json.token);
        }).catch((error) => { console.log("err29:", error) });
  }
  ```
  And into the backend:
  ```javascript
  if (identify('user', 'login')){
      action_user_login(request, payload )
      .then(content => {
          if(content.success == true){
              return action_session_create(request, payload); //create session
          }
          return content
      })
      .then(content=>{
          respond(response, content)});
  }
  ```

  And I removed the api url for `action_create_session`.

  This seems way more secure.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/51df969e52adda3e8362391ad4de4bb1f382da14)

  ## Register Creates Session
  Now register also creates a session, loggin the new user in.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/1c7d21af647c7df011879c4b2b0a20396181e215)

  ## Managing Sessions
  If I log in while someone is already logged in on that browser, the app writes over the last token without alerting them. I should probably make it so you cannot register or login while someone is already logged in.
  
  ## `action_session_get`
  This returns an object that tells us if anyone is currently logged in and who:

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/d975e04ec90c1945419f7fd7bba0fcd17b68c2de)

  Right now it won't work correctly if a token is sent in and that token isn't connected with any session. 
  
  Now it's fixed:

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/1b235f172b00f81f19379bdbdfade7e0876474ed)

  ## No Logging In If User Logged In
  I'm trying to make it so if the client tries to login but they're already logged in it won't let them. That's where I left off.
