
## Day 30, R3
### 9/27/19
- ## Node
  ## Where I Left Off
    I'm trying to understand the bodyparse module and why I didn't need it before. I'm working on making a sample app that uses socket IO in the browser.

  ## Why
  In the video [Create a post message service](https://www.linkedin.com/learning/learning-node-js-2/create-a-post-messages-service), the instructor says that express has no built in support to parse a body. He says you need to use the bodyparser module. But I was able to use express without bodyparser before.

  I realized what I did different. I was using the fetch API to post. The instructor is using jquery.post(). But why does one work without the body parser and one doesn't?

  ### Content-Type
  When you make a jquesry.post() request the content type defaults to  `'content-type': 'application/x-www-form-urlencoded; charset=UTF-8'`. In a fetch call you can specify the type. 

  ```javascript
  fetch('http://localhost:3000/messages',{
        method: 'POST', 
        body: JSON.stringify(message),
        headers: {
            "Content-Type": "application/json"
        }
  })
  ```

  So I wonder why the instructor said it has no build in support to parse the body. I guess he meant to parse the body when it's not set to `"Content-Type": "application/json"`. Maybe if it's already set to json, it's not considered parsing. Either way, that info is out of date. Express now includes body parser:

  ```javascript
  // Latest(4.16.0), Built in way:
  const express = require('express');
  const app = express();
  app.use(express.urlencoded({extended: true}));

  //Older, Seperate module way:
  const express = require('express');
  const bodyParser = require('body-parser'); 
  const app = express();
  app.use(bodyParser.urlencoded({extended: true}));
  ```
  -*from [Express now includes body-parser middleware by default](https://www.reddit.com/r/javascript/comments/78jjna/express_now_includes_bodyparser_middleware_by/)*

  ## Bootstrap
  I read a little bit about [bootstrap](https://getbootstrap.com/docs/4.3/getting-started/introduction/), a framework for building responsive, mobile-first sites.

  ## Where I Left Off
  I started experimenting with bootstrap in my socket IO sample browser chat.