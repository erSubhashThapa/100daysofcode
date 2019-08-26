## Day 38, R3
### 8/26/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ### Where I Left Off
  I left off working on a helper function. It's being `require`d by `api.js`. But it cannot access a global variable of `api.js` anymore since it's in another file. I'm trying to figure out a way to access global variables of the main javascript file from required functions. I thought I could use a closure but that didn't work or I didn't do it the right way. I'm going to try to get it to work.

  ## Defining Terms
  I want to form the right question to the above problem. But I don't know the terms I need to form the question. Here are my meta-questions:
  1. What do you call the main script that gets executed by node? Executed module?
     - After some research I found that it's the **main module**, **current module**, or **module**. You can find the module like so:
          ```bash
          process.mainModule.filename
          "/some/path/to/a/file.js"

          module.filename
          "/some/path/to/a/file.js"
          ```
  2. What do you call the required scripts of that executed script? I supposed it could be modules? Required modules? 
     - After some research I found that these are called **dependencies**, **modules**, or **children**. You can find the first child like so:
        ```bash
        process.mainModule.children[0].filename
        "/some/path/to/a/file.js"

        module.children[0]
        "/some/path/to/a/file.js"
        ```

  ## Somethings I Read/Skimmed:

  [Cycles](https://nodejs.org/api/modules.html#modules_cycles)

  [Circular dependencies in node.js](https://coderwall.com/p/myzvmg/circular-dependencies-in-node-js)

  [In what scope are module variables stored in node.js?](https://stackoverflow.com/questions/15406062/in-what-scope-are-module-variables-stored-in-node-js)

  [What is the 'global' object in NodeJS](https://stackoverflow.com/questions/43627622/what-is-the-global-object-in-nodejs)

  ## See If A Variable Is In Scope

  You can check to see if a variable has been declared by:
  ```javascript
  typeof someVariable
  // returns "undefined" if not in scope 
  ```
  [JavaScript: Null vs Undefined vs Undeclared](https://techbrij.com/javascript-null-undefined-undeclared)

  ## Giving Variable Access To a Dependency

  Dependencies can access global variables, which in node are variables declared without `var`, `let`, or `const` or declared on the global object (*ex: `global.newVar = "value";`*). But child modules can't access variables of the main modules scope declared with `var`, `let`, or `const`.

  ```javascript
  //main.js
  const moduleFunction = require('./childModule');

  globalVar = "global variable";
  var varVar = "var variable";

  console.log(moduleFunction("some argument"))
  // returns Array(3) ["some argument", "globalVar is string", "varVar is undefined"]
  ```
  ```javascript
  //childModule.js
  const moduleFunction = function(){

    return [...arguments, `globalVar is ${typeof globalVar}`, `varVar is ${typeof varVar}`]

  };

  module.exports = moduleFunction;
  ```

  ## But Actually Don't Use Global Variables
  I'm not sure why.
  >Most people advise against using global variables. If you want the same logger class in different modules you can do this
  >```javascript
  >//logger.js:
  >
  >module.exports = new logger(customConfig); 
  >
  >//foobar.js:
  >
  >var logger = require('./logger');
  >logger('barfoo');
  >```

  -*[How to use global variable in node.js?](https://stackoverflow.com/questions/10987444/how-to-use-global-variable-in-node-js)*

  ## Exporting Variables From Main Module to Child Module
  If you have a child module like this that requires the main module:
  ```javascript
  //childModule.js
  const globalVar = require('./main')

  const moduleFunction = function(){
      return `globalVar: ${globalVar}`
  };

  module.exports = moduleFunction;
  ```

  You can export a variable from the main module to the child. But it can't be exported after the child is `require`d. This imports an empty object:
  ```javascript
  //main.js
  var globalVar = "global variable";
  const moduleFunction = require('./childModule');
  module.exports = globalVar; //export AFTER requiring childModule

  console.log(moduleFunction()) //globalVar: [object Object]
  ```
  It must be exported before:
  ```javascript
  //main.js
  var globalVar = "global variable";
  module.exports = globalVar; //export BEFORE requiring childModule
  const moduleFunction = require('./childModule');

  console.log(moduleFunction()) //globalVar: "global variable"
  ```

  ## Where I Left Off
  I found a few ways to get a child module to access a variable from the main module. I didn't do much with my app but I did a lot of sandbox learning by playing with node in the debugger. Tomorrow, I'll try to get back to the app.


