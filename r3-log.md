
# #100DaysOfCode Log - Round 3 - Dashiell Bark-Huss

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

