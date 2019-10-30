

## Day 103, R3
### 10/30/19

## A Note On Insomnia
I always forget the extent that lack of sleep affects my coding. 

Last week, a bout of insomnia made me so incompetent, I questioned whether coding was for me. 

Luckily, I got my insomnia under control by:
- Temporarily sleeping alone
- Drinking warm magnesium tea before bed
- Talking with my spouse and then Googling before bed
- When in bed, I listed items. 
  - **Example**: Pick a category *(Halloween Candy*) and list items *(mary janes, bit o' honey, mounds, candy corn...)*

After I regained my sleep, I could code again! 

While most people would tell you not to google before bed, I wonder if this helped me sleep. I have an extremely active brain at night. Maybe, googling gave me an opportunity to answer some of the racing questions in my brian. But maybe it was just a coincidence.

People also recommend journaling before bed to reduce thoughts. However, sometimes I find this revs up my brain.

- ## Where I left off
  I went back to working on my express project. I need to plan what to do next.

  ## Express Project: what needs to be done?
  - Front End: UI that shows frequency of Reality Checking
  - Refactor
  - User login
  - IndexDB
  - Look into Flic PWA integration

  ## Issue
  Rc not adding to database.
  Steps:
  - Turn my wifi off 
  - click addRC() on user 1's timeline
  - Turn my wifi back on.
  
  The rc's don't sync. I expected them to sync when wifi is back on because of the service worker sync event:

  ```javascript
   self.addEventListener("sync", event => {
     if (event.tag.substring(0, 2)=="rc") {
         const info = event.tag.substring(3);
         event.waitUntil(
             fetch(`/rc`, {
               method: 'POST', 
               headers: {
                   'Content-Type': 'application/json',
               },
               body: info, 
             })
                 .then(r => r.text())
                 .then(x=>JSON.parse(x))
                 .then(x=>console.log("Added to database: ", x.time.substring(16, 24), x.coords))
             )
     }
   })

  ```

  ## Refactoring
  I think I need to refactor some functions that do too much. Some of my functions do two things like creating an object and then storing that object. This makes debugging hard.

  Here `synLocalStorage` fetched data and stores it. I think it either needs to be renamed to `syncPromiseDataOfRCsToLocalStorage` or rewritten.
  ```javascript
    function syncLocalRcs(promise){ //promise is a fetch to get rc's for a user
      return promise
      .then(x=>
          x.text()
          )
      .then(x=> 
          JSON.parse(x))
      .then(x=>{
          localStorage['rc'+x.userId] = JSON.stringify(x.results);
          return x.results;
          }
      )
      .catch(err=>console.log(err))

  }
  ```
  ### Updated Function
  I changed the name. I think this is more clear.
  ```javascript
  function saveToLocalRcs(responseJson){ //promise
    return responseJson
    .then(x=>
        x.text()
        )
    .then(x=> 
        JSON.parse(x))
    .then(x=>{
        localStorage['rc'+x.userId] = JSON.stringify(x.results);
        return x.results;
        }
    )
    .catch(err=>{
        console.log(err);
        return [];
    }
  )}
  ```
  ## Updated Function
  I realized this function should really only be saving the rc's to local storage but this was also returning them so then I could do something with them later, but that's unnecessary nd confusing. I simplified the function:
  ```javascript
  function saveToLocalRcs(responseJson){ //promise
    if(!responseJson) return[];
    localStorage['rc'+responseJson.userId] = JSON.stringify(responseJson.results);
  }
  ```

  ## Where I Left Off
  I did some refactoring on my project. I need to work on why the timeline doesn't populate when wifi is off.
