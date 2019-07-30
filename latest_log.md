## Day 11, R3
### 7/30/19

- ## Node
  
  ### Where I left off:
  Yesterday, I continued my Node app that will have CRUD *and* sessions/logins so I can get more practice with sessions.

  I changed the status code for serving the 404.html file back to 200 and didn't test it with 404. I'll do that today.

  I need to better understand how fetch is working.

  ## Can Only Call `.json` Once
  You can only call `.json()` once on the response object for `fetch` otherwise you get this error:

  ``` bash
  Uncaught (in promise) TypeError: Failed to execute 'json' on 'Response': body stream is locked
  ```

  ### NO:
  ```javascript
  fetch('http://127.0.0.1:3000/api/lol')
  .then(promise=>{
    console.log("response: ", promise);
    console.log(".json(): ", promise.json()); // 1st time
    return promise.json(); // 2nd time
  });
  ```
  ### YES:
  ```javascript
  fetch('http://127.0.0.1:3000/api/lol').then(promise=>{
    console.log("response: ", promise);
    const json = promise.json(); // set promise.json() to variable
    console.log(".json(): ", json)
    return json;
  });
  ```

  ## Reviewing Fetch
  I reviewed the docs for using the fetch API: [Using Fetch
](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) and [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

  ## Fetch UI
  I have a working fetch call on the UI that is simplified, so it demonstrates better what's going on with fetch:
  
  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/tree/c8ec88b8bc7ca0dee96c9f3dffd33f001784f033)

  ## 404 Status Code
  I changed the status code back to 404 and it still serves the 404.html file.

  ## `catchAPIrequest` and `respond` helper
  I added the static API method `catchAPIrequest()` to see if the request is an API request. I moved the body of `respond.on('end')` to a `respond` helper function.  

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/95d4a9b5293cc3d0c8d44fdc316b341e0b54005d)

  ## Removed Body Of `request.on('data')`

  I realized since we have no payload yet, the body of `request.on('data')` didn't do anything. So I removed the body for now. I still needed `request.on('data', ()=>{})  ` or `request.on('end')` wouldn't get called. 
  
  I also added an `identify()` helper and `action_user_login` with no body.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/e32b27f1c5d9c572819ce952484cb0c8c978c3e1)

  ## Tomorrow
  Tomorrow, I'll continue adding to the login API endpoint.