## Day 35, R3
### 8/23/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I Left Off
  I did a lot of debugging and testing yesterday. It took me a while to understand what value `bcrypt.compare()` was returning and how to use it in a promise. Tomorrow, I'll use it in the verify endpoint.

  ## Promises
  I was having trouble using promises when I needed to get values from two asynchronous functions. I took some time to play with promises in the browser using setTimeout() to practice. 


  ```javascript
  const timeOut = ()=>{
    return new Promise((resolve, reject)=>{
        setTimeout(function(){ 
            resolve("first"); }, 0);
    }) // promise with PromiseValue = "first"
    .then(x=>{
           return new Promise((res, rej)=>{
            setTimeout(function(){ 
                res(`second, ${x}`); }, 0);
            })
    })  // promise with PromiseValue = "second, first"
    .then(x=>{return(`third, ${x}`)}) //promise with PromiseValue = "third, second, first"
  }
    
  timeOut() //promise with PromiseValue: "third, second, first"
  .then(x=>console.log(x)) // logs "third, second, first"
  ```
  I haven't figured out exactly what I was doing wrong before. I need to get my verify endpoint working but the promises are all messed up. That's where I left off. I'll continue here tomorrow

