## Day 29, R3
### 8/17/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Yesterday, I added bcrypt to my project. Today, I'll test it some more and push my progress. Then I'll continue with the next api endpoint.

  ## Bcrypt
  I got `bcrypt` working. It's more complicated to use than `md5` but more secure and slower. Maybe I'll use `bcrypt` for passwords and for session tokens I can use a faster hashing algorithm like `sha`. I wonder if it's ok to use `md5` for sessions?

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/cdff6894b7640781177c38b14d5c5b6076a384ab)

  I tried to use `sha512` but I didn't find a lot of info on it. For now I'll use bcrypt for sessions too.

  ## Playing With Promises
  I played around with promises in the browser using `setTimeout()` to get a better feel for how they work. 
  
  I want to figure out how to handle the data from two separate promises and put them together. I didn't quite figure it out yet. I think it involves some nesting. I'll continue here tomorrow.

  ```javascript
  // how do we get two values from asynchronous functions and put them into one object?
  // {firstval: "first value", secondval: "second value"}

  function prom1(){
    return new Promise ((res, rej)=> {
      setTimeout(
        ()=>res("first value"), 1000
      )
    })
  }

  function prom2(){
    return new Promise ((res, rej)=> {
      setTimeout(
        ()=>res("second value"), 1000
      )
    })
  }

  // Not working yet
  prom1().then(content1=>{
    return prom2().then(content2=> { return {firstVal: content1, secondVal: content2}});
  })
  .then(c=>console.log("c:",c))
  ```