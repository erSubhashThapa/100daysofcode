

## Day 78, R3
### 10/5/19
- ## Node
  ### Where I Left Off
  I'm having an issue where my server isn't emitting the socket event. It only emits it after I refresh the client. I need to investigate more.

  ## Socket IO
  I was trying to figure out why the server couldn't emit an event to the sockets.

  ```javascript
  app.post('/messages', (req, res) =>{
      messages.push(req.body)
      const chatRoom = io.of(`/${req.body.chat}ChatRoom`);
      chatRoom.emit(`message`, req.body);
      res.sendStatus(200)
  })
  ```

  I got the above code to work when I made the connection to the sockets outside of the scope of app.post().

  ```javascript
  var io = require('socket.io')(http)

  io.of(`/garyChatRoom`);
  io.of(`/workChatRoom`);
  ```
  `.of` initializes and retrieves a namespace.
  >server.of(nsp)
  >- nsp (String|RegExp|Function)
  >- Returns Namespace
  >
  >Initializes and retrieves the given Namespace by its pathname identifier nsp. If the namespace was already initialized it returns it immediately.

  -*from [server.of(nsp)](https://socket.io/docs/server-api/#server-of-nsp)*

  ## Socket IO Sample Namespaces
  I finished my sample Socket Io app with multiple namespaces.

  [Socket Sample Multiple Namespaces](https://github.com/DashBarkHuss/multiple_namespaces_socket_IO/commits/master)

  ## Where I Left Off
  I started testing out the express app for two different users.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/3a6dda91d277c1a5324daa3c594548f2b7ca691c)

