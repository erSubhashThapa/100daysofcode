
## Day 80, R3
### 10/7/19
- ## Node
  ### Where I Left Off
  I have two users on index now. I think I need to do some refactoring. I want to get the two separate user times to have different socket namespaces.

  ## Twitch
  Today, I'm trying to set up twitch and live stream. 
  
  [Twitch streaming from your PC guide: Recording your stream](https://www.cnet.com/how-to/twitch-streaming-from-your-pc-guide-recording-your-stream/)
  
  ## addRC Not Posting
  I ran into an issue where add Rc isn't posting to the database. The service worker is handling the post using sync manager. I'm really new to service workers. People on twitch gave me some ideas.

  ## Help From People On Twitch 
  >**wridgeu:** waituntil literally waits until a promise is finished and might want to get used to full reload with rmb on the refresh button while dev tools are open
  >**nd9600:** hot reloading might be good

  [nd9600](https://twitter.com/CaYD4D) suggested reading: [What is hot-reloading exactly, is it just another fancy term for live-reloading?](https://hashnode.com/post/what-is-hot-reloading-exactly-is-it-just-another-fancy-term-for-live-reloading-cirvu9avg0c8mmk53b5zxr3ga)

  [wridgeu](https://twitter.com/Wridgeu) suggested reading[The Service Worker Lifecycle](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle)

  ## Where I Left Off
  I left off still not knowing why the post isn't going through. I'm going to look at [wridgeu](https://twitter.com/Wridgeu) and [nd9600](https://twitter.com/CaYD4D)'s suggested reading tommorrow.
