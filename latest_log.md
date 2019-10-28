
## Day 101, R3
### 10/28/19

Even though I finished round 3, I'm going to continue to post on here. I'm not committing to an entire 4th round of #100DaysOfCode, but I am committed to finishing the year. 

- ### Where I Left Off:
  I left off trying to figure out what "eval and friends" means. I feel that I got side tracked yesterday, so while I brought up questions that I should look into later, I'm going to continue practicing delivering alternative content when offline with service workers

  ## new Response 
  How to use the Response constructor:
  ```javascript
  new Response(JSON.stringify({"property":"value"})).json() // returns a promise with the object as the promise value
  ```

  ## Only One `Event.respondWith`
  I was getting a lot of unexpected behavior in the service worker that was confusing me.

  I realized it was because `event.respondWith` was being called twice. I need to `return` in my conditional so the later conditional with `event.respondWith()` isn't called.

  ## Unexpected Behavior
  In my fetch handler I have this:

  ```javascript
  self.addEventListener("fetch", event => {
    const parsedURL = new URL(event.request.url);

    if (parsedURL.pathname == "/info.json" && !navigator.onLine){

        event.respondWith(fetch("/offline.json")); //if we're offline, respond with this cached file
        return;
    }
      event.respondWith(caches.match(parsedURL.pathname).then(response=>{
          if (response){
              console.log(response);
              return response;
          } else {
              return fetch(parsedURL);
          }
      }))
  })
  ```

  When I call `fetch("info.json")` I get:
  > The FetchEvent for "http://127.0.0.1:5500/info.json" resulted in a network error response: the promise was rejected.

  Even though the code is getting to conditional 
  ```javascript
  if (parsedURL.pathname == "/info.json" && !navigator.onLine)
  ```
  . Which means it should be getting to this line:
  ```javascript 
  event.respondWith(fetch("/offline.json"));
  ```
  And `offline.json` is in the cache. So why isn't it fetching?

  ## Where I Left Off
  The above is what I left off trying to figure out.