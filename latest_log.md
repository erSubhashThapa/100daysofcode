
## Day 100, R3
### 10/27/19

  ### Where I Left Off
  I started practicing delivering alternative content when offline with service workers.

  ## Stack: "anonymous"
  I was trying to understand the code from the [Vanilla Javascript: Service Workers](https://www.linkedin.com/learning/vanilla-javascript-service-workers/) tutorial. So I paused the code at `serviceworkers.js:88`. 
  
  ```javascript
  self.addEventListener("fetch", event => {
    console.trace();
    const parsedUrl = new URL(event.request.url);
    if (parsedUrl.host=="explorecalifornia.org" && !navigator.onLine) {
        event.respondWith(fetch("offline.json")); //line 88
    }
  ```

  I looked at the call stack to see how the code got there and I saw this:

  <img src = "log_imgs/stack_10-27-19.PNG" width = "200">

  I've seen this before, but I never really looked up what it meant. 
  
  ### Anonymous Functions
  According to [this article](https://www.linkedin.com/pulse/javascript-named-vs-anonymous-functions-chris-ng/), it looks like this means an **anonymous function** called our current function.

  **Anonymous functions** are functions without a name.

  I would think we'd get a line number or something in the stack trace, but no.

  But then, when looking into my code I ended up finding the function that called the current function (or did it?). It was named.

  So we got to the fetch listener by 
  - `fetchWeather("san diego")` 
  - and `fetchWeather` calls fetch 
  - which then triggers a fetch event

  So why does `console.trace()` show anonymous in the fetch event?

  Maybe because we're getting here by triggering an event, the function is anonymous? 

  ## Event Handler
  I  put a `console.trace()` in every event listener. They all showed "anonymous".

  If I moved the listener out into a named function, it then showed the name of the listener in the trace.

  ```javascript
  // callback in event handler

  self.addEventListener("someevent", event=>{
    console.trace() //returns anonymous
    //some code
  })

  //callback outside of handler

  function callbackName(event){
    console.trace() //returnns callbackName
    //some code
  }
  self.addEventListener("someevent", callback)

  ```

  But `console.trace()` didn't show what called the named callback.

  I couldn't find any info on this but I guess it makes sense. 

  When an event listener is triggered, it's not directly triggered by a function. It's triggered by an event. A function may have triggered the event, but the event looks like it starts a new stack.

  ## Javascript Event Loop
  I'm reading about the [Javascript Event Loop](https://flaviocopes.com/javascript-event-loop/) to try get more clarity.

  ## VM
  I added a mouseover event listener to see what the stack would be.

  ```javascript
  elem.addEventListener('mouseover', e=>console.trace(e))
  ```
  This time we have anonymous but with a weird code.
  ![](log_imgs/debug_10-27-19.PNG)

  I've seen this before and I vaguely understand what they are.

  I think it's like a virtually generated code or something or possibly something that just dev tools does. I'm not sure.

  ### What is the vm file?
  I looked it up:
  >[VM] (scriptId) has no special meaning. It's a dummy name to help us to distinguish code which are not directly tied to a file name, such as code created using eval and friends.

  -from [Chrome Development Tool: [VM] file from javascript](https://stackoverflow.com/questions/17367560/chrome-development-tool-vm-file-from-javascript)

  ## Where I Left Off:
  I left off trying to figure out what eval and friends means.
