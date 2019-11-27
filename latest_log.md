
## Day 130, R3
### 11/26/19

- ##  HackerRank 
  I did the [Counting Valleys](https://www.hackerrank.com/challenges/counting-valleys/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup) on [HackerRank](https://www.hackerrank.com/)

  ```javascript
    function jumpingOnClouds(c) {
    let jumps=0;
        for(var i=0; i<c.length-1; i++){

            if(c[i]==0 && c[i+2]==0){ 
                i++;
            } 
            jumps++;   

        }
        return jumps;
    }
  ```

  I'm in Florida for Thanksgiving so keeping this short!

## Day 129, R3
### 11/25/19

- ##  HackerRank 
  I did the [Counting Valleys](https://www.hackerrank.com/challenges/counting-valleys/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup) on [HackerRank](https://www.hackerrank.com/).

  ```javascript
    function countingValleys(n, s) {
        s = s.split("");
        let valleys = 0;
        let level = 0;
        for (var i =0; i<s.length; i++){
            if (s[i] == "D" && level == 0){
                valleys++;
            } 
            if(s[i]=='D'){
                level--;
            } else if(s[i]=='U'){
                level++;
            }
        }
        
        return valleys;
    }
  ```
  It took me a while because I started doing it wrong. I misunderstood the challenge. Next time read slower! 
  
  I was really distracted because I was coding on the plane but the lady next to me was really talkative. Finally, after the plane I got the answer pretty fast once I reread the challenge.
    