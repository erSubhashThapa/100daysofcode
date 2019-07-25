
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
  