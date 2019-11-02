

## Day 106, R3
### 11/2/19
- ### Where I Left Off
  Today I'm looking into [Flic](https://flic.io/flic2). Does Flic have to be native? Can I do this in a PWA? I know I can use Flic if I'm connected to the internet, but can I directly affect the PWA offline?

  ## Flic
  I think I need native mobile code if I want to use flic offline.

  Here's some resources I looked at:
  - [Flic for iOS: Part 1](https://partners.flic.io/partners/developers/ios-tutorial)
  - [fliclib Reference](https://partners.flic.io/partners/developers/documentation/ios/index.html)
  - [The Beginner’s Guide to Objective-C: Methods](https://blog.teamtreehouse.com/the-beginners-guide-to-objective-c-methods)

  ## Objective C

  In the fliclib documentation I saw some words I didn't understand:

  >The **delegate** of a SCLFlicButton object must adopt the SCLFlicButtonDelegate protocol. There are not any required delegate methods, but all are recommended for proper use of the Flic.

  -*from [SCLFlicButtonDelegate Protocol Reference](https://partners.flic.io/partners/developers/documentation/ios/Protocols/SCLFlicButtonDelegate.html)*

  What's a **delegate**? Apparently it's something specific to objective c:

  >What is an Objective-C Delegate? Well.. An Objective-C delegate is just an object that has been assigned as a delegate of another. 

  -*from [How to create an Objective-C Delegate](https://www.ios-blog.com/tutorials/objective-c/how-to-create-an-objective-c-delegate/)*

  That sounds like a namespace to me. 
  
  I figured I might have to get familiar with objective c to use flic. Here's an Objective C tutorial I can look at:

  [Objective-C Essential Training](https://www.linkedin.com/learning/objective-c-essential-training/)

  ## At An Impasse
  Do I want to start learning objective C to continue with my app? Or do I want to keep learning Javascript related skills? 
  
  ## Javascript Concepts
  I decided to look more into javascript concepts or language agnostic concepts. I think having a better base in javascript will help me pick up objective C in the future. And getting more specific with javascript might make me more employable. 

  ## Courses
  I'm looking to get more organized in my code. So these were three courses I was interested in:

  - [Programming Foundations: Test-Driven Development](https://www.linkedin.com/learning/programming-foundations-test-driven-development-2/small-steps-to-great-things): I want to learn test driven development. However, this course is in Java. So I think it would be a bit confusing for me.

  - [Node.js: Testing and Code Quality](https://www.linkedin.com/learning/node-js-testing-and-code-quality/welcome): I want to learn about unit testing, but I want to learn about *fullstack* testing, not just node. Still, this might be useful.

  - [Learning Functional Programming with JavaScript ES6+](https://www.linkedin.com/learning/learning-functional-programming-with-javascript-es6-plus/a-functional-approach-to-transform-code): I thought this might help me better structure my code, but I'm not really sure functional programming is preferable to object oriented programming. Maybe I'll look into it later.

  I'm going to go with [Node.js: Testing and Code Quality](https://www.linkedin.com/learning/node-js-testing-and-code-quality/welcome).

  ## [Node.js: Testing and Code Quality](https://www.linkedin.com/learning/node-js-testing-and-code-quality/welcome):

  ## Example Application Setup
  In the video [Demo application setup and tour](https://www.linkedin.com/learning/node-js-testing-and-code-quality/demo-application-setup-and-tour), the instructor goes over the setup of the application. I found this helpful to see how code can be organized into different directories; directories like `public` for frontend code, `routes`, `migrations`, and more. 

  ## What Is Code Quality?
  - Functional: Does what it's supposed to do
  - Deficiency Free
    - Usefulness
      - flexible and reusable
    - Maintainability
      - Can you maintain the code?
      - Can someone else maintain it without help?
      - Can someone else read and understand design and intent?

  -*from [What is code quality?](https://www.linkedin.com/learning/node-js-testing-and-code-quality/what-is-code-quality)*

  ## Where I Left Off
  I left off on this video: [What is code quality?](https://www.linkedin.com/learning/node-js-testing-and-code-quality/what-is-code-quality)


  