
## Day 65, R3
### 9/22/19

- ## Node
  ### Where I left off
  I started working on getting reality check info for the user from the database to the UI.

  ## RC's In Local Storage
  Here I grabbed all the rc's from the database and saved them to localStorage. 

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commits/master)

  ## Can The Server Talk To The Client?
  I was wondering this exact question:

  >What I'd like to know is if there's a way to have the server broadcast a message to clients. An example of this would be a client page that has a newsfeed, and every time a new story comes in to the server, the server sends that information out to the client and the client updates its page's newsfeed. I don't want the client to constantly be polling the server every few seconds, asking "hey, is there a new story now? what about now? what about now???" I want the client to be doing its own thing, and then be interrupted by a message from the server.

  The answers said to look into [Web Sockets](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
  >For newer browsers, you can use web sockets to open a continuous connection to a server and then client/server can send each other messages whenever they want.

  This answer is from 2011, so I'm guessing most browsers work with web sockets now.

  Question and answer from: [how to get the server to talk to the client](https://stackoverflow.com/questions/8626249/how-to-get-the-server-to-talk-to-the-client)

  ## Web Sockets
  I watched these two videos:

  - [Create A WebSocket](https://www.linkedin.com/learning/node-js-essential-training-web-servers-tests-and-deployment/create-a-websocket)
  - [Broadcast messages with WebSocket](https://www.linkedin.com/learning/node-js-essential-training-web-servers-tests-and-deployment/broadcast-messages-with-websocket)

  Now I'm going to try to do what the instructor did.

  [WebSocket Docs](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)

  ## Sample App: WebSocket Using `ws`
  I made a sample app that has a websocket connection and uses the `ws` module:

  [Sample WebSocket using ws](https://github.com/DashBarkHuss/sample_websocket)

  ## Sockets.io
  Sockets.io is a websocket framework that fails back to a different data polling technique in environments that do not support webSocket. It also comes with tools to help build large scale applications with ease.
  
  I watched these two videos about Socket.io:

  - [Create a WebSocket with Socket.IO](https://www.linkedin.com/learning/node-js-essential-training-web-servers-tests-and-deployment/create-a-websocket-with-socket-io)
  - [Emit Socket.IO events](https://www.linkedin.com/learning/node-js-essential-training-web-servers-tests-and-deployment/emit-socket-io-events)

  ## Where I Left Off:
  I want to try to build a socket.io sample app tomorrow.
  
  I started creating a GET request for my express app that sends the locally stored rc information so only the new info is sent back.
