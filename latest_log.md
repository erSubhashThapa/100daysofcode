
## Day 75, R3
### 10/2/19
- ## Node
  ### Where I Left Off
  I ended trying to get the rc's to store to local storage before the database updates, so that if we're offline we still get an updated timeline. I thought I did this already but I guess I didn't.

  ## Mysterious Port 3306
  Mysteriously, local host on port 3306 was serving files even though I didn't have node or nodemon running. I finally realized it's because the service workers cached the files.

  ## Timeline Updates Offline
  Now the timeline updates when we're offline and we add an RC.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/10ca8396e19e6891cf1b31fb4901a99fb664f442)

  ## Where I Left Off:
  I'm testing to see what happens if I clear the local storage and reload the page while offline. It seems like it's connecting to the server somehow when it's offline.

  [Here's my last commit](https://github.com/DashBarkHuss/express_proj/commit/e3ec838daa2545c1a64e88d38e24241523398f78)