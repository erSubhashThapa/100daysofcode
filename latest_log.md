## Day 36, R3
### 8/24/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I Left Off

  I need to get my verify endpoint working but the promises are all messed up. That's where I left off. I'll continue here.

  ## Undefined Variable in Promise
  I was having a bunch of issues with a new Promise statement. It turns out there was an undefined variable in the promise. Normally, node would give me a reference error if I had an undefined variable. But because the variable was in a promise, it didn't behave the same. It was evading my capture! The code in the promise would stop with no error, but the rest of the code would go on. 

  So, after all that there may have been nothing else wrong with my promise chain. 

  ## Resolve and Reject Switched
  I ended up having another issue: resolve and reject were switched in the parameters:
  ```javascript
  //wrong way:
  return new Promise((reject, resolve)=>{
      
  //right way:    
  return new Promise((resolve, reject)=>{
  ```

  ## Throw, Reject, Resolve

  I made this script to see the difference between throw, reject, and resolve.

  ```javascript
  const timeOut = (x)=>{
      return new Promise((res, rej)=>{
          setTimeout(function(){ 
              res(x); 
          }, 0);
      })
  }

  function prom(x){
      return new Promise((resolve, reject)=>{        
          timeOut(x)
          .then(x =>{
              console.log(".then #1 arg:", x);
              if(x=="throw") throw(x)
              if(x=="reject") reject(x)
              if(x=="resolve") resolve(x)
          })
          .then(x=>{
              console.log(".then #2 arg:", x);
              resolve("2nd resolve");
              reject("2nd reject");
              return x
          })
          .then(x => {
              console.log(".then #3 arg:", x);
          })
          .catch(error=>{
              console.log("catch");
              console.log(error);
              reject("catch error: " + error)
          });
      });
  }
  ```

  I called prom with `"throw"`, `"reject"`, and `"resolve"` like this:
  ```javascript
  prom("resolve").then(x=>console.log("final resolved:", x))
  .catch(rejected=>console.log("final rejected: ", rejected))
  ```

  ### **Console Logs:**
  In every situation, the second reject and resolve calls- `reject("2nd reject")` and `resolve("2nd resolve")`- were ignored.

  ### **Resolve** 
  **Resolve** executed the `.then()` chain inside `prom()` but didn't pass them any promise values. It sent the promise value back to the `prom("resolve")` call and executed it's `.then()`s:
  
  ```
  test.js:50 .then #1 arg: resolve
  test.js:71 final resolved: resolve
  test.js:56 .then #2 arg: undefined
  test.js:62 .then #3 arg: undefined
  ```
  ### **Reject** 
  **Reject** also executed the `.then()` chain inside `prom()` and didn't pass them any promise values. The final `.catch()`, on the promise chain of where we called `prom("resolve")`, was executed but the `.then()`s were skipped:

  ```
  test.js:50 .then #1 arg: reject
  test.js:56 .then #2 arg: undefined
  test.js:72 final rejected:  reject
  test.js:62 .then #3 arg: undefined
  ```
  ### **Throw** 
  **Throw** skipped all the `.then()` calls inside `prom()` and executed `.catch` inside `prom()`. Because we call `reject()` in that first `.catch()` body, the program also executes the final `.catch` at the end of the `prom("throw")` call:

  ```
  test.js:50 .then #1 arg: throw
  test.js:65 catch
  test.js:66 throw
  test.js:72 final rejected:  catch error: throw
  ```

  My conclusion: **Throw** means skip the rest of the `.then()` executions, execute `.catch()`. **Reject** means continue calling the next `.then()`s in the chain but without a promise value. Send this promise value back and skip the `.then()`s on that chain. Instead execute the final `.catch()`. **Resolve** means continue calling the next `.then()`s in the chain but without a promise value. Send back the value and execute the remaining `.then()`s on that promise chain.

  ## Where I Left Off
  I spent the day again trying to understand promises instead of working on my app. Tomorrow, I'll really finish that verify endpoint!