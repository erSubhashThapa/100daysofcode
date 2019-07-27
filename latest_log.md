## Day 8, R3
### 7/27/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-api-source-27588087).

  ### Where I left off:
  Yesterday, I added an endpoint that updates the *butts* but I'm getting an error related to the MySQL query.

  I also had a lot of problems with my mac so I had to wipe it clean and move the files over from my last back up. All of my applications are gone along with their settings and extensions. So I'll need to deal with that.

  ## Installing Homebrew And Node

  I have to install Homebrew and Node:

  [How to install NodeJS and NPM on Mac using Homebrew](https://www.dyclassroom.com/howto-mac/how-to-install-nodejs-and-npm-on-mac-using-homebrew):

  Install brew:
  ```bash
  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  ```

  Install Node:
  ```bash
  $ brew install node
  ```
  
  ## Markdown Extension
  I had this extension before:
  [Markdown All in One.](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)

  I added it back.

  It gives you some short cuts for working with markdown. For example, `cmd` + `b` makes text bold.

  ## MySQL Query Error

  I solved my query error. I was missing quotes.
  ### Wrong:
  ```sql
  update butts set shape = big where owner = dash
  ```
  ### Correct:
  ```sql
  update butts set shape = 'big' where owner = 'dash'
  ```
  
  ```javascript
  // line 51,api.js
  let q = `update butts set shape = '${payload.shape}' where owner = '${payload.owner}'`;
  ```

  ## CRUD
  Now I've fully implemented CRUD:
  - **Create**: `action_butt_add`

  - **Read**: `action_butt_find`

  - **Update**: `action_butt_update`

  - **Delete**: `action_butt_delete`


   ### [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/ca3bcd1c8c5a3039e0c6a33deb8552669eafb2f0)

   ## Next
   Next, lets add more UI. Right now I can only **add** and **find** in the UI.

   ## UI Added
   I added a simple and not so pretty UI.

   <img src="log_imgs/ui_7-27.PNG" width="500">

   [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/commit/3d908f93106ad43777e5be15d4e889bb01d24321)

   ## Readme
   I added to the readme.

   [Link To Work](https://github.com/DashBarkHuss/node_server_multiple_endpoints/tree/15c3761058dfcf2547efbedcaa471826ed0e8823)

   ## What Do I Still Need To Know?
   I still probably need more experience with making bigger databases with lots of tables. How do they need to relate to each other? I know there are best practices.

   I also should get more practice with authentication and sessions.

   I'm going to start another project again from scratch. This one will have authentication/logins. Maybe I'll even make something useful, instead of a butt api.

- ## Thoughts And Feelings:
  I know so much more about creating a backend now. It's fun. I feel like I am getting closer to being able to pop out apps. I wonder what else there is to learn regarding backend? It seems like this is all it is? Maybe AI and data science is considered backend.

  I wonder if I should next learn express? Is it necessary?
  
