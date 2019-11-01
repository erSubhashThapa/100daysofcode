
## Day 105, R3
### 11/1/19
- ### Where I Left Off
  `addRc()` doesn't add an RC when the local storage is cleared. I have to fix this. Was this online or offline?

  ## Pending Local Host
  Something causes retrieving localhost to pend for a very long time.

  I thought the cause was *pausing the debugger on sync event*. But I tried that a few times. Sometimes it caused localhost to pend on reload, sometimes not.

  **I figured it out.** The service workers context can be pause in the debugger. But then when you switch to the '**top**' context it might not be paused. 
  
  Then when you try to refresh, the service worker is still paused even though it doesn't look like it. So the document can't retrieve localhost.

  ![](log_imgs/context_11-1-19.gif)
  
  ## Force Reload
  If you `shift` + reload, refresh will work even if the service worker is paused. This is called force reloading an it bypasses the service worker.

  ## Express Project
  Now the express project does add an RC when the local storage is cleared. 

  ## Where I Left Off
  It seems like everything is syncing nicely. I did some refactoring and debugging. Next could I test it on mobile and implement (Flic)[https://flic.io/flic2]? Does Flic have to be native? Can do this in a PWA? I know I can do it if I'm connected to the internet, but can I directly affect the PWA offline?

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/70999fbccea5e70270d0c1dcea293b4ce314a92b)