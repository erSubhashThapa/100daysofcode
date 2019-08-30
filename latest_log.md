## Day 42, R3
### 8/30/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ### Where I Left Off:
  Yesterday I had a stomach ache and fever so I had a hard time concentrating. I didn't get a lot done on the app, but I started watching some videos on React and Express. Today, I'll continue working on the login endpoint.

  ## `userLoggedIn`
  I created a function that checks if the user is logged in. It's not totally finished. I think it only works if the user is logged in right now. I committed it because I wanted to explore how to make the code more efficient.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/7f721328c304862b81ec20a3a55687b1f04fae61)

  ## Loops and Promises
  In `userLoggedIn`, I use a for loop to see if any of the session tokens in the database for the user in match the payload token. This seems inefficient. If any of the tokens match, the for loop still continues. Even if I used do while, I don't think it would work because the function in the for loop that checks if the tokens match is asynchronously itself. I skimmed [JavaScript async and await in loops](https://zellwk.com/blog/async-await-in-loops/), I'm not sure if this has the answer.

  I'm noticing there's a lot wrong with this function but I'm paisting it just to show where the for loop is.
  ```javascript
  function userLoggedIn(request, payload){
    //promise that returns boolean
    return new Promise((resolve, reject)=>{
        if (!payload.token) throw false;
        database.findValues('sessions', 'token', `username='${payload.username}' AND useragent = '${request.headers['user-agent']}'`)
        .then(results=>{
            if (!results.success) throw false;
            return new Promise((res,rej)=>{
                for(i=0; i<results.results.length; i++){
                    compareHash(payload.token, results.results[i].token)
                    .then(isMatch=>{
                        console.log(isMatch, 129);
                        if (isMatch) res(true); //or resolve
                    })
                }
            })
        })	        
    })
    .then(loggedIn=>console.log({loggedIn, line: ".then 135"}))
    .catch(loggedIn => {console.log({loggedIn, line: "catch"})})
  }
  ```

  ## Twitter API
  Yesterday, I reapplied to the Twitter API key. Last time I was rejected. I'm applying again on a different account, because you can't reapply on an account that was once rejected. So I created a new account. I'm also applying with a different project. Today, I got an email, asking for more information. So I spent sometime replying to that email.

  ## Where I Left Off:
  I'm working on looping with promises in `userLoggedIn`.
