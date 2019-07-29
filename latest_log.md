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
