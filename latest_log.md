
## Day 102, R3
### 10/29/19
- ## Where I left off
  I left off trying to figure out why when offline and I call `fetch("info.json")` I get:
  > The FetchEvent for "http://127.0.0.1:5500/info.json" resulted in a network error response: the promise was rejected. 

  ## What The Hell
  Now it's working. What's going on??

  ## DevTools Offline 
  I'm trying to test what the project would be like offline. So I set the devtools to `offline`.
  
  However `navigator.onLine` still gave me `true`.

  So I followed this:

  From [when throttling chrome to offline the navigator.onLine is still true](https://stackoverflow.com/questions/39828173/when-throttling-chrome-to-offline-the-navigator-online-is-still-true):

  >```javascript
  >Object.defineProperty(navigator, "onLine", {value: false})
  >```
  >If you want to restore it later, keep a reference to the old property descriptor:
  >
  >```javascript
  >var oldOnLineDescriptor = Object.getOwnPropertyDescriptor(navigator.constructor.prototype, "onLine") 
  >//...
  >Object.defineProperty(navigator, "onLine", oldOnLineDescriptor)
  >```

  This only changed the online status where I put it. So I needed it in the service worker, not the index.html. Then I was able to see how my service worker would work offline. 
  
  I think this is because there's a different navigator for the worker. When I look at the `navigator` in the console for the service worker, it's called a `WorkerNavigator`:

  <img src="log_imgs/worknav_10-29-19.PNG" width="300">

  Where as, in the regular console scope it's just a `Navigator`:

  <img src="log_imgs/nav_10-29-19.PNG" width="300">

  I don't know why the offline button in devtools doesn't set `navigator.onLine` to false.

  ## Service Worker Offline
  Now my practice project gives different data when we're offline:

  <img src="log_imgs/offline_10-29_19.PNG" width="300">

  [Link To Work](https://github.com/DashBarkHuss/service_worker_practice/commit/718e66eee27ce18c3607737c19cb6d33a60ad345)

  ## Express Proj
  I went back to my [Express project](https://github.com/DashBarkHuss/express_proj).
  
   When I last left off, I wrote this:
  >I ran into an issue where add Rc isn't posting to the database. The service worker is handling the post using sync manager. I'm really new to service workers. People on twitch gave me some ideas.

  But today I'm not able to recreate that issue.

  ## Better Documentation Of Issues
  I need to keep better documentation of issues. I find problems and then I can't recreate them. I need to know the steps to recreate the issues.

  ## Where I Left Off
  I went back to working on my express project. I need to plan what to do next.