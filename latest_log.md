
## Day 132, R3
### 11/27/19

- ##  HackerRank 
  I did the [2D Array Challenge](https://www.hackerrank.com/challenges/2d-array/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays) on [HackerRank](https://www.hackerrank.com/)

  This is where I left off. It works when I test it myself but now on HackerRank. Maybe I'm using the wrong data type for the input. I'll look at it tomorrow.
  ```javascript
  function hourglassSum(arr) {
    
  // array of sums for one row
    function sumRow(ypos){
        const arrayOfSumsRow=[]
        for(xpos=0;xpos<4;xpos++){
            arrayOfSumsRow.push(sumIndividualHourglass(xpos,ypos));
        }
        return arrayOfSumsRow;
    }

  //sum of individual        
    //xpos= 0-3, ypos 0,3
    function sumIndividualHourglass(xpos, ypos){

        const top = arr[ypos].slice(xpos,xpos+3).reduce((t,c,ind)=>{
            return t+c;
        },0);
        
        const middle = arr[ypos+1][xpos+1];

        const bottom = arr[ypos+2].slice(xpos,xpos+3).reduce((t,c,ind)=>{
            return t+c;
        },0);

        hourglassSumIndividual = top + middle + bottom;
        return hourglassSumIndividual;
    }

    function allHourglassSums(){
        const arrayOfSums=[];
        for (ypos=0; ypos<4;ypos++){
            arrayOfSums.push(...sumRow(ypos));
        }
        return arrayOfSums;
    }

    
  const max =  allHourglassSums().sort((a, b)=> {
    return a > b ? -1 : b > a ? 0 : -1;
    })[0];

  return max;
  }
  ```
  Outside of seeing why it doesn't work on HackerRank, I think this can be improved further for speed. 
  
  You exit the calculations if the current hourglass couldn't possible be larger than the largest.

  For example if we calculate the sum of this:
  ```
  434
   4
  444
  ```
  We get 27.

  If we start calculating a new hour glass and it starts with 1:
  ```
  1
  ```
  We can stop looping through this hourglass because we know it can't be larger than 27 even if all the other numbers were 4.
