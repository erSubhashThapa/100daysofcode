# Post #100DaysOfCode Log - Dashiell Bark-Huss

I completed my 365 days of code. But I'm going to continue to add to this log when I want to save notes.

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
  From the Docs for [react-native-linear-gradient](https://www.npmjs.com/package/react-native-linear-gradient):

  >Add it to your project
  >First, install it with npm install react-native-linear-gradient --save
  >
  >Then you can try to link the project automatically:
  >
  >$ react-native link react-native-linear-gradient

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