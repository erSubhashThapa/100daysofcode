
## Day 73, R3
### 9/30/19
- ## Node
  ### Where I Left Off
  I left off working on getting an SVG timeline to render based on the times of the RC's.

  ## Storage Event
  I was trying to use the storage event to update the timeline. So when local storage updates, the timeline does too. 
  
  I tried using the storage event 
  - [Using The Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
  - [storage.onChanged](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/storage/onChanged)
  
  However:
  >The storage event is only triggered when a window other than itself makes the changes.
  
  -[storage Event](https://www.w3schools.com/jsref/event_storage_url.asp)
  
  So unless I fire the event on another page it won't work.

  ## Where I Left Off
  I got the timeline to update after a socket event updates the local storage. I also made tooltips on my timeline that show the times of each reality check. It seems a little slow so I have to reexamine what I'm doing. I think I have some extra requests that I could get away with not using.

  ![](log_imgs/timeline_9-30-19.gif)
  
  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/8799e64527ca6f5da6be87a73781fff58d2cf982)
