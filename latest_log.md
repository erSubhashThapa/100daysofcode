
## Day 128, R3
### 11/24/19

## Interview Prep
In preparation for interviews I want to do more coding challenges. I signed up on [HackerRank](https://www.hackerrank.com/). Before I was doing code wars.

I did the [Sock Merchant](https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup) challenge.

```javascript
function sockMerchant(n, ar) {
    let socks = ar;
    let socksByColor = [];
    while (socks.length!=0){
        socksByColor.push(socks.filter(x=>x==socks[0]).length);
        socks = socks.filter(x=>x!=socks[0]);
    }    
    return socksByColor.reduce((t, c, i, arr)=> { 
           return Math.floor(c/2)+t;
    }, 0)

}
```
It took me about an hour. I wonder if that's too long? I used reduce and [reduce](https://www.w3schools.com/jsref/jsref_reduce.asp) always confuses me when I haven't used it in a while.