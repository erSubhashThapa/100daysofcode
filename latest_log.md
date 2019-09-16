## Day 59, R3
### 9/16/19

- ## Node
  ### Where I Left Off
  I started making a new branch on my express app to test adding a service worker in so that I can save data while offline.

  ## Service Workers Video
  [Introduction to Service Workers](https://pusher.com/sessions/meetup/js-monthly-london/introduction-to-service-workers)

  ## LinkedIn Learning
  I found out my school finally canceled my Lynda account (now LinkedIn Learning). I got a free 6 month LinkedIn Pro membership from Ray Villalobos for completing 100 days of code. But now I'm still having trouble logging in to that. I'm realizing now how much I miss this resource! I need it back.

  ## Questions
  Is there a way to intercept `navigator.geolocation.getCurrentPosition(success, error)` with service workers? I see you can intercept `fetch` requests but what about getting a geolocation?

  If there is an `addListenerEvent` event for `fetch`, in there one for  `navigator.geolocation.getCurrentPosition()`?

  ## Override Geolocation DevTools
  This was helpful for testing: [Override Geolocation With Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/device-mode/geolocation)

  ## Rethinking My Code
  I realized that you could be offline but have access to GPS. In that case you still want to store location. So I need to add that to my code.

  ## Where I Left Off
  I'm trying to figure out the best way to deal with intercepting a post request to store the geolocation and timestamp. What if GPS isn't working but the user is online? What if the user if offline but GPS works? What if they're both not working? I will probably have to look into indexedDB tomorrow.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/249ce1faa112586e3a1c6ede9415d73074ccb589)
