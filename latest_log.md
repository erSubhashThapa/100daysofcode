
## Day 88, R3
### 10/15/19

- ## Node
  ### Where I Left Off
  I'm trying to figure out why I'm getting this error when I go to e go to the url index.html.

  >`The FetchEvent for "http://localhost:5000/index.html" resulted in a network error response: a redirected response was used for a request whose redirect mode is not "follow".`


  ## Service Worker Game

  I played this [Service Workies Game](https://serviceworkies.com/) recommended to me by [@RichDonnellan](https://twitter.com/RichDonnellan).

  ## Game Notes

  - The game made me wonder what is the difference between a web worker and a service worker, so I looked it up.
  
    [What can service workers do that web workers cannot?](https://stackoverflow.com/questions/38632723/what-can-service-workers-do-that-web-workers-cannot)

  - The game also made me realize that when you refresh a page that registers a service worker, if the code has changed, the new code replaces the waiting service worker now the active service worker.

  - If you refresh a page that registers a service worker, the install event only gets called once. A service worker will only enter each stage of it's life cycle once.

  - In the game, Kolohe, the young service worker warrior, terminates whenthe "Portal" is closed. I think thats a symbol for closing a tab. So I suppose a service worker terminates when a tab is closed?

  - Unlike the install event, the registration success Promise resolves every time the page loads and register is called for a valid Service Worker.

  - The `.ready` promise will resolve every time the page is refreshed so long as there is an active Service Worker.
    ```javascript
    navigator.serviceWorker.ready.then(registration => {
      console.log("SW activated: ",
      registration.active)
    })
    ```

  - The `updatefound` event fires when theres an updated service worker.

  - The `statechange` event fires when theres a state change.
    ```javascript
      navigator.serviceWorker.register("/game/kolohe.js").then((registration) => 
    {
      const kolohe = registration.installing;
      kolohe.addEventListener("statechange", (event) => {
        console.log("state changed to:", event.target.state)
      })
    })
    ```

  ## Where I left Off
  I ended on Chapter 2 Level 7 of Service Workies.

- ## Thoughts and Feelings
  Playing Service Workies helped me slow down. It takes longer to go through a "voyage" and learn about service workers than to read a doc. But slowing down help me soak in what the service worker is truly doing. This is a lesson in learning. I don't need to rely on games to teach me, but I need to be ok with slowing down when learning a new concept. Take in each small part slowly, iterating the new micro concepts until you understand them.