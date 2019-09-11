## Day 54, R3
### 9/11/19

- ## Node
  ## Where I Left Off
  I left off playing with [geolocation](https://www.w3schools.com/html/html5_geolocation.asp) in the console because I want to use it in my app. I started working on the post method.

  ## Serve Static Files in Express
  To serve up static files from the same directory I added:
  ```javascript
  app.use(express.static("./"))
  ```
  [Serving static files in Express](https://expressjs.com/en/starter/static-files.html)

  ## Fetch With Express
  I spent a while trying to figure out how to send a fetch request with express. My mistake was I didn't add JSON.stringify() to the body. Here is how it should be:
  ```javascript
  app.use(express.json());

  fetch('http://127.0.0.1:3306/test',         
  {
    method: "POST",
    body: JSON.stringify({user_id: 1}),
    headers: {
      "Content-Type": "application/json"
    }
  }).then(x=>{console.log('done')})
  ```
  ## Where I left Off
  I'm trying to figure out how the timestamp should be saved to the database, what datatype it should be.
  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/b96219fa2b2783aa6961310f5e9fd9715aa7d557)