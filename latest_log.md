
# #100DaysOfCode Log - Round 3 - Dashiell Bark-Huss

## Day 120, R3
### 11/16/19
- ## Twitter Bot
  What I need to do today
  - How do I get the access token and secret from passport twitter?

  ## SOLVED
  I solved my issue. It was in the documentation for [passport-twitter](https://github.com/jaredhanson/passport-twitter) all along. Man, I spent days on this issue.

  >The strategy also requires a verify callback, which receives the **access token** and **corresponding secret** as arguments, as well as profile which contains the authenticated user's Twitter profile. 
  >
  -*from [passport-twitter readMe](https://github.com/jaredhanson/passport-twitter)*
  

  In the example in the [docs](https://github.com/jaredhanson/passport-twitter), you can see `token` and `tokenSecret` in the params.
  ```javascript
  passport.use(new TwitterStrategy({
    consumerKey: TWITTER_CONSUMER_KEY,
    consumerSecret: TWITTER_CONSUMER_SECRET,
    callbackURL: "http://127.0.0.1:3000/auth/twitter/callback"
    },
    function(token, tokenSecret, profile, cb) {
      User.findOrCreate({ twitterId: profile.id }, function (err, user) {
        return cb(err, user);
      });
    }
  ));
  ```

  I read this and saw this before. But assumed this was the the **consumer key** and **consumer secret**. I didn't realize it was what I was looking for: the **access token** and **access secret**.

  ## Youtube Tutorial
  I promised myself if I figured this out I would make a youtube tutorial on it. There's no youtube tutorial on this. So someone keep me accountable to making this!

  ## What's Left
  I still have to finish the code and then figure out how to deploy it.

  ## Finished Code
  I finished the code. Check it out:

  [Link To Commit](https://github.com/DashBarkHuss/helpmecodebot/commit/bb8eab6b62ced0bdc376bc134a8bd5165c507f74)

  I still have to deploy. Right now it's running live on my localhost. But it's up and running, atleast while I have my computer on. So feel free to use the **#helpmecode** hashtag.