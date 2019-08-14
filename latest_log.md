## Day 26, R3
### 8/14/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Last time I started making the API endpoint for registering a user. I'll continue here.

  ## Storing Session Key Incorrectly?

  I'm reading ['Re-Hashed: The Difference Between SHA-1, SHA-2 and SHA-256 Hash Algorithms'](https://www.thesslstore.com/blog/difference-sha-1-sha-2-sha-256-hash-algorithms/) and this made me think I'm storing session keys incorrectly:

  > the client generates a session key, then encrypts a copy of it and sends it to the server where it can be decrypted and used for communicating throughout the duration of the connection 

  I created the session key on the backend and just sent back the session key. Oh wait I know what I did. I created the session key by hashing a time stamp in the backend. So maybe I should have sent back the time stamp instead of the session key.

  I watched videos 3.1-3.6 of [Advanced Express](https://www.lynda.com/Node-js-tutorials/Advanced-Express/798496-2.html) to try to see if the token stored on the client side is different from what's stored on the database but I couldn't find anything.

  I read '[Should I also hash my session id before storing it in the database? [duplicate]](https://security.stackexchange.com/questions/138389/should-i-also-hash-my-session-id-before-storing-it-in-the-database)'. It brought up an unrelated point, that matching sessions to an ip might cause issues if the user is mobile. That can change the IP address, for example switching to a different wifi (I think). 
  
  I read [How to secure store sessions values in webapps?](https://security.stackexchange.com/questions/136122/how-to-secure-store-sessions-values-in-webapps) and this said you ***do*** want to hash the token and send the un-hashed token back to the browser. 
  
  This makes sense because if the database were accessed by a hacker and the tokens weren't hashed they could just use the tokens in the database to authenticate actions. Well, but why would that matter since if they have access to the database they can just change the database directly? Maybe there's some instances where a hacker can get the database info but can't change it.

  I found this [Session Management Cheat Sheet](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Session_Management_Cheat_Sheet.md) for best practices.

  ## Hashing Algorithm
  I couldn't find a straight answer on which hashing algorithm to use. So I posted to twitter. So we'll see what they say. I'll keep using md5 until I find something better. I know it's not supposed to be good but I'm not making anything real right now so it's ok.

  ## Where I left off
  I worked more on the api register endpoint. 
  
  I started to create a database method that searches the database and returns `true` or `false` if the record exists. It's not working. 