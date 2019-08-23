
# #100DaysOfCode Log - Round 3 - Dashiell Bark-Huss

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

## Day 33, R3
### 8/21/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I Left Off:
  I got bcrypt to recognize when a password matches a hashed password but I didn't put that function in the verify endpoint yet. That's what I'll do today.

  ## Debugging 
  Yesterday, I posted on twitter for help with debugging node. A lot of different tools were recommended: [Quokka](https://quokkajs.com/docs/index.html), [ndb](https://github.com/GoogleChromeLabs/ndb), and even the VSC debbuger. I tried them all. 
  
  It turns out VSC's debugger works for what I wanted, but I didn't know you had to pause the script to be able to call a function. In DevTools on the client side you don't have to pause a script unless the function is not in scope. I think scope works different in Node, so that's why I have to pause it.

  Quokka is interesting too. It works a bit differently. But the free version isn't helpful to me and I'm not sure if I want the paid version.

  ## Refactored handleContent

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/d650708888f1c1ac7cc520f0ab8f2383e3686b0c)

  ## Debugger Error
  I was getting this error when I tried to use the debugger in VSC:

  ```bash
  Error: connect ECONNREFUSED 127.0.0.1:3306
  ```

  It went away when I changed http.createServer to listen to port to 3306. I tried to figure out how to control what port the debugger uses but I couldn't find how.

  ## Where I Left Off
  I continued action user verify. I added a database method that returns a value from the database. Tomorrow, I'll continue to work on the verify endpoint.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/e70218f7463b7f34b964dd3d1a10f12691df3ec0)


## Day 32, R3
### 8/20/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ## Where I Left Off:
  Bcrypt isn't working as expected. For some reason it hashes the same token differently each time. I wonder if this has to do with the 'salt' which I didn't look into so much. I'll look more into bcrypt.

  ## Bcrypt `compare()`
  I found out that bcrypt isn't like md5. In Md5 in order to compare a password with a hashed password you'd do something like `md5(password) == hashedPassword`. Hashing a given password with `md5()` will always give the same output. But this isn't true with bcrypt. 

  If I hash a password with bcrypt, and then hash the same password again, I will get two different hashes. So, in bcrypt we use a different function to hash a password than to compare the password to its hashed version.

  The video [Compare Hash Password W/ Node.js & BCrypt](https://www.youtube.com/watch?v=Yc2VKb4_jdY) shows how to do this using the compare method.

  ```javascript
   function compareHash(token, hashedToken, cb){
      return new Promise((reject, resolve)=>{
          bcrypt.compare(token, hashedToken, (err, isMatch)=>{
              if (err){
                  reject(cb(err));
              }
              resolve(cb(null, isMatch));
          });
      });
  };
  ```

  ## Throw vs Reject

  > Any time you are inside of a promise callback, you can use throw. However, if you're in any other asynchronous callback, you must use reject.

  -*[JavaScript Promises - reject vs. throw](https://stackoverflow.com/questions/33445415/javascript-promises-reject-vs-throw)*

  I want to play around in with throw and reject to see the difference.

  ## Return vs. Resolve

  >The rule is, if the function that is in the then handler returns a value, the promise resolves/rejects with that value, and if the function returns a promise, what happens is, the next then clause will be the then clause of the promise the function returned, 

  -*[What's the difference between returning value or Promise.resolve from then()](https://stackoverflow.com/questions/27715275/whats-the-difference-between-returning-value-or-promise-resolve-from-then)*

  ## Debugging
  I'm trying to figure out what type of object bcrypt.compare returns and if it's asynchronous.

  On the browser, I'd just use the console to look into this. But how do I do it with node.js? 

  Using just console.log statements and test functions is ok. But there must be a better way.

  If I have a function `hi()` that's in a javascript file available to the client, I can test that in DevTools right in the console:

  ![](log_imgs/console_8-20-19.PNG)

  Is there a way to do this with vsc and node.js? Can I run a function in a node.js project directly from some console?

  Someone recommended I try I [Quokka](https://quokkajs.com/docs/index.html).

  ## Where I Left Off:
  I got bcrypt to recognize when a password matches a hashed password but I didn't put that function in the verify endpoint yet. That's what I'll do tomorrow.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/bdd36e71fcab50af943405b0b6464af7be4f4307)

## Day 31, R3
### 8/19/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  I left off working on the verification URL. That's where I'll continue. My code is getting cumbersome. I need to refactor it.

  ## Where I Left Off
  Not a lot of note taking today. 
  
  I did a lot of refactoring and drying my code today. 
  
  I got the verification URL working, sort of. The only thing is bcrypt isn't working as expected. For some reason it hashes the same token differently each time. I wonder if this has to do with the 'salt' which I didn't look into so much. I'll look more into bcrypt tomorrow.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/2a156a542d7f2a1587bf88272001f1a90b40d656)

- ## Thoughts and Feelings: 
  I took a longer break today. This helped me code longer in total. I normally code 2 hours. Today, I felt like I could keep going. So I did. It may have also helped that I took less log notes. Maybe notes are tiring.

## Day 30, R3
### 8/18/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Yesterday, I wanted to figure out how to handle the data from two separate promises and put them together. I thought I didn't figure it out. But it works now. So maybe I hadn't refreshed it.

  ## Returning Two Promises

  ```javascript
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

  prom1().then(content1=>{
    return prom2().then(content2=> { return {firstVal: content1, secondVal: content2}});
  })
  .then(c=>console.log("c:",c))
  //> c: {firstVal: "first value", secondVal: "second value"}
  ```

  ## Email Error
  I kept getting an error when trying to send an email using the `Nodemailer` module:

  ```bash
  Error: Missing credentials for "PLAIN"
  ```

  This was because in `createTransport` I had
  
   `password: process.env.GMAILPW` 
   
   instead of 
   
   `pass: process.env.GMAILPW`. 
   
   Here it's fixed:

  ```javascript
  const transporter = nodemailer.createTransport({
    service: 'gmail',
    auth: {
        user: process.env.GMAIL,
        pass: process.env.GMAILPW
    }
  })
  ```
## Git Issues
I'm wondering how people track issues that need to be addressed in their projects. I though you could track issues with git because I see issues posted on github repos.

I looks like [git isn't meant to track issues](https://stackoverflow.com/questions/7060973/keeping-track-of-to-do-and-issues-in-git) but you can use github to track issues: [About issues](https://help.github.com/en/articles/about-issues).

But maybe I just need to make a to do list.

## Where I Left Off
My register endpoint registers and sends a verification email. I left off working on the verification URL. That's where I'll continue tomorrow. My code is getting cumbersome. I need to refactor it.

[Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/581f4ee3c022ca354aa4f8e023f65310fb2050bb)



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

## Day 28, R3
### 8/16/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.
  
  Today, I'll continue working on my new branch that handles the returned promise from `database.existsIn`.

  ## `database.existsIn` Return Promise
  Now `database.existsIn` returns a promise. 

  [Link To Work]([`database.existsIn`](https://github.com/DashBarkHuss/crud_login_node_app/commit/3fa9b4f307af3b3b404eaf738fc1f042d034eff5))

  I still feel it could be more DRY.

  ## Branch and Merge
  I reviewed merging and merged my branch.

  [3.2 Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

  ## `database.insertIn`
  I added a method for database that inserts records called `database.insertIn()`:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/867e76f9bcfa7aa4860a74cd32173b325cf6fee6)

  ## Bcrypt
  I watched [How To Hash A Password W/ BCrypt](https://www.youtube.com/watch?v=lWDws1j8fo4).

  I didn't know what a salt was so I looked it up: [Salt (cryptography)](https://en.wikipedia.org/wiki/Salt_(cryptography)). I don't fully understand it, but it seems salts provide an extra layer of protection.

  ## Where I left off
  I added bcrypt to my project. Tomorrow, I'll test it some more and push my progress. Then I'll continue with the next api end point.

## Day 27, R3
### 8/15/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Yesterday, I started to create a database method that searches the database and returns `true` or `false` if the record exists. It's not working. I'll continue here

  ## Database Method Working
  My database method wasn't working because I didn't understand that .query() in MySQL is asynchronous. I thought I could just return a value from it

  ```javascript
  static existsIn(table, clause){
    const q = `select * from ${table} where ${clause};`
    this.connection.query(q, (err, results)=>{
        if (err) console.log(err);
        return results.length !== 0;
    });
  };
  ```

  This doesn't work. But I can resolve the promise from here:

  ```javascript
  static existsIn(table, clause, resolve, content){
      const q = `select * from ${table} where ${clause};`
      this.connection.query(q, (err, results)=>{
          if (err) console.log(err);
          if (results.length !== 0) resolve(content);
      })
  };
  ```
  This function made my code so much cleaner:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/3fa9b4f307af3b3b404eaf738fc1f042d034eff5)

  ## Resolve Overwriting
  I'm noticing that if I have multiple places where my promise can resolve it will resolve wherever it reaches the resolution first, it seems. But since I have places where the resolution is in an asynchronous function this confuses me. How do I make sure it reaches the right resolution first?

  ## Where I Left Off
  I worked  a lot on making the register API function DRY and readable. 
  
  I played around with promises. 
  
  I created a new branch to try out a different way of dealing with `database.existsIn()`. This other way returns a promise so you can handle the content within the api function. 
  
  I played with seeing where the code flows if you resolve it at different points. It seems so keep going on to the next `.then()` even if you resolve it. But it won't resolve again. I think if you throw an error it won't go on to the next `.then()`. That made me wonder if I should be throwing an error instead of resolving.
  
   Tomorrow, I'll continue working on my new branch that handles the returned promise from `database.existsIn`.


## Day 26, R3
### 8/14/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Last time I started making the API endpoint for registering a user. I'll continue here.

  ## Storing Session Key Incorrectly?

  I'm reading ['Re-Hashed: The Difference Between SHA-1, SHA-2 and SHA-256 Hash Algorithms'](https://www.thesslstore.com/blog/difference-sha-1-sha-2-sha-256-hash-algorithms/) and this made me think I'm storing session keys incorrectly:

  > the client generates a session key, then encrypts a copy of it and sends it to the server where it can be decrypted and used for communicating throughout the duration of the connection 

  I created the session key on the backend and just sent back the session key. Oh wait I know what I did. I created the session key by hashing a time stamp in the backend. So maybe I should have sent back the time stamp instead of the session key.

  I watched videos 3.1-3.6 of [Advanced Express](https://www.lynda.com/Node-js-tutorials/Advanced-Express/798496-2.html) to try to see if the token stored on the client side is different from what's stored on the database but I couldn't find anything.

  I read '[Should I also hash my session id before storing it in the database? [duplicate]](https://security.stackexchange.com/questions/138389/should-i-also-hash-my-session-id-before-storing-it-in-the-database)'. It brought up an unrelated point, that matching sessions to an ip might cause issues if the user is mobile. That can change the IP address, for example switching to a different wifi (I think). 
  
  I read [How to secure store sessions values in webapps?](https://security.stackexchange.com/questions/136122/how-to-secure-store-sessions-values-in-webapps) and this said you ***do*** want to hash the token and send the un-hashed token back to the browser. 
  
  This makes sense because if the database were accessed by a hacker and the tokens weren't hashed they could just use the tokens in the database to authenticate actions. Well, but why would that matter since if they have access to the database they can just change the database directly? Maybe there's some instances where a hacker can get the database info but can't change it.

  I found this [Session Management Cheat Sheet](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Session_Management_Cheat_Sheet.md) for best practices.

  ## Hashing Algorithm
  I couldn't find a straight answer on which hashing algorithm to use. So I posted to twitter. So we'll see what they say. I'll keep using md5 until I find something better. I know it's not supposed to be good but I'm not making anything real right now so it's ok.

  ## Where I left off
  I worked more on the api register endpoint. 
  
  I started to create a database method that searches the database and returns `true` or `false` if the record exists. It's not working. 

## Day 25, R3
### 8/13/19
- ## Arduino
  Today, I took a break from Node to work on a top secret arduino project that's 7 years in the making!

  Since it's top secret I don't have much to post. I'm taking notes else where. To the curious cats out there, don't worry: I will make my project public soon.

  A requirement of this project is a Twitter API key. It's been months and Twitter hasn't gotten back to me on the status of my API key application. Maybe I should contact twitter in some other ways?

  ![](log_imgs/arduino_8-13.jpg)

## Day 24, R3
### 8/12/19
- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Today, I'll work on connecting the database and handling API requests.
  
  ## Database
  I linked the app to the database:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/28a3df025ff366d3b5d3604c84b3a287bcd364c3)

  ## `catchAPIrequest`
  I  made the `catchAPIrequest` function that determines if the request url is an API request.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/781aca305804f7cccdbae3f73765207cb1dfe48d)

  ## Identify
  I made an identify function that identifies any amount of api parts using the arguments object:

  ```javascript
  //api.js line 16
  function identify(){
      const arr = [];
      for (i = 0; i<arguments.length; i++){arr.push(arguments[i])};
      return JSON.stringify(arr) == JSON.stringify(API.parts.slice(1, API.parts.length));
  }
  ```
  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/8580bcfab56b6fbca9570a7548aa6b73a69b7c8c)

  ## Register
  I started the register user api:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commits/master)

- ## Thoughts and Feelings
  Two flies were distracting me. When I killed them I finally could concentrate. Lesson: Kill flies.


## Day 23, R3
### 8/11/19

- ## Node 
  Two days ago I finished the Node login app. Now I'm going to try to make an app that has login and crud with authentication.

  ## MySQL Commands
  I wanted to practice making a database in the command line instead of in the GUI.
  ```sql
  mysql> create database crud_login_app;

  mysql> use crud_login_app;

  mysql> create table user (username VARCHAR(128), email VARCHAR(320), verificationToken CHAR(32), password CHAR(32), isVerified TINYINT(1));

  mysql> alter table user add id INT NOT NULL AUTO_increment Primary key;

  mysql> alter table user modify column id int first;

  mysql> alter table user alter isVerified set default 0;
  ```
  These commands created the `crud_login_app` database and the `user` table.

  ![](log_imgs/user_8-11-19.PNG)

  For the `sessions` table I only had to do one command because I got everything right in the first command:
  ```sql
  mysql> create table sessions ( id INT not null auto_increment primary key, token CHAR(32), username CHAR(128), ip CHAR(15), useragent VARCHAR(255));
  ```
  ![](log_imgs/sessions_8-11-19.PNG)

  ## What I Did Today
  I started the app. I completed most of `index.js` adding mime types this time.

  For more mime types: [Incomplete list of MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types)

  Here are all my commits for today:
  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commits/3ee477fbc8b49dd5d59bbe47f60e7ac23df6f37b)

  Tomorrow, I'll work on connecting the database and handling API requests.

## Day 22, R3
### 8/10/19

- ## Reviewing Front End  
  Today I took a break from node to review frontend and make a project. I started a new streak tracker.

  ## Classes
  I read about classes:
  [Javascript Classes — Under The Hood](https://medium.com/tech-tajawal/javascript-classes-under-the-hood-6b26d2667677)

  ## Tracker
  I ended with this for today. 
  
  ![](log_imgs/streak_8-10-19.png)
  [Link To Work](https://github.com/DashBarkHuss/streak-tracker/commit/38d9b33c83d909558ddd8022f2a34a694f5bebc5)

  I'll find some time to make it pretty.
  
  I also reviewed grid, and javascript dates.

- ## Thoughts and Feelings:
  Time went by really fast today. Probably because I was building something and reviewing old concepts instead of learning something new.

## Day 21, R3
### 8/9/19

- ## Node

  ### Where I left off
  I started to add the verification token to `action_user_register`. I'll continue here.

  ## Verification Token
  Now the `action_user_register` creates a verification token. Next we need to email the user the token url.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/100437c63cd464c5d02828c2d431096df982ed1f)

  ## How Is MD5 Secure?
  If all you have to do to translate md5 tokens is run md5(token), how is that secure? Couldn't anyone take that token and get md5 and run md5(token)? I'm thinking that maybe there's another step here.

  I read [WHAT IS THE DIFFERENCE BETWEEN HASHING AND ENCRYPTING](https://www.securityinnovationeurope.com/blog/page/whats-the-difference-between-hashing-and-encrypting). 

  I don't really understand how it works still.

  I read that [md5 isn't secure](https://searchsecurity.techtarget.com/definition/MD5). But I think the reason it's insecure is unrelated to what I don't understand about it. I think other hashing methods like SHA work the same way and they are secure but I still don't understand why.

  I watched this video [How hash function work?](https://www.youtube.com/watch?v=xsp--srKWKw) which helped me understand better. Also the teacher was funny.

  ## Email Verification
  The email verification is complete.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/e7a1b0c9825b31cf430783b3aba4fe53be40c7de)

  ## What's left?
  For learning purposes this app is complete. It demonstrates how to login/logout and register. 

  ### What is the app missing?
  - There's nothing stopping you from registering different usernames under the same email. 
  - A UI for resending the verification code
  - An endpoint that deletes or updates accounts
  - Some errors don't catch properly
  - Some promises should throw an error but they don't

  These would be the only things related to accounts that's missing. All of them are easy fixes. Obviously this isn't a very useful app because it does nothing but create users. But this is for demonstration purposes for myself and anyone else who wants to see how you can make an app with logins.

  ## Completed Project
  I added a readme.md. Here's the complete project:

  [Node Server Session](https://github.com/DashBarkHuss/node_server_sessions)

  ## Next
  I've put together a [CRUD app](https://github.com/DashBarkHuss/node_server_multiple_endpoints) and a [Sessions app](https://github.com/DashBarkHuss/node_server_sessions). Next I could put together an app that has both. I also wonder if I should learn express and when I should go back to learning react.

  I started this login app on 7/28, day 209. So this project took me 13 days. I wonder if I can do a combined crud and sessions app in a shorter amount of time. 

## Day 20, R3
### 8/8/19

- ## Node

  ### Where I left off
  I left off having created an email module. Today, I'm going to use that email module to make a verification email.

  ## Rejecting A Promise
  When do you reject a promise? It seems like anytime you could reject a promise you could also just resolve it with a message that says 'something went wrong'. Maybe it's when you don't want the rest of the `then()` functions to get called?

  ## Payload
  When you're not using fetch and you're just using a URL, where is the payload? Is it in the URL?

  I think maybe a payload is different than the parameters you send in a URL. It looks like you only send [a payload for a POST request and parameters for a GET request](https://stackoverflow.com/questions/14551194/how-are-parameters-sent-in-an-http-post-request). But what's really the difference? They seem the same? It seems like you could use POST or GET for the same thing. Is POST more secure?

  Here's some differences: [GET vs. POST](https://www.diffen.com/difference/GET-vs-POST-HTTP-Requests)

  ## MySQL
  I reviewed some command line mysql commands to do somethings to the database.

  [Create MySQL Database, Table & User From Command Line Guide](https://www.a2hosting.com/kb/developer-corner/mysql/managing-mysql-databases-and-users-from-the-command-line)

  [Create boolean column in MySQL with false as default value?](https://stackoverflow.com/questions/2221069/create-boolean-column-in-mysql-with-false-as-default-value)
  
  [SQL ALTER TABLE Statement](https://www.w3schools.com/sql/sql_alter.asp)

  ## Register
  I thought I made my register endpoint log the user in. But that's not happening.

  I changed the frontend code so now it logs the user in. It wasn't storing the token.

  ## `action_user_verify()`
  I made an `action_user_verify()` function that uses parameters sent in a url to verify the user. I added two columns to the database: `isVerified` which is a boolean and `verificationToken`:

  ![](log_imgs/table_8-8-19.PNG)

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/702d68a22dad09abdb999165c032cc0b4e3abf2e)

  Next I need to create the function(s) that create the verification token and send an email with the verification URL. I started to add the verification token to `action_user_register`. I'll continue here tomorrow.


## Day 19, R3
### 8/7/19

- ## Node

  ### Where I left off
  I left off trying to make an email verification api to register a new user.

  ## Authentication
  I read a little bit about authentication:

  [SECURING WEB APIS - PART 1
The Basics with Node.js Examples](https://resources.infosecinstitute.com/securing-web-apis-the-basics-with-node-js-examples/)

  ##  Email Verification
  Steps:
  >- User signs up into application.
  >- A user cannot sign in yet into application until their email is verified.
  >- A user receives an email with a verification link that contains a token.
  >- User clicks on verification link to get redirected to the application where the token is used to verify them.

  -*from [How to implement Email Verification feature in your NodeJS app using Express, SendGrid, Sequelize ORM(MySQL).](https://medium.com/the-andela-way/how-to-implement-email-verification-feature-in-your-nodejs-app-using-express-sendgrid-sequelize-e5b255bf92a2)*

  ## Send An Email In Node.js
  I read this tutorial on sending an email using Node.js:

  [Node.js Send an Email](https://www.w3schools.com/nodejs/nodejs_email.asp)

  I added Nodemailer.
  ```bash
  npm install nodemailer --save-dev
  ```

  ## Set Up Gmail App Password
  I ran into an error:
  ```bash
  Error: Invalid login: 535-5.7.8 Username and Password not accepted. Learn more at
  535 5.7.8  https://support.google.com/mail/?p=BadCredentials t133sm129744943iof.21 - gsmtp
  ```
  I followed the link above, [I can't sign in to my email client](https://support.google.com/mail/?p=BadCredentials).

  I created an app password:
  [Sign in using App Passwords](https://support.google.com/accounts/answer/185833)

  ## Delete Last Commit
  I accidentally pushed sensitive information to github so I deleted the last commit locally (this wasn't the right way):
  ```bash
  git reset --hard HEAD~1
  ```
  Then I force pushed to github:
  ```bash
  git push origin +master --force
  ```
  This didn't actually work. It deleted my last updated files locally too which I didn't want to do. Luckily, I was able to get what I need and put it back together.
  
  ## App Sends Email
  Now my app sends a simple email.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/b3d099c96dbce58978c0582e8963be5b6ad693a5)

  ## Email Module
  I turned my sendEmail.js script into a function that can be imported. I read about exporting modules:
  [Export Module in Node.js](https://www.tutorialsteacher.com/nodejs/nodejs-module-exports)

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/842584d0c8fb3d1065f3845a4ceedd6f38a439b0)

## Day 18, R3
### 8/6/19

- ## Node
 
  ### Where I left off:
  Yesterday, I was trying to make it so if the client tries to login but they're already logged in it won't let them. That's where I left off.

  ## Login
  Now you can't log in if someone is already logged in:

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/76e489712b01c3b639ecd7c683b849c9a6428eea)

  I don't know if this is necessary. We could just log out anyone who is logged in.

  ## Local Storage
  I was having trouble with my local storage returning undefined. I wanted to see where it was stored in Chrome:

  >It's simple. Just go to the developer tools by pressing F12, then go to the Application tab. In the Storage section expand Local Storage. After that, you'll see all your browser's local storage there.

  -*from [How to view or edit localStorage](https://stackoverflow.com/questions/9404813/how-to-view-or-edit-localstorage)*
  
  ## CSS Selectors
  I used this reference:
  [CSS Selector Reference](https://www.w3schools.com/cssref/css_selectors.asp)

  ## Logged In VS Logged Out Views
  I made it so the view is different depending on whether the client is logged in or logged out.

  <img src="log_imgs/loggedviews_8-6.gif" width="450"/>

  The code is on the frontend. I think I should eventually move some of this to the backend or organize the views into different files on the frontend to be cleaner. Maybe the code should route to different pages if the user is logged in/logged out.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/d3652ac8e7fc5d630ba645890c7c5c6706d7ab98)

  ## Email Verification
  I'd like to implement an email verification for when a user registers. I looked up how email verification works:

  >- User signs up into application.
  >- A user cannot sign in yet into application until their email is verified.
  >- A user receives an email with a verification link that contains a token.
  >- User clicks on verification link to get redirected to the application where the token is used to verify them.

  -*from [How to implement Email Verification feature in your NodeJS app using Express, SendGrid, Sequelize ORM(MySQL).](https://medium.com/the-andela-way/how-to-implement-email-verification-feature-in-your-nodejs-app-using-express-sendgrid-sequelize-e5b255bf92a2)*

  That's where I'll leave off for today. I'll work on the email verification tomorrow.


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


## Day 16, R3
### 8/4/19

- ## Node
 
  ### Where I left off:

  Yesterday, I started changing `action_session_create`. Before, the query looked only for existing sessions associated with the `user_id`. Now I'm also searching for `user-agent` and `ip`. I'll continue working on `action_session_create`.

  ## Logout
  I got more answers for my [log out question](https://twitter.com/DashBarkHuss/status/1157687032279379970) that were all pretty different.

  So I guess there isn't one agreed upon way to manage a logout endpoint.

  ## User Agent
  I got a weird result console logging `user-agent`. I was on Chrome but the log showed that the browser was Firefox(Mozilla), Chrome, and Safari:
  ```bash
  Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.142 Safari/537.36
  ```

  I found this explanation:
  > most Web browsers use a User-Agent string value as follows:
  >
  >`Mozilla/[version] ([system and browser information]) [platform] ([platform details]) [extensions].`
  >
  >- Mozilla is a byproduct of browser wars.
  >
  >- AppleWebKit/537.36 is the platform used by your browser.
  >
  >- Chrome/51.0.2704.63 is your browser
  >
  >- Safari/537.36 was added for historic reasons, where Safari was treated differently.
  
  -*[Why does Chrome send four browsers in the user-agent header?](https://security.stackexchange.com/questions/126407/why-does-chrome-send-four-browsers-in-the-user-agent-header)*

  ## Data Types For IP and User Agent
  I found this answer for what data types you should use for IP and User Agent in my session table: [What types should I use for these data in MySQL?](https://stackoverflow.com/questions/8263806/what-types-should-i-use-for-these-data-in-mysql)

  - **IP:** CHAR(15)
  - **user-agent:** VARCHAR(255)

  There are probably other ways to go about it too, as the answer says, "*This **depends a bit on your personal taste**/your company's conventions, but I'd use:..."*.

  More on [SQL Data Types here.](https://www.journaldev.com/16774/sql-data-types)


  ## Session Table
  If there's more than one session per username you can't have username be the primary key. You'll get an error:
  ```bash
  Error: ER_DUP_ENTRY: Duplicate entry 'someusername' for key 'PRIMARY'
  ```
  So I made an id a primary key
  ![](log_imgs/session_8-4.PNG)

  ## Updated `action_session_create` and `action_user_login`
  `action_user_login` now queries for the session by username, ip, and, user agent. `action_session_create` now adds the user agent and the ip address to the session.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/d504488faf38bfd6172b5c405f5134beb744520b)

  ## Logout
  I started to make the logout endpoint. It's not working. The session is still in the table.
  - 


## Day 15, R3
### 8/3/19

- ## Node
 
  ### Where I left off:
  I'm making a Node app that has a login.

  I started to add the login UI but it's not working yet.

  ## Login UI
  I got the login UI working.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/057aeb7e17f681c72e409413258bf9460083bc5a)

  ## Storing Client Login Info
  I thought it might be good for security reasons to keep track of which devices each auth token is being stored on. So I wanted to know how to access information about the client.

  [How to determine a user's IP address in node](https://stackoverflow.com/questions/8107856/how-to-determine-a-users-ip-address-in-node)

  [How to get information about the client in node.js](https://stackoverflow.com/questions/3895434/how-to-get-information-about-the-client-in-node-js)

  ```javascript
  console.log(request.connection.remoteAddress); //127.0.0.1
  console.log(request.headers['user-agent']); //Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.142 Safari/537.36
  ```
  I could save this information in the sessions table. But what if the user deletes the local storage on their own without pressing the logout button? Then I'd have devices in the sessions table that say they are logged in but aren't. So maybe it's not a good idea. 

  I also need to think about how I need to change my code to prevent multiple logins of different users on the same client.

  ## `localStorage` Syntax
  [Window.localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
  ```javascript
  localStorage.setItem('myCat', 'Tom');
  var cat = localStorage.getItem('myCat');
  localStorage.removeItem('myCat');
  localStorage.clear();
  ```

  ## Secure Logout
  Right now I have the logout function on the frontend.

  ```javascript
  const logout = (payload) => {
    localStorage.removeItem('token');
  }
  ```

  This doesn't seem secure. What if someone changes the javascript so that it just looks like it logs out but the token doesn't delete? I'm not sure if that's possible but It seems like it is.

  I did some research but was having trouble finding an answer so I posted on twitter:

  ![](log_imgs/twitter_8-3.PNG)

  I got an [answer](https://twitter.com/the_moisrex/status/1157687913448165376) from [@moisrex](https://twitter.com/the_moisrex). Basically, what I had a few days ago was correct. You ***do*** delete the session from the database when the user logs out. So you *can* have ***multiple*** sessions for each user. Different devices will have different sessions for the same user in order to log out separately. Otherwise, logging out on your phone would also log you out of your computer.

  I thought this was wrong  because in [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087), **Greg only has *one* session per user:**
 
  In `action_create_session` of the github file, the session is found by the `user_id`.
  
  [Node.js – Server Setup Github](https://github.com/javascriptteacher/node/blob/master/module/api/api.js) Code:
  ```javascript
  database.connection.query("SELECT * FROM session WHERE user_id = '" + payload.id + "' LIMIT 1",
        (error, results) => { // Check if session already exists
  ```

  If we're just searching by `user_id`, that would mean there's only ***one*** auth token per each user. But we will actually need to look up the token by `username` and `user.agent` and `IP`, because there may actually be multiple sessions per user.

  I think [@moisrex](https://twitter.com/the_moisrex)'s way is correct. It makes more sense to me. Also Greg told me the Node book is still a work-in-progress so it's possible his query is just a mistake. Or maybe it's just a simplified way to create a session for learning purposes.

  ## Changing Session
  Now I have to go back and change how the app creates the session.

  I changed the query. Before, I was just searching for `username`. Now it also looks for `user-agent` and `ip`:

  ```javascript
  // line 74, api.js `action_session_create`
  let q = `select * from session where username = '${payload.username}' AND ip = ${request.connection.remoteAddress} AND user-agent = ${request.headers['user-agent']}` ;
  ```

  This is where I left off. I'll continue working on `action_session_create` tomorrow.

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


## Day 13, R3
### 8/1/19

- ## Node
  New month! I looked back at my  posts from a month ago. It feels like progress is so slow, but looking back, I can see I accomplished a lot. I hadn't even connected my database to any Node app yet. Since then, I've connected databases to apps multiple times. I've also figured out so much about creating a node app on my own, soldiering through many issues that the book tutorial hadn't addressed.
  
  ### Where I left off:
  Yesterday, I continued my Node app that will have CRUD *and* sessions/logins so I can get more practice with sessions.

  I started to add the database query. I'll continue that today.

  ## Database Query
  I got `action_user_login` to query the database to see if the username passed into the payload exists.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/92889e68b0ba588a44ffe299227199bd6ac8d12c)

  ## MD5
  I added the md5 package with --save-dev:
  ```bash
  npm install md5 --save-dev
  ```
  And required it in api.js:
  ```javascript
  const md5 = require('md5');
  ```

  ## `action_user_register`
  I added action_user_register. Now users can register with just a username and password. MD5 encrypts the password.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/212e3f9fd91cc07ae36ce2f72c4e0e93fb762869)

  ## Login Checks Password
  `action_user_login` only outputs a message that the user logged in if the passwords match. No session is created yet.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/801b6518d5dc246780beb1c8f9336ac516bf805d)

  ## `action_session_create`
  I added the session table and started adding the code for `action_session_create`. I'll continue that tomorrow.


## Day 12, R3
### 7/31/19

- ## Node
  
  ### Where I left off:
  Yesterday, I continued my Node app that will have CRUD *and* sessions/logins so I can get more practice with sessions.

  I started the login API endpoint and I'm continuing that.

  ## Promise Syntax
  I had a really weird error where my a promise constructor executor was catching an error but the error was the resolve value. It was because I had switched the order of the parameters for the executor. I did `(reject, resolve)` but it should be `(resolve, reject)`.

  [Promise Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
  ### No:
  ```javascript
  return new Promise((reject, resolve)=>{ //wrong order
      if (!payload){
          reject("Oops no payload")
      };
      resolve(`{"success": true}`); 
  }).catch((error) => { console.log("err:", error) });
  ```
  ### Yes: 
  ```javascript
  return new Promise((resolve, reject)=>{
      if (!payload){
          reject("Oops no payload")
      };
      resolve(`{"success": true}`); 
  }).catch((error) => { console.log("err:", error) });
  ```

  ## `action_user_login` Returns Promise
  Now `action_user_login` returns a promise.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/10414a907e0f55ee02e5c9c6a3198a222455e180)

  ## `request.on('data')`
  I added the callback function for `request.on('data')` and added a payload to my test fetch call.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/0cb8e2aa5b26a5327f26f227f0ab5c711f7f34b6)

  ## Database Class
  I added the database class and created a connection to the database.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/a79461e580773cffec62d1d13a8ddc9efc309dd9)

  ## Database Connection Query
  I started to add the database query. I'll continue that tomorrow.

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

## Day 10, R3
### 7/29/19

- ## Node
  
  ### Where I left off:
  Yesterday, I started a new app that will have CRUD *and* sessions/logins. The 404.html file isn't serving.

  ## No Slash in Path Parameter
  The 404.html file wasn't serving because of the syntax. There shouldn't be a leading forward slash in the path parameter for `fs.readFile`.

  ### No:
  ```javascript
  fs.readFile('/404.html', function(error,content){
      ...
  ```

  ### Yes:
  ```javascript
  fs.readFile('404.html', function(error,content){
  ```
  
  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/tree/f957b813a456371f869ebf677fc20b9fae2b72a6)

  ## `response` Parameter In `requestListener()`
  I was confused about the response parameter in the request listener in `http.createServer(). We don't yet know the response when we pass the parameter in. So what is it?

  >The second parameter represents a ServerResponse object, which has methods for handling the response stream back to the user parameter 

  -*[Node.js requestListener() Function](https://www.w3schools.com/nodejs/func_http_requestlistener.asp)*

  ## Markdown Spellcheck
  I added back the spellcheck extension I had called [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker). I thought it didn't have suggested spellings but I looked again in the docs and it does.

  ## `promise.text()`
  You can use `.text()` on a promise to see what the response is. This helped me debug an issue when `.json()` gave me an error for an unexpected token and the response couldn't be parsed.

  [Unexpected token < in JSON at position 0](https://daveceddia.com/unexpected-token-in-json-at-position-0/)

  ## API.exec Sends Response To Fetch
  I got API.exec to send a response to fetch.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/tree/08f8703f26d4c2882a313632f5f5c94bdee18444)

  ## Tomorrow
  I changed the status code for serving the 404.html file back to 200 and didn't test it with 404. I'll do that tomorrow.

  I need to better understand how fetch is working.

- ## Thoughts And Feelings:
  Doing multiple passes of this project has me looking at details and trying to understand more each time through. 

  For example, today I really looked closely at how the fetch promise gets resolved.

  Going through the tutorial multiple times has me understanding the big picture so I can ask the right questions about the details.


## Day 9, R3
### 7/28/19

- ## Node
  
  ### Where I left off:
  Yesterday, I finished implementing CRUD for my 'butts' api.

  Today, I'll start a new app that has CRUD *and* sessions/logins.

  ## Live Server VSC Extension
  I mentioned yesterday that all my computer apps,settings , and extensions had to be deleted. So today I'm adding back this [Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) for VSC.

  ## Password Input
  Here's how you can get that hidden password input:

  ```html
  <input type="password"></input>
  ```

  <img src="log_imgs/login_7-28.PNG" width = "400"/>

  More info: [MDN, \<input type="password">](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/password)

  ## `response.writeHead` And `response.end`
  Info on `response.writeHead` and `response.end`:

  >writeHead writes the HTTP header (status code 200), end writes the body and closes the response. 

  -*[response.writeHead and response.end in NodeJs](https://stackoverflow.com/questions/14243100/response-writehead-and-response-end-in-nodejs)*

  More info here: [HTTP, Node Docs](https://nodejs.org/api/http.html)

  ## `fs.readFile`
  >Asynchronously reads the entire contents of a file.

  More here: *[Node Docs: fs.readFile(path[, options], callback)](https://nodejs.org/api/fs.html#fs_fs_readfile_path_options_callback)*

  ## Status Code 404
  In the Node server tutorial I followed, when you request a page that doesn't exist you get redirected to 404.html page. And you write back a 200 status code:
  ```javascript
  fs.readFile('/404.html', function(error,content){
      response.writeHead('200', {'Content-Type':'text/html'});
      response.end(content, 'utf-8')
  }
  ```

  But I think you need to send a 404 code.

  >When a user requests a nonexistent URL on your website, you should return an individual error page that lets them know that the requested URL does not exist. You should also make sure that the server returns the correct HTTP status code “404“.

  -*[Why should a 404-error page return the correct HTTP status code and not be redirected, for example?](https://www.sistrix.com/ask-sistrix/onpage-optimisation/http-status-code/4xx-client-error-404-error-page/why-should-a-404-error-page-return-the-correct-http-status-code-and-not-be-redirected-for-example/)*

  I'm changing the code to 404.

  ## Not Serving 404.html
  I added more conditionals `fs.readFile`. Now the 404.html file isn't serving. I wonder if it's because it won't serve unless you pass 200 into `response.writeHead`. I'll need to work on this tomorrow. 


## Day 8, R3
### 7/27/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ### Where I left off:
  Yesterday, I added an endpoint that updates the *butts* but I'm getting an error related to the MySQL query.

  I also had a lot of problems with my mac so I had to wipe it clean and move the files over from my last back up. All of my applications are gone along with their settings and extensions. So I'll need to deal with that.

  ## Installing Homebrew And Node

  I have to install Homebrew and Node:

  [How to install NodeJS and NPM on Mac using Homebrew](https://www.dyclassroom.com/howto-mac/how-to-install-nodejs-and-npm-on-mac-using-homebrew):

  Install brew:
  ```bash
  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  ```

  Install Node:
  ```bash
  $ brew install node
  ```
  
  ## Markdown Extension
  I had this extension before:
  [Markdown All in One.](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)

  I added it back.

  It gives you some short cuts for working with markdown. For example, `cmd` + `b` makes text bold.

  ## MySQL Query Error

  I solved my query error. I was missing quotes.
  ### Wrong:
  ```sql
  update butts set shape = big where owner = dash
  ```
  ### Correct:
  ```sql
  update butts set shape = 'big' where owner = 'dash'
  ```
  
  ```javascript
  // line 51,api.js
  let q = `update butts set shape = '${payload.shape}' where owner = '${payload.owner}'`;
  ```

  ## CRUD
  Now I've fully implemented CRUD:
  - **Create**: `action_butt_add`

  - **Read**: `action_butt_find`

  - **Update**: `action_butt_update`

  - **Delete**: `action_butt_delete`


   ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/ca3bcd1c8c5a3039e0c6a33deb8552669eafb2f0)

   ## Next
   Next, lets add more UI. Right now I can only **add** and **find** in the UI.

   ## UI Added
   I added a simple and not so pretty UI.

   <img src="log_imgs/ui_7-27.PNG" width="500">

   [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/commit/3d908f93106ad43777e5be15d4e889bb01d24321)

   ## Readme
   I added to the readme.

   [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/15c3761058dfcf2547efbedcaa471826ed0e8823)

   ## What Do I Still Need To Know?
   I still probably need more experience with making bigger databases with lots of tables. How do they need to relate to each other? I know there are best practices.

   I also should get more practice with authentication and sessions.

   I'm going to start another project again from scratch. This one will have authentication/logins. Maybe I'll even make something useful, instead of a butt api.

- ## Thoughts And Feelings:
  I know so much more about creating a backend now. It's fun. I feel like I am getting closer to being able to pop out apps. I wonder what else there is to learn regarding backend? It seems like this is all it is? Maybe AI and data science is considered backend.

  I wonder if I should next learn express? Is it necessary?
  


## Day 7, R3
### 7/26/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ### Where I left off:
  I made a dynamic query and returned the data to the UI. I refactored the code into helper functions so it's DRY. I added a new endpoint but I need to add the body to the endpoint

  ## Adding Butts
  I created the body for `action_butt_add`.
  ![](log_imgs/add_7-26.gif)

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/e7d994e80d3fd927415eed8ae0869aad2b3eba8e0)

  ## Added Alert
  I added an alert for when the butt is added to the database.

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/a19b9ce23adcabd996577f8d30760989cf0f2672)

  ## CRUD
  Now we have the create and read parts of CRUD implemented. I want to implement the rest of crud: update and delete.

  ## Deleting Butts
  Now my app deletes butts. There's no UI for delete yet, so you have to run `Butt.delete('somebuttowner')` in the console.

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/61d9298d701fb27ec7818414b0a554b181d3d5a8)

  ## Tomorrow
  I added an endpoint that updates the butts but I'm getting an error related to the MySQL query so that's what I'll work on tomorrow.

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/ba72f6b3d475960e75c5120b3a4845a616bcff4c)
## Day 6, R3
### 7/25/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).


  ### Where I left off:
  Yesterday, I got the API to connect to the database and grab information statically: the API always queried the same query.

  Today, I'm going to try to make the call dynamic, using the payload. I'm also going to try to send the info back to the frontend through the promise returned in the fetch call.

  ## Dynamic Query and Return Query Info
  I got the api to query the database dynamically, based on the payload. 

  The query sends the data back to the front end console. 

  ### Link To Work: [node_server_multiple_endpoints](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/6a62d127a1f76cbd9eb47abe129cdf30ea0b7753)

  ## Next:
  Let's put the data in the UI.

  ## Query Info Returned To UI
  Now the query info goes to the UI.
  ### Link To Work: [node_server_multiple_endpoints](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/77ac5effd8e80a183efe2aa2a23432d10e804541)

  ## Next
  Let's add another API Query and move some of our code into helper functions so it's DRY. 

  ## Added Helper Functions, New Endpoint
  I refactored the code into helper functions so it's DRY. I added a new endpoint but I need to add the body to the endpoint tomorrow.
  ### Link To Work: [node_server_multiple_endpoints](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/8e106e3b073e276320ca5de5d090e7db6e0d784a)
  

## Day 5, R3
### 7/24/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).


  ### Where I left off:
  I'm on my 3rd round of doing the tutorial. I'm not using the book, except as a reference when needed. I'm using my finished files as references.

  Yesterday, I made an API class. I left off with a bug when I call fetch from the UI:

  ```bash
  SyntaxError: Unexpected token b in JSON at position 1
  ```

  But I'm not getting that error when I call the same code from the backend.

  ## Refreshing
  I'm not getting that error now, so I think it was just a refreshing problem.

  ## Returning Promise To UI
  I got my UI to request an endpoint. The end point returns data to the UI. I'm not really sure where in the code the data is getting returned to the UI. Maybe it's when I call `response.end(content, 'utf-8')`?Maybe that sends the content to the fetch call??

  ### Link To Work: [promise returned to UI no helper functions](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/589d27985e62690916835a02eb13da7537cb6984)

  ## What Next
  I think I should try to get the api to change the database now.

  ## MySQL
  I added a query to the database. Our endpoint grabs all the butt's of the owners who have flat butts.

  Well really it grabs all the *owners*, but I wanted to say it *grabs all the butts* for the pun.
  
  ```javascript
  // line 24, api.js
  let q = "select owner from butts where shape = 'flat'"
  database.connection.query(q, (error, results)=>{
    if (error)
      throw error;
    console.log(results);
  })
  ```


  <img src ="log_imgs/owners_7-24.PNG" width="500"/>

  <img src ="log_imgs/query_7-24.PNG" width="500"/>

  We've successfully grabbed 2d-Man's and Flatty Mcflat's *flat* butts. We didn't grab my *round* butt or my moms *square* butt. Those aren't *flat*.

  ### Link To Work: [flat butt query](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/f2bb95b67b86713d7c05c17c990b5f3d37d21dd8)

  ## Tomorrow
  Tomorrow, I'll work on using the payload to change the query and returning information from the query back to the UI.

## Day 4, R3
### 7/23/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).


  ### Where I left off:
  I'm on my 3rd round of doing the tutorial. I'm not using the book, except as a reference when needed. I'm using my finished files as references.

  I need to make an API class and tell the `requestListener` in `httpCreateServer` what to do when it gets an API url.

  ## `.constructor`
  I thought this was an interesting conditional:
  ```javascript
  if (request.constructor === String)
  ```
  
  ## Testing API Calls With `node-fetch`
  `fetch` doesn't work in node because it's a WEB API. Node is on the backend so it doesn't have access to the Web API's. 

  I wanted to automatically fetch an API endpoint while testing it every time I restart the server. So I figured I needed to fetch the api from the node file on the backend, index.js. 

  To do this I installed `node-fetch`:
  ```bash
  npm install node-fetch --save
  ```

  I required `node-fetch` in index.js:
  ```javascript
  const fetch = require('node-fetch');
  ```

  I called `fetch()`. You much use an absolute URL for `node-fetch`:
  ```javascript
  fetch('http://127.0.0.1:3000/api/butt', {
    method: 'post',
    headers: {
      'Accept': 'application/json'
    },
    body: JSON.stringify({butt: 'round'})
  })
  ``` 

  ## What Next
  I made an API class. I'm working on getting it to one endpoint. I left off with a bug when I call fetch from the UI:

  ```bash
  SyntaxError: Unexpected token b in JSON at position 1
  ```

  But I'm not getting that error when I call the same code from the backend.


## Day 3, R3
### 7/22/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).


  ### Where I left off:
  Yesterday I started to redo the tutorial again. This time, without reading the book. I'm only using the book as a reference when needed. I'm using my finished files as references. This time I want to make multiple endpoints.

  I made a new database and created a server. I started to get the server to redirect `/` requests to `index.html`.

  ## Serves Html Files

  I made a server that serves html files. I used dotenv again to upload the directory without publishing my database server info. I'll use the database server info later to connect to the database.
  

  Link to work: **[node_server_multiple_endpoints, commit: serves html files](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/ce8b0cdda6994d70852d053148c7f22a9e02be08)**
  ```javascript
  // index.js
  let http = require('http');
  let fs = require('fs');

  const ip = '127.0.0.1';
  const port = 3000;

  http.createServer(function(request,response){
    console.log(request.url);
    let file;
    if (request.url === '/') file = 'index.html'
    else file = request.url.slice(1, request.url.length);
    fs.readFile(file, function(error, content){
      if(error){
        if (error.code='ENOENT'){
          fs.readFile('/404.html', function(error, content){
            response.writeHead(200, {'Content-Type': 'text/html'});
            response.end(content, 'utf-8')
          });
        } else {
          response.writeHead(500);
          response.end('Error: ' + error.code + '\n');
        }
      } else {
        response.writeHead(200, {'Content-Type': 'text/html'})
        response.end(content, 'utf-8');
      };
    });

  }).listen(port, ip);
  ```
  I didn't yet add the mime type code. So if you put a png image in the directory and try requesting that image file, the server will interpret the image as html. You'll see a bunch of weird text. Changing this is not complicated but I'm going to skip it for now because I'm less interested in that.

  <img src="log_imgs/table_7-22.PNG" width="400"/>

  Next, should I try to connect to the database or make the API class? 
  
  I'm going to connect to the database.

  ## `--save-dev`
  >--save-dev: Package will appear in your devDependencies.

  -*[Difference between — save-dev and — save while running npm](https://medium.com/@arnab.k/difference-between-save-dev-and-save-while-running-npm-50e3c0784153)*
  
  I added the mysql npm package and the md5 package so I could require them. I used `--save-dev` so that they'll be included when others download my repo.

  ## No Semicolon In `.env` File

  I had semicolons in my `.env` file. That made the semicolons part of the variables:

  ```
  SOMEVAR = 'somevalue'; // the value will be "'somevalue';" with the semicolon included.
  ```

  It should be *without* semicolons, but it seems that you can *include **or** leave out* the quotes.

  ## Database Connects
  I added an `api.js` file and made the `database.create()` function in there. I required `api.js` in `index.js` and called the `database.create()`  function. 
  
  Since I'm using dotenv, when I run the module I use `node bin/dev`. `bin/dev` requires `dotenv/config` and `index.js` modules. Running `node index.js` won't work because `index.js` doesn't require the `dotenv/config` module, so `index.js` can't access the environment variables on its own. 

  Link to work: **[node_server_multiple_endpoints, commit: database connects](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/06c8700932099e1c334c298654c89c1b12b7f476)**

  ```javascript
  // api.js
  const mysql = require('mysql');
  const md5 = require('md5');

  class database {
    constructor() {}
    static create(){
      let message = "Creating mysql connection...";
      this.connection = mysql.createConnection({
        host: process.env.HOST,
        user: process.env.DBUSER,
        password: process.env.PASSWORD,
        database: process.env.DATABASE
      })
      this.connection.connect();
      console.log(message + 'ok');
    }
  }

  module.exports = {database};
  ```

  ## What Next?

  Next, I need to start adding the API code. I need to make an API class. I'll need to tell the `requestListener` in `httpCreateServer` what to do when it gets an API url. Normally it would follow the file path requested. The API url may look like a file path, but it's not.

  Example:
  ```
  /api/user/create
  ```

  There is no api folder, user folder, or create file. Instead, we'll use conditionals to let the server know how to handle a request that starts with '/api'.

  I'm not sure if **'API URL'**, is the correct term. It may just be called an **'API endpoint'**.

## Day 2, R3
### 7/21/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).


  ### Where I left off:
  Continuing to redo the [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087) tutorial.

  ## Super User Tips

  [Hotkey for switching between tabs / window panes on a Mac](https://superuser.com/questions/609821/hotkey-for-switching-between-tabs-window-panes-on-a-mac):
  - **Command + Tab** = switch between applications
  - **Command + ~** = switch between windows of an application
  - **CTRL + Tab** = move forward through tabs (in same window)
  - **CTRL + Shift + Tab** = move backward through tabs (in same window)

  ### Mission Control

  Go here for [Chrome keyboard shortcuts](https://support.google.com/chrome/answer/157179?hl=en)

    [How to Switch Between Open Apps in macOS](https://www.laptopmag.com/articles/switch-between-open-apps-macos):
  - **Swipe up on the touchpad with three fingers** = mission control


  [Use Mission Control on your Mac](https://support.apple.com/en-us/HT204100):

  - **Swipe left or right with three or four fingers on your Multi-Touch trackpad** = switch to another desktop space

  ## Dotenv
  I set up dotenv following this tutorial: [Setup environment variables with Node.js + Dotenv Tutorial](https://www.youtube.com/watch?v=zDup0I2VGmk_)

  Now I can push to github and not worry about my sensitive info.
  ```javascript
  // line 9, api.js
  this.connection = mysql.createConnection({
    host: process.env.HOST,
    user: process.env.DBUSER, //Don't use `USER` because it's already an environment variable
    password: process.env.PASSWORD,
    database: process.env.DATABASE
  })
  ```

  ## Posted To Git Hub
  I added dotenv to my project and posted what I did with the tutorial this second time to github. It's just like the finished files except I only have one api endpoint, `action_register_user`.

  ### Link to work: [Sample Node Server API](https://github.com/DashBarkHuss/sample-node-server-api)

  ## Redo Tutorial Take 3
  I'm going to try to redo the tutorial again. This time, without reading the book. I'm only going to use the book as a reference when needed. I'm also going to use my other finished files as reference. This time I want to make multiple endpoints.

  I made a new database and created a server. I started to get the server to redirect `/` requests to `index.html`.




## Day 1, R3
### 7/20/19

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



## Round 3
Today is the start of round 3. This round I want to make some full stack apps, learn React, and play with unit testing. I want to get into AI and React Native if I have time.

The last two rounds I studied for 2 hours a day. I will continue that for now. 

So far, I've dedicated at least 400 hours this year to coding.

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).


  ### Where I left off:
  Continuing to redo the [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087) tutorial.

  ## Currying
  I saw this weird "chained function":

  ```javascript
  // line 355, api.js
  const resp = response => content => respond(response, content);
  ```
  I found out it's called ***currying***:
  >Named after Haskell Brooks Curry, currying is breaking down a function into a series of functions that each a single argument.
  
  -*[Currying in JS](https://hackernoon.com/currying-in-js-d9ddc64f162e)*

  ## Redid Tutorial Through Chapter 6
  I redid the tutorial through chapter 6. I'm trying to run `node index.js` but I ended with:
  ```bash
  Error: Cannot find module 'mysql'
  ```
  I need to add the mysql module.

- ## Thoughts and Feelings:
  To do:
  - Set up a second monitor.
  - Take my mac in to be checked out.
    - Why is the fan always on
    - What is making my storage go down so quickly
  - Get note cards from van.

