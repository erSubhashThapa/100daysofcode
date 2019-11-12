## Day 116, R3
### 11/12/19
- ## Today 
  I've been doing [Khan Academy's Algorithms](https://www.khanacademy.org/computing/computer-science/algorithms) course. But I think I want to MAKE something today to review skills.

  ## Project
  Let's make a small project that uses backend and frontend to brush up on a collection of skills.

  I looked through Florin Pop's [100 Days Of Project](https://www.florin-pop.com/blog/2019/09/100-days-100-projects/) list for inspiration.

  I thought, since I love self quantification, why not make a project that tracks my feelings.

  ## Stack
  I'm going to use express and Node.js.

  ## Error

  When serving my application, I tried to go to the server at `https://127.0.0.1:3000/` but I got this error.

  ```bash
  This site can’t provide a secure connection127.0.0.1 sent an invalid response.
  ERR_SSL_PROTOCOL_ERROR
  ```

  I also tried fetching in node with `node-fetch`:

  ```javascript
  fetch('https://127.0.0.1:3000/').then(x=>console.log(x, "pp"))
  ```
  But got this error:
  ```bash
  FetchError: request to https://127.0.0.1:3000/track_energy failed, reason: write EPROTO 4408569152:error:1408F10B:SSL routines:ssl3_get_record:wrong version number:../deps/openssl/openssl/ssl/record/ssl3_record.c:332:
  ```

  I found this [stackoverflow thread](https://stackoverflow.com/questions/20841242/node-js-https-get-via-proxy-generates-ssl3-get-record-wrong-version-number-error) which led me to a solution:

  **Solution:** I needed to change `https` to `http` when fetching or **going to*** a url. 
  
  *What's the correct term for **"going to"**? I'm drawing a blank.

  ## Where I Left Off

  This is how far I got today.

  [Link To Work](https://github.com/DashBarkHuss/mood_tracker/commit/2d9939851f7aa19db213f4751a1b9367e04ce92f)

  I might just start a whole new project tomorrow even though I didn't finish. I'm trying to just get the hang of popping a project out fast. I could even just do the same project from the beginning.
