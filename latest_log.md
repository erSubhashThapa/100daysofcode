
## Day 93, R3
### 10/20/19

- ## Node
  ### Where I Left Off
  I'm on the second to last chapter of the game and I can't get through it. I can't get this last code right. But I can't see what I'm doing wrong.
  ![](log_imgs/mycode_10-19-19.PNG)

  ## I Quit Service Workies
  Nobody online could find a difference between the two codes. So I quit! I'm thinking this might be a bug in the game. I Tweeted at the creator, maybe others have had this problem?

  ## File Extensions On Caches
  When I cache files and try to retrieve them, if I cache with the `html` file extension I get this error when navigating to the file with the extension.

  Service Worker Code: 
  ```javascript
  self.addEventListener('install', function(event) {
    event.waitUntil(
      caches.open("cacheName").then(function(cache) {
        return cache.addAll(
          [
            '/offline.html',
            '/'
          ]
        );
      })
    );
  });

  self.addEventListener('fetch', function(event) {
    event.respondWith(
      caches.match(event.request).then(function(response) {
        return response || fetch(event.request);
      })
    );
  });
  
  ```

  Navigate to: `http://localhost:5000/offline.html`

  **Error**: `The FetchEvent for "http://localhost:5000/offline.html" resulted in a network error response: a redirected response was used for a request whose redirect mode is not "follow".`

  Change `/offline.html`, to `offline` to make this work:
  ```javascript
  self.addEventListener('install', function(event) {
    event.waitUntil(
      caches.open("cacheName").then(function(cache) {
        return cache.addAll(
          [
            '/offline.html',
            '/'
          ]
        );
      })
    );
  });

  self.addEventListener('fetch', function(event) {
      event.respondWith(
        caches.match(event.request).then(function(response) {
          return response || fetch(event.request);
        })
      );
    });
    ```
    I'm not sure why though.


  ## Where I Left Off

  I went back to the Service Workers Tutorial on LinkedIn starting on this video [Implement a network-first policy](https://www.linkedin.com/learning/vanilla-javascript-service-workers/implement-a-network-first-policy)