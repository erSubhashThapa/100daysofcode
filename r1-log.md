# #100DaysOfCode Log - Round 1 - Dashiell Bark-Huss

Dashie here, looking to start this challenge with the new year, **Jan 1, Tuesday, 2019.** Today is December 25th. I'm at a Starbucks in Tequesta, FL. I'm originally from Chicago, but I'm a nomad living in a Rialta, a van sized RV, with my spouse Shlomo. I decided to learn to code when our van broke down at a Barnes and Nobles in early 2017 and I bought a programming book. Now I'm looking to get more serious with my time so I'm commiting to this challenge. I already aim to spend 100 minutes a day doing coding tutorials, but I've decided to commit to an hour a day of hands on coding with this challenge. I'm not sure if my van's solar power set up will be able to handle the power required for these commitments, but I'm going to attempt the challenge anyways. I may still aim to just do 100 minutes a day, but use 60 minutes of that just for hands on coding and 40 minutes for tutorials. Ok, be back on Jan 1st!
## Pre-Round-Log
### PR1D1 - 12/26/18
I decided to do some preliminary days before the New Year starts. This way I can test power supply issues and other issues that come about from van lifing. Today, I coded for 63 minutes and 35 seconds. At the hour mark I was down to 68% power from 95%. I am looking into web dev environments I can use on my iPhone to save power.

Today I coded a very simple program. I used HTML, CSS, and Javascript. I wanted to stay away from jQuery, which I'm learning, because I want to make sure I have some experience with just Javascript so I'll be able to tell the two apart better in the future.

My program counts the number of times you click a button. My goal was to code this from scratch- no copy and pasting snipets of code. I started with a blank page and did the whole HTML/code by hand. I deleted it and started from a blank page a few times in a row until I could do it without any typos and errors.

Ok now I need to figure out how to push it to github and link it here. Power currently at 63%.

OK here it is! Not sure If I should have done it as a gist or repository. I still don't know how this all works.

**Link to work:** [Simple Button Click Counter](https://github.com/dangerousdashie/Simple-Button-Click-Counter)

Computer power now at 59%.

### PR1D2 - 12/27/18

I coded for an 1:19hr but not all at once. I practiced coding from scratch and from memory an html document with externally linked css and javascript. Then I tried to make a program that gave you points everytime you clicked a button. If it was during a randomized special bonus time you'd get extra points. This is a miniversion of a feature I want in a brain training app I'm making. I was having trouble getting the program to toggle the bonus time on and off at random times. Still working on this. It's too much of a mess to post on github. Should I post things that are a huge mess?

### PR1D3 - 12/28/18
I continued the project from yesterday. I was able to get a function called at random intervals. Now I'm dealing with an issue trying to reference a variable that stores a dom element. It only works from inside the function. But I thought outside the function, the variable is still in scope. What's going on? I coded for 65 minutes.

### PR1D4 - 12/29/18
I found out why the variable only works from inside the function. Since the script is run in the head of the HTML doc, the variable is created before the DOM. The DOM element doesn't exist yet, so it saves as null. I'm trying to figure out how to save it globally. I tried window.onload but it's not working. I also reviewed how to push to github from the command line and find files in unix. I pushed this project to github from the command line. 

**Update:** I did some more coding and I figured out the issue. I was calling the function that I set equal to onload, instead of just setting it equal to onload. Now my little program is working.  

**Link to work:** [Random Bonus Points](https://github.com/dangerousdashie/Random_Bonus_Points)

### PR1D5 - 12/30/18
I coded for around 1:40 hr. I spent today trying to rewrite [Random Bonus Points](https://github.com/dangerousdashie/Random_Bonus_Points) from scratch & memory to review what I learned. I ran into a bug  that only happened when my code was in a certain order. I spent so long trying to figure out why. I totally overcomplicated it. The solution was that the code was missing a semicolon!! I thought it had to do with something complex, something with how self executing functions work. OMG I spent so long on this stupid issue! I only figured it out because I posted it on stackoverflow and someone showed me. But I learned my lesson. I always thought semicolons were optional in javascript. Sometimes my code works without them. I guess they aren't! I might continue my jQuery tutorial or responsive design tutorial later today if I have time.

**Thoughts/Feelings:** Feels like I wasted so much time, but I know it's all part of the process. My back and eyes feel stressed. Need to take a break.

### PR1D6 - 12/31/18
I coded in the passengers seat while driving to Fort Myers today. I re-coded [Random Bonus Points](https://github.com/dangerousdashie/Random_Bonus_Points/tree/eb7ebbbc6ace242072246ad62c8464a886ef47a3) from scratch and memory all over again. Then I added some responsive CSS. Then I went on code wars and started the [Count the Digits](https://www.codewars.com/kata/566fc12495810954b1000030) kata. I didn't get to coding the challenge but I made an HTML interface for the challenge. So really I worked on how to pass HTML input values as Javascript function parameters. I haven't put it on github yet. I might try to do some tutorials today too, but it's NYE so we'll see if I have time.

**Thoughts/Feelings:** Feeling good. Getting more comfortable with the stuff I'd been using but didn't really understand.

## Round-1-Log
### R1D1 - 1/1/19
I did some coding from scratch and memory; taking html input values as javascript function parameters. Then I finished the [Count the Digits](https://www.codewars.com/kata/566fc12495810954b1000030) kata I looked at yesterday. I started working on a different solution to the same kata before I submitted but I couldn't figure it out. It looks like some of the top answers are what I was trying to do. 

**Thoughts/Feelings:** Good day. Got some skeeter bites from coding outside. I feel a little overwhelmed when I see how good these other kata answers are. I'm going to review some of the top ones.

**Link To Work:** [Dashie's Solution to Count the Digits](https://www.codewars.com/kata/566fc12495810954b1000030/solutions/javascript/me/best_practice)

### R1D2 - 1/2/19
Today I reviewed the other answered to the [Count the Digits](https://www.codewars.com/kata/566fc12495810954b1000030) kata. I tried it the way the top answer did it. Then I worked with the canvas API. Gonna try to make a Javascript program that draws using the canvas API.

### R1D3 - 1/3/19
I made a program that uses the canvas api. When the user clicks a button it adds a random gradient to the canvas. I didn't like the blacks and grays. I realized I can use hsl color instead of rgb color to generate random colors with high saturation and medium to high lightness to avoid grays. I would love to try to make this so that the colors change depending on where the sun is in the sky. For example, bright colors in mid day, blues at twighlight, etc. Maybe there is an API for sun position?

**Link To Work:** [Random Color Generator](https://github.com/dangerousdashie/RandomColorGradient/tree/d450bcc4c9288c7fbf85a5c067178a3fb04a4b04)

### R1D4 - 1/4/19
Played with CSS grid. Wondering how to keep the grid items proportional even if the grid cells' proportions change. Is this possible? So in my example below; even though the grid cells can change to rectangular or square depending on the viewport, could I make the width and height for the grid item stay proporional. So in this case the grit items would always be cirlces and never become ovals even when the grid cell is a rectangle.

**Thoughts/Feelings:** Confused.

**Link To Work:** [grid_layout_practice](https://github.com/dangerousdashie/grid_layout_practice/tree/3dfe4f76488bf7f9eb0b7ea6bed602a9440e517b)

### R1D5 - 1/5/19
Worked on the [Number of trailing zeros of N!](https://www.codewars.com/kata/52f787eb172a8b4ae1000a34/train/javascript) kata on code wars. I didn't finish it. I spent most of the time trying to understand factorials. Kind of annoying. I don't like when these katas make you learn something unrelated to programming. But I also couldn't stop once I started.

**Thoughts/Feelings:** Annoyed about having to learn about factorials. But I think I will finish it tomorrow.

### R1D6 - 1/6/19
Learned how to use Chrome DevTools to debug my javascript code. It seems more efficient than doing console.log() for everything. I tried to debug my code for the [Number of trailing zeros of N!](https://www.codewars.com/kata/52f787eb172a8b4ae1000a34/train/javascript) codewars kata. I'm having trouble because for some reason one variable is giving me a weird result when I += a number to it. It becomes undefined. 

I've also been doing lynda tutorials and other tutorials but I havn't been talking about them on here because we're not supposed to count tutorials for this challenge. But maybe I will start talking about what I'm learning on the tutorials just to track what I'm learning.

**Thoughts/Feelings:** Glad I finally started debugging in DevTools. I knew console.log() could not be the best way to debug. I would like to learn more about debugging.

### R1D7 - 1/7/19
I tried using Jasmine.js to run a simple unit test. [This](https://evanhahn.com/how-do-i-jasmine/) tutorial was helpful in getting started. Outside of my hour of coding I did an hour of a jQuery tutorial on lynda.com.

**Thoughts/Feelings:** Felt like I did more reading than coding but I'm glad I got one unit test written.

**Link To Work:** [Trying Out Jasmine](https://github.com/dangerousdashie/unit_testing/tree/master/jasmine-standalone-3.3.0)

### R1D8 - 1/8/19
I worked on a jQuery challenge from my lynda tutorial. I solved half of it. I didn't solve the other half because we hadn't actually learned the solution. So I was thrown off. I could have figured it out with some googling but I assumed I just missed the answer from the tutorial. But it wasn't actually in the tutorial. But the answer was similar to what I thought I just didn't know the properties/function I needed to know. Then I set up jasmine again, this time on a single html page. Then I set it up with my solution for the codewars kata, [Number of trailing zeros of N!](https://www.codewars.com/kata/52f787eb172a8b4ae1000a34/train/javascript). 

**Thoughts/Feelings:** I didn't take a break between my tutorials this morning and my coding hour. I think I work better when I take a break. It's nice to be done early now, but my break makes my actual work better and makes me more present. I was also distracted listening to shlomo talk to his friends on the phone. So I either have to ask Shlomo to be quiet or put clasical music or something on my head phones. Lesson: it's more important to be focused than to try to check off that I did something.

**Link To Work:** [Jasmine Single Page Addition](https://github.com/dangerousdashie/single_page_jasmine_simple)

### R1D9 - 1/9/19
  I finished the [Number of trailing zeros of N!](https://www.codewars.com/kata/52f787eb172a8b4ae1000a34/train/javascript) kata. I used the debugger and jasmine unit tests. My solution was so unnecessarily verbose. It had an entire step that was unnecessary but that was more due to the fact that I misunderstood the equation to finding the trailing 0's for factorials than my ability to write clean code. Which is why I'm not a fan of these kata's that make you learn non-programing ideas. Uchhh! Maybe it will come in handy in trivia one day? But even still my code was verbose because I refactored it after realizing I didn't need that step and it is still long. I'll look at the other solutions later. It was a 5 kyu kata so it was hard. 
  I ran into an infinite loop today and debugged it. I'd like to learn more about debbugging. I think it's the one thing that by learning it everything else will be easier. That's the focusing question from The One Thing. 
  Outside of coding, I did more of the jQuery tutorial on lynda. It helped to take a break between my tutorial and coding. I think I might do more coding later because it's only 12:33 and I finished my tutroial, my coding, and my workout so I'm done really early.

### R1D10 - 1/10/19
I looked at some of the other katas. Then I practiced jQuery. I made a project that involved my friends faces. I want to make it more fun. I did more jquery tutorial outside of coding.

**Link To Work:** [Friends Faces](https://github.com/dangerousdashie/friends_faces/tree/dc5ba4b7514dac337f300cb71ebcca6f05f93eda)

### R1D11 - 1/11/19
I'm reading this book called The One Thing. The book talked about "Goal Setting to the Now" which helps you take a long-term view of your goals and narrow it down to what you need to do right now to move towards that goal. So I used the technique to figure out how I need to spend my coding time. I decided that I need to really practice my javascript. So today I looked at some of the other solutions on the katas I've done. I looked at the methods that people used and read the documentation on them. I tried them out myself. Even just reading the documentation is helpful because I'm getting exposed to terminalogy. The more I read the documentation the more I'm able to understand new information I read in the documentation. I want to do some more coding later, I feel inspired to learn more.

### R1D12 - 1/12/19
I am trying to grab the parameter value from the uri so I can append the poduct name from the uri to the page. It's not working and I'm not sure why but I think it may be a mistake it how I formed the uri to begin width. I'm going to compare what I did to what the teacher did. 

**Thoughts/Feelings:** Annoyed that I spent a whole hour hardly accomplishing anything. But I think every experience I have is good in some way.

### R1D13 - 1/13/19
I figured out my bug from yesterday. I was trying to decide a uri but i had never encoded it. I  dont totally ubderstand  why you have to do it that way. 

### R1D14 - 1/14/19
I worked on flexbox. The tutorial on lynda I'm doing gave me a challnge so that's what I worked on. I am having an issue with the header in the media query. It's doing somethings I don't expect it to do. It must have something to do with the css that it's inheriting, from before the media query. I wonder the best way to debug it. Maybe there's a course on debugging css. I use the debugger but maybe I can do a better job.

**Link To Work:** [Lynda Flexbox Challenge](https://github.com/dangerousdashie/lynda_flexbox_challenge/tree/f65a6daea1e88da7f5a38d86a1ec48ae98e33850)

### R1D15 1/16/19
I completed day 15 yesterday but didn't update my log.  I finished the responsive layout challenge from the responsive layout tutorial on lynda. i had to look at what the teacher did. I had way over complicated what I was supposed to do. I finished the Responsive Layout tutorial and the jQuery tutorial.

**Link To Work:** [Lynda Flexbox Challenge](https://github.com/dangerousdashie/lynda_flexbox_challenge/tree/894e4398aaea4168ebbfe295b73028ea4d69e2bd)

### R1D16 1/16/19
I went through grid garden. Then I tried making a responsive 12 column grid with media queries. I realized I understand less than I thought.

**Thoughts/Feelings:** I need to work on getting more pumped while coding like I do with exercise. I need to implement "goal setting to the now" breaks to reinvigorate my brain. I think I may need more of a concrete goal with coding. Today, I was just like, "let's practice responsive design." But maybe I need to plan more what I'm going to try to make to have a goal I can accomplish.

**Link To Work:**[Resonsive Grid Practice](https://github.com/dangerousdashie/responsive_design_practice/tree/072164083ab3b3ffcd29b06cbe434aac512edc3f)
