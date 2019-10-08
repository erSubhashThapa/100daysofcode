
## Day 81, R3
### 10/8/19
- ## Node
  ### Where I Left Off
  I left off still not knowing why the post isn't going through. I'm going to look at [wridgeu](https://twitter.com/Wridgeu) and [nd9600](https://twitter.com/CaYD4D)'s suggested reading today.

  ## Debugging Service Workers Trick:
  >You can detect if a client is controlled via `navigator.serviceWorker.controller` which will be null or a service worker instance.

  -*from [The Service Worker Lifecycle](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle)*

  ## Caching Headers

  >**What is the Cache-Control Header**
  >
  >Cache-control is an H‘TTP header used to specify browser caching policies in both client requests and server responses. Policies include how a resource is cached, where it’s cached and its maximum age before expiring (i.e., time to live).

  -*from [Cache Control](https://www.imperva.com/learn/performance/cache-control/)*

  >
  ## Cache Names
  In the tutorial [The Service Worker Lifecycle](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle) I saw this:

  ```javascript
  caches.open('static-v1')
  ```
  But I didn't know where they're getting `'static-v1'`. I read about [CacheStorage.open()](https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage/open) and found out that's the cache name, but how are they getting that cache name? No where was a cache name set, so is `'static-v1'` a default cache name created by the browser?

  After playing around, I think you can just make up any cache name, because I think .open is basically setting the name, not retrieving some cache that already exists.

  I found out that this is true!
  >If the named cache does not exist it is created
  
  -*from [Using the Cache API
](https://developers.google.com/web/fundamentals/instant-and-offline/web-storage/cache-api)*

  ## Notes On [The Service Worker Lifecycle](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle)

  - ### `install`
    - The install event is the first event a service worker gets. It's triggered as soon as the worker executes, and it's only called once per service worker. 
    - The install event is your chance to cache everything you need before being able to control clients.
    - The promise you pass to event.waitUntil() lets the browser know when your install completes, and if it was successful.

  - ### By default, a page's fetches won't go through a service worker unless the page request itself went through a service worker. So you'll need to refresh the page to see the effects of the service worker.
  
  - ### Updating the service worker
    - waiting
      - After it's successfully installed, the updated service worker delays activating until the existing service worker is no longer controlling clients. This state is called "waiting", and it's how the browser ensures that only one version of your service worker is running at a time.
    - Skip the waiting phase
      - The waiting phase means you're only running one version of your site at once, but if you don't need that feature, you can make your new service worker activate sooner by calling self.skipWaiting().


