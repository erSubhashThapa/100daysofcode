
## Day 69, R3
### 9/26/19
- ## Node
  ## Where I Left Off
   I was  watching the LI Learning video [Connect to Socket.io from the browser app](https://www.linkedin.com/learning/learning-node-js-2/connect-to-socket-io-from-the-browser-app). I ran into a weird error when following along:

  `Access to XMLHttpRequest at 'http://localhost:3000/messages' from origin 'http://127.0.0.1:3000' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.`

  Aren't these the same origin?:
    - 'http://localhost:3000/messages
    - 'http://127.0.0.1:3000'
  
  Localhost is the same as 127.0.0.1 and /messages isn't part of the origin, is it? So how are they not the same? What's going on?

  ## Localhost vs 127.0.0.1
  My browser is at the address: `http://127.0.0.1:3000/`

  When I fetch `127.0.0.1:3000/messages` I get the data I want. But when I fetch  `localhost:3000/messages` I'm blocked by CORS.

  ![](log_imgs/same_origin_9-26.PNG)

  >Origin is defined as a scheme/host/port (port is the default value for a scheme if it doesn't exist, e.g. port 80 for http, 443 for https). Same-origin is defined as a matching scheme/host/port. "localhost" and "127.0.0.1" are different hosts in this case.
  
  -*from [Are 127.0.0.1 and localhost considered as two different domains by browsers?](https://stackoverflow.com/questions/5256251/are-127-0-0-1-and-localhost-considered-as-two-different-domains-by-browsers)*

  More here: [Origin determination rules](https://en.wikipedia.org/wiki/Same-origin_policy#Origin_determination_rules)

  ## Socket IO Tutorial
  I watched to video from the course Learning Node.js:

  - [Create your Socket.io event](https://www.linkedin.com/learning/learning-node-js-2/create-your-socket-io-event)
  - [Connect to Socket.io from the browser app](https://www.linkedin.com/learning/learning-node-js-2/connect-to-socket-io-from-the-browser-app)

  Now I can see how to use socket IO in the browser.

  I also watched this video: [Express](https://www.linkedin.com/learning/learning-node-js-2/express-2)

  In the video [Create a post message service](https://www.linkedin.com/learning/learning-node-js-2/create-a-post-messages-service), the instructor says that express has no built in support to parse a body. He says you need to use body parser. Why was I able to use express without body parser before?

  ## Where I Left Off
  I'm trying to understand body parse and why i dodn't need it before. I'm working on making a sample app that uses socket IO in the browser.