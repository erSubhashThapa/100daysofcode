## Day 56, R3
### 9/13/19

- ## Node
  ### Where I Left Off:
  I want to change the datatype for longitude and latitude to include more decimals. I need to see what happens when the user doesn't send a position.

  ## Null Location
  Now the code can handle if the location is null.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/a5e01fd4fde17884c8fb5e3dc4c397d3b5e514cc)

  ## Store RC Locally
  If not connected to the internet store the RC(reality check, contains timestamp) to local storage.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/2dd1c237cab3bc27532c73f3f515fd663ba9c31b)

  ![](log_imgs/storeLocal_9-13.PNG)

  ## Where I Left Off
  Now if the user is not connected to the internet the app collects a timestamp and saves it to local storage. Next I'll handle how it will send the timestamp from local storage to the backend.
