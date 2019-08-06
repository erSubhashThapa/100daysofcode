## Day 18, R3
### 8/6/19

- ## Node
 
  ### Where I left off:
  Yesterday, I was trying to make it so if the client tries to login but they're already logged in it won't let them. That's where I left off.

  ## Login
  Now you can't log in if someone is already logged in:

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/76e489712b01c3b639ecd7c683b849c9a6428eea)

  I don't know if this is necessary. We could just log out anyone who is logged in.

  ## Local Storage
  I was having trouble with my local storage returning undefined. I wanted to see where it was stored in Chrome:

  >It's simple. Just go to the developer tools by pressing F12, then go to the Application tab. In the Storage section expand Local Storage. After that, you'll see all your browser's local storage there.

  -*from [How to view or edit localStorage](https://stackoverflow.com/questions/9404813/how-to-view-or-edit-localstorage)*
  
  ## CSS Selectors
  I used this reference:
  [CSS Selector Reference](https://www.w3schools.com/cssref/css_selectors.asp)

  ## Logged In VS Logged Out Views
  I made it so the view is different depending on whether the client is logged in or logged out.

  <img src="log_imgs/loggedviews_8-6.gif" width="450"/>

  The code is on the frontend. I think I should eventually move some of this to the backend or organize the views into different files on the frontend to be cleaner. Maybe the code should route to different pages if the user is logged in/logged out.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/d3652ac8e7fc5d630ba645890c7c5c6706d7ab98)

  ## Email Verification
  I'd like to implement an email verification for when a user registers. I looked up how email verification works:

  >- User signs up into application.
  >- A user cannot sign in yet into application until their email is verified.
  >- A user receives an email with a verification link that contains a token.
  >- User clicks on verification link to get redirected to the application where the token is used to verify them.

  -*from [How to implement Email Verification feature in your NodeJS app using Express, SendGrid, Sequelize ORM(MySQL).](https://medium.com/the-andela-way/how-to-implement-email-verification-feature-in-your-nodejs-app-using-express-sendgrid-sequelize-e5b255bf92a2)*

  That's where I'll leave off for today. I'll work on the email verification tomorrow.
