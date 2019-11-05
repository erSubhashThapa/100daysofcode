

## Day 109, R3
### 11/5/19
- ### Where I Left Off
  I left off on the tutorial playing with Mocha, a testing framework.

  It was a busy day so I'm keeping today's post short.
  
  ## Practice Unit Test With Mocha
  Function:
  ```javascript
  module.exports = function sayHi(name){
    const firstLetterIsLowerCase = name.charAt(0) == name.charAt(0).toLowerCase();
    if (firstLetterIsLowerCase) name = name.charAt(0).toUpperCase() + name.slice(1);

    if(name.toLowerCase() == "god") return "You are not god";

    return "Hi " + name;
  }
  ```
  Unit Test:
  ```javascript
  const chai = require('chai');
  const should = chai.should();
  const sayHi = require('../../../lib/sayHi');

  describe('Say hi', function(){
      context('name entered', function() {
          it('should capitalize the name when saying hi', function() {
              const name = 'dash';
        
              sayHi(name)
                .should.equal('Hi Dash');
          });

          it('Say hi to a person', function() {
              const name = 'Dash';
        
              sayHi(name)
                .should.equal('Hi Dash');
          });
          it('should say you are not god if someone enters god', function() {
              const name = 'God';
        
              sayHi(name)
                .should.equal('You are not god');
          });
      });
  });
  ```

  ## Where I Left Off:
  I watched more of the tutorial on testing. I'm playing with testing a function with a callback.


  
