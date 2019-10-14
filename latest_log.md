
## Day 86, R3
### 10/14/19

- ## Node
  ### Where I Left Off
  I'm exploring service workers in depth in the browser but the behavior is so funny to me.

  ## Service Workers Funny Behavior
  I'm finding so much strange behavior when working with service workers.

  ### skip waiting
  Sometimes skip waiting doesn't work. Why woud this be?

  ![](log_imgs/skipWaiting_10-14-19.PNG)

  It seems to be doing this when local host is pending but I don't know why localhost is pending for so long.

  It happened another time when local host wasn't pending.

  It seems to happen whenever there is a grey highlight behind "skipWaiting". No it also happened when it wasn't grey but local host was pending.

  ### fetch handler not called
  The fetch handle wasn't getting called even though I had this in the service worker:
  
  ```javascript
  self.addEventListener('fetch', (e)=>{
    console.log("fetch event: ", e.request.url);
  })
  ```
  I figure this problem out. This happened when the service worker was installed by not the controller for the page. I have to refresh the page for it to be the controller.

  Check if the service worker is controlling the page:
  ```javascript
  navigator.serviceWorker.controller
  ```

  ### Not caching index.html
  When you save your precache list it has to be the url, not the file name. For example, if you navigate to "http://localhost:5000/" but you cached index.html, that wont work. You have to cache "/". But then what happens when we go to the url index.html?

  hmmm I get an error:

  >`The FetchEvent for "http://localhost:5000/index.html" resulted in a network error response: a redirected response was used for a request whose redirect mode is not "follow".`

  Info on this error: [Only in Chrome (Service Worker): '… a redirected response was used for a request whose redirect mode is not “follow” '](https://stackoverflow.com/questions/45434470/only-in-chrome-service-worker-a-redirected-response-was-used-for-a-reque)

  I don't understand the answer. And I'm confused because this is my code is straight off the docs: [Caching Files with Service Worker](https://developers.google.com/web/ilt/pwa/caching-files-with-service-worker)

  ```javascript
  const precacheList = ["styles.css",'/index.html', '/', "/dashie.html"]

  self.addEventListener('install', function(event) {
    event.waitUntil(
      caches.open("cach1").then(function(cache) {
        return cache.addAll(
          [
            '/',
            '/styles.css',
            '/index.html',
            "/dashie.html"
          ]
        );
      })
    );
  });
  self.addEventListener('fetch', function(event) {
    console.log('fetch: ', event.request.url);
    event.respondWith(
      caches.match(event.request).then(function(response) {
        return response || fetch(event.request);
      })
    );
  });
  ```

  ## Where I Left Off
  I'm trying to figure out why I'm getting this error.