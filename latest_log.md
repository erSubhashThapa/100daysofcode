## Day 134, R3
### 11/30/19

- ## HackerRank

I made a function that reverses the order of two numbers in an array because I knew I'd use this.
  ```javascript
  function reverse(arr, first){
      const second = first + 1;
      return [...arr.slice(0, first), ...arr.slice(first,second+1).reverse(), ...arr.slice(second+1,arr.length)]
  }
  ```

  I'm going to try to move the items around until its a consecutive array. But I feel theres a different way to do this ust with math. I'm not sure.

  I want to keep working but I'm keeping my coding to a min on vacation. So here's where I left off. I remembered that arrays can't equal arrays. That's want I need to work on tomorrow. I feel like there's a better way to do this whole thing. But my focus has been getting the challenges done not perfect.

  ```javascript
  function minimumBribes(q) {
    let count =0;
    const movesArray=[];
    for(i=0;i<q.length;i++){
        let moves = 0;
        if (q[i]>q[i+1]){
            q = reverse(q, i);
            moves++;
        }
        movesArray.push(moves);
        if(q!=[1,2,3,4,5] && i == 4){
            console.log(q);
            console.log(q===[1,2,3,4,5]);
            count++;
            if (count>100) return"oops";
            i=-1;
        };
    }

    function reverse(arr, first){
        const second = first + 1;
        return [...arr.slice(0, first), ...arr.slice(first,second+1).reverse(), ...arr.slice(second+1,arr.length)]
    }
    return {movesArray,q};
  }
  ```