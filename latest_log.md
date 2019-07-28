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
