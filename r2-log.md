# #100DaysOfCode Log - Round 2 - Dashiell Bark-Huss

## Day 4, R2 --edting
### 4/14/19

- ## Recipe Calculator

  I have 


[Matrices to solve a system of equations](https://www.youtube.com/watch?v=AUqeb9Z3y3k&fbclid=IwAR2SaAZPtdZZmbSFi8QWkIne989Z_-kPWa8H4tG0un9tDDkoG9Z18Wdb5NI)

https://simbi.com/dashiell-bark-huss/math-help

https://www.mathpapa.com/calc.html?q=x+y%3D7%2C%20x+2y%3D11 not working firr 3 variables

https://www.symbolab.com/solver/system-of-equations-calculator/1x%2B3y%20%2B2z%3D10%2C%203x%2B3y%2B1z%3D15%2C%202x%2B4y%2B1z%3D13 not working for more than 2 variables

https://www.emathhelp.net/calculators/algebra-2/system-of-equations-solver/?s=25b%2B3a%2B0g%3D28%2C+0b%2B10a%2B0g%3D10%2C+15b%2B1a%2B100g%3D116&v= worked for 3 variables, DOesn't  shows steps!!

[Solves for 3 variables and shows steps](https://www.emathhelp.net/calculators/algebra-2/system-of-linear-equations-calculator/)

25b+3a+0g=28, 0b+10a+0g=10, 15b+1a+100g=116 all amounts should equal 1


[Solution using emathhelp](https://www.emathhelp.net/calculators/algebra-2/system-of-equations-solver/?s=25b%2B3a%2B1g%3D20%2C+1b%2B10a%2B2g%3D7%2C+15b%2B1a%2B100g%3D20&v=)
[Solution using emathhelp with steps](https://www.emathhelp.net/calculators/algebra-2/system-of-linear-equations-calculator/?s=3a%2B25b%2B1g%3D20%2C++10a%2Bb%2B2g%3D7%2C++1a%2B15b%2B100g%3D20&v=&method=j&steps=on)
Per 100 grams:

- Apple : { protein: 3, carbs: 10, fat: 1 }
- Beef: { protein: 25, carbs: 0, fat: 15 } 
- Ghee: { protein: 1, carbs: 1g, fat: 100 }

3a+25b+1g=20

10a+b+2g=7

1a+15b+100g=20  

Solve for ***a, b, g***

Answer: a=7151171≈**0.610589239965841**, b=8471171≈**0.72331340734415**,  g=1001171≈**0.085397096498719**
- 61g of apple
- 72g of beef 
- 8.5 grams of ghee



What if there are no answers? What if the answers are negative? How do we find the next best answer? What if the answer is too small? Probably round??



## Day 3, R2
### 4/13/19

I went to a meetup today that had a lot of coders. This guy Joe was talking me up the wazoo so I didn't get a lot done. His favorite saying was "Too make a short story long". But he was cool and gave me some good advice. 
  
Joe told me to reexamine how deeply I want to go into a subject as opposed to using a framework. I have been doing a lot of vanilla JavaScript. Maybe it's time to try react soon?
  
For more on this conundrum Joe recommended listening to this podcast:
 - [Episode #205: Beginners and Experts Panel](https://talkpython.fm/episodes/show/205/beginners-and-experts-panel)
 
His general advice for picking a tech podcast to listen too was to find some old dude who's been around the block but isn't yet bitter. I think that's good advice.

He also said to start working with a linter because it makes it easy for others to read your code. Uniformity.
  
  
- ## Recipe Calculator

  I basically am thinking through the problem from yesterday both on code and on paper. I think I'm closer. But I am so far from an answer. I'm gonna leave my log short today because I've just done a ton of brain storming and working through this problem. So not much concrete to post about. And because I was delayed from all the meetup shmoozing. See you tomorrow.
  

## Day 2, R2
### 4/12/19

- ## Recipe Calculator

  ## How To Find The Right Combination of Ingredients?
  
  I'm trying to figure out how to find how much of each ingredient I need given a certain amount of nutrient-totals the user wants to reach. 
  
  I thought the answer would be complicated and I would need to find some complex algorithm. But my very helpful twitter peer [Khawar Jatoi](https://twitter.com/khawar_jatoi) said that an algorithm isn't necesary. He said, think about iterations and things you already know. I decided to give it a shot. Heads up, I didn't get the answer yet and I'm probably doing a bunch of things worng but this is my exploration into the problem. 
  
  ## Experimenting On Paper
  I started by trying to figure out the answer on paper using my brain. This way I would get an idea of what the code needs to do.
  
  Using my example from yesterday: 
  
  ```javascript
   {
      object1: { blue: 3, red: 20, yellow: 0 }
      object2: { blue: 0, red: 2,  yellow: 12 }
      object3: { blue: 20 red: 4,  yellow: 6 }

   }

   // How much of each object to total as close as possible to: blue: 70 red: 40, yellow: 15?
   ```
 
  I went through each object: How much of object1 would I need to total to blue:70? Blue for object 1 is 3 so 70/3 is 23.33. What would that do to the rest of our numbers: Multiply them by 23.33. Well, red would be too high, yellow would sill be zero.
 
  I thought through this for a while. It started to clarify some things to me. I decided to make a program to help me play around with this idea. 
 
    
  ## Experiementing In Code
 
  I took this problem to code, inorder to play around with it faster.
 
  ```javascript
   var array=[

      {fat:1, protein:2, carbs:4},
      {fat:4, protein:2, carbs:1},
      {fat:1, protein:4, carbs:2}

    ]
    
    const a = array[0];
    const b = array[1];
    const c = array[2];
    
    //__________________some made up desied totals the user might want
    var tFat = 15;
    var tProtein = 10;
    var tCarbs = 7;

  ```
  I made this array with objects representing foods with different amounts of nutrients. Then I made functions to help figure out what I was doing on paper, but faster in code. I'm not going to post the entire code because I left off with a bug and and some messiness. I will post it tomorrow. 
  
  You can see here how I could use my functions to tell me what all of our total nutrients would be if we used only one ingredient to reach an exact amount of our desired fat, or carbs, or protein:
  
   <img src="log_imgs/ndb_4-12.PNG"  width="350"/>
  
  Q is the [quotient](http://www.amathsdictionaryforkids.com/qr/d/division.html) (How much we need of the ingredient)
  
  F, P, C are fat protein and carbs.
  
  The parenthesis show how much under or over the macro totals would be from our desired totals.
  
  This helped me see how, if we were going to only use one ingredient (an over simplified answer to my problem), the best answer would probably be the one where the absolute values of the numbers in the parenthesis add up to the lowest amount.
  
  Still a lot to do.
  
  ## CSS In Console
  
  I used this article to try to get [CSS in my logs](https://hackernoon.com/styling-logs-in-browser-console-2ec0807dc91a). I didn't finish.

  ## Can you Spot the problem?
  
  I spent a while on this issue. Whenever I called `overOrUnder`, I got `undefined`. I spent way too long on this problem.

  Can you spot the issue?
  ```javascript
  const over = 'background-color: red';
  const under = 'background-color: yellow';
  const exact = 'background-color: green';
  
  const overOrUnder= (x)=>{
    if(x=0)return exact;
    if(x>0)return over;
    if(x<0)return under;
  }
  ```
  
  ## Answer
  
  I used the equals assignment operator `=` instead of the equals relational operator `==`.

## Day 1, R2
### 4/11/19

## Starting Round 2
Round 2 let's go!

- ## Recipe Calculator
  
  ## `.find()`
  
  I used `find()` to get the object in an array that matches a nutrient id. ex: 
  
  ```javascript
  nutrientRecipeArray[0].nutrients.find(x=>x.nutrient_id=="208")
  ```
  
  This is where I look for array methods and where I found `find()`: [JavaScript Array Reference](https://www.w3schools.com/jsref/jsref_obj_array.asp)

  ## Added A bunch of Functions
  
  I added a bunch of functions:
  - `nutrientValue(food, nutrient)`
    - returns a nutrient value for a specified food object. 
    - ex: `nutrientValue(nutrientRecipeArray[0], "fiber")`
  - `calories(food)`
    - short cut for `nutrientValue(food, "calories")`
  - `netCarbs(food)`
    - finds the net carbs from `nutrientValue(food, "carbs")` & `nutrientValue(food, "fiber")`
  - `fat(food)`
    - short cut for `nutrientValue(food, "fat")`
  - `protein(food)`
    - short cut for `nutrientValue(food, "protein")`
  - `nutrientRatio(food, nutrient, perNutrient)`
    - gets the ratio of a two nutrients for a specified food object. 
    - ex: `nutrientRation(nutrientRecipeArray[0], "protein", "calories")`
  - `sortDescending(array, nutrient, perNutrient)`
    - Sorts the food objects of an array by nutrient ratio. 
    - ex: `sortDescending(nutrientRecipeArray, "netCarbs", "calories")`
    
 ## Thinking Through Functions
 
 I really thought through how to seperate the functions so that they could be reused by other function. I think I did a good job. A lot of my functions use other functions that I made. This makes it easier to change add other related functions later and cleaner to see.
 
 ## Do I need An Algorithm?
 
 I feel like this next part is complex. But I feel like there might be an algorithm to solve it. I haven't really learned about algorithms.
 
 I'm trying to get the amounts needed of a list of ingredients that would total to specified nutrients or close to specified nutrients.
 
 I'm not sure what to search to even begin.
 
 ### Using another example: 
 If I have a collection of objects, each with different values of colors:
 
 ```javascript
 {
    object1: { blue: 3, red: 20, yellow: 0 }
    object2: { blue: 0, red: 2,  yellow: 12 }
    object3: { blue: 20 red: 4,  yellow: 6 }
    
 }
 
 // How much of each object to total as close as possible to: blue: 70 red: 40, yellow: 15?
 ```
 
 How much do we need of each object inorder to total as close as possible to specific amounts?  **ex totals: blue: 70 red: 40, yellow: 15**
 
- ## Thoughts and Feelings:
  Can't believe I'm on round two! I got a lot done because I saved most of my log until the end, instead of logging while coding.
 
 
 
    
 
