## Day 30, R3
### 8/18/19

- ## Node
  I'm making a vanilla Node.js app with CRUD and sessions.

  Yesterday, I wanted to figure out how to handle the data from two separate promises and put them together. I thought I didn't figure it out. But it works now. So maybe I hadn't refreshed it.

  ## Returning Two Promises

  ```javascript
  function prom1(){
    return new Promise ((res, rej)=> {
      setTimeout(
        ()=>res("first value"), 1000
      )
    })
  }

  function prom2(){
    return new Promise ((res, rej)=> {
      setTimeout(
        ()=>res("second value"), 1000
      )
    })
  }

  prom1().then(content1=>{
    return prom2().then(content2=> { return {firstVal: content1, secondVal: content2}});
  })
  .then(c=>console.log("c:",c))
  //> c: {firstVal: "first value", secondVal: "second value"}
  ```

  ## Email Error
  I kept getting an error when trying to send an email using the `Nodemailer` module:

  ```bash
  Error: Missing credentials for "PLAIN"
  ```

  This was because in `createTransport` I had
  
   `password: process.env.GMAILPW` 
   
   instead of 
   
   `pass: process.env.GMAILPW`. 
   
   Here it's fixed:

  ```javascript
  const transporter = nodemailer.createTransport({
    service: 'gmail',
    auth: {
        user: process.env.GMAIL,
        pass: process.env.GMAILPW
    }
  })
  ```
## Git Issues
I'm wondering how people track issues that need to be addressed in their projects. I though you could track issues with git because I see issues posted on github repos.

I looks like [git isn't meant to track issues](https://stackoverflow.com/questions/7060973/keeping-track-of-to-do-and-issues-in-git) but you can use github to track issues: [About issues](https://help.github.com/en/articles/about-issues).

But maybe I just need to make a to do list.

## Where I Left Off
My register endpoint registers and sends a verification email. I left off working on the verification URL. That's where I'll continue tomorrow. My code is getting combersome. I need to refactor it.

[Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commit/581f4ee3c022ca354aa4f8e023f65310fb2050bb)

