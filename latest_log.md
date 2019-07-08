## Day 89, R2
### 7/8/19

- ## Twitch
  I played with streaming on twitch. But it slowed down my computer so much. I explained my AR project. 
  
  I decide not to twitch my node project because it was slowing my computer down. My computer's been acting weird anyways so I should get it taken in.


- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ## Tracing Where `action_create_session` Gets Called
  Yesterday I left off trying to find where `action_create_session` get's called or if it's even getting called.

  ## The function itself in api.js on line 233:
  ```javascript
  //line 233, api.js
  function action_create_session( request, payload ) { 
    // Create unique authentication token
    function create_auth_token() {
        let token = md5( timestamp( true ) + "");
        return token;
    } //...
  ```
  ## A reference to the function in api.js on line 336:
  ```javascript
  Action.create_session = action_create_session;
  ```

  ## The reference getting called conditionally in api.js on line 392:
  ```javascript
  //line 392, api.js
  if (identify("session", "create")) // Create session 
    Action.create_session( request, json( request.chunks ) )
    .then( content => respond(response, content) );
  ```
  ## Where Does `identify()` Get Called?
  I added a log statement to the `identify()` function.
  
  ```javascript
  //line 310, api.js
  function identify(a, b) { 
  console.log("identify");
    return API.parts[0] == "api" && API.parts[1] == a && API.parts[2] == b;
    }
  ```

  I thought it *wasn't* getting logged because I was looking at the *browser console*. It was instead getting logged in the *terminal*.

  ## Git Repo
  I broke my code, but pressed 'undo' until it worked again.

  I need to version control this because if I screw it up and can't get it back, that would be bad. 

  I forked javascript teachers repo, and then added that as the remote for my local repo:
  
  [Adding a remote](https://help.github.com/en/articles/adding-a-remote)

  ## Logging
  I'm used to DevTools that I forgot the amount of debugging you could do with log statements. So I was playing with logging and started to understand a lot more of the code.

  ```javascript
  // line 309, api.js"
  function identify(a, b) {
    console.log(`API: ${API}`); //returned the entire API class from line 345, api.js
    console.log(`a: ${a}, b:${b}`); //a: user, b:authenticate
    console.log(`identify, line 3:11, API.parts: ${API.parts}`);//identify, line 3:11, API.parts: api,user,login


      return API.parts[0] == "api" && API.parts[1] == a && API.parts[2] == b;
  }
  ```





