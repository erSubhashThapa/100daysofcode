## Day 62, R3
### 9/19/19

- ## Node
  ## Where I Left Off
  I played with background sync and I got it to work with a param and get request. I made a sample project. Tomorrow I'll try to get it to work with POST.

  ## localStorage Service Workers
  >You cannot access localStorage (and also sessionStorage) from a webworker process, they result will be undefined, this is for security reasons.
  >
  >You need to use postMessage() back to the Worker's originating code, and have that code store the data in localStorage.
  >
  >You should use localStorage.setItem() and localStorage.getItem() to save and get data from local storage.

  -*from [Access localStorage from service worker](https://stackoverflow.com/questions/40887635/access-localstorage-from-service-worker)*

  >You can't cache POST requests using the Cache API. See https://w3c.github.io/ServiceWorker/#cache-put (point 4).
  >
  >There's a related discussion in the spec repository: https://github.com/slightlyoff/ServiceWorker/issues/693
  >
  >An interesting solution is the one presented in the ServiceWorker Cookbook: https://serviceworke.rs/request-deferrer.html Basically, the solution serializes requests to IndexedDB.

  -*from [Can service workers cache POST requests?](https://stackoverflow.com/questions/35270702/can-service-workers-cache-post-requests/35272243#35272243)*

  ## Where I left off
  I got the service worker to post but then it seemed like it wasn't posting. 

- ## Thoughts And Feelings
  I'm feeling really fatigued. I think it's from my wisdom tooth.