## Day 133, R3
### 11/29/19

- ## HackerRank
  Yesterday I started the [2D Array Challenge](https://www.hackerrank.com/challenges/2d-array/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays) on [HackerRank](https://www.hackerrank.com/). I'm going to continue today.

  I'm getting this result from the test on hacker rank:
  ```
  Input
  1 1 1 0 0 0
  0 1 0 0 0 0
  1 1 1 0 0 0
  0 0 2 4 4 0
  0 0 0 2 0 0
  0 0 1 2 4 0

  Your Output
  7

  Expected Output
  19
  ```

  But when I test that input in Chrome I get 19. The correct answer. But maybe I'm misinterpreting how they're putting in that input. I have it as an array of arrays:

  ```
  (6) [Array(6), Array(6), Array(6), Array(6), Array(6), Array(6)]
  0: (6) [1, 1, 1, 0, 0, 0]
  1: (6) [0, 1, 0, 0, 0, 0]
  2: (6) [1, 1, 1, 0, 0, 0]
  3: (6) [0, 0, 2, 4, 4, 0]
  4: (6) [0, 0, 0, 2, 0, 0]
  5: (6) [0, 0, 1, 2, 4, 0]
  ```

  I tried returning the arguments to the function to see what HackerRank has as it's input. It can me back this:

  ```
  1,1,1,0,0,0,0,1,0,0,0,0,1,1,1,0,0,0,0,0,2,4,4,0,0,0,0,2,0,0,0,0,1,2,4,0
  ```

  So it looks like it's maybe just one long array. But then I returned `arr[0]` and it was `[1,1,1,0,0,0]` so now it does look like an array of arrays.

  ## .sort()
  I found the problem. It's in the sort method.

  In HackerRank this sort method gives a weird array:
  ```javascript
  allHourglassSums().sort((a, b)=> {
        return a > b ? -1 : b > a ? 0 : -1;
  })
  
  >>[7,19,2,0,4,8,10,8,4,6,7,6,3,9,14,3]
  ```
  In chrome you get a sorted array:
  ```javascript
  arr.sort((a, b)=> {
        return a > b ? -1 : b > a ? 0 : -1;
  })

  >>[19, 14, 10, 9, 8, 8, 7, 7, 6, 6, 4, 4, 3, 3, 2, 0]
  ```

  I've seen this before. There are different javascript engines, I believe, that cause this difference in `.sort()`.

  I changed the 0 to 1 in the callback function and it works now 
  ```javascript
  (a, b)=> {
        return a > b ? -1 : b > a ? 1 : -1;
  }
  ```

  ## Working Code
  ```javascript
  function hourglassSum(arr) {
    
    function sumRow(ypos){
        const arrayOfSumsRow=[]
        for(var xpos=0;xpos<4;xpos++){
            arrayOfSumsRow.push(sumIndividualHourglass(xpos,ypos));
        }
        return arrayOfSumsRow;
    }

    function sumIndividualHourglass(xpos, ypos){

        const top = arr[ypos].slice(xpos,xpos+3).reduce((t,c,ind)=>{
            return t+c;
        },0);
        
        const middle = arr[ypos+1][xpos+1];

        const bottom = arr[ypos+2].slice(xpos,xpos+3).reduce((t,c,ind)=>{
            return t+c;
        },0);

        const hourglassSumIndividual = top + middle + bottom;
        return hourglassSumIndividual;
    }

    function allHourglassSums(){
        const arrayOfSums=[];
        for (var ypos=0; ypos<4;ypos++){
            arrayOfSums.push(...sumRow(ypos));
        }
        return arrayOfSums;
    }

      
  const max =  allHourglassSums().sort((a, b)=> {
      return a > b ? -1 : b > a ? 1 : -1;
      })[0];
  return max;
  }
  ```

  This works. But I could add code that would make the code longer but the process faster. I talked about this yesterday.

  ## String To Array Of Arrays
  I tried to practice more code while I did this challenge. Instead of manually making an array of arrays for the input:

  ```javascript
  [[1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1]]
  ```

  I wrote code to turn a string of numbers into an array of arrays:

  ```javascript
  //input
  "1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1"

  //output
  [[1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1], [1,1,1,1,1,1]]
  ```

  Code:
  ```javascript
  var num = "1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1"
  for (i=0;i<num.length;i++){
    if (i==0){
      newarr=[];
      num = num.split(" ").map(x=>parseInt(x));
    };
    newarr.push(num.slice(i, i+6));
    i=i+5;
  }
  ```

