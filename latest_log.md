
## Day 63, R3
### 9/20/19

- ## Node
  ### Where I left off
  I got the service worker to post but then it seemed like it wasn't posting. 

  ## Background Sync Post
  I got background sync to post and insert into the database.

  [Link To Work](https://github.com/DashBarkHuss/service_worker_background_sync/commit/62aebdd16328de00cfd21be40f669d463345ce9d)

  ## Background Sync Issue
  Background sync is skipping fetch calls when the request bodies are exactly the same. This isn't an issue for my application, but I wonder why it works like this.

  Maybe it's because if the request bodies of two different requests are the same, in my app they also both register with the same name. 
  ```javascript
  registration.sync.register(`post-${value}`);
  ```
  ## Where I Left Off
  I'm trying to get the right timestamps to post but something looks off.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/b7de365777a661c299a3896a1c7c65541403c63f)
