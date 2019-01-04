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

### R1D3 1/3/19
I made a program that uses the canvas api. When the user clicks a button it adds a random gradient to the canvas. I didn't like the blacks and grays. I realized I can use hsl color instead of rgb color to generate random colors with high saturation and medium to high lightness to avoid grays. I would love to try to make this so that the colors change depending on where the sun is in the sky. For example, bright colors in mid day, blues at twighlight, etc. Maybe there is an API for sun position?

**Link To Work:** [Random Color Generator](https://github.com/dangerousdashie/RandomColorGradient/tree/d450bcc4c9288c7fbf85a5c067178a3fb04a4b04)

### R1D4 1/4/19
Played with CSS grid. Wondering how to keep the grid items proportional even if the grid cells' proportions change. Is this possible? So in my example below; even though the grid cells can change to rectangular or square depending on the viewport, could I make the width and height for the grid item stay proporional. So in this case the grit items would always be cirlces and never become ovals even when the grid cell is a rectangle.

**Thoughts/Feelings:** Confused.

**Link To Work:** [grid_layout_practice](https://github.com/dangerousdashie/grid_layout_practice/tree/3dfe4f76488bf7f9eb0b7ea6bed602a9440e517b)

