
## Day 91, R3
### 10/18/19

- ## Node
  ### Where I Left Off
  Yesterday, I played with service workers in the browser and played the Service Workies Game. I'm on level 4 chapter 3.


  ## `caches.addAll`

  If one resources fails when using caches.addAll, they all fail().

  ## .html


  ## Solving An Issue
  *I want to walk through an issue I solved to try to better clarify how problems are fixed.*

  One of the hardest parts of solving a problem is that you often don't know the actual problem.

  All you know is: *Something isn't acting as expected.* You have ***unexpected behavior***, but you don't know the problem.

  Then you must clarify the issue.

  If you ask yourself, google, or a friend about the unexpected behavior, you will get a different answer than if you find the problem and then ask the question about the problem.

  So it's important to recognize if you can vocalize the problem, or if you can only vocalize the unexpected behavior.

  ### Example 
  **Unexpected Behavior:** I was trying to cache a file called `offline.html.` 

  ```javascript
  self.addEventListener('install', function(event) {
    event.waitUntil(
      caches.open("cacheName").then(function(cache) {
        return cache.addAll(
          [
            '/offline.html'
          ]
        );
      })
    );
  });
  ```
  When I went offline and tried to retrieve it, the cache disappeared. I got this error on the page:

  >The webpage at http://localhost:5000/offline.html might be temporarily down or it may have moved permanently to a new web address.
  >
  >ERR_FAILED

  **Finding the Problem:** The above is the unexpected behavior, it's not the problem. I thought the problem was that I couldn't cache that page. The problem had nothing to do with caching. 
  
  After experimenting, I was able to recreate this error without caching. Whenever I went to offline.html while online, I'd get the same error. 

  But, when I deleted the service worker, then /offline.html redirected to /offline. The page was served.

  So I tried it again with service workers. But I deleted different parts of the code in the service worker.

  I pin pointed the problem. The problem only occured when I had my fetch code in the service worker:

  ```javascript
  self.addEventListener('fetch', function(event) {
    console.log('fetch: ', event.request.url);
    event.respondWith(
      caches.match(event.request).then(function(response) {
        return response || fetch(event.request);
      })
    );
  });
  ```

  **Further Pin Pointing The Problem:**
  I haven't actually solved my problem. So maybe we can only be sure we found the problem once we solved it. So I've simple come across a more specific unexpected behavior. I've clarified a more specific unexpected behavior.

  To find the real problem, we'll need to get more specific. We'll need t find more specific instances where we see the unexpected behavior, within the fetch event block perhaps.

  But because we've gotten more specific we can form a question:

  - Our fetch event tries to serve offline.html which doesn't work. But when we simply go to offline.html without fetch, it redirects to offline.html. Why? Why doesn't fetch behave the same as if we put .html in the url?

  **Clearer Problem:** I've yet again found more information, a more specifically defined problem.

  It seems fetch isn't the problem because I'm able to retrieve `offline.html` with this code:

  ```javascript
  self.addEventListener('fetch', function(event){ event.respondWith(fetch(event.request));
  });
  ```

  but not this:

  ```javascript
  self.addEventListener('fetch', function(event) {
    event.respondWith(
      caches.match(event.request).then(function(response) {
        return response || fetch(event.request);
      })
    );
  });
  ```

  So I've further pin pointed the problem to the caches.match code.

  **I Forgot, I did solve the problem:** Earlier I said maybe we can't know the problem until we solved the problem. But actually I forgot I had found a solution to the problem. Instead of caching `offline.html` cache `offline`. 
  
  That being said, I still don't know why that is. I don't know why you can't cache `offline.html`. I won't to know why.

  **Deeper Exploration:**

  caches.match(event.request) returns different responses for `offline.html` and `offline`

  ### `offline.html`:
  ```json
  body: (...)
  bodyUsed: false
  headers: Headers {}
  ok: true
  redirected: true
  status: 200
  statusText: "OK"
  type: "basic"
  url: "http://localhost:5000/offline"
  __proto__: Response
  ```
  I get this in the terminal:
  >`The FetchEvent for "http://localhost:5000/offline.html" resulted in a network error response: a redirected response was used for a request whose redirect mode is not "follow".`

  ### `offline`
  ```json
  body: (...)
  bodyUsed: true
  headers: Headers {}
  ok: true
  redirected: false
  status: 200
  statusText: "OK"
  type: "basic"
  url: "http://localhost:5000/offline"
  __proto__: Response
  ```

  I looks like the issue is that offline.html redirects. And for some reason we can't do that.

  **More info:** The above happened when both `offline.html` and `offline` were cached.

  If I only have `offline` cached I get this:

  Navigating to `offline`:
  ```
  serviceworker.js:14 fetch:  http://localhost:5000/offline
  serviceworker.js:17 response
  Navigated to http://localhost:5000/offline
  ```
  Navigating to `offline.html`:
  ```
  serviceworker.js:14 fetch:  http://localhost:5000/offline.html

  serviceworker.js:17 fetch

  serviceworker.js:14 fetch:  http://localhost:5000/offline

  serviceworker.js:17 response
  Navigated to http://localhost:5000/offline
  ```

  ## Where I Left Off
  I'm trying to understand why I'm getting unexpected behavior when fetching from the cache.