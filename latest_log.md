
## Day 113, R3
### 11/9/19
- ## Today 
  Today I'm going to look into some language agnostic concepts line Big O notation.

  ## Big O Notation
  **Big O Notation**: How time scales with respect to some input variables.

  **Example:**

  The Big O notation of mowing a square lawn could be: 
  - O($s^2$) where **s** is a **side** of the square lawn
  - 0($a$) where **a** is the area of the lawn
  
  Both are the same. The time to mow a lawn depends on the area of the lawn.
  
  Here's a video on [Big O Notation](https://www.youtube.com/watch?v=v4cd1O4zkGw)

  Big O Rules (from the video above):
  - Different steps get added
  - Drop constants
  - Different Inputs => Different Variables
  - Drop non-dominant terms

  I want to practice big o notation. Where can I do that?

  More Big O examples: https://dev.to/jainroe/the-ultimate-guide-to-big-o-notation--learning-through-examples-5ecp

  ## Code Test
  I worked on this code [test](https://www.interviewcake.com/question/python/product-of-other-numbers): 

  >You have a list of integers, and for each index you want to find the product of every integer except the integer at that index.
  >
  >Write a function `get_products_of_all_ints_except_at_index()` that takes a list of integers and returns a list of the products.
  >
  >For example, given:
  >
  >`[1, 7, 3, 4]`
  >
  >your function would return:
  >
  >`[84, 12, 28, 21]`
  >
  >by calculating:
  >
  >`[7 * 3 * 4,  1 * 3 * 4,  1 * 7 * 4,  1 * 7 * 3]`
  >
  >Here's the catch: You can't use division in your solution!

  ### My answer
  ```javascript
  function get_products_of_all_ints_except_at_index(array){
  multArr=[];
     for(i=0;i<array.length;i++){
        newArr = [...array.slice(0, i), ...array.slice(i+1, array.length)]; array.slice(i+1, array.length))
       multArr.push( newArr.reduce((total, item)=>total*item));
     };
  return multArr;
  }
  ```
  I didn''t realize the site's solution would't be in javascript so I didn't get to see an answer in javascript. Their answer was really long and complicated.

  I wrote a test to test my code:
  ```javascript
  test = ()=>{
    const answer = JSON.stringify(get_products_of_all_ints_except_at_index(arr));
    const expected = JSON.stringify([84, 12, 28, 21]);

    return  answer === expected ? "passed! returns [84, 12, 28, 21]": `failed, should return [84, 12, 28, 21], instead got ${answer}` 
  }
  ```

