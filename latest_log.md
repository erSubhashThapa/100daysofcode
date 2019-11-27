
## Day 131, R3
### 11/27/19

- ##  HackerRank 
  I did the [Repeated String Challenge](https://www.hackerrank.com/challenges/repeated-string/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup) on [HackerRank](https://www.hackerrank.com/)

  At first I thought I had it figured out and I had this:
  ```javascript
  function repeatedString(s,n){
    let numOfAs=0;
    const sLength = s.length;
    s = s.repeat(n/sLength)+s.substr(0,n%sLength);
    numOfAs = s.match(/a/g).length;
    return numOfAs;
  }
  ```

  But `s.repeat(n/sLength)` created an invalid string when n was over a certain amount. I guess you can't have a string that long.

  I ended with this.

  ```javascript
  function repeatedString(s,n){
    let AsInSArray = s.match(/a/g);
    if(!AsInSArray)return 0;

    const remainderLength = n%s.length

    const repeatedWholeAs = Math.floor(AsInSArray.length/s.length * (n-remainderLength));
    let AsInRemainder = s.substring(0, n%s.length).match(/a/g);
    let remainderOfAs = 0;
    if (!AsInRemainder){remainderOfAs = 0}
    if (AsInRemainder) {remainderOfAs = AsInRemainder.length;}
    
    const numOfAsInRepeatedS = repeatedWholeAs+remainderOfAs;
    return numOfAsInRepeatedS;
  }
  ```
  I think it's a bit difficult to understand though.I'm not sure if I gave the variables understandable names.

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
    