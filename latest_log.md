## Day 49, R3
### 9/6/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ### Where I Left Off
  I only have Delete of CRUD left to do. I haven't been setting any relationships between the tables in my database. I might want to look into that.

  ## My Process
  I thought I would share some of my process. I generally don't do much Googling for answers when I code. I mostly experiment in the browser console when I have a question about Javascript.

  For example, I wanted to know if in an `async function` can I return the last `.then()` value of a promise in a return statement. Or will the first promise value be returned. 

  So I took it to the console to find out. Here's some of what I did:

  <img src="log_imgs/console_9-6.PNG" width=500>

  ## Some Resources I Used Today

  [Async/await](https://javascript.info/async-await)

  [Basic MySQL Tutorial](http://www.mysqltutorial.org/basic-mysql-tutorial.aspx)

  ## Finished CRUD
  I finished my app.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/fb92d32cf67c044cd548b9b380b1ed49057a0ce4)

  It works but here are somethings I could still change:
    
  - My database helpers should be more uniform. They should probably all return the results of the query and I should handle the results from the function call. Instead, the results are handled in some of the helpers, which makes it hard to remember what the helper is going to return.
  - Some catch statements are missing.
  - I used some `async function`s for my API endpoints and some functions that `return` a `new Promise`. In production, I'd stick to one or the other to make the code more uniform and easier to read. But in this project I played with both for practice.

  ## Readme
  I added a readme file.

  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/a329b16e1a0f33615c157159e7593ce3ce945153)

  ## Lynda Account Not Working
  I use Lynda.com to learn lots of new subjects. Today, I couldn't log in. I wonder if my school finally closed my account? I emailed Lynda to see what's going on. 
  
  When I signed in with Safari, I got a different message. It said my account had been moved to LinkedIn Learning but I couldn't figure out how to log in.
  
  I guess I'll use Youtube for now. 

  ## Express ReST API Tutorial
  I started watching this tutorial:
  [Express.js Tutorial: Build RESTful APIs with Node and Express | Mosh](https://www.youtube.com/watch?v=pKd0Rpw7O48)

  ## Where I Left Off
  I'm watching this express tutorial: [Express.js Tutorial: Build RESTful APIs with Node and Express | Mosh](https://www.youtube.com/watch?v=pKd0Rpw7O48). I'll continue watching, tomorrow.