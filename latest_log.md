
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
