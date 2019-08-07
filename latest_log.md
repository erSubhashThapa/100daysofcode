## Day 19, R3
### 8/7/19

- ## Node

  ### Where I left off
  I left off trying to make an email verification api to register a new user.

  ## Authentication
  I read a little bit about authentication:

  [SECURING WEB APIS - PART 1
The Basics with Node.js Examples](https://resources.infosecinstitute.com/securing-web-apis-the-basics-with-node-js-examples/)

  ##  Email Verification
  Steps:
  >- User signs up into application.
  >- A user cannot sign in yet into application until their email is verified.
  >- A user receives an email with a verification link that contains a token.
  >- User clicks on verification link to get redirected to the application where the token is used to verify them.

  -*from [How to implement Email Verification feature in your NodeJS app using Express, SendGrid, Sequelize ORM(MySQL).](https://medium.com/the-andela-way/how-to-implement-email-verification-feature-in-your-nodejs-app-using-express-sendgrid-sequelize-e5b255bf92a2)*

  ## Send An Email In Node.js
  I read this tutorial on sending an email using Node.js:

  [Node.js Send an Email](https://www.w3schools.com/nodejs/nodejs_email.asp)

  I added Nodemailer.
  ```bash
  npm install nodemailer --save-dev
  ```

  ## Set Up Gmail App Password
  I ran into an error:
  ```bash
  Error: Invalid login: 535-5.7.8 Username and Password not accepted. Learn more at
  535 5.7.8  https://support.google.com/mail/?p=BadCredentials t133sm129744943iof.21 - gsmtp
  ```
  I followed the link above, [I can't sign in to my email client](https://support.google.com/mail/?p=BadCredentials).

  I created an app password:
  [Sign in using App Passwords](https://support.google.com/accounts/answer/185833)

  ## Delete Last Commit
  I accidentally pushed sensitive information to github so I deleted the last commit locally (this wasn't the right way):
  ```bash
  git reset --hard HEAD~1
  ```
  Then I force pushed to github:
  ```bash
  git push origin +master --force
  ```
  This didn't actually work. It deleted my last updated files locally too which I didn't want to do. Luckily, I was able to get what I need and put it back together.
  
  ## App Sends Email
  Now my app sends a simple email.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/b3d099c96dbce58978c0582e8963be5b6ad693a5)

  ## Email Module
  I turned my sendEmail.js script into a function that can be imported. I read about exporting modules:
  [Export Module in Node.js](https://www.tutorialsteacher.com/nodejs/nodejs-module-exports)

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/842584d0c8fb3d1065f3845a4ceedd6f38a439b0)
