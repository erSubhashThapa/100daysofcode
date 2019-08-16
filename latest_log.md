## Day 28, R3
### 8/16/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.
  
  Today, I'll continue working on my new branch that handles the returned promise from `database.existsIn`.

  ## `database.existsIn` Return Promise
  Now `database.existsIn` returns a promise. 

  [Link To Work]([`database.existsIn`](https://github.com/DashBarkHuss/crud_login_node_app/commit/3fa9b4f307af3b3b404eaf738fc1f042d034eff5))

  I still feel it could be more DRY.

  ## Branch and Merge
  I reviewed merging and merged my branch.

  [3.2 Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

  ## `database.insertIn`
  I added a method for database that inserts records called `database.insertIn()`:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/867e76f9bcfa7aa4860a74cd32173b325cf6fee6)

  ## Bcrypt
  I watched [How To Hash A Password W/ BCrypt](https://www.youtube.com/watch?v=lWDws1j8fo4).

  I didn't know what a salt was so I looked it up: [Salt (cryptography)](https://en.wikipedia.org/wiki/Salt_(cryptography)). I don't fully understand it, but it seems salts provide an extra layer of protection.

  ## Where I left off
  I added bcrypt to my project. Tomorrow, I'll test it some more and push my progress. Then I'll continue with the next api end point.
