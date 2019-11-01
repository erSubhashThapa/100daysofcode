
## Day 104, R3
### 10/31/19
- ## Where I left off
  I did some refactoring on my project. I need to work on why the timeline doesn't populate when wifi is off.

  ## Background Sync Working Again
  I got background sync working but I'm not actually sure what I changed. That's why I should commit before I change something. I'll commit now! Oh wait I have a problem still so I'm trying to fix that first.

  ## Fixed Timeline Bug

  I was trying to get the first and last reality check of the day. I had this code:


  ```Javascript
  const firstRC = (()=>{
    return times.reduce((minimum, time) => time < minimum ? time : minimum, times[0]);
  })();

  const timespan = times[times.length-1]-firstRC;
  ```
  This code assumes the last reality check in the database chronologically last order. But that's not always true. I can have a reality check from 5pm first in the database and then one from 4:59pm after it. So I changed the code:

  ```Javascript
  const firstRC = (()=>{
    return times.reduce((minimum, time) => time < minimum ? time : minimum, times[0]);
  })();
  const lastRC = (()=>{
      return times.reduce((maximum, time) => time > maximum ? time : maximum, times[0])
  })();
  const timespan = lastRC-firstRC;
  ```
  This is easier to read too.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/d67a3b8f227ae569638c9e27e0d498de25616b52)

  ## Where I Left Off
  `addRc()` doesn't add an RC when the local storage is cleared. I have to fix this.
