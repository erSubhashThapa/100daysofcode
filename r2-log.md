# #100DaysOfCode Log - Round 2 - Dashiell Bark-Huss


## Day 35, R2
### 5/15/19

- ## Node JS Notes
  Continued notes on node.js lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## Debugging?
  So far we have only run these node files in the terminal. But how do I debug them?
  
  I guess I don't know yet because I don't know how to put our files into the browser. I think you have to set up a node server or something so node an compile the code.
  
  ## `setTimeout` and `setInterval`
  
  I started to recreate the instructer's project but I wanted to make it more interesting. This let to my playing with `setTimeout` and `setInterval`. 
  
  I'me having trouble getting a loop to delay using `setTimeout` or `setInterval`.
  
  I redid my code so I can do it in the browser and use the debugger.
  
  The answer on the thread [How do I add a delay in a JavaScript loop?](https://stackoverflow.com/questions/3583724/how-do-i-add-a-delay-in-a-javascript-loop) looks like it uses recursion:
  
  ```javascript
  
  var i = 1;                     //  set your counter to 1

  function myLoop () {           //  create a loop function
     setTimeout(function () {    //  call a 3s setTimeout when the loop is called
        alert('hello');          //  your code here
        i++;                     //  increment the counter
        if (i < 10) {            //  if the counter < 10, call the loop function
           myLoop();             //  ..  again which will trigger another 
        }                        //  ..  setTimeout()
     }, 3000)
  }

  myLoop();                      //  start the loop
  
  ```
  
  There was debate about whether the recursion was a problem in the comments.


## Day 34, R2
### 5/14/19


- ## Helping
  I looked at [Swishyfishie's @Swishyfishie2](https://twitter.com/Swishyfishie2) code. He has a counter here. You can add 1 or 2 and then submit to save to `sessionStorage`. 
  
  <img src="log_imgs/swishy_5-14.PNG" width=300>
  
  It was adding more numbers than expected after you press submit. 
  
  I made a `log(func)` function to call from each function that Swishy made to see where the problem was. The `log(func)` function console logs the function name and the `count` variable's value:

  ```javascript
  function log(func) {
    console.log(`func:${func}, count:${count}`);
  };
  ```
  You call `log(func)` from each function, passing in a name for your function such as "+1" or "save".

  What I saw was that when the submit button was pressed, `count` increased by one. Sure enough Swishy was adding 1 to `count`, probably left over from copy and pasting from his first function.
 
  ```javascript
  btnSave.onclick = function () {
      saved.innerHTML = localStorage.getItem('county', count += 1); //oops adding 1 here
      log("save");
  }
  ```
  
  Seems to work after deleting `count += 1` from that line. 
 
- ## Node JS Notes
  Continued notes on node.js lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  [How, in general, does Node.js handle 10,000 concurrent requests?](https://stackoverflow.com/questions/34855352/how-in-general-does-node-js-handle-10-000-concurrent-requests)
  
  ## Global Object
  
  [Mozilla Docs: Global Object](https://developer.mozilla.org/en-US/docs/Glossary/Global_object)
  
  >The global object's interface depends on the execution context in which the script is running. For example:
  >
  >- In a web browser, any code which the script doesn't specifically start up as a background task has a Window as its global object. This is the vast majority of JavaScript code on the Web.
  >
  >- Code running in a Worker has a WorkerGlobalScope object as its global object.
  >
  >- Scripts running under Node.js have an object called global as their global object.

  [Node.js v12.2.0 Documentation: Global Objects](https://nodejs.org/api/globals.html)
  
  ## Modules
  
  Every node.js file we create is refered to as a module.
  
  ## `require()`
  
  `require()` is used to load external modules. Modules are other javascript files containing code. We can either load modules that have shipped with our installation of Node.js, modules we install with npm, or other modules that we create. `require()` is available to us on the global object.
  
  # `process` object
  The `process` object contains information about the current process as well as tools to allow us to interact with the process.
  
  ![process](log_imgs/process_5-14.PNG)
  
  ## Practice What I Learned
  
  I made my own version of a little questions program that the instructor made. I did different questions.
  
  ```javascript
  const questions = [
    "Who do you love?",
    "Who are you?",
    "Are you horny? Answer y or n"
  ];

  const ask = (i = 0 ) => {
    process.stdout.write(`\n${questions[i]} \n\n`);
  }

  ask()

  const answers = [];

  process.stdin.on("data", (data)=>{
    answers.push(data.toString().trim());

    if (answers.length < questions.length) {
      ask(answers.length);
    } else {
      process.exit();
    }
  });

  process.on("exit", ()=>{
    const [lover, name, horny] = answers;

    const doThisTo = horny === "y" ? "make love to": "kiss";
    console.log(`
    ${name.charAt(0).toUpperCase() + name.slice(1)}, you should ${doThisTo} ${lover.charAt(0).toUpperCase() + lover.slice(1)}!
    `);
  });
  ```
  
  ![questions](log_imgs/questions_5-14.gif)
  
- ## Thoughts and Feelings:
  If I don't do some sort of hands on coding (not just coding along with the tutorial), I get super bored by tutorials. So I need to always try to do something at least slightly creative along with the tutorial. Today, that meant recreating the questions program with my own questions.

 
## Day 33, R2
### 5/13/19

- ## NPM Notes
  I continued this npm tutorial:
  [Learning npm the Node Package Manager Tutorial](https://www.lynda.com/Node-js-tutorials/Learning-npm-Node-Package-Manager-2018/761956-2.html)
  
  ## Notes:
  
  `npm outdated`: To see if any packages are outdated locally, `-g` to get global
  
  `npm update <package>` or `npm install <package>` to update package.
  
  `npm uninstall <package>`: uninstall a dependency
  
  ## "devDependencies" vs "dependencies"
  >The difference between these two, is that devDependencies are modules which are only required during development, while dependencies are modules which are also required at runtime.
  
  -*from [NPMmmm #1: Dev Dependencies, Dependencies](https://medium.com/@dylanavery720/npmmmm-1-dev-dependencies-dependencies-8931c2583b0c)*

  
  ## Semantic Versioning
  ![version](log_imgs/version_5-13.PNG)
  
  ### Controlling Version:
  
  ### ^1.x.x
  
  The ^ caret symbol means:
  
  Update all releases that have a major release of 1.
  
  ```javascript
   "devDependencies": {
    "babel-preset-env": "^1.7.0",
  }
  ````
  
  ### ~1.7.x
  
  The ~ tilde symbol means:
  
  Update all releases that have a major release of 1 and a minor release of 7.
  
  ```javascript
   "devDependencies": {
    "babel-preset-env": "~1.7.0",
  }
  ````
  
  ## `package-lock.json` vs `package.json`
  Confused about the difference between these two.
  
  It seems like `package-lock.json` controls things more, specifies things more. But then what's the point of having both?
  
  [Everything You Wanted To Know About package-lock.json But Were Too Afraid To Ask](https://medium.com/coinmonks/everything-you-wanted-to-know-about-package-lock-json-b81911aa8ab8)
  
  >package-lock.json: records the exact version of each installed package which allows you to re-install them. Future installs will be able to build an identical dependency tree.
  >
  >package.json: records the minimum version you app needs. If you update the versions of a particular package, the change is not going to be reflected here.
  
  -*from [What is the difference between package.json and package-lock.json](https://delegatecall.com/questions/what-is-the-difference-between-packagejson-and-packagelockjson-2bd0e4e1-a65f-4d78-b8d8-b51905a37adb)*
  
  ## npm Cache
  
  npm keeps a cache of your install modules so that it doesn't have to get them everytime. Clearing your cache should always be a step in your troubleshooting when working with modules and not understanding what's happening.
  
  `npm-cache-verify`: Verifies you cache. (What does that mean?)
  `npm-cache-clean --force`: clean the cache
  
  ## npm audit
  
  Hard to understand this video without having context for it.
  
  `npm audit` is a command that will check the dependencies of your project and make sure they are safe to use.
  
  [Run an npm audit Lynda Video](https://www.lynda.com/Node-js-tutorials/Run-npm-audit/761956/800277-4.html?autoplay=true)
  
  ## Scripting in package.json
  Scripting in a package.json file gives us a way to do a simple command, to repeat, or execute complex commands.
  
  [npm-scripts docs](https://docs.npmjs.com/misc/scripts)
  
  ![scripting](log_imgs/npmscript_5-13.PNG)
  
  **Run:**`npm <preset script name>` or `npm run <your own script name>`
  
  ## npm npx
  
  npx lets you temporarily install a package just to run one of the commands from that package. This way you avoid package pulution.
  
  [npm npx docs](https://www.npmjs.com/package/npx)
  
- ## Node JS Notes
  Notes on node.js lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## Single Threaded non-blocking event driven IO
  ### Single threaded
  Node is single threaded. This confuses me because what if an application has millions of users? How can they all be on the same thread without slowing things down?
  
  ### I/O
  I don't know what I/O means for and I had trouble finding out. 
  
  >Node.js is an open source project designed to let you write JavaScript programs that talk to networks, file systems or other I/O (Input/Output) sources
  >...
  >What is an "I/O based program"? Here are some common I/O sources:
  >
  >Databases (e.g. MySQL, PostgreSQL, MongoDB, Redis, CouchDB)
  >APIs (e.g. Twitter, Facebook, Apple Push Notifications)
  >HTTP/WebSocket connections (from users of a web app)
  >Files (image resizer, video editor, internet radio)
  
  -*from [introduction to node: Understanding node](https://gist.github.com/maxogden/4011336#understanding-node)*
  
- ## Helping
  
  I started to look at some code that [Swishyfishie @Swishyfishie2](https://twitter.com/Swishyfishie2) was stuck on but I didn't get enough time to really check it out. Will look at it tomorrow!
  
## Day 32, R2
### 5/12/19

- ## Testing eslint-plugin-html
  I got the plugin to work again a different way. I just copied and pasted the `node_modules` folder from the other projects into a new project and copied the `.eslintrc.json` file.
  
  ## User Settings vs `.eslintr.json`
  But if I remove this from the user settings:
  
  ```javascript
    "eslint.options": {
    "plugins": [
      "html"
    ]
  },
  ```
  
  Eslint stops linting HTML on the last two project folders: `testing_eslint_project` and `playing with javascript`. But it still works on `perfect_fit_meal`.
  
  Now I see why. The `.eslintrc.json` in `perfect_fit_meal` had: 
  
  ```javascript
  "plugins": [
    "html"
  ]
  ```
  
  But the other two didn't have those settings in their `.eslintrc.json` file.
  
  ## Global Vs Local `eslint_plugin_html`
  
  I can also see that `perfect_fit_meal` has `eslint-plugin-html` in the `node_modules` folder. The other two projects don't. They must be getting the plugin globally. 
  
  The other two also don't have `eslint-plugin-html` listed in the `"dependenies"` property in the `package.json` file like `perfect_fit_meal` does. I think I got it there when I ran `npm install --save-dev eslint-plugin-html`.
  
- ## Prettier
  
  I think I understand a bit more about these plugins now. I'm going to try to install prettier again.
  
  ## Wes Bos Prettier + ESLint Video
  
  I followed this Wes Bos [How to Setup VS Code + Prettier + ESLint](https://www.youtube.com/watch?v=YIvjKId9m2c) video again. I still get ***"Failed to load plugin prettier: Cannot find module 'eslint-plugin-prettier'"***
  
  ## No Dependency
  Now that I understand a little more I can see that I do not have that module in my `node_modules` folder; globally or locally. It's also not in the `package.json` file's `"dependencies"`. 
  
  But why doesn't Wes Bos tell you how to get the dependency?
  
  ## Adding The Dependency Through the Terminal
  
  I'm guessing I need to add it like how I got the eslint dependency, `npm install --save-dev eslint-plugin-html`
  
  So I ran:
  
  `npm install --save-dev eslint-plugin-prettier`
  
  Now I see `"eslint-plugin-prettier": "^3.1.0"` in my `"dependencies"` in my `"package.json"` file.
  
  ## No Dependency In node_modules
  
  Even though I see `"eslint-plugin-prettier": "^3.1.0"` in `"package.json"`, I don't see it in my `node_modules` folder. Even though it says it added the plugin:
  
  ![screenshot](log_imgs/prettier_5-12.PNG)
  
  ## Another Missing Dependency
  I restarted VSC and got this error: 
  
  ***[Error - 13:55:17] Cannot find module 'eslint-config-prettier' Referenced from: /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/.eslintrc.json***
  
  So I also ran:
  
  `npm install --save-dev eslint-config-prettier`
  
  Now I see `eslint-plugin-prettier` but no `eslint-config-prettier` in the node_modules. But I do see both in the `"dependencies"` in the `package.json`.
  
  ## Restart VSC to See the Dependencies
  
  I restarted VSC and now I see the `eslint-config-prettier`! ***So maybe after you add a dependency through the terminal you have to refresh VSC.***
  
  ## Prettier Configs
  
  I added this back to the `.eslintrc.json` file which Wes Bos said to add:
  
  ```javascript
    "prettier/prettier": [
    "error",
    {
      "singleQuote": true
    }
  ]
  ```
  
  But I got this error:
  
  ***Error: ESLint configuration in /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/.eslintrc.json is invalid:***
  ***Unexpected top-level property "prettier/prettier".***
  
  In these [docs for eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) they have ***the `"prettier/prettier"` property inside the `"rules"` property. I moved it there and that error went away.***
  
  ```javascript
  "rules": {
    "no-console": "off",
    "prettier/prettier": [
      "error",
      {
        "singleQuote": true
      }
    ]
  }
  ```
  
  ## Still Missing Dependencies
  
  But I have new errors:
  
  ***[Error - 14:13:42] ESLint stack trace:***
  ***[Error - 14:13:42] Error: Cannot find module 'prettier'***
  
  So I ran:
  
  `npm install --save-dev prettier`
  
  and restarted VSC.
  
  No errors!
  
  Now let's see if it worked.
  
  ## Working (sort of)!
  
  It fixing on save on .js files on. But not .html. It is registering prettier on those files:
  
  ![screenshot](log_imgs/prettiernotif_5-12.PNG)
  
  But when I save it doesn't change the quotes.
  
  ## Prettier Doesn't Work on Script Tags
  
  Looks like it's not possible to fix on auto save in the HTML files:
  
  >It's a planned feature but not supported just yet.
  
  ***-from [How to format code in script tags?](https://github.com/prettier/prettier/issues/2648)***
  
  ## Summary
  
  Looks like I got it working. My problem was that I never actually installed the dependancies. I don't know why that wasn't part of the Wes Bos tutorial. Now I understance a little more about how the dependancies work, where they are, and how to add them. I'm glad I took the time to figure this out because I understand these packages better. That will come in handy when I learn node which I'm going to do soon!

## Day 31, R2
### 5/11/19

- ## Getting ESLint to Work on HTML AGAIN

  I'm trying to figure out these npm packages. I can't get ESLint to lint the HTML in my `playing_with_javascript` directory.
  
  I tried adding configurations to the user settings instead of the `.eslintrc.json` file according to this tutorial: [Eslint setup in Visual Studio Code](https://youtu.be/o2H8kvuwMKE?t=344)
  
  I deleted all my files in `playing_with_javascript` related to node or eslint. I followed this video to install eslint: [Eslint setup in Visual Studio Code](https://youtu.be/o2H8kvuwMKE?t=344). I made sure my terminal was in my project directory.
  
  I got this notification in my terminal: ***"We recommend using this local copy instead of your globally-installed copy."*** How do I control which one my project uses? Not sure, but I can see that it's loading locally in the ESLint tab.
  
  ## ESLint HTML Plugin
  
  In my project directory I ran `npm install --save-dev eslint-plugin-html`, following: [How can I get ESLint to lint HTML files in VSCode?](https://stackoverflow.com/questions/54138689/how-can-i-get-eslint-to-lint-html-files-in-vscode/54138880#54138880)
  
  I added this to the `.eslintrc.json` file:
  ```javascript
  "plugins": [
    "html"
  ]
  ```
  
  I also ran `eslint --ext .html,.js playing_with_javascript` while in the `100daysofcode` directory:
  
  > Note: by default, when executing the eslint command on a directory, only .js files will be linted. You will have to specify extra extensions with the --ext option. Example: eslint --ext .html,.js src will lint both .html and .js files in the src directory. See ESLint documentation.
  
  -*from [BenoitZugmeyer/eslint-plugin-html](https://github.com/BenoitZugmeyer/eslint-plugin-html#usage)*
  
  ## It Works Now But...
  
  Ok I just realized it actually works. ESlint is linting HTMl files in `playing_with_javascript`. But I hadn't realized it was working for a while. I'm not sure for how long. So I'm not sure what I did that was necessary and what was unneccessary.
  
  ## Undoing Adding ESLint
  
  I'm going try to undo everything I did when trying to add ESLint and the html plugin. Then do it again so I can see when it actually starts linting the HTML.
  
  ## Uninstalling ESLint
  Following this: [Uninstalling packages and dependencies](https://docs.npmjs.com/uninstalling-packages-and-dependencies). 
  
  In my project directory, I ran `npm uninstall eslint` and it didn't look like it did anything. 
  
  So I also ran `npm uninstall --save eslint`. That didn't look like it did anything either because my `node_modules` folder, `.eslintrc.json` file, and package.json file were all still there. 
  
  But when I restarted VSC it wasn't loading ESlint anymore. I looked it my `package.json` file and I could see eslint wasn't there, just some of the plugins that go with eslint were there:
  
  ```javascript
  "devDependencies": {
    "eslint-config-airbnb-base": "^13.1.0",
    "eslint-plugin-html": "^5.0.3",
    "eslint-plugin-import": "^2.17.2"
  }
  ```
  
  And I no longer saw the `eslint` folder in `node_modules`. So I guess the command **did** remove ESLint, it just didn't get rid of npm. Maybe that seems like obvious behavior to most people, but I'm still trying to understand this all.
  
  ## Uninstalling NPM
  
  I couldm't find any information about removing npm locally through the terminal, except for this:
  
  > Local installs are completely contained within a project’s node_modules folder. Delete that folder, and everything is gone (unless a package’s install script is particularly ill-behaved).
  
  -*from [npm-removal Cleaning the Slate](https://docs.npmjs.com/misc/removing-npm.html)*
  
  It doesn't mention the `package.json` file or other files that were installed with npm. I'm just going to delete them.
  
  ## `--ext`
  
  The only thing I still have to undo is this command: `eslint --ext .html,.js playing_with_javascript`. But I'm not sure what it did? How to undo it? I could maybe set it back to just `.js`, like this: `eslint --ext .js playing_with_javascript` But I'm not sure if that would undo the command to lint html extensions. I really don't know what this command is changing? Is there a configuration somewhere?
  
  >My questions are:

  >I couldn't find the configuration option for doing this from .eslintrc.
  >
  >...
  >
  
  One of the answers:
  >You can’t define this in .eslintrc files because file traversal happens before the configuration is read
  [Configuration option for '--ext' switch #3469](https://github.com/eslint/eslint/issues/3469)
  
  So it's not in the  `.eslintrc.json` file. 
  
  I think if I just pass in .js, it will set it to only use .js extensions again because I found this:
  
  >Use only .js2 extension
  >eslint . --ext .js2
  
  -*from [Command Line Interface](https://eslint.org/docs/user-guide/command-line-interface#--ext)*
  
  I ran `eslint --ext .js playing_with_javascript`. I got an error:
  
  ![screenshot](log_imgs/error_5-11.PNG)
  
  This is confusing. If you can't define the extensions in the `.eslintrc` files, then why would it matter that there is no `.eslintrc` file? But maybe, even though the extenson configurations aren't stored there, you for some reason still need that file.
  
  ## Starting over
  
  I think everything is reset to how it was to begin with in my `playing_with_javascript` directory. So I started again.
  
  ## It worked!
  
  This is what I did:
  
  I ran these commands on the project directory and followed the prompts for each:
    
  `npm init`
  `eslint --init`
  
  I restarted VSC and ESLint now ***lints the HTML*** on the `playing_with_javascript` directory even though I did nothing else. Probably because I put this in the user settings for my workspace earlier:
 
  ```javascript
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "html"
  ],
  "eslint.options": {
    "plugins": [
      "html"
    ]
  },
  ```
  
  Normally the plugins can be put in the `.eslintrc.json` file. But when it's in the user settings in `"eslint.options"` it applies to the workspace.
  
  I'm not sure if `eslint --ext .html,.js playing_with_javascript` did anything earlier. 
  
  ## Summary
  
  So I did a lot of stuff I didn't need to do but I learned a lot in the process.
  
## Day 30, R2
### 5/10/19

- ## Helping
  Today I got to help someone who posted about a css issue on Twitter. I have yet to hear back if it was helpful. Hopefully it was.
  
  They were having trouble getting these inputs to vertically align:
  
  ![img](log_imgs/help_5-10.PNG)
  
  ### 1. To start, I added a border to all the divs to see better what was going on:
  
  ```css
  * {
  border: 1px solid red;
  }
  ```
  
  ### 3. I got rid of these extra divs:
  
  ![img](log_imgs/start_5-10.PNG)
  
  ![img](log_imgs/divs_5-10.PNG)
  
  ### That gave me these centered but misaligned inputs:
  
  ![img](log_imgs/centered_5-10.PNG)
  
  ### 4. I added a class to the labels so I could make their widths uniform to align everything:
  
  ![img](log_imgs/labelclass_5-10.PNG)
  
  ### 5. Added `text-align: right` to line up the colons.
  
  ![img](log_imgs/done_5-10.PNG)
  
- ## Prettier
  Now I need to figure out how to get prettier to work. I'm going to do some investigating to see how these extensions work.
  
  ## ESLint-plugin-html
  
  I have the plugin `eslint-plugin-html` locally and globally. I wasn't sure which I was using with my `perfect_fit_meal` project. To find out, I messed with the file name of my local plugin.
  
  <img src="log_imgs/name_5-10.PNG" width="300">
  
  When I restarted VSC it gave me this error:
  
  ![img](log_imgs/terminal_5-10.PNG)
  
  So now I know that my `esLint-plugin-html` is coming from the local directory.
  
  ## What about other project directories?
  
  I wonder how ESLint will work in other project directories? Where will it load from?
  
  I opened the directory for a project called `playing_with_javascript`, a project that didn't have ESLint installed locally to see what would happen. One thing to note is both these directories, `playing_with_javascript` and `perfect_fit_meal`, are in the same workspace. So I believe they share the same user settings.
  
  ## No Local ESLint? Load Globally
  
  This directory, `playing_with_javascript`, loaded ESLint from my global modules.
  
  ![img](log_imgs/noconfig_5-10.PNG)
  
  As you can see from the underlined error, it looks like your `.eslintrc.json` should in to your project directory even if there's no local ESLint.
  
  ## Adding Configs
  
  I copied the `.eslintrc.json` file from my `perfect_fit_meal` directory and pasted it in to `playing_with_javascript`. Now we can see it's using the config file to get the airbnb style guide, but it can't find the airbnb module.
  
  ![img](log_imgs/noairbrb_5-10.PNG)
  
  ## Adding `node_modules`
  
  To get the air bnb module into the project, I copied the `node_modules` directory from the `perfect_fit_meal` directory. I pasted it into the `playing_with_javascript` folder.
  
  Now `playing_with_javascript` loads the ESLint locally from the local `node_modules` folder instead of the global one. And it's gettting the airbnb module from there. We can tell that it's getting the airbnb module from there because that error went away after adding `node-modules`.
  
  ![img](log_imgs/local_5-10.PNG)
  
  But our html files aren't getting linted.
  
  ## Why Aren't HTML Files Getting Linted?
  
  I messed with the `eslint-plugin-html` directory name again to see if that would cause issues. It did. So I know the html plugin is being accessed. 
  
  ![img](log_imgs/failed_5-10.PNG)
  
  I changed the folder name back. The error went away. 
  
  But why isn't ESLint linting the html files in `playing_with_javascript`?
  
  This is where I left off. Confused still, but a little less so. So I'm stoked!
  
  
## Day 29, R2
### 5/9/19

- ## Recipe Calculator
  ## To Do
  - Set Up dotenv
  - lint my code
  - Look into Prettier vsc extension because [Jacob M-G Evans  ⚛ @JacobMGEvans](https://twitter.com/JacobMGEvans) said it goes well with ESLint (but what about Beautify?)
  
  ## Prettier
  I started to set up Prettier as a ESLint plugin following Wes Bos's tutorial.
  
  [How to Setup VS Code + Prettier + ESLint](https://www.youtube.com/watch?v=YIvjKId9m2c)
  
  ## Errors!
  Now my ESlint is underlining the wrong things. For example, it underlines `this.readyState` but when I hover over `this.readyState`, ESLint tells me what's wrong with a *different* part of my code.  I deleted everything I added to my settings and configurations and it works again. 
  
  It's probably not working because *Prettier* failed to load:
  
  Terminal:
  
  ```
  Failed to load plugin prettier: Cannot find module 'eslint-plugin-prettier'
  Happened while validating /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/index.html
  This can happen for a couple of reasons:
  1. The plugin name is spelled incorrectly in an ESLint configuration file (e.g. .eslintrc).
  2. If ESLint is installed globally, then make sure 'eslint-plugin-prettier' is installed globally as well.
  3. If ESLint is installed locally, then 'eslint-plugin-prettier' isn't installed correctly
  ```
  
  So these extra *Prettier* configurations are maybe throwing off my ESlint configs since Prettier isn't actually installing. I don't know but I want to get *Prettier* to work.
  
  ## Is My ESLint Installed Globally?
  
  Since these errors had to do with whether ESLint was installed locally or global, I had to figure that out.
  
  [How to tell if npm package was installed globally or locally](https://stackoverflow.com/questions/26104276/how-to-tell-if-npm-package-was-installed-globally-or-locally):  
  - `npm list -g`
  - `npm list -g --depth=0`
  
  ### My Global Packages:
  
  <img src="log_imgs/terminal_5-9.PNG" width="400"/>
  
  Looks like **it's installed globally.** 
  
  But, it's **also installed locally** since I can see the *ESlint* files in my project directory. That's probably causing issues.
  
  ## ESLint Button
  
  I figured out how to get that little "ESLint" button to show up in the corner:
  
  Put `"eslint.alwaysShowStatus": true` in your user settings in vsc.
  
  ![eslint_button](log_imgs/eslint_5-9.PNG)
  
  When I click on the ESLint status button button, a tab pops up that shows where my project is getting *ESLint* from:
  
  >[Info  - 14:55:45] ESLint server is running.
  >
  >[Info  - 14:55:45] ESLint library loaded from:
  >
  >/Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/node_modules/eslint/lib/api.js
  
  So it looks like it's getting it locally. But I'm not sure. Maybe the global installation is interfering?
  
  Also I'm curious where it's getting the ESLint html plugin from, because I saw it both locally and globally. 
  
  I think there's problems with ESLint being local and global. 
  
  ## What To Do?
  
  ### Do I need to install the ESLint prettier plugin both locally *and* globally?
  
  or
  
  ### Do I need to uninstall either my global or local ESLint package so that I only have one package? And then get prettier to work for that?
  
  I'm nervous that if I delete either package, I'll break my `eslint_html_plugin` which took me a while to get to work.

  ## `.eslintrc.json`
  
  I wanted to see if I could find a `.eslintrc.json` file in the global installation of EsLint. To find the global directory:
  
  [Where does npm install packages](https://stackoverflow.com/questions/5926672/where-does-npm-install-packages):
  
  - `npm list -g`
  
  <img src="log_imgs/path_5-9.PNG" width="400"/>
  
  To see this file from the GUI (Finder) I followed this: [how to browse /usr/local directory in finder?](https://discussions.apple.com/thread/5418731)
  
  I didn't see `.eslintrc.json` file in the global eslint directory. So I'm not sure how to add Prettier globally and then how do you configure it? Or do you install it through the command line globally and then configure it locally? Do you just manually add the `.eslintrc.json` file to the global package? So confused.
  
  ## Should ESLint be Global or Local?
  
  > We generally recommend installing ESLint and dependencies locally. It makes for a more reliable experience and it's better for collaboration as well.

  *[Kevin Partington platinumazure](https://github.com/eslint/eslint/issues/10533)*

  >If you want to include ESLint as part of your project’s build system, we recommend installing it locally. 
  >...
  >
  >If you want to make ESLint available to tools that run across all of your projects, we recommend installing ESLint globally.
  
  [Getting Started with ESLint](https://eslint.org/docs/user-guide/getting-started)
  
  ## Uninstalling NPM Packages:
  
  I wanted to see how to uninstall ESlint. I found this:
  
  [Uninstalling packages and dependencies](https://docs.npmjs.com/uninstalling-packages-and-dependencies):
  
  - Unscoped packages: `npm uninstall <package_name>`
  - Scoped packages: `npm uninstall <@scope/package_name>`
  
  What does "scoped" mean? Here's the documentation for [npm-scope Scoped packages](https://docs.npmjs.com/misc/scope), but this is over my head. Is my ESLint scoped? I think not:
  
  > The scope folder (@myorg) is simply the name of the scope preceded by an @ symbol, and can contain any number of scoped packages.
  *[npm-scope Scoped packages](https://docs.npmjs.com/misc/scope)*
  
  ESlint isn't preceded by an **@** symbol *so I think it's **not** a scoped package.*
  
- ## Thoughts & Feelings:
  These packages keep running me into trouble. I don't really understand how they work. I'm not sure how to get more practice with them or what resources to use to understand them. I was watching an npm tutorial but I feel like it skipped a lot of information. Maybe I need to finish that tutorial. But then how to I get hands on practice/experience with these packages?

## Day 28, R2
### 5/8/19

- ## Recipe Calculator
  ## Custom Type Ahead
  
  I got the custom type-ahead to select the suggestion when it is either clicked or `enter` is pressed. 
  
  I changed around the event listeners:
  
  ```javascript
  foodInput.addEventListener('keyup', displaySavedFoods);
  form.addEventListener('keydown', formHandler);
  suggestions.addEventListener('mouseover', changeFocus);
  suggestions.addEventListener('click', searchSuggestedFood);
  ```
  Now, `changeFocus` is called on the `suggestions` list element, before it was called on `form`, which `suggestions` is a child of. I think it reads better.

  I also had to change the callback for `form.addEventListener('keydown',...` from `traverseFocus` to `formHandler`. This is because `form.addEventListener('keydown',...` now has two possible callbacks: `traverseFocus` or `searchSuggestedFood` depending on what key the user pressed.
  
  I also cleaned up irrelevent css and but my css in a separate file. 
  
  Thanks to [Philippe Vaillancourt
@snowfrogdev](https://twitter.com/snowfrogdev) and [Giuseppe 🇮🇹
@montyDev_](https://twitter.com/montyDev_) for the ideas to clean up the CSS and move the event listener to a different element.
  
  ## Added Documentation for Type-ahead Search
 
  I'm calling this a finished project! 
  
  It's just one part of my larger project, but I the search feature it might help others with their projects so I put it out with documentation.
  
  You can go to [Type-ahead Search](https://github.com/DashBarkHuss/type_ahead_search) to see the complete project, along with the documentation.
  
  ![screenrecording](log_imgs/ux_5-8.gif)

**Link To Work:** [Type-ahead Search](https://github.com/DashBarkHuss/type_ahead_search)

- ## Thoughts & Feelings:
  Lately I haven't had to take much breaks. For the most part, I've sped through my two hours of coding with no breaks. Maybe coding is getting more habitual, and my brain needs less breaks because coding is less effortful for me now. Maybe it's because I raised my calories and my brain has excess fuel? I hope it's not that, because that means when I do a cut, my brain will need more breaks.

## Day 27, R2
### 5/7/19

- ## Recipe Calculator
  ## Custom Type Ahead
  
  Today I created two event listeners that change the focus to different suggestions in the type-ahead feature.
  
  ```javascript
  form.addEventListener('keydown', traverseFocus);
  ```
  `traverseFocus()` traverses through the suggestions when you press the up or down arrow.
  
  ```javascript
  form.addEventListener('mouseover', changeFocus);
  ```
  
  `changeFocus()` changes the focus to whatever suggestion you mouseover.
  
  <img src="log_imgs/ui_5-7.gif" width="400">
  
  ## Focus
  
  I used the [`focus()` method](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/focus) to set the focus.
  
  I used the [.activeElement property](https://developer.mozilla.org/en-US/docs/Web/API/DocumentOrShadowRoot/activeElement) to find the last element that had focus in order to traverse the suggestions.
  
  ## To Do
  
  I still have to add functionality for when you select a suggestion.
  

**Link To Work:** [Type Ahead Search, not finished](https://github.com/DashBarkHuss/type_ahead_search/tree/5699e5a8a6580426cea92c5d07808d8bdd87a5b5)
  

## Day 26, R2
### 5/6/19

  
- ## Recipe Calculator
  ## Custom Type Ahead Conditionals
  I got my conditionals working. In "link to work."
  
  ## Functionality
  I started working on the functionality of the 'type ahead' feature. The up and down arrows should traverse the options and enter should select it. Mouse should work too. I'm not posting it cause it's a mess still. 
  
  This is going to be a short post today because I'm in a hurry to get to my host's house.
  
**Link To Work:** [Type Ahead Search, not finished](https://github.com/DashBarkHuss/type_ahead_search/tree/a74f0cfdf79e954a85ba00ee050fe57f4606ffd4)


## Day 25, R2
### 5/5/19

- ## Recipe Calculator
  Today we're moving the type ahead output from the console to the UI. This type ahead feature suggests foods to search form a list of saved foods in a json file.
  
  ## Custom Type Ahead UX
  
  I wasn't sure about the UX for the type ahead feature. Should choosing a suggested entry *search* that entry? Or should it *select* that entry and add it to the recipe? I decided to copy what the [USDA database](https://ndb.nal.usda.gov/ndb/search/list) does.
  
  ![usda](log_imgs/usda_5-5.gif)
  
  If you select the suggestion it searches the suggestion. It doesn't choose that entry, which on the USDA database would mean taking you directly to that entries nutrient page.
  
  
  ## Conditionals Not Right
  
  I need to redo my conditional statements so that the `#suggestions` div doesn't display anything when there's no input in the search field. This doesn't work quite right:
  
  ```javascript
  async function displaySavedFoods(){
  const foods = await fetch("saved_food_data.json").then(x=>x.json()).then(x=>x.foods);
  const searchTerm = foodInput.value;

  const filtered = filter(foods, searchTerm);
  const filteredChanged = filtered.length != lastFiltered.length;
  if (filteredChanged){
       const div = document.querySelector("#suggestions");
       div.innerHTML="";
       div.style.width = `${foodInput.offsetWidth}px`;
       if(searchTerm==""){
         lastFiltered="";
         return;
       } else {
         filtered.forEach(x=>div.innerHTML+=`<li>${x.name}</li>`);
         lastFiltered = filtered;
       }
     }
  }
  ```
  <img src="log_imgs/ui_5-5.gif" width="400">
  
  As you can see, even though I have no input in the text field at the end of this gif, the `#suggestions` div still displays.

**Link To Work:** [Type Ahead Search, not finished](https://github.com/DashBarkHuss/type_ahead_search/tree/644753d33806dd4994883e68d4177c2182a9be67)


## Day 24, R2
### 5/4/19

- ## Recipe Calculator
   May the 4th and day 24th be with you!
   
  ## Devtools Console + Sources
  
  To open the **console** and **sources** at the same time:
  
  Press `esc` while on the **Sources Panel**
  
  ![sources and console](log_imgs/console_sources_5-4.gif)
  
  ## Custom Type Ahead
  
  I got my custom type-ahead to pick the correct saved foods. But right now it just logs the results to the console. 
 
  ```javascript
  const form = document.querySelector("form[name=food_search]");
  foodInput = form.querySelector("#food_to_search"); //food search input
  let lastFiltered=[];
  
  async function displaySavedFoods(){
  const foods = await fetch("saved_food_data.json").then(x=>x.json()).then(x=>x.foods);
  const searchTerm = foodInput.value;
  const filtered = filter(foods, searchTerm);
  const filteredChanged = filtered.length != lastFiltered.length;
  if (filteredChanged){
    console.log("%cFiltered:", "color:red;font-size:20px;");
    filtered.forEach(x=>console.log(x.name));
    lastFiltered = filtered;
  }
  }

  function filter(foods, searchTerm){
    let filtered = foods;
    const terms = searchTerm.split(" ").map(x=>x.toLowerCase());
    for(i=0; i<terms.length; i++){
      filtered = filtered.filter(food=>food.name.toLowerCase().includes(terms[i]));
    }
    return filtered;
  }
  
  foodInput.addEventListener('keyup', displaySavedFoods);
  ```
  
  ![type-ahead](log_imgs/type_ahead_5-4.gif)
  
  I tried to use regex for this but had trouble. I think regex would improve the performance of the algorithm.

## Day 23, R2
### 5/3/19

- ## Async, Ajax, Promises
   Was confused why `getData()` was returning a promise when 'name' is not a promise. I did the same lines of code that are in my `getData()` function, in the console to compare what `name` returns in the console with what `getData()` returns.

  ![async](log_imgs/async-5-3.PNG)
  
  Oddly, you can only use `await` inside a function with the `async` keyword. So, I'm not sure how it's working in my console, but it is.
  
  ## Async Always Returns a Promise
  
  This is why `getData()` returns a promise:

  >The word “async” before a function means one simple thing: a function always returns a promise. Even If a function actually returns a non-promise value, prepending the function definition with the “async” keyword directs JavaScript to automatically wrap that value in a resolved promise.
  
  *[Async/await](https://javascript.info/async-await)*
  
  ## Loading in Parallel vs in Sequence
  
  In the [Fun Fun Function Async/Await video](https://youtu.be/568g8hxJJp4?t=991) the instructor says that in his async/await example the images are being loaded in *sequence* and in the promise example they are being loaded in *parallel*.
  
  I read a little more about that here: [JavaScript Async/Await: Serial, Parallel and Complex Flow](https://techbrij.com/javascript-async-await-parallel-sequence)
  
  Still not quite sure what that means, but I have more of a broad idea now.
  
- ## Recipe Calculator
  ## Custom Type Ahead
  
  I went back to my type-ahead problem for my recipe calculator. This is the one chrome does automatically. But I want my custom type-ahead to pull from a list of saved ingredients.
  
  ### Chrome's Type-Ahead
  <img src="log_imgs/type_ahead_5-3.PNG" width="500">
  
  I ended up using async/await for this. 
  
  I also realized that async/await can help with debugging because it's easier to debug with sequencial code. But I'm not sure if that really makes sense. 
  
  I didn't finish. I should start commiting my work again, but not today.  

## Day 22, R2
### 5/2/19

- ## Async, Ajax, Promises
  I read this article that I started yesterday:
  
  [Async, Callback & Promise](https://medium.com/front-end-weekly/ajax-async-callback-promise-e98f8074ebd7)
  
  It also talked about CORS and JSONP which I'm still new to.
  
  ## Async Call Values
  
  Yesterday I learned:
  
  > you cannot return from an asynchronous call inside a synchronous method.
  
  *[How To Return Value from an Asyncronous Callback Function](https://stackoverflow.com/questions/6847697/how-to-return-value-from-an-asynchronous-callback-function)*
  
  So today I redid my AJAX call. It pushes the data to an array instead of tryin to return the data.
  
  ![array](log_imgs/array_5-2.PNG)
  
  ## Redo Above With Promise:
  
  I redid the above with a promise.
  
  ![promise](log_imgs/promise_5-2.PNG)
  
  ## Async Await
  I went back to [this video by Fun Fun Function about async/await](https://www.youtube.com/watch?v=568g8hxJJp4) to learn about async/await now that I've played with promises more.
  
  I like this definition the instructor gives about async/await:
  
  ![async/await](log_imgs/async_await_5-2.PNG)
  
  I played with async/await a bit.

## Day 21, R2
### 5/1/19

- ## Promises
  
  I played with this function that returns a promise of an XMLHttpRequest.
  
  ```javasript
  const makeRequestPromise = (url) => {
    const request = new XMLHttpRequest();

    return new Promise((resolve, reject) => {
      request.onreadystatechange = () => {
        if (request.readyState !== 4) return;
        if (request.status >= 200 && request.status < 300) {
          resolve(request);
        } else {
          reject(new Error({
            status: request.status,
            statusText: request.statusText,
          }));
        }
      };
      request.open('GET', url, true);

      request.send();
    });
  };
  ```
  
  It helped me see how promises work and `.then()`
  
  ![promises](log_imgs/promise_5-1.PNG)
  
  ## Return Value Asyncronous Callback
  
  ![return](log_imgs/return_5-1.PNG)
  
  > you cannot return from an asynchronous call inside a synchronous method.
  
  *[How To Return Value from an Asyncronous Callback Function](https://stackoverflow.com/questions/6847697/how-to-return-value-from-an-asynchronous-callback-function)*
  
  ## Promises vs AJAX & Callbacks
  
  Still trying to sort these out. Here's some resources I'm looking at.
  
  >You are confused about promises and Ajax calls. They are kind of like apples and knives. You can cut an apple with knife and the knife is a tool that can be applied to an apple, but the two are very different things.
  >
  >Promises are a tool for managing asynchronous operations. They keep track of when asynchronous operations complete and what their results are and let you coordinate that completion and those results (including error conditions) with other code or other asynchronous operations. They aren't actually asynchronous operations in themselves. An Ajax call is a specific asynchronous operation that can be used with with a traditional callback interface or wrapped in a promise interface.

  *[What's the Difference Between Promise and Ajax](https://stackoverflow.com/questions/39751395/whats-the-difference-between-promise-and-ajax)*
  
  [Async, Callback & Promise](https://medium.com/front-end-weekly/ajax-async-callback-promise-e98f8074ebd7)
  
  

## Day 20, R2
### 4/30/19

- ## Fetch API

  ### Warning, I was confused during this word vomit:

  I was examing the the Fetch API and I wanted to know what `.json()` does. I couldn't find it in the Promise directory (`console.dir(Promise)`). I found out [.json()](https://developer.mozilla.org/en-US/docs/Web/API/Body/json) is a [method on the Body mixin](https://developer.mozilla.org/en-US/docs/Web/API/Body) of the Fetch API.

  ## Mixins
  >As defined in Wikipedia, a mixin is a class that contains methods for use by other classes without having to be the parent class of those other classes.
  
  *[Mixins](https://javascript.info/mixins)*
    
  ```javascript
  // mixin
  let sayHiMixin = {
    sayHi() {
      alert(`Hello ${this.name}`);
    },
    sayBye() {
      alert(`Bye ${this.name}`);
    }
  };

  // usage:
  class User {
    constructor(name) {
      this.name = name;
    }
  }

  // copy the methods
  Object.assign(User.prototype, sayHiMixin);

  // now User can say hi
  new User("Dude").sayHi(); // Hello Dude!
  ```
  
  In the example above, we see the mixin methods in the `Users` prototype.
  
  <img src="log_imgs/user_4-30.PNG" width="300">
  
  But I don't see that in the Promise directory.
  
  >The Body mixin of the Fetch API represents the body of the response/request...
  >
  >Body is implemented by both Request and Response
  
  *[Body, Mozilla Docs](https://developer.mozilla.org/en-US/docs/Web/API/Body)*
  
  ### Unconfused:
  
  **Oh duh**, it's on the ***Fetch API**, not a method on **Promise!*** I was confusing Promise with the Fetch API.
  
  [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API):
  
  > Fetch provides a generic definition of Request and Response objects (and other things involved with network requests).
  
  [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request)
  
  [Response](https://developer.mozilla.org/en-US/docs/Web/API/Response)
  
  The [Body methods](https://developer.mozilla.org/en-US/docs/Web/API/Body#Methods) **are** in the Response directory for example. Same with Request.
  
  <img src="log_imgs/response_4-30.PNG" width="400">
  
  
  I'm less confused but still kind of confused with how all of these relate.
  
  >The fetch() method takes one mandatory argument, the path to the resource you want to fetch. It returns a Promise that resolves to the Response to that request, whether it is successful or not...
  > 
  >Once a Response is retrieved, there are a number of methods available to define what the body content is and how it should be handled (see Body).
  
  A little more clear.
  
  ## Promises
  
  >Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function.
  
  *[Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)*
  
  Theres an example on that page of a Promise with attached callbacks vs passing callbacks into a function.
  
  To understand the difference between Promises and regular XHR I looked at this [page on how to combine XHR and promises](https://gomakethings.com/promise-based-xhr/). I followed along and made this Promise based XHR. Then I made a regular XHR. Tomorrow, I'll play around with them.
  
- ## Thoughts and Feelings:
  Sometimes writing my thoughts out in my log can help me understand what I'm thinking and why I'm confused. 
  
  I need to remember that when I feel like I don't want to code because something is hard, that feeling will soon pass. And come again. And pass again.
  
## Day 19, R2
### 4/29/19

- ## Helping
  I helped someone today on twitter. They sent their code and I showed them what each line was doing and where they had a typo:
  
  **Typo:**
  <hr>
  <img src="log_imgs/typo_4-29.PNG" width="300">
  
  **Step Through:**
  <hr>
  <img src="log_imgs/help_4-29.PNG" width="600">
  

- ## Toggle Eslint
  I couldn't find a built-in way to do this but I found this [Setting Toggle extension by Ho-Wan](https://marketplace.visualstudio.com/items?itemName=Ho-Wan.setting-toggle).
  
  I set my user settings to toggle the `eslint.enable` setting.
  
  <img src="log_imgs/settings_4-29.PNG" width="500">
  
  Then I can press this button to turn Eslint on and off.
  
  <img src="log_imgs/toggle_4-29.PNG" width="500">
  
- ## What Happen To My Log
  
  I looked at my old log and the markdown is not rendering:
  
  https://github.com/DashBarkHuss/100-days-of-code/blob/master/r1-log.md
  
  <img src="log_imgs/log-29.PNG" width="500">
  
  It looks like I'm in edit mode but I'm not. What's up?
  
  Ok I don't know what happened, it's working again.
  
- ## Async/Await & Promises

  I ran into this [exact problem on stackoverflow](https://stackoverflow.com/questions/54082327/why-does-logging-the-result-of-fetch-break-it-body-stream-is-locked) with `fetch()`. I get this error when I try to `console.log` the promise: `Uncaught (in promise) TypeError: Failed to execute 'json' on 'Response': body stream is locked`
  
  The reason is because:
  
  >.json() (and .body(), .text()) may only be called once.
  >
  >The HTTP request is modeled as a stream, and you can't really read from a stream twice.

- ## Thoughts and Feelings:
  Coding was hard today because I was hungry and freezing in the super cold cafe.

## Day 18, R2
### 4/28/19

- ## NPM
  ## Lynda: Learning npm the Node Package Manager
  ### Notes:
  **--save-dev** is used to save the package for development purpose. 
  
  **Where global packages are stored on Mac** /user/local/lin/node_modules or /user/local/lin/node
  
  **-g or -glabal**: add to `npm install` command to install globally
  
  **How to resolve permissions errors**: [Resolving EACCES permissions errors when installing packages globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)

- ## ESLint
  ## ESLint on HTML!
  I decided to go back and try to get ESLint to work on HTML files. 
  
  I found this [stackoverflow thread](https://stackoverflow.com/questions/54138689/how-can-i-get-eslint-to-lint-html-files-in-vscode) on ESlint and HTML files.
  
  One of the answers says:
  >I have this in <projectfolder>/.vscode/settings.json
  >
  >{
  >  "eslint.validate": [ "javascript", "html" ]
  >}
  
  `.vscode` is in the directory for the workspace folder, *not* the project folder. That confused me! I found these settings in that file:
  
  ```javascript
  "eslint.validate": [
    "javascript",
    "javascriptreact"
  ]
  ```
  That file is **read-only** so I added this to the **user settings** panel.
  ```javascript
   "eslint.validate": [
        "javascript",
        "javascriptreact",
        "html"
      ]
  ```
  <img src="/log_imgs/settings_4-28.PNG" width="500" />
  
  ### Success! 
  
  <img src="/log_imgs/eslint_4-28.PNG" width="500" />
  
  Glorious red lines!
  
  ## Format in VSC
  
  <img src="/log_imgs/format_4-28.PNG" width="500" />
  
  ## AirBnb Style Guide
  
  I setup my EsLint to use the [AirBnb style guide](https://github.com/airbnb/javascript).
  
  ### Format Tabs
  AirBnb format uses 2 spaces for tabs so I changed my user settings so that tab is 2 spaces not 4. 
  
  [How to customize the tab-to-space conversion factor when using Visual Studio Code?](https://stackoverflow.com/questions/29972396/how-to-customize-the-tab-to-space-conversion-factor-when-using-visual-studio-cod)
  
  ### Functions
  
  I'm noticing that the airbnb style guide has some rules about naming functions. The style guide explains why [here](https://github.com/airbnb/javascript#functions) and [here it talks about arrow functions](https://github.com/airbnb/javascript#arrow-functions).
  
  ## Linting Is FUN!
  Maybe not fun, but this is really helpful! I'm always wondering "How should I best organize my code?" and "How can I make my code more readable?" Linting is like having a teacher over your shoulder telling you what to do and not to do. And then I can look up why in the [AirBnb style guide](https://github.com/airbnb/javascript). This is great! I need to thank that guy from the meetup in Austin!

  ## ESLint Toggle?
  If I want to temporarily toggle off the markings from ESlint; is there a way to do this **quickly**?
  
  I've seen a little ESLint button on the status bar of VSC in other people's setups. But it's not showing up on mine. I wonder if you can toggle ESLint on and off with this.
  
  ### My Status Bar
  <hr>
  <img src="/log_imgs/mineVSC_4-28.PNG" width="500" />
  
  ### Others' Status Bars
  <hr>
  <img src="/log_imgs/othersVSC_4-28.PNG" width="500" />
  
  Couldn't find anything about this in all my searches.
  
## Day 17, R2
### 4/27/19

I decided to look into npm today because I didn't know what I was doing yesterday trying to get ESLint to work. I'll probably be using npm a lot more. Getting more comfortable with npm will help prepare me for learning node.

- ## NPM
  Looked through some of this: [A Beginner’s Guide to npm — the Node Package Manager](https://www.sitepoint.com/beginners-guide-node-package-manager/)

  Watched some of this short a lynda video on package management: [Package Management Basics](https://www.lynda.com/Linux-tutorials/Package-management-Basics/618702/772939-4.html)
  
  Started watching the [Learning npm the Node Package Manager](https://www.lynda.com/Node-js-tutorials/Learning-npm-Node-Package-Manager-2018/761956-2.html) course on lynda.
   
  ## Lynda: Learning npm the Node Package Manager
  ### Notes:

  **package.json:** map for building your project and setting your dependencies.

  **npm init:** base command to initialize a new package.json file.

  **`Cmd` + `Shift` + `.` (dot):** toggle hide/show hidden files

  **locally installed:** When a package is installed locally it's installed on your projects directory.
  
  **globally installed:** When a package is installed globally it will be installed in your system available to all projects.
  
  ## Command Prompt Undo?
  
  I came accross this dilemma and posted it on [stackoverflow](https://stackoverflow.com/questions/55883264/is-it-possible-to-go-back-and-change-the-last-input-you-entered-into-a-command-p)
  
  <img src="log_imgs/npm_4-27.PNG"  width="600"/>

  ## JavaScript Modules: ES6 Import and Export
  The instructor in the lynda tutorial used `import`. I've seen this before but I've never used it.
  
  Here's the [`import` docs page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import).
  
  Here's a video on `import` and `export` that I didn't yet finish: [JavaScript Modules: ES6 Import and Export](https://www.youtube.com/watch?v=_3oSWwapPKQ).


## Day 16, R2
### 4/26/19
- ## Recipe Calculator
  ## Async/Await & Promises
  
  I played around with fetch and promises.
  
  I reviewed this video on promises: [Promises - Part 8 of Functional Programming in JavaScript](https://www.youtube.com/watch?v=2d7s3spWAzo)
  
  Then I started to watch this video on async/await: [async / await in JavaScript - What, Why and How - Fun Fun Function](https://www.youtube.com/watch?v=568g8hxJJp4)
  
  ## VSC Extensions
  In the async await video the instructor uses a cool inline evaluation tool called [Quokka](https://quokkajs.com/). I wanted to use it too but after downloading it following the [Quokka documentation](https://quokkajs.com/docs/) and the [Manage Extensions in Visual Studio Code](https://code.visualstudio.com/docs/editor/extension-gallery) page, I realized that to do what the teacher is doing I need the pro version. So forget quokka.
  
  ## ESLint
  
  I also added the ESLint extension and the Beautify extension.
  
  To set up ESLint I followed this: [Eslint setup in Visual Studio Code](https://www.youtube.com/watch?v=o2H8kvuwMKE). The process was a little different for me, so the video might be a little out of date. 
  
  ## ESLint on HTML Files
  I realized ESLint doesn't work on javascript sections on HTML files. It only works on .js files. However, you can add the [eslint-plugin-html](https://github.com/BenoitZugmeyer/eslint-plugin-html) to get ESLint to work on html files.
  
  ## Not Working on HTML Files
  I'm having trouble getting this to work. I'm not sure what this means, in the [docs](https://github.com/BenoitZugmeyer/eslint-plugin-html)
  
  > Note: by default, when executing the eslint command on a directory, only .js files will be linted. You will have to specify extra extensions with the --ext option. Example: eslint --ext .html,.js src will lint both .html and .js files in the src directory.
  
  I'm not sure what the `src` file should be in `eslint --ext .html,.js src`. I tried a path that goes out of my currect directory and back in like this:
  
  `perfect_fit_meal Dashie$ eslint --ext .html,.js ../perfect_fit_meal`
  
  But that didn't work. Now sure what to put there.
  
  I tried going out of the directory and then using the full path:
  
  `Fri Apr 26 ~ Dashie$ eslint --ext .html,.js /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal`
  
  That didn't work. I tried it again after installing the extension glolablly and that still didn't work.
  
## Cows Showed Up While I Was Coding
  
![cows](log_imgs/cows_4-26.jpg)

## Day 15, R2
### 4/25/19
- ## Recipe Calculator
  
  ## #100DaysOfMath
  In addition to the coding, I added 30 minutes of math study to complement #100daysofcode. I need some math skills for this app. I need to understand a math subject called *optimization*. 
  
  I talked to a twitter peer, Ross Mason, who said he under estimated the amount of math he needs for AI. Since I want to learn AI, I figured I'd start now brushing up on my math.
  
  So I'm doing a mini, not-so-serious, #100DaysOfMath. By not-so-serious I mean I probably won't post about it and I might skip days. It depends on what seems to be a priority on that day. I don't want to take on too much extra study, and then fall behind on what's really important.
  
  ## Scrollbar Size
  
  I figured out how to change the scroll bar size, add bottom `margin` to the `-webkit-scrollbar-track`. I added a top margin too because I thought it looked better. 
  
  ```css
  #search_results_wrapper::-webkit-scrollbar-track {
      margin: 4% 0 var(--add-button-height);
  }
  ```
  
  <img src="log_imgs/scroll_4-25.gif"  width="300"/>
  
  ## Promises & Fetch
  
  I worked on changing my `XMLHttpRequest`s to `fetch()` calls so I can work with promises. I also want to have a pedictive type ahead feature in my search bar like Wes Bos does in [Javascript30](https://courses.wesbos.com/account/access/5c51dab432bb6d664e015352/view/194130156). The problem is I don't think I can do one request for all food names and then just filter throught them, like Wes does. The NDB limits the number of items in a single request. Maybe there is a work around.

## Day 14, R2
### 4/24/19

- ## Recipe Calculator
  ## Overriding User Agent Stylesheet Issue

  <img src="log_imgs/override_4-24.PNG"  width="600"/>
  
  Both of these pages show a workaround, but I didn't find an explanation for why this happens:
  - https://css-tricks.com/snippets/css/change-autocomplete-styles-webkit-browsers/
  - https://mariusschulz.com/blog/how-to-remove-webkits-banana-yellow-autofill-background
  
  ### Workaround:
  
  <img src="log_imgs/overridegood_4-24.PNG"  width="600"/>
  
  Now it's working in my app!
  
  <img src="log_imgs/uiselected_4-24.PNG"  width="300"/>
  
  ## Scroll Bar
  
  I ended trying to add a scrollbar to the box that contains food search results. This way the user knows they can scroll.
  
  Depending on the browser window size, the user may not realize they can scroll:
  - Obvious Scroll:
     - <img src="log_imgs/scrollclear_4-24.PNG"  width="300"/>
  
  - Unclear Scroll:
    - <img src="log_imgs/scrollunclear_4-24.PNG"  width="300"/>
  
  I found [this tutorial](https://scotch.io/tutorials/customize-the-browsers-scrollbar-with-css) which helped me add a scroll bar. 
  
  ### Scrollbar Size
  Now I want to change the size of the scrollbar and scrollbar thumb. I think it might have something to do with `webkit-scrollbar-thumb`.
  
  This might help: https://stackoverflow.com/questions/26493446/change-size-of-scrollbar-thumb-with-css.
  
## Day 13, R2
### 4/23/19

- ## Recipe Calculator
  ## Wrapper Vs Container:
  
  
  >In programming languages the word container is generally used for structures that can contain more than one element.
  >
  >A wrapper instead is something that wraps around a single object to provide more functionalities and interfaces to it.
  
  *[CSS Language Speak: Container vs Wrapper?](https://stackoverflow.com/questions/4059163/css-language-speak-container-vs-wrapper)*
  
  ## Overriding User Agent Stylesheet Issue
  
  I ended with this issue. I'm having trouble over riding the `user agent stylesheet`.
  
  ![screenshot](log_imgs/override_4-23.PNG)
  
  ## Today's End Result
  
  <img src="log_imgs/ui_4-23.gif"  width="300"/>

## Day 12, R2
### 4/22/19

- ## Recipe Calculator
  ## Relative Position & Border Radius
  
  If you have a relative div inside an unpositioned div with rounded corners, you have to add positioning to the container div and z-index.
  
  ### Bad
  <img src="log_imgs/cornersbad_4-22.PNG"  width="300"/>
  
  ```css
  #container{
      border: 5px solid green;
      border-radius: 20px;
      height: 200px;
      overflow: scroll;
  }

  .rectangle{
      height: 60px;;
      background: rgb(31, 255, 31);
      border: 3px solid rgb(255, 255, 255);
      position: relative;
  }
  ```
  
  ### Good
  <img src="log_imgs/cornersgood_4-22.PNG"  width="300"/>
  
  ```css
  #container{
      border: 5px solid green;
      border-radius: 20px;
      height: 200px;
      overflow: scroll;
      position: relative; //________________added
      z-index: 0; //________________________added
  }

  .rectangle{
      height: 60px;;
      background: rgb(31, 255, 31);
      border: 3px solid rgb(255, 255, 255);
      position: relative;
  }
  ```
  ## Absolute Positioned Element in Front of Scroll
  
  This was hard to figure out. Finally got it.
  
  <img src="log_imgs/scroll_4-22.PNG"  width="300"/>
  
  ```css
    #big_container{
      border: 5px solid green;
      border-radius: 20px;
      height: 200px;
      overflow: hidden;
      position: relative;
      z-index: 0;

  }
  #container{
      overflow: scroll;
      position: relative;
      height: 100%;
  }

  .rectangle{
      height: 60px;;
      background: rgb(31, 255, 31);
      border: 3px solid rgb(255, 255, 255);
      position: relative;
  }
  .red{
      background: rgb(255, 31, 199);
      border: none;
      height: 40px;
      position: absolute;
      width: 100%;
      bottom: 0;
  }
  ```
  
  ```html
  <div id="big_container">
      <div id="container">
          <div class="rectangle"></div>
          <div class="rectangle"></div>
          <div class="rectangle"></div>
          <div class="rectangle"></div>
          <div class="rectangle"></div>
      </div>
      <div class="rectangle red"></div>
  </div>
  ```
  ### Push The Last Item Up
  I realized that when you scroll to the bottom the pink element is still covering part of the last item, so I added this css to push the last item up:
  
  ```css
  #container>.rectangle:last-child{
      margin-bottom: 40px;
  }
  ```
  
  ## Form Attribute
  In HTML5, you can use the form attribute to have a form submit button element outside of the respective form element:
  https://stackoverflow.com/questions/6644128/html-input-field-outside-of-form
  
  ## Coded While Driving Through a Dust Storm! 
  <img src="log_imgs/dust_4-22.gif"  width="600"/>

## Day 11, R2
### 4/21/19

- ## Recipe Calculator
  ## Shadow Color
  
  Originally I had a dark green color that matched the hue of the main background color but was a darker green.
  
  ```css
  --shadow: 0px 010px 8px rgb(7, 161, 136);
  --main-hue: rgb(5, 219, 184);
  ```
  
  This colored shadow caused issues. I couldn't use this shadow on other background colors. You don't naturally see dark green shadows on a white background, for example. Thar color of a shadow should change if the background is a gradient of two different colors.
  
  Colored shadows are limited. This green shadow works well on the green side of the gradient, but not the blue.
  
  <img src="log_imgs/greenshadow_4-21.PNG"  width="300"/>
  
  Black shadows with low opacity work on all colors.
  
  <img src="log_imgs/greyshadow_4-21.PNG"  width="300"/>  
  
  So I changed the shadow to black with a very low opacity.
  
  ```css
  --shadow: 0px 010px 8px rgba(0, 0, 0, 0.26);
  ```
  
  Now this shadow will work on any color.
  
  ## White Gap
  
  If you zoom in very close, you can see a white gap between a container that has a border, and the content inside that has a background color.
  
  ```html
  <style>
      #container{
          border: 5px solid green;
          border-radius: 
      }
      #content{
          background: green;
      }
  </style>
  <div id="container">
    <div id="content">
        some content
    </div>
  </div>
  ```
  <img src="log_imgs/whitegap_4-21.PNG"  width="300"/>
  
  You can't see it when zoomed out.
  
  <img src="log_imgs/nogap_4-21.PNG"  width="300"/>
  
  However you can see it in the corners when the corners of the divs are rounded.
  
  <img src="log_imgs/round_4-21.PNG"  width="300"/>
  
  ```html
  <style>
        #container{
            border: 5px solid green;
            border-radius: 20px;
        }
        #content{
            background: green;
            border-radius: 15px; //takes into account 5px border
        }
  </style>
  </head>
  <body>
  <div id="container">
    <div id="content">
        some content
    </div>
  </div>
  ```
  
  ### My solution: 
  Instead of giving the content div a border radius, give the container div an `overflow` of `hidden` or `scroll`. 
  
  ## To Do
  I left off with an issue where the content div is not contained in the container div even with the container is set to `overflow: scroll`. This only happens when the user hovers over the content div which changes the background color.
  
- ## Thoughts and Feelings:
  My log is taking up a lot of my time. I'm not sure if anyone reads it, and I'm not sure how much of it is for me. I think I will cut down on logging. I need to only post the things that will help me, like links that will be helpful later or explanations of concepts I have trouble with and need to remember. 
  
  It might be hard to see when a concept should be logged or not. I probably need a lot less words and explanation than I post now, if I'm going to just log to help myself.
  
  I think it's especially important that I cut down on logging while traveling. My internet & power is limited. I want to learn as much as I can without worrying as much about my log. My log should be a tool to help me, not something that holds me back and takes up my time. Right now it can take longer than an hour just for my log.
  
  I took a break from logging while at Big Bend because there wasn't enough reception out there. I found I got a lot done.



## Day 10, R2
### 4/20/19

  I didn't have internet on this day until th
