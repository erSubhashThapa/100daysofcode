
## Day 21, R3
### 8/9/19

- ## Node

  ### Where I left off
  I started to add the verification token to `action_user_register`. I'll continue here.

  ## Verification Token
  Now the `action_user_register` creates a verification token. Next we need to email the user the token url.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/100437c63cd464c5d02828c2d431096df982ed1f)

  ## How Is MD5 Secure?
  If all you have to do to translate md5 tokens is run md5(token), how is that secure? Couldn't anyone take that token and get md5 and run md5(token)? I'm thinking that maybe there's another step here.

  I read [WHAT IS THE DIFFERENCE BETWEEN HASHING AND ENCRYPTING](https://www.securityinnovationeurope.com/blog/page/whats-the-difference-between-hashing-and-encrypting). 

  I don't really understand how it works still.

  I read that [md5 isn't secure](https://searchsecurity.techtarget.com/definition/MD5). But I think the reason it's insecure is unrelated to what I don't understand about it. I think other hashing methods like SHA work the same way and they are secure but I still don't understand why.

  I watched this video [How hash function work?](https://www.youtube.com/watch?v=xsp--srKWKw) which helped me understand better. Also the teacher was funny.

  ## Email Verification
  The email verification is complete.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/e7a1b0c9825b31cf430783b3aba4fe53be40c7de)

  ## What's left?
  For learning purposes this app is complete. It demonstrates how to login/logout and register. 

  ### What is the app missing?
  - There's nothing stopping you from registering different usernames under the same email. 
  - A UI for resending the verification code
  - An endpoint that deletes or updates accounts
  - Some errors don't catch properly
  - Some promises should throw an error but they don't

  These would be the only things related to accounts that's missing. All of them are easy fixes. Obviously this isn't a very useful app because it does nothing but create users. But this is for demonstration purposes for myself and anyone else who wants to see how you can make an app with logins.

  ## Completed Project
  I added a readme.md. Here's the complete project:

  [Node Server Session](https://github.com/DashBarkHuss/node_server_sessions)

  ## Next
  I've put together a [CRUD app](https://github.com/DashBarkHuss/node_server_multiple_endpoints) and a [Sessions app](https://github.com/DashBarkHuss/node_server_sessions). Next I could put together an app that has both. I also wonder if I should learn express and when I should go back to learning react.

  I started this login app on 7/28, day 209. So this project took me 13 days. I wonder if I can do a combined crud and sessions app in a shorter amount of time. 