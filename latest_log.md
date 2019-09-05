## Day 48, R3
### 9/5/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ### Where I Left Off
  I finished the Create part of CRUD. Next, Read?

  ## `ELIFECYCLE` Error
  When I'm testing my app in the browser, if I run into an `ELIFECYCLE` error the whole program will shut down.

  In this example there's a problem with my code.

  <img src="log_imgs/error_9-5-19.gif" width=500>

  I'm not wondering what caused this error. I'm wondering, since the error shut the whole program down, if this was in production, would my whole website go down just because one person interacted with a broken endpoint?

  ## Read
  I finished the read part of CRUD but I didn't handle the content for the front end. It just gets logged in the console for now.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/2eb0fa03721ed71ee659aed1bda0fd15dd5776bc)

  ## Sequel Pro Query
  You can you Sequel Pro to practice queries

  <img src="log_imgs/query_9-5.PNG" width=300>

  ## Update
  I finished update of crud.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/8fcb170375144acd43d2e99b54379ae8afb6fbca)

  ## Refactored
  I refactored a bit because I'm going to reuse code that was in the update function for the delete function. So I took that code out of `action_posts_update` and moved in into it's own function `isAuthorizedToEditPost`.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/7040860e0db2c70a6b9077d67a5d3cc44cfd0689)

  ## Where I Left Off
  I only have Delete of CRUD left to do. I haven't been setting any relationships between the tables in my database. I might want to look into that.