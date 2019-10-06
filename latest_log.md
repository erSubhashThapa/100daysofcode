

## Day 79, R3
### 10/6/19
- ## Node
  ### Where I Left Off
  I started testing out the express app for two different users.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/3a6dda91d277c1a5324daa3c594548f2b7ca691c)

  ## Line Selection Not Working

  I'm trying to use the expandLineSelection shortcut in VSC to select an entire line. 

  In my Keyboard shortcut settings (Menu Bar -> Code-> Preferences -> Keyboard Shortcuts) I can see that the short cut is set:
  
  ![](log_imgs/vsc_10-6.PNG)

  However, nothing happens when I press `cmd`+`L`.

  VCS Version: 1.38.1

  ### Fix: I changed the key binding to `cmd`+`;` and it worked. Then I changed it back to `cmd`+`L` and that worked.

  ## Where I Left Off
  I have two users on index now. I think I need to do some refactoring. I want to get the two separate user times to have different socket namespaces.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/e368eab4dbae61522a6fa8a1b48376fec1405d04)


