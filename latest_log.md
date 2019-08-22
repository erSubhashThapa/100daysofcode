## Day 34, R3
### 8/22/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I Left Off
  Yesterday, I continued action user verify. I added a database method that returns a value from the database. Today, I'll continue to work on the verify endpoint.

  ## Bcrypt Compare Return Promise?
  I was really confused about bcrypt.compare(). In the information when you hover over it, it says it returns a promise. At least that's what I thought it was saying:

  ![](log_imgs/compare_8-22-19.png)

  But when I called .then() on compare it didn't work:

  ```javascript
  bcrypt.compare(token, hashedToken, (err, isMatch)=>{
      if (err){
          return(cb(err));
      }
      return (isMatch);
  }).then(x=>console.log(x)); //TypeError: Cannot read property 'then' of undefined
  ```

  I think what compare is actually doing is returning a promise that, once resolved, gets passed in the callback as the second parameter, `isMatch`. So compare doesn't actually return a promise, it returns a resolved promise value to the callback.

  This threw me off for a while.

  If I want to use it as a promise I have to do it like this :
  ```javascript
  const someToken = process.env.TOKEN;
  const someHash = process.env.HASH;

  new Promise((resolve, reject)=>{
      bcrypt.compare(someToken, someHash, (err, isMatch)=>{
          if (err) reject(err);
          console.log(isMatch);
          if (isMatch) resolve({isMatch});
      })
  }).then(x=>console.log(x))
  ```

  ## Testing
  I created a `bin/test.js` file where I require different functions and test them.

  ## `.env` Bug
  I ended a line with a variable in `.env` with "`;`" and that's wrong. 

  `SOMEVAR = 'something';`
  
  You don't end lines with a semi colon in a `.env` file. It will make your variable include the semicolon.

  ## Where I Left Off
  I did a lot of debugging and testing today. It took me a while to understand what value `bcrypt.compare()` was returning and how to use it in a promise. Tomorrow, I'll use it in the verify endpoint.
  
  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/3cb8c5914f79831f26cb34d4295bc51d1b3446fd)

-  ## Thoughts And Feelings:
   Today I coded for a longer time. But I was also distracted for part of the time because I got some serious news and I'm shaken up. Hoping for the best and going to try to stay focused on coding and be there for my family.


