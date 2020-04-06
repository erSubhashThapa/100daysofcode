# Post #100DaysOfCode Log - Dashiell Bark-Huss

I completed my 365 days of code. But I'm going to continue to add to this log when I want to save notes.

### 04/05/20
I haven't been logging much. I'm trying to take a different approach. That being- *Don't talk about a project until it's complete.* It helps motivate me to finish the project. Also, logging slows me down. 

But I wanted to post some updates here.

## Lucid Dream Home Lab
I'm currently building a lucid dream lab the will induce lucid dreams and enable a user to communicate from a lucid dream to the outside world. I started this project in 2012. But it's been an on and off adventure.

After participating a lucid dream study at Northwestern, I was inspired to revisit the project and add some features that Northwestern had.

## Alpha Detection
Yesterday, I finished creating an alpha brain wave detector. This will be involved in detecting when a person is in REM from EEG data.

  <img src="log_imgs/alpha_4-5-20.gif" width= 100%>

I did a lot of research on brain waves and signal filtering. I won't post all of that here. The info I got was mostly on Youtube. But here is the paramount video that helped me signal process the alpha waves:

[My Weekend Project: Audio Frequency Detector Using An Arduino](https://www.youtube.com/watch?v=wbeV0J30LGQ)

The only relevent part is the section on the code. For hardware, I'm going a different route- using the [Backyard Brains Heart and Brain SpikerShield](https://backyardbrains.com/products/heartandbrainspikershieldbundle). I followed their tutorial [Experiment: EEG-Record from the Human Brain](https://backyardbrains.com/experiments/EEG). I combined this Backyard Brains tutorial with the Youtube [Audio Frequency Detector](https://www.youtube.com/watch?v=wbeV0J30LGQ) tutorial in order to programmatically detect alpha waves.

## The Code

Though the project in the Youtube video detects audio frequency, it's pretty much the same for brain waves but the sampling frequency is different. 

```arduino
#include "arduinoFFT.h"
#define SAMPLES 128
#define SAMPLING_FREQUENCY 300

arduinoFFT FFT = arduinoFFT();
unsigned int samplingPeriod;
unsigned long microSeconds;

double vReal[SAMPLES];
double vImag[SAMPLES];


void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
  samplingPeriod = round(1000000*(1.0/SAMPLING_FREQUENCY)); //PERIOD in microseconds


}

void loop() {
  for(int i=0; i<SAMPLES; i++){
    microSeconds= micros();
    
    vReal[i] = analogRead(0);
    vImag[i] = 0;

    while(micros()< (microSeconds + samplingPeriod)){
      
    }
  }

  FFT.Windowing(vReal, SAMPLES, FFT_WIN_TYP_HAMMING, FFT_FORWARD);
  FFT.Compute(vReal, vImag, SAMPLES, FFT_FORWARD);
  FFT.ComplexToMagnitude(vReal, vImag, SAMPLES);

  double peak = FFT.MajorPeak(vReal, SAMPLES, SAMPLING_FREQUENCY);
  
  if(peak<12 && peak >8){
    Serial.println("You have alpha waves of "+String(peak)+"hz. Your eyes must be closed."); 
  } else {
    Serial.println(String(peak)+"hz");
  }
}
```
Watch the tutorial to get an explanation of the code.

This project uses the library ardiunoFFT, which is a ***fast fourier transform*** library. Fourier transform is an algorithm that identifies frequencies from raw data. [Here's a great video explaining fourier transorm](https://www.youtube.com/watch?v=spUNpyF58BY).

Raw data will look like a bunch of numbers that, when mapped over time, will represent the waves. 

In my case, the electrodes glued to my head will *detect voltages from my brain*(don't quote me on this). Those numbers will look like this: 

**Example data:**
535
549
555
563
565
568
576
583
572
569
575
569
554
546
548
552
551
551
553
542 etc....

Each of these points of data occurred every 1 milliseconds. So you can map these numbers over time to get a visual idea of the waves:

![](log_imgs/graph_eeg_4-5-20)

  <img src="log_imgs/graph_eeg_4-5-20.png" width= 100%>

**Fourier transform** takes these numbers, and figures out the frequencies.

Let me know if you have any questions on Twitter [@DashBarkHuss](https://twitter.com/DashBarkHuss).

### 01/24/20
- ## Nutrition Project
  Yesterday we looked at daily values. Today I want to go through [my RDA's](https://health.gov/dietaryguidelines/2015/guidelines/appendix-7/) for my gender and age.

  Female 19-30 RDA's:

  **General:**
  - Energy: 1800 kcal
  - Water: 1500 g ---no RDA information

  **Vitamins**
  - B1 (Thiamine): 1.1 mg
  - B12 (Cobalamin): 2.4 μg
  - B2 (Riboflavin): 1.1 mg
  - B3 (Niacin): 14 mg
  - B5 (Pantothenic Acid): 10 mg ---no RDA information, cronometer put 5mg
  - B6 (Pyridoxine): 1.3 mg
  - Biotin: 300 μg ---no RDA information
  - Choline: 425 mg
  - Folate: 400 μg
  - Vitamin A: 700 mcg RAE ---cronometer put 2333 IU
  - Vitamin C: 75 mg
  - Vitamin D: 600 UI
  - Vitamin E: 15 mg
  - Vitamin K: 90 μg
  
  **Minerals**
  - Calcium: 1000 mg
  - Chromium: 120 μg ---no RDA information
  - Copper: 900 mcg
  - Iodine: 150 μg ---no RDA information
  - Iron: 18 mg
  - Magnesium: 310 mg
  - Manganese: 1.8 mg
  - Molybdenum: 75 μg ---no RDA information, cronometer put 45
  - Phosphorus: 700 mg 
  - Potassium: 4700 mg --cronometer put 2600
  - Selenium: 55 μg
  - Sodium: 2300 mg cronometer put 1500
  - Zinc: 8 mg

  **Carbohydrates**
  - Carbs: 130 g
  - Added Sugars: 10% of kcal
  - Fiber: 25.2 g

  **Lipids**
  - Fat: 20-35
  - Saturated Fat: 10% of kcal
  - Cholesterol: 300 mg  ---no RDA information

  **Protein**
  - Protein: 46 g

  ---no RDA information = number listed is cronometers DV's from yesterdays screenshots

  The macronutrients are of no importance to me. So let's disregard those.

  For my app, I'll just use what cronometer gave me for my micros.
  
  
### 01/23/20
- ## Nutrition Project
  I want to make something that has to do with nutrition density optimization. Nutrition density refers to the amount of micro nutrients per calorie.

  **Micronutrients**/**Calories**

  It's a not a specific measure, but it's used to describe foods. Organ meats are nutrient dense. Vegetables are generally more nutrient dense than fruits. Coconut oil is very low in nutrient density.

  Nutrient density isn't the "end all be all" to determining the best foods to eat, but it's a factor often over looked.

  **Macronutrients** include nutrients that provide calories: *fats*, *carbs*, and *protein*. **Micronutrients** are the vitamins and minerals.

  ## Daily Values
  I'll want to take note of the Daily Values for the USDA.

  Here are the **Daily Values** for a 2000 calorie diet according to the USDA, taken from Cronometer:

  **General:**
  - Energy: 2000 kcal
  - Water: 1500 g

  **Vitamins**
  - B1 (Thiamine): 1.5 mg
  - B12 (Cobalamin): 6 μg* 
  - B2 (Riboflavin): 1.7 mg
  - B3 (Niacin): 20 mg
  - B5 (Pantothenic Acid): 10 mg
  - B6 (Pyridoxine): 2 mg
  - Biotin: 300 μg
  - Choline: 550 mg
  - Folate: 400 μg
  - Vitamin A: 5000 IU*
  - Vitamin C: 60 mg
  - Vitamin D: 400 UI
  - Vitamin E: 20.13 mg
  - Vitamin K: 80 μg
  
  **Minerals**
  - Calcium: 1000 mg
  - Chromium: 120 μg
  - Copper: 2 mg
  - Iodine: 150 μg
  - Iron: 18 mg
  - Magnesium: 400 mg
  - Manganese: 2 mg
  - Molybdenum: 75 μg
  - Phosphorus: 1000 mg
  - Potassium: 3500 mg
  - Selenium: 70 μg
  - Sodium: 2400 mg
  - Zinc: 15 mg

  **Carbohydrates**
  - Carbs: 300 g
  - Added Sugars: 50 g
  - Fiber: 25 g

  **Lipids**
  - Fat: 65
  - Saturated Fat: 20 g
  - Cholesterol: 300 mg

  **Protein**
  - Protein: 50 g


  \* μ means micro, μg = micrograms

  \* IU means [International Unit](https://en.wikipedia.org/wiki/International_unit)

  To cross reference for accuracy, here's screenshots of Cronometer

  <img src="log_imgs/dv1_1-23-20.PNG" width= 45%>
  <img src="log_imgs/dv2_1-23-20.PNG" width= 45%>
  <img src="log_imgs/dv3_1-23-20.PNG" width= 45%>
  <img src="log_imgs/dv4_1-23-20.PNG" width= 45%>

  ## Daily Values vs Recommended Dietary Allotment

  **Daily Values** are on USDA labels. For example, we see above that the DV for **Vitamin C is 60 mg**. So if a food has 30 mg of vitamin C, you'll see *"Vitamin C 50%"* on the label.

  But Daily Values on labels are not the recommendations for everyone. The USDA has different Recommended Dietary Allowances (RDA) *"for your age, gender and life stage. These recommendations don't change based on your size."*[-Cronometer forum](https://forums.cronometer.com/discussion/1829/what-are-chronometers-daily-mirco-nutrient-targets-based-on)
  
  [More info on RDA's](https://www.ncbi.nlm.nih.gov/books/NBK114332/)

  

### 01/22/20
- ## React Native
  Two days ago I got my app onto a phone. But I noticed that it wasn't user friendly.

  The key pad that popped up was for letters. Mine should be for numbers. Adding `keyboardType="numeric"` or `keyboardType="phone-pad"` to the input tag fixed this.

  But then there was no return button. The return button is nice because it moved the cursor to the next input.

  <img width='45%' src = "log_imgs/return1_1-22-20.PNG">
  <img width='45%' src = "log_imgs/return_1-22-20.PNG">

  Another issue was that on some phones, the keyboard cuts the bottom buttons off.

### 01/13/20
- ## React Native
  My mom and sister went on weight watchers. I made a weight watchers calculator so they can figure out the points without paying for the app.
  
  I still need to style it nicely, and learn how to um *deploy*? *compile*? I don't know the correct term. But I need to put the app on their phones.

  <img width='200' src = "log_imgs/wwcalc_1-13-20.gif">

  Here's the app.js code:
  ```javascript
  /**
   * Sample React Native App
   * https://github.com/facebook/react-native
   *
   * @format
   * @flow
   */

  import React, { Component } from 'react';

  import {
    SafeAreaView,
    StyleSheet,
    TextInput,
    ScrollView,
    View,
    Text,
    StatusBar,
    Button,
  } from 'react-native';

  class App extends Component {

    constructor(){
      super()
      this.state = {
        cal: '',
        satFat:'',
        sugar:'',
        protein:'',
        points:''
      }
    }

    save(text, stateKey){
      this.state[stateKey] = text;
    }

    calculate(){
      let error=false;

      Object.keys(this.state).forEach(key=>{
          if (this.state[key]=='' && key!='points') error=true;
          console.log(error, this.state[key]);
      })
        
      if(error) return;
        const points = (this.state.cal * .0305) 
        + (this.state.satFat * .275) 
        + (this.state.sugar * .12) 
        - (this.state.protein * .098);
        
      this.setState({
            points
      })
    }
    clear(){
      this.setState({
        cal: '',
        satFat:'',
        sugar:'',
        protein:'',
        points:''
      })
    }
        
        render(){
          console.log('render', this)
          return (
            <View>
          <Text style={[styles.title]}>Weight Watchers Smart Points Calculator</Text>
          <Text style={[styles.label, styles.push]}>Calories:</Text>
          <TextInput style = {styles.input} onChangeText={(text)=>this.save(text, 'cal')}>{this.state.cal}</TextInput>
          <Text style={styles.label}>Saturated Fat:</Text>
          <TextInput style = {styles.input} onChangeText={(text)=>this.save(text, 'satFat')}>{this.state.satFat}</TextInput>
          <Text style={styles.label}>Sugar:</Text>
          <TextInput style = {styles.input} onChangeText={(text)=>this.save(text, 'sugar')}>{this.state.sugar}</TextInput>
          <Text style={styles.label}>Protein:</Text>
          <TextInput style = {styles.input} onChangeText={(text)=>this.save(text, 'protein')}>{this.state.protein}</TextInput>
          <Button style = {styles.button} onPress= {this.calculate.bind(this)} title="calc"></Button>
          <Button style = {styles.button} onPress= {this.clear.bind(this)} title="clear"></Button>
          <Text style={[styles.label, styles.push]}>Points:</Text>
          <Text style = {styles.points}>{this.state.points}</Text>
        </View>
    );
      }
  };

  const styles = StyleSheet.create({
    title:{
      marginTop:110,
      marginHorizontal: 20,
      fontSize:21,
      color: 'blue'
    },
    push:{
      marginTop:30
    },
    label:{
      color: 'red',
      borderColor: 'blue',
      marginHorizontal: 90,

    },
    input:{
      color: 'red',
      borderColor: 'blue',
      borderWidth:1,
      marginHorizontal: 90,
    },
    points:{
      color: 'red',

      marginHorizontal: 90
    },
    button:{
      marginTop:90,
      color: 'red',
      borderColor: 'blue',
      borderWidth:1
    }
  });

  export default App;
  ```
### 01/12/20
- ## Bot
  My bots been up and it's used no dyno hours. I'm not sure how this is possible. It might be becaus eI have it up as a worker now. But I thought I had it up that way before and the hours were still going down.
  
### 01/11/20
- ## Shell Scripting
  Yesterday, I wanted to get a boolean.

  I tried 
  ```bash
  echo [ u == u ]
  >> [ u == u ]
  ```

  It just returned the statement back to me. What's going on?

### 01/09/20
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

  
### 01/08/20
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

### 01/07/20

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



### 01/04/20

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


### 01/03/20

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