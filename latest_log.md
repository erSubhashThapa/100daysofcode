

## Day 77, R3
### 10/4/19
- ## Node
  ### Where I Left Off
  I made a sample socket IO app that sends messages to different chat rooms conditionally. But I didn't yet use multiple name spaces.

  ## Submit Default Event

  I was wondering why the radio buttons were appearing as query parameters after I sent the messages: 
  
  `http://localhost:3000/?chat=work` <--query parameter

  `e.preventDefault()` stopped this from happening so I read about the submit event:
[HTMLFormElement: submit event](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/submit_event)

  >When you click the Send button, the form is submitted, meaning that the content of its field is packed into an HTTP request and the browser navigates to the result of that request.
  >
  >When the \<form> element’s method attribute is GET (or is omitted), the information in the form is added to the end of the action URL as a query string. The browser might make a request to this URL:
  >
  >`GET /example/message.html?name=Jean&message=Yes%3F HTTP/1.1`

  -*from [HTTP and Forms](https://eloquentjavascript.net/18_http.html)*

  ## Debugging Socket IO
  Info on debugging: [Available debugging scopes](https://socket.io/docs/logging-and-debugging/)

  ## Issue With Socket IO
  I'm having an issue where my server isn't emitting the socket event. It only emits it after I refresh the client. I need to investigate more.
