
## Day 7, R3
### 7/25/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ### Where I left off:
  I made a dynamic query and returned the data to the UI. I refactored the code into helper functions so it's DRY. I added a new endpoint but I need to add the body to the endpoint

  ## Adding Butts
  I created the body for `action_butt_add`.
  ![](log_imgs/add_7-26.gif)

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/e7d994e80d3fd927415eed8ae0869aad2b3eba8e0)

  ## Added Alert
  I added an alert for when the butt is added to the database.

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/a19b9ce23adcabd996577f8d30760989cf0f2672)

  ## CRUD
  Now we have the create and read parts of CRUD implemented. I want to implement the rest of crud: update and delete.

  ## Deleting Butts
  Now my app deletes butts. There's no UI for delete yet, so you have to run `Butt.delete('somebuttowner')` in the console.

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/61d9298d701fb27ec7818414b0a554b181d3d5a8)

  ## Tomorrow
  I added an endpoint that updates the butts but I'm getting an error related to the MySQL query so that's what I'll work on tomorrow.

  ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/ba72f6b3d475960e75c5120b3a4845a616bcff4c)