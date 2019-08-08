## Day 19, R3
### 8/8/20

- ## Node

  ### Where I left off
  I left off having created an email module. Today, I'm going to use that email module to make a verification email.

  ## Rejecting A Promise
  When do you reject a promise? It seems like anytime you could reject a promise you could also just resolve it with a message that says 'something went wrong'. Maybe it's when you don't want the rest of the `then()` functions to get called?

  ## Payload
  When you're not using fetch and you're just using a URL, where is the payload? Is it in the URL?

  I think maybe a payload is different than the parameters you send in a URL. It looks like you only send [a payload for a POST request and parameters for a GET request](https://stackoverflow.com/questions/14551194/how-are-parameters-sent-in-an-http-post-request). But what's really the difference? They seem the same? It seems like you could use POST or GET for the same thing. Is POST more secure?

  Here's some differences: [GET vs. POST](https://www.diffen.com/difference/GET-vs-POST-HTTP-Requests)

  ## MySQL
  I reviewed some command line mysql commands to do somethings to the database.

  [Create MySQL Database, Table & User From Command Line Guide](https://www.a2hosting.com/kb/developer-corner/mysql/managing-mysql-databases-and-users-from-the-command-line)

  [Create boolean column in MySQL with false as default value?](https://stackoverflow.com/questions/2221069/create-boolean-column-in-mysql-with-false-as-default-value)
  
  [SQL ALTER TABLE Statement](https://www.w3schools.com/sql/sql_alter.asp)

  ## Register
  I thought I made my register endpoint log the user in. But that's not happening.

  I changed the frontend code so now it logs the user in. It wasn't storing the token.

  ## `action_user_verify()`
  I made an `action_user_verify()` function that uses parameters sent in a url to verify the user. I added two columns to the database: `isVerified` which is a boolean and `verificationToken`:

  ![](log_imgs/table_8-8-19.PNG)

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/702d68a22dad09abdb999165c032cc0b4e3abf2e)

  Next I need to create the function(s) that create the verification token and send an email with the verification URL. I started to add the verification token to `action_user_register`. I'll continue here tomorrow.

