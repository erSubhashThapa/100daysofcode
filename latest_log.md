
## Day 97, R3
### 10/24/19
- ## Node
  ### Where I Left Off
  I'm following along with the LinkedIn Service Workers Tutorial. I'm on this video: [Use stale-while-revalidate](https://www.linkedin.com/learning/vanilla-javascript-service-workers/use-stale-while-revalidate?autoplay=true)

  ## `Promise.all`
  >The Promise.all() method returns a single Promise that resolves when all of the promises passed as an iterable have resolved or when the iterable contains no promises. It rejects with the reason of the first promise that rejects. 

  -from [Promise.all()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

  ## `.waitUntil`
  >In service workers, waitUntil() tells the browser that work is ongoing until the promise settles, and it shouldn't terminate the service worker if it wants that work to complete.
  >
  >The install events in service workers use waitUntil() to hold the service worker in the installing phase until tasks complete. If the promise passed to waitUntil() rejects, the install is considered a failure, and the installing service worker is discarded. This is primarily used to ensure that a service worker is not considered installed until all of the core caches it depends on are successfully populated.
  >
  >The activate events in service workers use waitUntil() to buffer functional events such as fetch and push until the promise passed to waitUntil() settles. This gives the service worker time to update database schemas and delete outdated caches, so other events can rely on a completely upgraded state.

  -from [ExtendableEvent.waitUntil()](https://developer.mozilla.org/en-US/docs/Web/API/ExtendableEvent/waitUntil)

  ## Where I Left Off
  I left off on the video [Keep your storage clean](https://www.linkedin.com/learning/vanilla-javascript-service-workers/keep-your-storage-clean).