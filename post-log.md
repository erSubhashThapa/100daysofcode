# Post #100DaysOfCode Log - Dashiell Bark-Huss

I completed my 365 days of code. But I'm going to continue to add to this log when I want to save notes.


  
### 1/9/20
- ## Shell Scripting

  To set an env variable in the terminal:
  ```bash
  export var=value
  echo $var 
  >> value
  ```
  -*from [UNIX: Set Environment Variable](https://www.cyberciti.biz/faq/set-environment-variable-unix/)*

  Get A Substring:
  ```bash
  STRING="this is a string"
  POS=1
  LEN=3
  echo ${STRING:$POS:$LEN}   # his
  ```
  -*from [Basic String Operations](https://www.learnshell.org/en/Basic_String_Operations)*

  
### 1/8/20
I'm on Siesta Key on Vacation, so I've been taking a break from my regular coding, and learning some shell scripting! Let's learn some more!

- ## Shell Scripting
  
  [Heroku CLI Commands](https://devcenter.heroku.com/articles/heroku-cli-commands)

  I'm got these commands from [CLI commands for dyno management](https://devcenter.heroku.com/articles/dynos#cli-commands-for-dyno-management):

  ```bash
  //turn on a dyno
  heroku ps:scale worker=1 -a helpmecodebot

  //stop a dyno
  heroku ps:stop worker.1 -a helpmecodebot

  //see if your dyno is on
  heroku ps -a helpmecodebot
  ```

  I want to make a script that turns the dyno on and off depending on if computer is on or not.

### 1/7/20

- ## Shell Scripting
  ## 1st Tutorial
  I wanted to write a bash script in unix so I followed this tutorial: [How to make a simple bash script (Mac)](https://www.hastac.org/blogs/joe-cutajar/2015/04/21/how-make-simple-bash-script-mac)

  ## Terms
  I googled the difference between the terms: *terminal*, *bash*, *command line*, *console*, and *shell*. I use these terms interchangeably, which is probably incorrect.
  ## 2nd Tutorial
  Next, I looked at this   tutorial: [Quick guide to writing a bash script on the Mac/Linux command-line](http://omgenomics.com/writing-bash-script/). This one showed how to add variables to your script. The shebang line didn't work for me. I changed it to the shebang in the other tutorial above. 
  
  This second tutorial left out steps.  Like that you have to exit out of nano or add the variable in to the script. So, if you're new to command line, this second tutorial might be confusing.

  ## Open A File in VSC From Terminal

  First, make sure you set up VSC to work with the coomand line:
  >Correct way is to open Visual Studio Code and press `Ctrl+Shift+P` then type `install shell command`. At some point you should see an option come up that lets you install shell command, click it. Then open a new terminal window and type `code`.

  -*From [How To Open Visual Studio Code Using Terminal](https://askubuntu.com/questions/852076/how-to-open-visual-studio-code-using-terminal)*

  Then type in Terminal: 
  ```bash
  code myscript
  ```

  ## You Are Dreaming Script
  In my [lucid dream club meetups](https://www.meetup.com/Active-Dreaming-Group/), I like to make my computer tallk to people after I leave the room and make it tell them they are dreaming. I was doing this manually in the command line. Now, I wrote a script that I can use.

  ```bash
  #!/bin/bash

  FIRSTNAME=${1?Error:no first name given}
  LASTNAME=${2?Error:no last name given}

  sleep 17; say "Hello?"; 
  sleep 6; say "Hello"; 
  sleep 2; say "Hello, $FIRSTNAME."; 
  sleep 2; say "I have a message for you."; 
  sleep 1; say "Yes, You. $FIRSTNAME $LASTNAME"; 
  sleep 1; say "The message is this: You are dreaming, $FIRSTNAME. WAKE UP!"
  ```
  
  To call the function, you run this is the command line from the directory the script is in:

  ```bash
  code Shlomo Karbal
  ```



### 1/4/20

- ## React Native
  I'm trying to figure out how to change the black underlay to another color. 

  <img width=600 src="log_imgs/rnopac_1-4-20.GIF">

  Link to sample code: [Link](https://facebook.github.io/react-native/docs/touchablehighlight#onhideunderlay)

  [@adescode](https://twitter.com/adescode) on twitter helped me. Together we found this to be the answer:

  ```html
  <TouchableHighlight
          underlayColor='blue'>
  ```
  Add `underlayColor='<somecolor>'` to the `TouchableHighlight` tag.


### 1/3/20

- ## React Native
  I followed the instructions under the "***React Native CLI Quickstart***" tab on the page [Getting Started](https://facebook.github.io/react-native/docs/getting-started). This way, I can use modules that have native code. You can't with Expo.

  ## Linear Gradient
  Now I followed the instructions from the docs for [react-native-linear-gradient](https://www.npmjs.com/package/react-native-linear-gradient):

  >Add it to your project
  >
  >First, install it with `npm install react-native-linear-gradient --save`
  >
  >Then you can try to link the project automatically:
  >
  >`$ react-native link react-native-linear-gradient`

  I had to add `npx` to the second command: `npx react-native link react-native-linear-gradient` 

  This still gave me an error: something about `BVLinearGradient`. So I had to cd into `ios` and run `pod install`. That got rid of the error.

  <img width="200" src="log_imgs/gradient_1-3-20.PNG">

  Added to my project:

  <img width="200" src="log_imgs/app_1-3-20.PNG">


### 1/2/20

- ## React Native
  I'm having trouble. When I run `npm run ios` I got this:

  ```
  Invariant Violation: `<appName>` has not been registered. This can happen if: * Metro (the local dev server) is run from the wrong folder. Check if Metro is running, strop and restart it in the current project. A module failed to load due to an error and 'AppRegistry.registerComponent' wasn't called.
  ```

  I found that I had a terminal running so I closed it and tried again.

  But then I go this:

  ```
  No bundle URL present.
  
  Make sure you're running a packager server or have included a .jsbundle file in your application bundle.
  ```
  From [No Bundle URL Present](https://forums.raywenderlich.com/t/no-bundle-url-present/63018/9):

  >Before the step you’re asking about, you should have this code in the file:
  >
  >export default class App extends >`Component<{}> { 
     // A bunch of stuff
  }`
  >
  >Change the first line, so essentially you have:
  >
  >`class SearchPage extends Component<{}> {
  >  // A bunch of stuff
  >}`

  So I changed 
  ```javascript
  export default class App extends Component 
  ```
  To
  ```javascript
  class SearchPage extends Component
  ```
  Which gave me another error but then when I changed it back it somehow worked now. I don't know how that happened.

  ## Linking
  From the docs for [react-native-linear-gradient](https://www.npmjs.com/package/react-native-linear-gradient):

  >Add it to your project
  >
  >First, install it with `npm install react-native-linear-gradient --save`
  >
  >Then you can try to link the project automatically:
  >
  >`$ react-native link react-native-linear-gradient`

  This doesn't work for me. I get:
  ```bash
  bash: react-native: command not found
  ```

  Is this because I'm using Expo and I never installed the React Native CLI?

  How can you link with Expo?

  >You can't. It states this very clearly in [the docs](https://docs.expo.io/versions/latest/introduction/faq#what-is-the-difference-between-expo-and):
  >
  >>But no native modules…
  >>
  >>The most limiting thing about Expo is that you can’t add in your own native modules without detaching and using ExpoKit. Continue reading the next question for a full explanation.
  >
  >If you want to use anything that requires `react-native link`, then you need to [detach](https://docs.expo.io/versions/latest/expokit/detach) your project and then develop it [with or without ExpoKit](https://docs.expo.io/versions/latest/guides/expokit.html). You will lose certain features and integrations (off the top of my head, I think Push Notifications via Expo is one of them) when doing so, but that is the trade-off Expo provides as an all-in-one package. When detaching, you lose those features.
  
  *-from [react native link using expo?](https://stackoverflow.com/questions/44977693/react-native-link-using-expo)*

  So I guess I have to look into that!