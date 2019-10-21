
## Day 94, R3
### 10/21/19

- ## Node
  ### Where I Left Off
  I went back to the Service Workers Tutorial on LinkedIn starting on this video [Implement a network-first policy](https://www.linkedin.com/learning/vanilla-javascript-service-workers/implement-a-network-first-policy)

  ## Not Retrieving Cache Files While Offline
  I was trying to retrieve cached filed while offline. But it wasn't working. I thought it was because I didn't understand how caching worked. But it was much simpler. 

  Can you spot the problem?

  ```javascript
  self.addEventListener("fetch", event => {
    const parsedUrl = new URL(event.request.url);
    if (parsedUrl.pathname.match(/^\/_css*/)){
        event.respondWith(
            fetch(event.request)
                .catch(err=>{
                  return caches.match(event.request)
                })
            )
    } else {
        caches.match(event.request)
        .then( response => {
            if (response) {
                return response; // The URL is cached
            } else {
              return fetch(event.request); // Go to the network
            }
        })
      }
  });
  ```

  **The Problem:** I left out `event.respondWith`. The response was there but the service worker wasn't sending it back.

  I was able to see this better when I ***isolated the issue***. 
  
  What's isolating the issue?- When dealing with a  big project, it's hard to pin point the problem. So I often recreate the issue in a new project with as little code as possible.

  Working code:
  ```javascript
  self.addEventListener("fetch", event => {
      const parsedUrl = new URL(event.request.url);
      if (parsedUrl.pathname.match(/^\/_css*/)){
          event.respondWith(
              fetch(event.request)
                  .catch(err=>{
                      return caches.match(event.request)
                  })
              )
      } else {
          event.respondWith(
              caches.match(event.request)
          .then( response => {
              if (response) {
                  return response; // The URL is cached
              } else {
                  return fetch(event.request); // Go to the network
              }
          })
      )
      }
  });
  ```

  Sometimes the problem is more simple than you think!

  ## Where I Left Off
  I ended trying to get the service worker to retrieve the cached css when offline. Somehow, while I have `offline` checked in devtools it's still fetching and updating the css. I started to isolate the issue here to see the problem better.

