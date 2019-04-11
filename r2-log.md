# #100DaysOfCode Log - Round 2 - Dashiell Bark-Huss


## Day 1
### 4/11/19

## Starting Round 2

- ## Recipe Calculator
  
  ## `.find()`
  
  I used `find()` to get the object in an array that matches a nutrient id. ex: 
  
  ```javascript
  nutrientRecipeArray[0].nutrients.find(x=>x.nutrient_id=="208")
  ```
  
  This is where I look for array methods and wehere I found `find()`: [JavaScript Array Reference](https://www.w3schools.com/jsref/jsref_obj_array.asp)

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
    
 ## Thinking through functions
 
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
 
 
 
 
    
 
