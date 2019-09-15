## Day 58, R3
### 9/15/19

- ## Node
  ## Where I Left Off
  I learned about service workers so I could use them in my app. I still have to handle sending the local storage to my database.

  ## IndexedDB vs localStorage
  I'm not sure what this is talking about, because I got localStorage to work. But maybe that's because it's in a file that the service worker stored and not in the service worker file:
  >We’re using IndexedDB to do this because the localStorage API, while simpler, doesn’t work in a Service Worker.

  [Send messages when you’re back online with Service Workers and Background Sync](twilio.com/blog/2017/02/send-messages-when-youre-back-online-with-service-workers-and-background-sync.html)

  ## Issues Updating Service Workers 
  If you update your service worker it's hard to delete it from registration. I finally got it to delete. It required an extra refresh.

  [How to Uninstall, Unregister or Remove a Service Worker [With Example Code]](https://love2dev.com/blog/how-to-uninstall-a-service-worker/)

  ## Service Worker Send Local Storage
  I added more to my service worker app. It now saves to local storage and then has placeholder code for when the app is back online so the app can send the local storage to the database.

  [Link To Work](https://github.com/DashBarkHuss/service_worker)

  ## More Resources
  [Offline POSTs with Progressive Web Apps](https://medium.com/web-on-the-edge/offline-posts-with-progressive-web-apps-fc2dc4ad895)

  ## Where I Left Off
  I started making a new branch on my express app to test adding a service worker in so that I can save data while offline.

 - ## Thoughts and Feelings
    I'm so tired. My tooth ache has been keeping me up at night. Well, last night it was a combination of my tooth ache and my racing thoughts. It was difficult to work today and so excuse my log.