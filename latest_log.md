
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