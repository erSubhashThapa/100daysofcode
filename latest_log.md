
## Day 71, R3
### 9/28/19
- ## Node
  ### Where I Left Off
  I started experimenting with bootstrap in my socket IO sample browser chat.

  ## Getting Stuck In Git Terminal
  Sometimes I get stuck in the terminal when using a git command. This is how to get out.

  >You won't lose commits by closing the terminal.
  >
  >`ctrl+c` will exit the prompt `>`
  >
  >
  >What happened was you opened up a string with the odd number of ' characters.
  >Bash expects more input for your string, and allows you to enter it after the > prompt.
  >
  >Try typing `'` and hit `return`, you will get the same thing. If you close the string by typing `'` again, you will be back to your normal bash prompt.

  -*from [How do I exit my git commit message? I'm NOT in the VIM, I used the “ commit -m ” command](https://stackoverflow.com/questions/26228848/how-do-i-exit-my-git-commit-message-im-not-in-the-vim-i-used-the-commit-m)*

  ## .gitignore Not Working
  I added something to .gitignore and github didn't ignore it. This fixed the issue.

  >NOTE: First commit your current changes, or you will lose them.
  >
  >Then run the following commands from the top folder of your Git repository:
  >
  >```javascript
  >git rm -r --cached .
  >git add .
  >git commit -m "fixed untracked files"
  >```
  -from *[.gitignore is ignored by Git](https://stackoverflow.com/questions/11451535/gitignore-is-ignored-by-git)*

  ## Socket IO Sample Browser App
  I made a sample browser chat app using socket IO inspired by [Create your Socket.io event](https://www.linkedin.com/learning/learning-node-js-2/create-your-socket-io-event) and [Connect to Socket.io from the browser app](https://www.linkedin.com/learning/learning-node-js-2/connect-to-socket-io-from-the-browser-app).

  Project: [sample_socket_IO_browser](https://github.com/DashBarkHuss/sample_socket_IO_browser)

  ## Where I Left Off
  I got socket IO to tell the browser when a reality check has been added to the database. Now I'm trying to get the frontend to properly add the new data.


