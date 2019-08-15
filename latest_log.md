## Day 27, R3
### 8/15/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Yesterday, I started to create a database method that searches the database and returns `true` or `false` if the record exists. It's not working. I'll continue here

  ## Database Method Working
  My database method wasn't working because I didn't understand that .query() in MySQL is asynchronous. I thought I could just return a value from it

  ```javascript
  static existsIn(table, clause){
    const q = `select * from ${table} where ${clause};`
    this.connection.query(q, (err, results)=>{
        if (err) console.log(err);
        return results.length !== 0;
    });
  };
  ```

  This doesn't work. But I can resolve the promise from here:

  ```javascript
  static existsIn(table, clause, resolve, content){
      const q = `select * from ${table} where ${clause};`
      this.connection.query(q, (err, results)=>{
          if (err) console.log(err);
          if (results.length !== 0) resolve(content);
      })
  };
  ```
  This function made my code so much cleaner:

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/3fa9b4f307af3b3b404eaf738fc1f042d034eff5)

  ## Resolve Overwriting
  I'm noticing that if I have multiple places where my promise can resolve it will resolve wherever it reaches the resolution first, it seems. But since I have places where the resolution is in an asynchronous function this confuses me. How do I make sure it reaches the right resolution first?

  ## Where I Left Off
  I worked  a lot on making the register API function DRY and readable. 
  
  I played around with promises. 
  
  I created a new branch to try out a different way of dealing with `database.existsIn()`. This other way returns a promise so you can handle the content within the api function. 
  
  I played with seeing where the code flows if you resolve it at different points. It seems so keep going on to the next `.then()` even if you resolve it. But it won't resolve again. I think if you throw an error it won't go on to the next `.then()`. That made me wonder if I should be throwing an error instead of resolving.
  
   Tomorrow, I'll continue working on my new branch that handles the returned promise from `database.existsIn`.
