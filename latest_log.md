
## Day 66, R3
### 9/23/19

- ## Node
  ### Where I left off
  I want to try to build a socket.io sample app.
  
  I started creating a GET request for my express app that sends the locally stored rc information so only the new info is sent back.

  ## Local Storage Updating
  Now local storage updates on refresh. It would be cool to use webSockets to update in real time.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/19663cfe23272d00d5d35e5ed170091eef6d9665)

  ## Fetch Not Always Working
  Something is going on with fetch, it's not always working. I think I might understand this more if I learn how to debug using the network panel better.

  ## Added Time Helper
  I didn't want to add a heavy time library like moment.js so I just made a small time helper.

  ```javascript
  const epochToTime = epoch=>{
    const date = new Date(epoch); 
    const h = date.getHours(); 
    const m = date.getMinutes().toString().length == 2? date.getMinutes(): '0' + date.getMinutes();
    return h+':'+ m
  }
  ```

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/533296ff000306da0289111dc81e8067d71b9a84)

  ## Where I Left Off
  I still didn't get to play with Socket IO. 

  All the data is stored locally. Next I can either work on the UI of displaying the RC times, or I can work on the websockets side.
