## Day 60, R3
### 9/17/19

- ## Node
  ### Where I Left Off
   I'm trying to figure out the best way to deal with intercepting a post request to store the geolocation and timestamp. What if GPS isn't working but the user is online? What if the user if offline but GPS works? What if they're both not working? I will probably have to look into indexedDB tomorrow.

   ## Need To Start Node Server
   I was confused for why I couldn't connect to the data base through my UI. I finally realized I was just pressing the "Go Live" button in VSC. I need to run the node server!

   ## IndexedDB
   Read a little about indexedDB.

   [Getting Started with Persistent Offline Storage with IndexedDB](https://itnext.io/getting-started-with-persistent-offline-storage-with-indexeddb-1af66727246c)

  ## Background Sync
  > a low-level feature for running code inside registered events in the background when the user is connected to the Internet, even when the page itself is closed. In the context of offline support, you can use it to hold request until the user has their Internet connection back, to make sure that they are going to be sent. This way, you will make sure that your app is synced with a remote database and all changes a user made are there or will be sent there. 
  
  -*from [Make Your PWA Work Offline Part 2 - Dynamic Data](https://www.monterail.com/blog/pwa-offline-dynamic-data)*

  [Introducing Background Sync](https://developers.google.com/web/updates/2015/12/background-sync)

  ## 400 (Bad Request) and Fetch
  I kept getting a 400 error when trying to fetch using the POST method. It was hard to debug, I wasn't getting much info. I finally saw the problem was in the syntax of the request body. I had an extra quote symbol.

  ## Where I Left Off
  I'm playing around trying to get background sync to work.
