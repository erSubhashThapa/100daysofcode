
## Day 110, R3
### 11/6/19
  ## Where I Left Off:
  I watched more of the tutorial on testing. I'm playing with testing a function with a callback.

  ## Callbacks
  In the linkedin video [Testing callbacks with Mocha](https://www.linkedin.com/learning/node-js-testing-and-code-quality/testing-callbacks-with-mocha), we test an asynchronous callback using `done()`.

  ```javascript
  it('should fail a reservation with a bad email', function(){
      const reservation = new Reservation({
        date: '2017/06/10',
        time: '06:02 AM',
        party: 4,
        name: 'Family',
        email: 'username'
      });
      reservation.validator(function(error){
          error.should
            .be.an('error')
            .and.not.be.null
          done();
    });
  });
  ```

  But I'm not sure what done does because when I take `done` out of the parameters and remove `done()`, the test still works. So what's it doing?

  I'm going to go on to the next video about using done with promises to see if I get any clarification.

  ## Debugging Node.js
  I want to debug my tests, but I'm used to only debugging the main script. I'm trying to see how to debug different scripts. This way I could understand how testing works, like what exactly is `done`? 

  I'm reviewing debugging in Node. I think debugging is so important!
  
  [Getting started with Node.js debugging in VS Code](https://www.youtube.com/watch?v=2oFKNL7vYV8)

  ## Where I Left Off
  I started to review debbuging in NOde so I can debug my test script.

  ## Job Hunt
  I thought I'd document some of my job hunt. 
  
  On Monday I went to [Built In Chicago](https://www.builtinchicago.org/)'s *Top Companies Hiring.*
  
  I thought this would be a great way to find a job in the *informal* job market. But I was wrong! It was a very formal situation. 
  
  Most companies were looking for senior devs. It was a little discouraging. One lady talked to two other devs and myself. All of us were newbies. But, for some reason she looked at the other devs and avoided eye contact with me. This stook with me. I wondered why she didn't look at me? Anyways, kind of a stupid thing to dwell on, on my end!

  Today, [Jose Munoz](https://twitter.com/jjmvrk), a cool dude I met on Twiiter, showed me around Vintro headquarters. Vintro is a really cool app where you can pitch investors and mentors on your business ventures over video messages. It's sort of like cameo for business. It's started by a young entrepreneur named Noor Sugrue, I got to meet her too. I think the business is so cool and I can't wait to use it myself! 

  Jose was very kind and generous. He offered to connect me with a founder of another company after I told him I was looking for a dev job or apprenticeship where I could shadow an entrepreneur. 
  
  I think the key to getting what you want is asking. Most people don't know what they want and wont ask if they do. Anyways, I'm going to end this here, got ot make it over to [Next Door Cafe](https://nextdoorchicago.com/) for a workshop on job hunting.