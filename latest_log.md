## Day 50, R3
### 9/7/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ### Where I Left Off
  I'm watching this express tutorial: [Express.js Tutorial: Build RESTful APIs with Node and Express | Mosh](https://www.youtube.com/watch?v=pKd0Rpw7O48). I'll continue watching, today.

  ## Setting An Environment Variable in the Command Line

  Mac:
  ```bash
  $export SOMEVAR = 'somevalue'
  ```
  Use `set` instead of `export` for windows

  ## Proper Way To Set Port
  ```javascript
  const port = process.env.PORT || 3306;
  ```
  In production, your port will be in the environment variable `process.env.PORT`. 3306 is an arbitrary number to be used in development.

  ## Parameters
  ### **Route Parameters:** 
  Essential or required values.

  Here `api` and `courses` are route parameters.
  ```
  http://127.0.0.1:3306/api/courses/
  ```
  ### **Query String Parameters:**
  Optional values.
  
  Here the query string parameter is `sortBy=name`
  ```
  http://127.0.0.1:3306/api/courses/?sortBy=name
  ```
  ## Postman
  You can use [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop//%40) to test http services.

  [How to use Postman, video segment](https://youtu.be/pKd0Rpw7O48?t=2034)

  ## Schemas
  A schema defines the shape of our objects. What properties do we have in an object? What is the type of each property?

  Input validation with Joi creating a schema:
  ```javascript
  const schema = {
      name: Joi.string().min(3).required()
  }
  const result = Joi.validate(req.body, schema);
  ```
  ## Where I Left Off
  I'm watched more of the tutorial [Express.js Tutorial: Build RESTful APIs with Node and Express | Mosh](https://www.youtube.com/watch?v=pKd0Rpw7O48) and followed along. I left off at [41:22](https://youtu.be/pKd0Rpw7O48?t=2482)