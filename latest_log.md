
## Day 76, R3
### 10/3/19
- ## Node
  ### Where I Left Off
  I'm testing to see what happens if I clear the local storage and reload the page while offline. It seems like it's connecting to the server somehow when it's offline.

  ## Multiple Web Sockets
  How do you make multiple web sockets on the same app. For example, on facebook websockets update the news feed. But my news feed is different from Joe Shmoe's news feed. How do they do that?

  ## Custom Name Spaces

  >To set up a custom namespace, you can call the of function on the server-side:
  >```javascript
  >const nsp = io.of('/my-namespace');
  >nsp.on('connection', function(socket){
  >console.log('someone connected');
  >});
  >nsp.emit('hi', 'everyone!');
  > ```
  >On the client side, you tell Socket.IO client to connect to that namespace:
  >```javascript
  >const socket = io('/my-namespace');
  >```


  -*from [Custom Namespace Socket IO Docs](https://socket.io/docs/rooms-and-namespaces/#Custom-namespaces)*

  ## Front End

  I reviewed some bootstrap docs:
  - [Boot Strap Grid](https://getbootstrap.com/docs/4.3/layout/grid/)
  - [Forms](https://getbootstrap.com/docs/4.3/components/forms/)
  
  And JQuery:
  - [Attribute Equals Selector [name=”value”]](https://api.jquery.com/attribute-equals-selector/)


  ## Where I left off
  ### Socket IO Sample
  I made a sample socket IO app that sends messages to different chat rooms conditionally. But I didn't yet use multiple name spaces.

  [Socket IO Conditional Multiple Chat Rooms](https://github.com/DashBarkHuss/socket_iO_conditional_chat/commit/75a772be7a6f506c36e56ebbf88b3540946cac5f)