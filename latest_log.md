
## Day 97, R2
### 7/16/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ### Update:
  I got in touch with Greg Sidelnikov ([js_tut](https://twitter.com/js_tut)). He said he's working on the update to the [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087) book. The issues I ran into may be addressed in the next update.

  ### Where we left off:
  The [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087) finished files ***didn't work***. Over the past few days, I got the session to save to the session table. Today, I'm going to try to save the token to the front end.
  
  ## Storing The Token

  Yesterday, I was trying to figure out where to save the token. Where would I put this? Does it go in `index.html`, `api.js`, or `index.js`?

  ## Clarify Questions
  I was trying different ideas with my code but I'm confused so I want to clarify my questions:
  Right now I'm calling `action_create_session` within `action_login`. This is a promise within a promise. 
  
  - ### How do I get the data from `action_create_session` to go to the UI if I'm not fetching it from the UI?
    - Should I instead fetch `action_create_session` from the UI?
      - Is that secure?

  ## Fetching `action_create_session`

  I moved the `action_create_session()` call from api.js, inside `action_login`
  ```javascript
  // line 218, api.js
  action_create_session(request, payload)
  ```

  To the frontend in a fetch api call:
  ```javascript
  // line 74, index.html
  User.login = function(payload) {
      fetch("/api/user/login", make(payload)).then(promise => promise.json()).then(json => {
          console.log(json);
          if (json.success===true){
            return fetch("/api/session/create", make(payload))
          }
      }).then(promise => promise.json()).then(json => {
          console.log(json);
      });
  }
  ``` 

  Fetching `"/api/session/create"` will call `action_create_session`.
  
  I'm just confused if this is secure. Could someone change `json.success` from `false` to `true` on the frontend and  create a session without a password? Idk.

  [Using a fetch inside another fetch in javascript
](https://stackoverflow.com/questions/40981040/using-a-fetch-inside-another-fetch-in-javascript)

  ## Git Diff
  I made a mistake in my files and I wasn't sure what it was so I tried to use [`git diff`](https://veerasundar.com/blog/2011/06/git-tutorial-comparing-files-with-diff/) to see the difference between my current commit and my commit before. It was really hard to read so I just looked at the difference on github.
  