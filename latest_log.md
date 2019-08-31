## Day 44, R3
### 9/1/19

- ## Node
I'm making a vanilla Node.js app with CRUD and sessions.

### Where I Left Off
I finished `userloggedIn`. I need to test  to make sure `action_user_login` works in instances where the user isn't logged in.

## What Happens In Production When Node Errors?
Sometimes node stops running when I'm playing with it in the terminal because it runs into an error. What happens in production? Does the whole site go down? Maybe whatever happens when you play with it in the browser and it errors happens.

I played with it in the browser but I'm realizing now that I can't find a situation where node would error and shut down outside of it not being able to compile, which would make it so I can't play with it in the browser anyways. If I find an instance where it shuts down after already compiling, I'll try that in the browser.

## Login Finished
[Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/e8c60f8dbafd7b2b9b6e7327a5b1e531d86821e0)

## Drying My Code

Look at this gorgeous transformation:

```javascript
//Before:
if(identify('user', 'verify', API.parts)){
    handleContent(action_user_verify);
}

if(identify('user', 'register', API.parts)){
    handleContent(action_user_register, [payload]);
}

if(identify('user', 'verify', API.parts)){
    handleContent(action_user_verify)
}

if(identify('user', 'login', API.parts)){
    handleContent(action_user_login, [request, payload])
}

if(identify('user', 'logout', API.parts)){
    handleContent(action_user_logout, [request, payload])
}
```
```javascript
// After:
actionFor('user', 'verify', action_user_verify);

actionFor('user', 'register', action_user_register, [payload])

actionFor('user', 'verify', action_user_verify)

actionFor('user', 'login', action_user_login, [request, payload])

actionFor('user', 'logout', action_user_logout, [request, payload])


function actionFor(api1, api2, action, paramArray=[]){
    if(identify(api1, api2, API.parts)){
        handleContent(action, paramArray);
    }
}
```
[Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/67855119e8441bdc496c344e83fc7eacaef9c364)

## Nodemon
I set up nodemon. Nodemon makes it so you don't have to keep restarting the server when you make changes.
```bash
npm install --save-dev nodemon
```
Info on [nodemon](https://www.npmjs.com/package/nodemon)

To run nodemon use `nodemon` as you would `node`. Example: `nodemon index`

## Scripts
I set up some scripts in my `package.json` file.
```javascript
//package.json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node bin/test",
    "dev": "nodemon bin/test"
}
```
To run you'd enter `npm run nameofscript`.

## Where I left off
I need to test to make sure nodemon is working properly. I need to finish the logout endpoint.
