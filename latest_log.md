
## Day 111, R3
### 11/7/19
  
- ## Where I Left Off
  I started to review debugging in Node so I can debug my test script.

  ## How to debug tests?
  I want to pause my test script on a line in the test while debugging. Let's see if I can figure it out.


  ## How We Run Tests
  To run tests you run the command
  ```bash
  npm test
  ```
  Scripts in package.json:
  ```json
  "scripts": {
  "test": "mocha"
  ...}
  ```
  What is `"mocha"` from this script?

  It looks like npm scripts are just terminal commands:

  >```json
  >"scripts": {    "start": "node index.js",    ...}
  >```
  >You’ve probably seen this tons of times in your package.json files. And you probably know that you can type `npm start` to execute the script. But this example illustrates ***the first important aspect of NPM scripts — they are simply terminal commands.*** They run in the shell of the OS on which they’re executed. So it might be bash for Linux and cmd.exe for Windows.

  -*from [Introduction To NPM Scripts](https://www.freecodecamp.org/news/introduction-to-npm-scripts-1dbb2ae01633/)*

  But if npm scripts are just terminal commands, why does running `mocha` in the terminal do nothing? 
  ```bash
  $ mocha
  bash: mocha: command not found
  ```

  I would think `npm test` and `mocha` would give the same results in the the terminal if scripts are just terminal commands.
  ## npm test
  It turns out `npm test` is a special npm script.

  There are more special npm scripts here [npm-scripts](https://docs.npmjs.com/misc/scripts).

  >pretest, **test**, posttest: Run by the npm test command.
  
  -*from [npm-scripts](https://docs.npmjs.com/misc/scripts)*

  ### More info on npm test:
  >SYNOPSIS
  >
  >`npm test [-- <args>]`
  >
  >`aliases: t, tst`
  >
  >DESCRIPTION
  >
  >This runs a package’s “test” script, if one was provided.

  -*from [npm-test](https://docs.npmjs.com/cli/test.html)*

  I find it weird that the docs give no examples of what the arguments would be.

  ## Debugging Tests
  If we can only run the tests through the terminal command `npm test`, how do we debug them? 
  
  I found this tutorial: [Debugging Mocha Unit Tests In Visual Studio Code](https://scottaddie.com/2015/10/22/debugging-mocha-unit-tests-in-visual-studio-code/). This is where I left off.

  


