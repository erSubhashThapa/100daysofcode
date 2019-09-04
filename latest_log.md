## Day 47, R3
### 9/4/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  ### Where I Left Off
  I started working on crud.

  ## Varying Number of Passed Arguments
  I think this code is reassigning `callback` incase the function call didn't pass in an `options` argument. Which is a cool way to handle varying accepted amounts of arguments. But I'm not totally sure if that's what it's trying to do.
  ```javascript
  function readFile(path, options, callback) {
  callback = maybeCallback(callback || options); 
  // more code bla bla bla
  }

  function maybeCallback(cb) {
  if (typeof cb === 'function')
    return cb;

  throw new ERR_INVALID_CALLBACK(cb);
  }
  ```
  ## VS Code Tooltip
  When I hover over the `fs` method `readFile`, the VSC tooltip shows all sorts of info. Like that path is either a string or a number or a buffer. How does it get that info?

  ![](log_imgs/info_9-4.PNG)

  Nothing in the function specifies the datatype of the path or the other information for the callback.

  ```javascript
  function readFile(path, options, callback) {
    callback = maybeCallback(callback || options);
    options = getOptions(options, { flag: 'r' });
    if (!ReadFileContext)
      ReadFileContext = require('internal/fs/read_file_context');
    const context = new ReadFileContext(callback, options.encoding);
    context.isUserFd = isFd(path); // File descriptor ownership

    const req = new FSReqCallback();
    req.context = context;
    req.oncomplete = readFileAfterOpen;

    if (context.isUserFd) {
      process.nextTick(function tick() {
        req.oncomplete(null, path);
      });
      return;
    }

    path = getValidatedPath(path);
    binding.open(pathModule.toNamespacedPath(path),
                 stringToFlags(options.flag || 'r'),
                 0o666,
                 req);
  }
  ```

  When I hover over my functions I don't get all that information.

  <img src="log_imgs/type_9-3.PNG" width=500>

  I thought you could only do type hinting with typescript, but I don't see anything to indicate this is typescript. So where is this hinting coming from? How did the authors of the `fs` module do this?

  ## Create Posts
  `action_posts_create` is done.
  
  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/8536d39c1f2e527328e774410fa5a48adcc93b3f)

  ## Where I Left Off
  I finished the Create part of CRUD. Next, Read?
