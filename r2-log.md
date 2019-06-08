# #100DaysOfCode Log - Round 2 - Dashiell Bark-Huss

## Day 59, R2
### 6/8/19


- ## Servers
  Today, I looked more into servers.

  ## Server Is Software?
  Yesterday, I found conflicting information about whether a server is the software or the hardware. In response, Marco ([@Wridgeu](https://twitter.com/Wridgeu)) said that it's software:

  <img src="log_imgs/marco1_6-8.PNG" width="500">
  <img src="log_imgs/marco2_6-8.PNG" width="500">

  ## Ubuntu Server or Regular?
  Yesterday, I wasn't sure if I should use the **server version** of Ubuntu, or the **regular version** of Ubuntu.

  I talked to Greg. He said it's all set up for you by your hosting service, so he wasn't sure. But probably the server version. So that's what I'll put on my virtual machine. 


  ## SSH Into A Virtual Machine?
  I was wondering if it's possible to SSH into a virtual machine and found this:
  [Trying to SSH to local VM Ubuntu with Putty](https://unix.stackexchange.com/questions/145997/trying-to-ssh-to-local-vm-ubuntu-with-putty)

  There were a lot of terms that I was not familiar with:
  - private network
  - host network
  - NAT(Natural Address Translation)
  - port forwarding
  - network preferences
  - port
  - daemon

  But when I look for pages about how to learn backend development, none of them mention learning this stuff. So I'm not sure what all this stuff is considered. 

  So I searched all these terms at once in google and lynda. It looks like this all has to do with "networking" which I know very little about.

  I found this tutorial on some exam called [CompTIA Server +](https://www.lynda.com/IT-Infrastructure-tutorials/Cert-Prep-CompTIA-Server-Exam-SK0-004-Basics/772338-2.html).

  I watched it a little, which clued me that I might be trying to understand [server administration](https://www.lynda.com/IT-Infrastructure-tutorials/Cert-Prep-CompTIA-Server-Exam-SK0-004-Basics/772338-2.html).

  I'm not trying to understand these in detail, I just want to understand the basics.

  ## Notes On "Networking Foundations: Servers" Course
  I found a course on lynda that covers these concepts: [Networking Foundations: Servers](https://www.lynda.com/Windows-Server-tutorials/Foundations-Servers/503999-2.html)
  
  The rest of my log is notes on what I learned.


  ## Form factor 
  
  "In computing, the form factor is the specification of a motherboard – the dimensions, power supply type, location of mounting holes, number of ports on the back panel, etc" -[Computer Form Factor, wikipedia](https://en.wikipedia.org/wiki/Computer_form_factor).

  Basically the hardware. Towers are form factors that can be used as servers or client side computer. We've probably all seen them with desktop computer setups. So this shows, that the hardware doesn't necessarily make something a server, since towers can be used as PC's or servers.
  
  Other form factors: server blades, rack mount server.

  ## Server Components

  Aka computer components, since a server is just a computer. However, computer components in a server are made to be more robust than a PC.

  - Motherboard
    - Main circuit board
    - Provides communication for all the components
  - CPU (Processor)
    - Located on the motherboard
    - Have different socket types, needs to match motherboard
    - Have different speeds
    - Cache (high speed memory)
    - Architecture: x86, x64, ARM(not in servers)
  - RAM(random access memory)
    - temporary memory
    - ECC vs non-ECC
    - DDR2 & DDR3
    - Different pin configs, needs to match mother board
  - Expansion Slot
    - Gives ability to add components to the system (expansion cards)
  - Interface Ports
    - ports built into the motherboard or expansion cards
    - Where you connect your network, monitor, usb
    - input/output communication
  - Hard Drives
    - Magnetic drives vs Solid state drives

  Many components can be changed without having to shut down the server (hot swappable)

  ## Power & Cooling

  Power Factors:
  - Voltage: Measurement of force of electricity
  - Amperage: Amount of movement of electricity (current)
  - Wattage: Actual measurement of electrical usage (volts x amps)

  #### Factors For Determining How Much Power We Need
  - Consumption: How much power the servers are going to consume.
  - Redundancy: More power than what's needed so our servers can be dependable.
  
  Cooling Factors:
  - Airflow: In the server room & inside the server itself.
  - Thermal dissipation: ex: sucking heat away from a component
  - Baffles and shrouds: deflectors to help with air flow
  - Fans: exhaust fans- blow the hot air away from components
  - Liquid Cooling

- ## Thoughts & Feelings
  I think it will be helpful to dive deeper into servers. But I also wonder if I'm getting distracted by stuff that doesn't matter. If you have any thoughts, I'm always open to critique on my learning path(on my respective twitter posts or linkedin posts for each log.)

## Day 58, R2
### 6/7/19


- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624) and setting up my remote server.

  ## Vanilla Stack
  Yesterday, I ended the day wondering what stack we're using in the Node server book. I asked Greg([@js_tut](https://twitter.com/js_tut)):

  ![messenger screenshot](log_imgs/vanilla_6-7.PNG)
  
  ## Vanilla FTW
  I thought this was really cool. It's a *vanilla* server! I really dislike working with a billion unnecessary frameworks. Frameworks/modules/libraries have a place in coding, but when you are learning they can be a huge mess.

  Let's say you run into a problem and you're using a bunch of modules. It's going to be really hard to find problem. *Is the bug related to one of the modules? Is it your code? Is it some other technology you're using?* The more minimal your code, the easier it will be to pin point the issue.

  But so many tutorials teach tutti frutti programming (a term I made up, opposite of vanilla). This makes it so much harder to learn. It's rare to find vanilla tutorials, especially the more advanced the subject. I gravitate towards the vanilla tutorials, especially when learning a new subject.

  ![messenger screenshot](log_imgs/vanilla2_6-7.PNG)

  ## Our Stack:

  Greg didn't directly answer what our stack was, but I think it's:

  - MySQL
  - MySQL Server
  - Node
  - Linux/Ubuntu

  ## Getting A Remote Ubuntu Server

  I still want to get an Ubuntu server, so I can follow the tutorial exactly. But my GoDaddy account is Cent OS unless I upgrade it. I probably eventually will upgrade it, but is there a way to get a free Ubuntu server?

  ## Virtual Machine

  I watched this video on virtual machines:
  [What is a Virtual Machine (VM)? In 3 minutes](https://www.youtube.com/watch?v=yIVXjl4SwVo)

  **Virtual Machine:** Virtual machines allow one or more 'guest' operating systems to run inside another

  So can I make an Ubuntu virtual machine that is just a server?

  ## Servers
  I watched this video on servers: [What Is A Computer Server?](https://www.youtube.com/watch?v=TQQA8RpKxqg)

  The tutorial pointed out:
  >You can *turn your computer into a server* by installing software on it that allows it to  be a server.

  So are we setting up a server on an Ubuntu OS? Or is Ubunto an OS just for servers? So it is a server itself?

  >Ubuntu is an open source software operating system that runs from the desktop, to the cloud, to all your internet connected things

  -*from [ubuntu.com](https://www.ubuntu.com/)*

  I read this 3-page tutorial on the difference between Linux and Ubunto. It helped me understand operating systems in general: [What's Ubuntu, and how is it different from Linux?](https://computer.howstuffworks.com/ubuntu.htm)

  ### What is Ubuntu?:
  >Ubuntu isn't just for personal computers. There's also a version of Ubuntu you can use if you want to turn a computer into a network server.

  -*from [What's Ubuntu, and how is it different from Linux?](https://computer.howstuffworks.com/ubuntu1.htm)*

  So are we using the *server version* of Ubuntu? Or the regular Ubuntu? Is this *a regular Ubunto OS* that we are *putting a server on*? Or are we directly ssh-ing into the server OS version of Ubuntu?

  > This section will walk you through the standard MySQL server configuration on a Ubuntu server, for no particular reason.
  
  -*from [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624)*

  So we're putting MySQL server configuration on an Ubuntu server. I think this means we're using the server version of the Ubuntu OS. But maybe you can have the regular version of Ubuntu on a server. So maybe I'm wrong. 

  ## Server Hardware vs. Software

  I'm confused what makes something a server... is it the hardware? The software? Or both?

  If I can turn my computer into a server, as the youtube video said, then it can't be the hardware that makes a server a server. 

  But if you look at pictures of servers, they have different hardware than computers, most notable no screen or keyboard.

  <img src="log_imgs/servers_6-7.PNG" width="500">

  I found this thread on Quora: [Does server mean hardware or software or both?](https://www.quora.com/Does-server-mean-hardware-or-software-or-both)

  It looks like it can mean both but usually means software.
  > While "server" can, in some circles as many have pointed out here, refer to a high-powered computer hardware system, I would venture to guess that most of the time when the term "server" is used by an IT or software engineering professional, it is usually referring to software.
  >
  >A "server" is merely a piece of software, usually with little or no user interface, that "serves" some kind of data or functionality up to "clients".

  -*from [Does server mean hardware or software or both?](https://www.quora.com/Does-server-mean-hardware-or-software-or-both)*
  

  But then I found this conflicting information on another site:
  >While almost any computer that meets the minimum hardware requirements can run a server operating system that alone does not make a desktop computer a true server. Even if the desktop computer had similar processor speeds, memory and storage capacity compared to a server, it still isn't a replacement for a real server. The technologies behind them are engineered for different purposes.

  -*from [Is Server different from a Desktop PC?](https://www.webopedia.com/DidYouKnow/Hardware_Software/difference_between_server_and_desktop.html)*
  
  It also mentioned:
  >a server manages all network resources

  ## What Are Network Resources?

  >Shared resources, also known as network resources, refer to computer data, information, or hardware devices that can be easily accessed from a remote computer through a local area network (LAN) or enterprise intranet. 

  -*from [Shared Resources](https://www.techopedia.com/definition/24796/shared-resources)*

  ## Summary
  So I'm finishing today with a bit of confusion that I slightly clarified:

  - In the node book, does Greg use:
    -  the ***server version of Ubuntu*** 
   
       or 
       
    -  the ***regular version of Ubuntu*** on a server, and then setup up the MySQL Server as the server inside of the Ubuntu OS (like a strange server sandwich)
  - Seems like nobody truly knows when something is a server and when it isn't.
  

## Day 57, R2
### 6/6/19

- ## Coding Coach Mentor
  I reached out to a guy on coding coach but he didn't have enough time to commit to what I wanted. But he agreed to answer questions I send him at his leisure. 

   Many mentors probably sign up looking for a low commitment mentorship, like the person I reached out to. **I think there is room to create an application, or a section of Coding Coach, that is more conducive to a low commitment mentorship.**
   
   When you are trying to choose a mentor it feels like dating. You are trying to pick “the one.” That’s time consuming and higher stakes for both the mentor and mentee. But if I had multiple mentors, I could be more casual about who I pick. Likewise, a mentor may be more open to who they are available to if they had many low commitment mentees. 
   
   ### So here’s my idea for a low-commitment mentor app:

    - Instead of scheduling meetings, the mentors turn on when they are available and on what mediums (phone, DM). These settings can be different for each of their mentees. 
      - **Example:** I’m a mentor and I’m going to work on my own project for 2 hours at my computer, but I’m ok with being interrupted. 
     
        So turn on my “Available” indicator. I set that I’m available by video chat & text. Only my approved 20 mentees can see this. 
        
        However, 3 of my mentees are really annoying! I have mentee “groupings”, so I set my *video availability* to just the 17 mentees. I set only *text availability* for the annoying group, today. Or I could only be available for 5 or my favorite mentees. 
        
        If I was a mentor I’d like this set up! It’s sort of like virtual co-working, but better because you can more easily control who has access to you.
   
    ## How To Build This?
    I wonder if I can contribute to coding coach and see if I can build this? Or should I just try to make it on my own? I still need to learn backend to do this. And I probably need a mentor!

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624) and setting up my remote server.

  ## Forcing Myself To Ask Questions

  I'm usually reticent about asking questions. I don't want to bother people. I try to figure out the answer before I ask, which is often the right choice. But I take this mentality to an extreme. 
  
  I'm going to push myself to ask more than I'm comfortable with. So as soon as I had a question, I forced myself to DM that question to not just one person but two people. Which feels like overkill, and even rude to me. But it is an experiment with getting comfortable with asking.

  ## Getting Help

  I reached out to Brian Morrison II ([@bmorrisondev](https://twitter.com/bmorrisondev)), who had said I could ask him some questions. 
  ### Question:
  <img src="log_imgs/que1_6-6.PNG" width="500"/>

  ### Answer:
  <img src="log_imgs/ans1_6-6.PNG" width="500"/>

  ## What Distro Does My Go Daddy Account Use?

  I tried to find out what my distro was through the command line but none of these worked except the first one which only gives the OS, but not the distro: [How to check OS and version using a Linux command [duplicate]](https://unix.stackexchange.com/questions/88644/how-to-check-os-and-version-using-a-linux-command)

  ## Apache, Ubuntu, What???

  I contacted GoDaddy on chat and asked what distro of Linux my server uses. The agent on chat said "Apache." I figured out that they were wrong: Apache is not a distro, it's something for servers, I'm not quite sure.

  ## VPS vs Dedicated vs Shared Hosting
  I called GoDaddy later and got an agent who was more knowledgeable. He told me that the distro was Cent 0S. Since I have a shared hosting plan I can't changed that. But If I got a Virtual Private Server or a Dedicated Server I could change the OS. 

  He explained that a Dedicated Server is expensive, it's literally an entire server, sort of like owning your own computer. A Virtual Private Server is in between. I didn't ask more about it, but I imagine it's something like owning a partition of a server.

  Here's a post on the differences between [Shared vs VPS vs Dedicated vs Cloud Hosting](https://wp-rocket.me/blog/shared-vs-vps-vs-dedicated-vs-cloud-hosting/).

  ## What Exactly Is Apache?

  After the agent brought up Apache, I found out "The Apache HTTP Server Project is an effort to develop and maintain an **open-source HTTP server** for modern operating systems including UNIX and Windows," [-apache.org](https://httpd.apache.org). So it's a server.
  
  ## Apache vs. MySQL
  So Apache is a server, but then what is mysql? *"MySQL is an open-source relational database management system,"* [-Wikipedia](https://en.wikipedia.org/wiki/MySQL). Oh right, those are very different. But, in the tutorial we're using MySQL server. So is that in place of an Apache server? I think these things are all part of the "stack."

  >Many people are still working with PHP servers. I love Apache and PHP but hate to say that this setup is becoming obsolete. There are good reasons for this. Node servers are used by companies to run libraries like React, which speeds development of the UI components by a large %, but Node is better even for solo developers.

  -*from [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624)*

  So, it looks like Apache uses PHP. And we're not using PHP, we're using Node.js. So we aren't using Apache.

  ## Stack

  "A **server stack** is the collection of software that forms the operational infrastructure on a given machine," 
  -*from [server stack](https://whatis.techtarget.com/definition/server-stack)*

  ### For example, the LAMP stack consists of:
  >- **Linux:** The operating system (OS) makes up our first layer. Linux sets the foundation for the stack model. All other layers run on top of this layer.
  >- **Apache:** The second layer consists of web server software, typically Apache Web Server. This layer resides on top of the Linux layer. Web servers are responsible for translating from web browsers to their correct website.
  >- **MySQL:** Our third layer is where databases live. MySQL stores details that can be queried by scripting to construct a website. MySQL usually sits on top of the Linux layer alongside Apache/layer 2. In high end configurations, MySQL can be off loaded to a separate host server.
  >- **PHP:** Sitting on top of them all is our fourth and final layer. The scripting layer consists of PHP and/or other similar web programming languages. Websites and Web Applications run within this layer.
  
  -*from [What is a LAMP stack?](https://www.liquidweb.com/kb/what-is-a-lamp-stack/)*

  I'm wondering what our stack in the Node Server Setup book is. I messaged Greg to ask him.

## Day 56, R2
### 6/5/19

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624) and setting up my remote server.

  ## Set Up SHH GoDaddy

  I followed how to [set up SHH here](https://www.godaddy.com/help/enable-ssh-16102).

  I got it to work, but instead of root I had to use my cpanel login:

  ```bash
  ssh cpanelUsername@xxx.xxx.xx.xx //replace with your cpanel username and ip address
  ```
  ## Remote Server Questions
  Now that I'm on my remove server, am I on an entirely different OS? What is it? Do I have to install MySQL-server all over again?
- ## Coding Coach
  Since backend is really new to me, I decided to get a mentor on [Coding Coach](https://codingcoach.io/). 

  I'm reading through the [Coding Coach Mentorship Guidelines](https://docs.google.com/document/d/1zKCxmIh0Sd4aWLiQncICOGm6uf38S0kJ0xb0qErNFVA/edit). It says to ***set mentorship expectations*** from the start:

  - What do you hope to achieve from the mentorship? 
  - How much time are you willing and able to commit?
  - Should the mentorship meetings be once a week, twice a week, once a month, or ad-hoc?
  - Is this mentorship open-ended or do you need just a few sessions?
  - What will your primary method of communication be?
  - How do you want to track your progress?

  It also talks about ***re-evaluating the mentorship***. I want to make it easy for mentor to end the mentorship if they no longer have time or for whatever reason. I imagine it would be hard for a mentor to confront a mentee about ending a mentorship, so I want to make it as easy as possible for them. We can make it easier on mentors by having scheduled low pressure re-evalutation sessions where they can end the the mentorship.
  

  ## Assessing Mentorship Goals

  The [Coding Coach Mentorship Guidelines](https://docs.google.com/document/d/1zKCxmIh0Sd4aWLiQncICOGm6uf38S0kJ0xb0qErNFVA/edit) suggests that you have goals for what you want from the mentorship.

  >Goals shouldn’t be too big or too small. They should be achievable within one or two sessions.

  ## Types Of Mentorship
  You can have a *technical* or *career mentorship*. I'd like both in the future, but now I'm focusing on technical. I like the idea of asking my mentor questions. Right now I have so many questions about backend.

  >You may also choose a technical mentorship structured more as a question and answer. It’s important to come to the meeting with questions already written out so you can maximize your mentorship meetings.

  ## Be A Good Mentee

  There's a whole section on being a good mentee. I live this advice:

  >Give them specific feedback about how they’ve helped you; it not only encourages them, but it also helps them become better mentors. 

  I like this because I think feedback is precious, and I read about how showing appreciation for someone can help them avoid burnout. I don't want a burnt out mentor!
  
  >...if in doubt, you can be direct about the best times/days to communicate.

  I think this applies to anything: if in doubt ask and make it easy for the mentor to be honest.

  ## What Do I Want From My Mentor?

  - Help directing me where to go with learning backend
  - Answer my questions related to backend

  Not necessary, but beneficial:
  - Someone who can work with me at times that I code (mid day-afternoon Pacific Time). I have limited access to electricity so this would be helpful, however I can probably figure it out.

  ## How would I want meetings to go?
  Ideally:
  - Occasional planned 15-30 minute phone/video conversations 
    - Estimated time: **1 per week - 1 per month**
  - Regular **"virtual co-working"**: meaning they keep themselves open to questions (text chat/voice/or video depending on the complexity of the question) during certain agreed upon times. This would virtually replicate being in same room, working by ourselves, but I could turn to them and ask them a question when I come across something. 
    - Estimated Time: **1-3 virtual co-working sessions per week, 2 hours at a time** (but the actual questions/answers for each session would probably take up **no more than 15 minutes during that time**)

  I haven't done anything like this, so I don't know how it would go. I'd be open to change this setup, of course.

  ## "Dating Period"

  I'm wondering if we should have a period where we see if we are a good fit?

  ## Find A Mentor
  Now that I know what I want from my mentor, it's time to [find a mentor](https://mentors.codingcoach.io/) and contact them.

  This was really hard! There were so many good options. I didn't know if I should contact everyone or just one person. I decided to start with one.
  
  I decided to first contact this guy who posted videos of himself teaching on twitch. Weird criteria, but I really like when people are comfortable on camera. I think those people are genuine and trustworthy. He had a really nice website. He's from near my hometown. He's self-taught, knows javascript and node.js. I think he will be able to help with backend if he knows node.js. I also like that he posts videos of himself coding, so you know he likes helping others.

- ## Thoughts and Feelings:

  I spent a lot of time looking into coding coach instead of coding today, but I think it was an important investment in my time that will highly contribute to my future coding. It was hard to pick who to contact. What if I pick the wrong person? Did I spend too much time thinking about this or not enough?

## Day 55, R2
### 6/4/19

- ## Markdown Editor
  
  I write in the Github markdown editor every day, but it's not so great. Switching between the *Preview Changes* tab and the *Edit File* tab is a time waster. I also can't spellcheck directly on Github. I want to try a different way to write markdown.
  
  ## VSC Markdown
  I found this extension for VSC: [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one).
  
  I got that extension but I'm not sure how necessary it is because it looks like [visual studios supports markdown out of the box](https://code.visualstudio.com/docs/languages/markdown). To see a side by side, plain text vs rendered pane, hit `cmd + K` and then `k`.

  <img src="log_imgs/sidebyside_6-4.PNG" width="700px"/>

  ## Markdown Preview Github Style: Fail
  I wanted the vsc markdown preview to render like Github. so I installed this [Markdown Preview Github Styling](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-preview-github-styles0) extension but it didn't do anything and there was very little documentation.


  ## Markdown Spellcheck
  I added a spellcheck extension called [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker). It's ok, but it doesn't show suggested spellings.

- ## Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624).

  ## Questions From Yesterday

  Yesterday, I was [confused by a few things.](https://github.com/DashBarkHuss/100-days-of-code/blob/master/r2-log.md#confused-6319)

  I'm going to go through what confused me and try to understand better.

  ## **Question:** Why would you need to make a new password/username? Why not just use root? What's the difference?
    
    <img src = "log_imgs/users_6-3.PNG" width="500"/>

    Greg ([@js_tut](https://twitter.com/js_tut)) reached out to me and answered this one.

    >the other users are just users with system privileges
    >
    >root is the main user added during installation
    >
    >others can be added, but with reduced access (cant delete database for example, only access it)
    >
    >whenever there are multiple users, it usually means difference in privileges: admin vs normal users for example
    
    I thought it was something like this, but now I understand that these users can be regular app users. I didn't understand that before. I thought adding *any* user would just add an *admin*. **I hadn't really thought through what it meant to add a user.**

  ## **Questions:*** Localhost vs Remote Server
    I had questions about localhost and the remote server:

    - **Question:** If I wanted to use a remote server, how do I find my *remote server address?* 
  
    - **Question:** What is a remote server? Is that like when I pay for Go Daddy hosting? Do I get a remote server address?

    Greg ([@js_tut](https://twitter.com/js_tut)) DM'd me:

    >on localhost, you can use "localhost" or "127.0.0.1" where you would use a remote address otherwise (yes its basically a hosted address, like godaddy etc)
    >
    >bind is usually set to 127.0.0.1 on localhost, if its skipped i think it will assume localhost
    >
    >because its like connecting to the mysql server from the program thats running on the same computer......

  ## Localhost:
  I read more about what [localhost actually is here](https://whatismyipaddress.com/localhost), but I didn't finish reading.
  ## **Question:** Do I skip this step if I'm just putting MySQL server on localhost?:
  
  >To log in to your web host open Terminal on your Mac and execute the command ssh root@XXX.XX.XX.XX and replace the X’es with your actual remote server address. Enter password, and you’re in!

  What is this command?: `ssh root@XXX.XX.XX.XX`

  ## SSH Command
  What is SSH?
  >SSH or secure shell, is a very widely used protocol for connecting to systems remotely to manage or use them.

  -*from [Learning SSH, lynda.com](https://www.lynda.com/Developer-Network-Administration-tutorials/Welcome/189066/365610-4.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3assh%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2)*

  >SSH will get you to the command prompt of a remote system.

  -*from [Learning SSH, lynda.com](https://www.lynda.com/Developer-Network-Administration-tutorials/What-you-should-know-before-starting-course/189066/365611-4.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3assh%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2)*


  So since I'm not trying to login to a remote server, I think I don't need this step. But it would be cool to try this tutorial with a remote server. I'm wondering how to do that.

  ## GoDaddy Remote Server

  I have some websites on GoDaady so I want to try use it as my remote server. I contacted GoDaddy in their chat box:

  >**Me:** I'm following a tutorial on setting up a server with Node. It says to log in to my remote server on the command line: ssh root@XXX.XX.XX.XX- and replace the X'es with your actual remote server

  The agent was really helpful. They showed me where I could find the IP address.

  I still can't login because the agent told me I have to [set up SHH here](https://www.godaddy.com/help/enable-ssh-16102). So I will do that tomorrow.

  
  ## **Question:** Why didn't I have a configuration file? How can MySQL server work without a configuration file? If mine worked without it, why would MySQL sometimes need one and sometimes not?
  This was my last question from yesterday, but I didn't get to look into it today.



## Day 54, R2
### 6/3/19
- ## MySQL & Node
  Continuing with Greg's book, [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624), and trying to get MySQL working.
  
  ## Uninstall MySQL: Success
  I was finally able to remove MySQL. I followed these instructions Greg ([@js_tut](https://twitter.com/js_tut)) suggested: [Uninstall MySql on a Mac OS X](https://community.jaspersoft.com/wiki/uninstall-mysql-mac-os-x)

  Now `which mysql` returns nothing! Yay!

  ## apt-get?
  I thought it would be best to get apt-get and download MySQL and MySQL server that way so I could follow Greg's tutorial but in [this thread](https://unix.stackexchange.com/questions/80711/how-to-install-apt-get-or-yum-on-mac-os-x) the answers say not to use apt-get on the Mac OS.
  
  ## MySQL Server UI Installer
  I decided to skip downloading MySQL and just download the MySQL server. I think the server *also* downloads MySQL. I think that's what caused my problems with the password yesterday. I think I accidently reset the MySQL password when I downloaded MySQL server. I followed this video tutorial: [How to Install and Configure MySQL Server on macOS Mac OS X](https://www.youtube.com/watch?v=Bgzf0AH1x-Y)
  
  I used vim instead of nano because the tutorial used vim and it was confusing to use. So I had to follow this page: [Vi / Vim: Save And Quit The Editor Command](https://www.cyberciti.biz/faq/linux-unix-vim-save-and-quit-command/)
  
  ## Back To Node.JS - Server Setup Book
  On page 36 of the Node book, section ***5.0.6 Make MySQL Open For Remote Access***, we edit the config file. But I had no config file.  I had to add the configuration file myself. Used the 2nd to last step in this tutorial for adding the [config file](https://blog.joefallon.net/2013/10/install-mysql-on-mac-osx-using-homebrew/).
  
  On page 38 of the book, it says to press `control` + `O` and then enter to save the file. This didn't work for me. I have to do `control` + `X`.
  
  ## Confused 6/3/19:
  ***Chapter 5: Setting Up MySQL Server*** is confusing me so much. 
  
  I got early access to the book so it's still a work in progress, so there will probably more clarifications in the next updates.
  
  ### My questions 6/3/19:
  
  - Do I skip this step if I'm just putting MySQL server on localhost?:
    - >To log in to your web host open Terminal on your Mac and execute the command
ssh root@XXX.XX.XX.XX and replace the X’es with your actual remote server
address. Enter password, and you’re in!

  - If I wanted to use a remote server, how do I find my *remote server address?* 
  
  - What is a remote server? Is that like when I pay for Go Daddy hosting? Do I get a remote server address?

  - Why didn't I have a configuration file? How can MySQL server work without a configuration file? If mine worked without it, why would MySQL sometimes need one and sometimes not?
  
  - Why would you need to make a new password/username? Why not just use root? What's the difference?
    - >Now we have user felix ready to log in to the database via localhost address with
provided password. This is the account you can use in your JavaScript code when
we get to the Chapter 6: Adding MySQL to api.js
      >
      >...now you can log into your MySQL server using a MySQL client
such as Sequel Pro on Mac or MySQL Workbench on Windows, using the login
token pair felix/PassWord557123! we created earlier.

      ![users screenshot](log_imgs/users_6-3.PNG)
  
  - Do I skip this step if I'm using localhost for my server?:
    - >Comment the line bind-address = 127.0.0.1 by adding # to the front:
  
  
  

## Day 53, R2
### 6/2/19

- ## MySQL & Node
  I'm continuing Greg Sildenikov's [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624), trying to get mysql-server to work. It was really hard to figure out since there aren't instructions for doing it on a mac yet in his book. I didn't get it to work.
  
  ## MySQL Server
  I followed this tutorial for getting mysql server, the section called [3. Using Homebrew service to download](https://tableplus.io/blog/2018/11/how-to-download-mysql-mac.html#3-using-homebrew-service-to-download).
  
  Then I went back to  Greg Sildenikov's [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624) on page 32 and ran `mysql -u root -p`. It worked but `mysql -u root -p` worked before following the instructions for mysql-server. So I'm not sure if that was necessary to get mysql-server: did I already have it? Is it doing something different that I don't understand/can't see? I'm not sure what it did.
  
  ## 5.0.6 Make MySQL Open For Remote Access
  In this section in the book Greg says:
  
  >...you need to find the actual mysql configuration file which should reside in one of the folders specified with !includedir.
   
  What does **specified with !includedir** mean?
  
  I'm not seeing any configuration file or related folder in etc. So maybe I still don't have mysql-server? When I run `which mysql-server` it shows nothing.
  
  ## UI Download
  I tried installing mysql server another way, using the [ui installer](https://dev.mysql.com/downloads/file/?id=486026). But when I run `which mysql-server` I'm still getting nothing. And I still don't see any configuration file or mysql folder in the ect directory.
  
  ## Another Download Method
  Here the author uses homebrew to install mysql-server but it's a different way than what I've already done: https://blog.joefallon.net/2013/10/install-mysql-on-mac-osx-using-homebrew/
  
  I tried to follow this tutorial but I ran into this error.
  
  ```bash
  Sun Jun 02 ~ Dashie$ mysql_secure_installation

  Securing the MySQL server deployment.

  Enter password for user root: 
  Error: Access denied for user 'root'@'localhost' (using password: YES)
  ```
  
  And now I can't log in with `mysql -u root -p` even with the password I wrote down. I'm sooo confused.
  
  ```bash
  Sun Jun 02 ~ Dashie$ mysql -uroot -p
  Enter password: 
  ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
  ```
  
  ## Uninstall MySQL
  So now in addition to not being able to use mysql-server, I can't get into mysql itself. I wonder if it's because I downloaded mysql-server a bunch of times and in a bunch of different ways. Maybe I accidently changed the password for mysql. I figure, I should uninstall and reinstall mysql to change the password back.
  
  I uninstalled mysql the way I did yesterday, but instead of installing it the way the post I linked to yesterday said, I followed this: https://blog.joefallon.net/2013/10/install-mysql-on-mac-osx-using-homebrew/.
  
  But then I got this error:
  ```bash
  Sun Jun 02 ~ Dashie$ mysql.server restart
  ERROR! MySQL server PID file could not be found!
  Starting MySQL
  ... ERROR! The server quit without updating PID file (/usr/local/var/mysql/dashielusssMBP2.jetpack.pid).
  ```
  
  So I uninstalled mysql with brew again. But it doesn't seem to be working because `which mysql` still shows that I have mysql:
  
  ```bash
  Sun Jun 02 ~ Dashie$ brew remove mysql
  Error: No such keg: /usr/local/Cellar/mysql
  Sun Jun 02 ~ Dashie$ which mysql
  /usr/local/mysql/bin/mysql
  ```
  
  I can't remove mysql.
  
  I am so confused and lost and frustrated today.
  
  <img src="log_imgs/uchh_6-2-19.png" width="400"/>

## Day 52, R2
### 6/1/19

- ## MySQL
  Yesterday, I ended with an error when I tried to log into MySQL.
 
  ```bash
  mysql -u root -p 
  >ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)
  ```
  I think it's because I don't remember my password. 
  
  ## MySQL Password
  I could try to guess my password, but I'm really wondering how I can find out what my password is? Shouldn't I be able to access my own password? Who am I trying to keep out? This is only on my computer?
  
  I wanted to see when I installed MySQL incase I need to delete it and reinstall it. I wanted to make sure I added it recently and I hadn't used it a while ago for something important taht I don't remember. But:
  
  >UNIX doesn't support creation date, windows does.
  
  -from *"[what's the command to find the creation date of a certain dirctory?](https://www.unix.com/shell-programming-and-scripting/157874-creation-date-directory.html)"*
  
  If Unix doesn't support creation date, then how does finder have a creation date?
  
  <img src="log_imgs/finder_6-1.PNG" width = "500">
  
  I ended up finding MySQL in my Finder by getting the path for MySQL using `which mysql` in the command line, then going to "Go" in finder and finding where mysql was. 
  
  <img src="log_imgs/go_6-1.PNG" width = "500">
  
  It showed that I installed MySQL on August 1, 2018, this past summer. So I don't think I have anything important that I could lose since then. I probably was just following a tutorial at the time or something. I don't know, had I had any databases, if uninstalling MySQL would cause any databases to be lost, but either way it won't matter: I probably don't have anything important. So I could uninstall it and reinstall it to reset the password if I have to. 
  
  ## Where Is The Password Stored?
  
  > MySQL passwords are stored in the user table of the mysql database and are encrypted using it's own algorithm.
  
  -from *[Security: Where are MySQL passwords stored?](https://serverfault.com/questions/326649/security-where-are-mysql-passwords-stored)*
 
  Since it's encrypted, I guess you can't go trying to get in there somehow and get the password.
  
  More info on password here: [MySQL Documentation: 6.2.1 Account User Names and Passwords](https://dev.mysql.com/doc/refman/8.0/en/user-names.html)
 
  ## Uninstalling and Reinstalling MySQL
  I followed [this tutorial](https://medium.com/@devontem/solved-cant-connect-to-local-mysql-server-through-socket-tmp-mysql-sock-2-f52c9c546f7) on uninstalling and reinstalling MySQL. This fixed the poster's error. But Not mine.
   
  After uninstalling and reinstalling MySQL, I suddely remembered where I saved my password, my Keychain Access! duh. Uninstalling and Reinstalling didn't give me an option to input a new password, so my old password should probably still work. But I still got the same error.
    
  ## Solution
  
  Someone posted the [same error on stackoverflow](https://stackoverflow.com/questions/15016376/cant-connect-to-local-mysql-server-through-socket-homebrew/15016441) and linked to this [other post about a different error](https://stackoverflow.com/questions/4359131/brew-install-mysql-on-macos/6378429#6378429). The solution to this other error worked for me. It's in this stackoverflow thread, the [instructions that Lorin Rivers gave.](https://stackoverflow.com/questions/4359131/brew-install-mysql-on-macos/6378429#6378429)
  
  ### Notes:
  - ### Step 2: I skipped step 2.
  - ### Step 4:
  In Step 4, change the file to the MySQL version you just downloaded.
  
  <img src="log_imgs/step4_6-1.PNG" width="500">
  
  <img src="log_imgs/mysqlversion_6-1.PNG" width="600">
  
  - ### Prompts:
  
  This is what I did for the prompts, though I didn't understand all of these fully:
  
  ```bash
  By default, a MySQL installation has an anonymous user,
  allowing anyone to log into MySQL without having to have
  a user account created for them. This is intended only for
  testing, and to make the installation go a bit smoother.
  You should remove them before moving into a production
  environment.
  Remove anonymous users? (Press y|Y for Yes, any other key for No) :
  ```
  I said yes
  
  ```bash
  Normally, root should only be allowed to connect from 'localhost'. This ensures that someone cannot guess at the root password from the network.

  Disallow root login remotely? (Press y|Y for Yes, any other key for No) : 
  ```
  I said yes
  
  ```bash
  By default, MySQL comes with a database named 'test' that anyone can access. This is also intended only for testing, and should be removed before moving into a production environment.

  Remove test database and access to it? (Press y|Y for Yes, any other key for No) :
  ```
  I said no, because I thought it might be good to see an example of a database.
  
  ```bash
  Reloading the privilege tables will ensure that all changes made so far will take effect immediately.

  Reload privilege tables now? (Press y|Y for Yes, any other key for No) : 
  ```
  I said yes, because why wouldn't I want it to take effect immedietly? What's the alternative?
  
  - ### Step 5:
  I didn't understand Step 5 from the stackoverflow post. But MySQL started working again, so I am good! I guess I didn't need anything after step 4. 
  
  And a tip from lil Dashie: go to your Keychain Access (or whatever it is on Windows) and manually add your mysql password. Although, that was wasn't my problem here. It's just a good tip.
  
  ## Where Does MySQL Start And SQL End?
  Whenever I learn something new this is always a confusion point. Where do things start and end? Where does Javascript end and the Web API start? What part of this project is Node and what part is javascript? What's the difference between the MySQL program and the MySQL server? Github vs Git? Technologies blend together and I usually can only separate them after some time with using them.
  
  I went back to the tutorial: [Learning MySQL Development](https://www.lynda.com/MySQL-tutorials/Up-Running-MySQL-Development/158373-2.html) on lynda. We're learning commands to show tables/databases/columns etc. But I don't know if they are MySQL commands or SQL commands.
  
  This page compares the two: [SQL vs MySQL: What's the Difference?](https://www.guru99.com/sql-vs-mysql.html):
  
  >SQL is a language which is used to operate your database. SQL is the basic language used for all the databases. There are minor syntax changes amongst different databases, but the basic SQL syntax remains largely the same.
  
  So my immediate thought is that it's SQL. However, looking into it [furthur online](https://www.quora.com/How-do-you-view-all-the-tables-in-SQL), it looks like some of these commands are specific to MySQL.
  
  ## Documentation
  You can find the documentation for MySQL here: [MySQL Online Manual](https://dev.mysql.com/doc/refman/8.0/en/)
  
  

## Day 51, R2
### 5/31/19

- ## MySQL
  I decided to look more into MySQL today. I followed [Learning MySQL Development](https://www.lynda.com/MySQL-tutorials/Up-Running-MySQL-Development/158373-2.html) on lynda.
  
  The internet is not great today, so we'll see how much I can do.
  
  ## SQLFiddle
  You can use SQL Fiddle to play with SQL:
  http://sqlfiddle.com/
  
  ## myPHPadmin Demo
  You can use myPHPadmin Demo to play with SQL:
  https://demo.phpmyadmin.net/master-config/server_sql.php?lang=en
  
  ## Database Normalization
  A way to organize your fields and your tables. The accepted standard of database normalization is Third Normal Form (3NF). It includes First and Second Normal Form.
  
  ### First Normal Form:
  Each record has a single value.
  
  ***Isn't a record an entire row? That is not what the instructor means...***
  
  ### Second Normal Form
  - Must be in 1NF
  - Fields not defining a row depend on fields that do. All the information in the table is dependant on what defines the row.
  
  ### Third Normal Form
  - Must be in 1NF
  - Must be in 2NF
  - All the non-defining fields are directly dependent on the defining fields.
  
  I'm confused how 3NF is different from 2NF. ***"All the non-defining fields are directly dependent on the defining fields."*** sounds exactly like, ***"Fields not defining a row depend on fields that do. All the information in the table is dependant on what defines the row."***
  
  ## 3NF vs 2NF
  I watched videos from another lynda tutorial to understand the differences.
  
  ### 2NF: 
  All fields in the primary key are required to determine the other non-key fields.
  
  -***Paraphrased** from [Learning Relational Databases](https://www.lynda.com/Access-tutorials/Second-normal-form/604214/648094-4.html)*
  
  ### 3NF:
  Follows a similar pattern to 2NF but instead of checking against the individual components of a composite primary key, we'll check each *non-key column* against every other *non-key column*. Here, we're looking for columns that are functionally dependent on another piece of information that isn't the promary key. For instance you might try storing the state, and the state abbreviation in an address table. Since state abbreviation is entirely dependent on the state or vice versa, one of those two fields should be removed from the table.
  
  -***Paraphrased** from [Learning Relational Databases](https://www.lynda.com/Access-tutorials/Third-normal-form/604214/648095-4.html)*
  
  ### Denormalization
  When you intentionally ignore some of the normalization rules. This is done usually to increase performance, but it's only used when absolutely necessary.
  
  ## DDL
  Data definition langauge: a set of SQL commands you can use to define tables and databases. It usually involves changing how the data is stored.
  
  ## DML
  Data manipulation langauge: how you manipulate data or change it.
  
  ## OLAP
  Online Analytical Processing: An application that does a lot of reports
  
  ## OLTP
  Online Transactional Processing: An application that does a lot of transactions 
  
  ## Some Terms
  **Column:** Field
  
  **Row:** Record (entire entry)
  
  **Queries:** Commands used to send statements to a table. DDL, DML, or reading and searching information from a table is  how we query tables.
  
  **Table:** a collection of records. A table stores the records that are described by the fields in their row.
  
  **Database:** a container that holds tables
  
  **Schema:** database
  
  **Changing a schema/creating a schema:** changing the definition of what is in the database.
  
  ## Can't Run MySQL
  
  When I run: 
  
  `mysql -u root -p`
  
  I get this error: `ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)`
  
  I get it no matter what password I put in, so maybe it's just because I don't remember my password. I don't know what password this is refering too.
  
  ## MySQL Password
  I'm not sure if I just forgot my password. I was thinking, maybe if I just uninstall and reinstall mysql I can make a new password. But what if this messes up some databases I have on here? I didn't put any mysql data bases on here, but what if some other program did? Is it possible? 
  
  I want to see the date that I installed MySQL. I couldn't find a way in bash to list the date created. But I couldn't find the MySQL folder in the GUI, even after pressing `cmd` + `shift` + `.`. So I couldn't see the date created by looking in the GUI either.
  
  I'll have to investigate more tomorrow.

## Day 50, R2
### 5/30/19

- ## Node
  Continuing Greg Sildenikov's [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624).
  
  ## Setting Up MySQL Server
  This next section confuses me. It talks about installing mysql on Windows and Ubuntu, but not Mac. Luckily Greg is pretty responsive on twitter so I wrote to him to tell him what confused me.
  
  ## Correspondence With Greg
  Greg got back to me and clarified a few things. He said he will include more clarification based on my feedback and questions.
  
  ## MySQL vs MySQL Server
  I was confused about the difference between mysql and mysql server.
  
  Greg said:
  >Well, mysql is a program just like any other. It runs on your computer.
  >
  >But when you write code, you have to install mysql modules to add to the node server with require keyword... that's  separate from the actual mysql program
 
  -*Greg Sidelnikov aka [JavaScript Teacher @js_tut](https://twitter.com/js_tut), Twitter DM*
 
  I'm not sure, but I think he is referring to the difference between MySQL and the mysql node module. I don't think mysql-server is a node module, but I'm not sure.
  
  ## What is MySQL
  
  >MySQL is an Oracle-backed open source relational database management system (RDBMS) based on Structured Query Language (SQL).
  
  -*[MySQL DEFINITION ](https://searchoracle.techtarget.com/definition/MySQL)*
  
  ## What is MySQL Server
  
  >MySQL server is the MySQL database software acting as a server/service towards clients. It is a concrete installation of MySQL.
  
  -*[Olaf Doschke, Quora: What is the difference between a MySQL server and a MySQL client?](https://www.quora.com/What-is-the-difference-between-a-MySQL-server-and-a-MySQL-client)*
  
  >Mysql is a SQL implementation.
  >
  >Mysql server is the application that runs mysql database system, where all the data is stored and processed.
  
  -*[Nicolas Martin Gonzalez, Quora: What is the difference between MySql & MySql Server?](https://www.quora.com/What-is-the-difference-between-MySql-MySql-Server)*
  
  ### Download MySQL:
  Greg said there was a UI to download the MySQL Server.
  
  I found this: [Download MySQL Community Server](https://dev.mysql.com/downloads/mysql/)
  
  Also when I go to the [MySQL github](https://github.com/mysql) there's a repo for MySQL server.
  
  I'm confused: It seems like MySQL server is required if you want to use mysql. So why have them separate? When would you ever need one without the other? Why download one and not the other? Why aren't they just part of the same package?
  
  ## More On MySQL
  I decided to do some more exploring of MySQL.
  
  >MySQL Community Server. When People talk about using MySQL, this us usually what they mean.
  
  -*[MySQL: Installing and Running Ruby on Rails on Mac](https://www.lynda.com/Ruby-Rails-tutorials/MySQL/500549/533096-4.html)*
  
  So maybe MySQL and mysql server do usually go together.
  
  
  
- ## Thoughts and Feelings:
  I spent a bit of my coding time talking to Greg. Part of the time we were talking about the book and he was helping me. For some of the time we were talking about ideas tangentially related to coding. So I dont know if that's cheating! But I'll count it for today.
  
  We talked about feedback. It's important to both give and recieve honest criticism. We shouldn't think of these things negatively. They are useful. It's a mitzvah to give constructive criticism and it's a blessing to recieve it. It's the only way to get better.
  
  Don't be afraid that you'll hurt someone's feelings by giving feedback. People don't just want your flattery. People who are passionate about their work love constructive criticism. The more specific and detailed the better. Likewise, if you want to excell you need to crave feedback too. And you need to let go of your bruised ego and grow a pair of tits, bro! Or should I say, bra? In my case, I have tits, so I needed to grow balls. Now I am complete.
  
  We also talked about embracing stupidity. You should never be afraid to look stupid. Stupidity is a blessing. It's a compass that shows us where we need to go next. When you feel confused, you know that you need to clarify that confusion. If we never felt stupid we wouldn't know what we need to learn next. Understanding your stupidity is it's own kind of wisdom. And, here too, we need to get over our egos. We are all stupid. Only those who ask the stupid questions will get past their stupidity.

## Day 49, R2
### 5/29/19

- ## Node 
  Continuing Greg Sildenikov's [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624).
  
  It's cool to see how things work behind the scenes. I can see how the server loads  the favicon for example:
  
  <img src="log_imgs/favicon_5-29.PNG" width="500">
  
  ## Debugging In Node, Server
  
  The last time I looked into debugging in node I found that you can [debug in VSC](https://github.com/DashBarkHuss/100-days-of-code/blob/master/r2-log.md#debbuging-node-in-vsc). 
  
  However, I'm still having trouble. It seems ***VSC doesn't like to keep the debugger on when I'm also running the file.*** 
  
  ### So how can I debug my server?
  
  For example, on line 14 we have the variable `extension`. 
  
  <img src="log_imgs/debug_5-29.PNG" width="500">
  
  It's made up of other expressions and variables which make it long and confusing.
  
  Sometimes I like to get a clearer picture of a confusing variable by using the DevTools debugger to pause the script and select and hover over all the expressions to see the value of each expression, like this:
  
  ![debugger](log_imgs/devtools_5-29.gif)
  
  I don't see a way of doing that with node and the VSC debugger. 
  
  I cannot run the server ***and*** the debugger at the same time. So I can't pause the script after a request is made to the server and then see the values of the expression `extension`. I wonder what the solution to this is?
  
  ### Possible Solutions:
  - Maybe there's a way of debugging that I don't know about
  - Could unit testing have something to do with this?
  - console log everything
  
  For now, I will console log everything, but there's got to be a better way.
  
  ## Building An API
  >So far we learned how to serve requested files. But if you want to build real web
applications, you might want to integrate support for API endpoints.
  >
  >An endpoint is a URL that follows a special pattern. We can intercept this pattern
and upon its presence we will execute an API command, instead of serving a file
  
  -*Greg Sildenikov, [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624).*
  
  When an API end point is requested, we cancel serving the file, and instead run some server-side commands and return a result.
  
  ## Static Keyword
  In our API class from page 26 of [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624), we use the keyword, `static`:
  
  ```javascript
  static catchAPIrequest(v) {
    // function body etc...
  ```
  
  ### What is the static keyword?:
  >The static keyword defines a static method for a class. Static methods aren't called on instances of the class. Instead, they're called on the class itself.
  
  -*from [static, Mozilla Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static)*
  
  ## Branching Out
  Greg uses the term *"branching out"*:
  
  >We used boolean result of API.catchAPIrequest to branch out.
   
  -*Greg Sildenikov, [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624).*
  
  ### What is branching out?:
  >branching is a way to make a program behave differently based on Boolean expressions (e.g., involving user input)
  
  -*from [Chapter 4: Boolean expressions and Branching](https://hank.feild.org/feild-guide-cpp/conditionals.html)*
  
  ## Confused About Mac:
  In next chapter, Chapter 5: Setting Up MySQL Server, the first two sections are:
  - 5.0.1 Install MySQL Server Locally on Windows
  - 5.0.2 Install MySQL Server on Ubuntu
  
  But nothing on installing it on a Mac.
  
  A few days ago, when I was confused about installing node on mac, Greg said:
  
  >(Ps: windows global installation is unique to the OS, on Linux you can call mysql from anywhere by default)
  
  Is this what he was talking about?
  
  It doesn't say anything about skipping these sections if you're on a Mac.
  
  Times up for today. I will figure it out tomorrow.
  
## Day 48, R2
### 5/28/19

- ## Node 
  Continuing Greg Sildenikov's [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624).
  
  ## Serving Files
  
  I'm now able to serve up files after following the code on page 23 of [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624).
  
  ## Review: Adding ESlint & prettier Locally
  Taking a break from the Node tutorial inorder to set up Eslint and Prettier in this project.
  
  Since this is local, all commands should be run in your project directory.
  ### ESLint
  1. added .eslintrc.json
  2. `npm init`
  2. `eslint --init` (make sure you get to the point where it asks if you'd like to install airbnb style dependancies)
  ### Prettier
  1. add `"prettier"` to `"extends"` and `"plugins"` in .eslintrc.json
  2. Configure prettier in .eslintrc.json in `"rules"`
  - ```javascript
    "rules": {
      "no-console": "off",
      "prettier/prettier": [
        "error",
        {
          "singleQuote": true
        }
      ]
    }
    ```
  3. `npm install --save-dev eslint-plugin-prettier`
  4. `npm install --save-dev eslint-config-prettier`
  5. This is already set up for my workspace but incase I change work spaces or for anybody else's benefit:
  - in User settings:
    ```javascript
    "editor.formatOnSave": true,
    "[javascript]": {
      "editor.formatOnSave": false
    },
    "eslint.autoFixOnSave": true,
    ```
  ## JSON Formatting
  I saw a cool way of formatting JSON in [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624):
  
  ### Colons/Values Aligned:
  <img src="log_imgs/colon_5-28.PNG" width="600"/>
  
  ### Instead of Properties Aligned:
  <img src="log_imgs/linestart_5-28.PNG" width="500"/>
  
  I wonder how this is done. I like how it looks.
  
  Couldn't find much online, I asked on twitter.
  
  ## ESLint: No Shadowing
  > Shadowing is the process by which a local variable shares the same name as a variable in its containing scope. For example:
  >```javascript
  >var a = 3;
  >function b() {
  >  var a = 10;
  >}
  >```
  
  
  ## Spellcheck When Writing In Markdown?
  Is there any way to enable spellcheck while I'm writing in my github markdown log? I have so many typos.
  
- ## Thoughts and Feelings:
  I got good news today related to the bad news that I got a few days ago. I'm so relieved. My focus is so much better. I'm so grateful. The issue is still going on, but the severity is not as extreme as previously thought. 
  


## Day 47, R2
### 5/27/19

- ## Node / Unix
  Today, I'm going to focus on Node and Unix again which I was last learning about on [May 23rd](https://github.com/DashBarkHuss/100-days-of-code/blob/master/r2-log.md#day-43-r2). 
  
  ## Windows Vs. Linux
  
  Last time I ran node from the terminal it worked without having to set up the  environment variables. I was surprised by this. But Greg Sidelnikov reached out to me and explained:
  
  >(Ps: windows global installation is unique to the OS, on Linux you can call mysql from anywhere by default)
  
  -*Greg Sidelnikov aka [JavaScript Teacher @js_tut](https://twitter.com/js_tut)*
  
  I don't know what mysql has to do with it, but I guess you can run node anywhere on a mac.
  
  <img src="log_imgs/terminal1_5-27.PNG" width="300"/>
  
  ## C:
  I know `C:` has something to do with paths and directories but what exactly does it mean?
  
  It's difficult to google questions that involve special symbols so I used [SymbolHound.com](http://symbolhound.com/) to search `C:`. Otherwise, google usually ignores punctuation and special symbols.
  
  >"Windows displays partition labels as uppercase letters (C:)." 
  
  -*[Stackoverflow](https://stackoverflow.com/questions/93228/is-a-hard-drive-partitions-label-upper-or-lowercase-c-or-c)*
  
  It looks like `C:\` is a way that windows represents a harddrive partition. I think you can have other letters for other partictions. Then a path would look like this: `C:\somefolder/somefile`. Since I don't use windows this was new to me. Atleast, I think it's just a windows things.
  
  ## Where Are Core Node Modules Stored?
  
  >Modules are stored in your node installation folder (C:\Program Files\nodejs
in our case) under node modules.
  >You might also find them in nodejs\npm folder:
C:\Program Files\nodejs\node modules\npm\node modules\
 
  -*Node.js – Server Setup, Greg Sidelnikov*

  ## `import`
  
  In the react tutorial from yesterday I saw the `import` keyword and was wondering what it was:
  
  > In browser-side JavaScript code, you can use import / export keywords. But in
addition to that, in node you can use require keyword to add useful modules to
your app from the main NPM repository.

  -*Node.js – Server Setup, Greg Sidelnikov*
  
  So it looks like it's basically the same as require but it's browser-side JavaScript code. So does that mean it's part of javascript or part of the Web API?
  
  It's also nice to know that ***`require()` is just pulling from the NPM repository***. I think that means the folders where the core modules are stored (as mensioned above). So, this clarifies how `require()` works and why you don't need to include the path for the core modules.
  
  ## Importance of a Node Server Continuously
  
  Here Greg is comparing the process of running a simple javscript file in node with running a node server continuously:
  
  >After executing index.js the node process quits, and
control is given back to cmd. This won’t help us run our application server. We
need to build something that runs continuously so we can serve a file every time
someone will access our server from their browser.

  -*Node.js – Server Setup, Greg Sidelnikov*
  
  So, this makes me question what we are actually about to do?:
  
  ***Can we actually deploy a site to the web if we make our own server? Or do we still need heroku and netify etc to do that? What actually is the server?*** I thought when we make a server it still only runs on our own computer and other people cannot access it. That's what I thought I had done in the past when running live servers on my computer to test certain code that couldn't be tested without a server. But here Greg Says, "every time someone will access our server." 
  
  So there's definetly a lot I'm realizing I don't understand. Let's see if I can figure it out in the upcoming sections.
  
  ## Node Server!
  So cool I got a simple node server running!
  
  ```javascript
  let http = require('http');

  const ip = `127.0.0.1`;
  const port = 3000;

  http.createServer(function(request, response){
    console.log('request: ', request.url);
  }).listen(port, ip);

  console.log(`Running at http://` + ip + `:` + port + `/`);
  ```
  
  ## Serving Requested Files
  So far we only are able to send requests. You can see the requests coming in to the terminal 
  
  <img src="log_imgs/requests_5-27.PNG" width="400">
  
  But the code doesn't serve up any files.
  
  I followed the code for serving up files which can be found on page 23 of the May 14th update to Greg Sildenikov's [Node.js – Server Setup](https://www.patreon.com/posts/node-js-book-26866624). It's not free but it's only a dollar a month to support his patreon and you get all his books. If you don't have an extra dollar, you probably should read a book on getting your finances in order (I'm currently reading I Will Teach You To Be Rich). But besides that if you ask 5 strangers for 25 cents they will probably oblidge and you can then support the patreon and buy yourself a candy.
  
  ## MIME?
  What is MIME? In our code we set up a mime variable:
  
  ```javascript
  // Define acceptable file extensions
  let mime = {".html":"text/html"};
  ````
  
  >A multipurpose internet mail extension, or MIME type, is an internet standard that describes the contents of internet files based on their natures and formats.
  
  -*[What Is a File Extension and MIME Type?](https://www.lifewire.com/file-extensions-and-mime-types-3469109)*
  
  

## Day 46, R2
### 5/26/19

- ## React
  Continuing [React tutorial on lynda.com](https://www.lynda.com/React-js-tutorials/Learning-React-js/800214-2.html) with Eve Porcello [@eveporcello](https://twitter.com/eveporcello).
  
  ### Question:
  Where does `props` go when we make a class? I'm guessing in the argument to `render()`?

  ## Conditionally Render Components     
  
  ```jsx
  const Dashboard = ({name})=>(<h1>Welcome {name}!</h1>);

  const App = ({loggedIn}) => (
    loggedIn 
    ? <Dashboard name = "Dash" /> 
    : <h1>You are not logged in</h1>
  );

  ReactDOM.render(
    <App  loggedIn = {false}/>, 
    document.getElementById("root")
  );
  ```
  ![condition](log_imgs/condition_5-26.gif)
  
  ## Render Components From A List
  
    > ...each child in an array or iterator should have a unique key property. So whenever we're rendering some sort of a list, with dynamic values,  we're going to need to give each a key, so that React can re-render things appropriately according to the rendering rules.  
    
  -[Eve Porcello](https://www.lynda.com/React-js-tutorials/Render-components-from-list/800214/2202388-4.html?autoplay=true)

  
  ```jsx
  const shoppingList = [
    "Avocado", "Tahini", "Organic Grass Fed Beef", "Spinach"
  ];

  const App = ({list}) => {
    return (
    <ul>
      {list.map((item, i)=><li key={i}>{item}</li>)}
    </ul>
    )
  };

  ReactDOM.render(
    <App  list = {shoppingList}/>, 
    document.getElementById("root")
  );
  ```
  
  <img src="log_imgs/list_5-26.PNG" width="400"/>
  
  ## Render Object List
  
  ```jsx
  const ingredients = [
    {id: 1, name: "Avocado", grams: 60},
    {id: 2, name: "Tahini", grams: 20},
    {id: 3, name: "Certified USDA Organic Grass Fed Beef", grams: 130},
    {id: 4, name: "Spinach", grams: 120},      
  ];

  const App = ({list}) => {
    return (<ul>
      {list.map((item)=><li key={item.id}>{item.grams}g {item.name}</li>)}
    </ul>
    )
  };

  ReactDOM.render(
    <App  list = {ingredients}/>, 
    document.getElementById("root")
  );
  ```
  
  <img src="log_imgs/objects_5-26.PNG" width="400"/>
  
  ## Create React App
  I already had create-react-app installed. I used it to make a new project.
  
  In the directory that you want to make your project in, run the command:
  
  `create reacte app <projectname>`
  
  ## Run A create-react-app Project In The Browser
  
  First make sure you are in your new project directory. Then run `npm i` to install dependencies. 
  
  Then run `npm start` to start up the project in the browser. This will run your project on local host 3000.
  
  ### Question:
  I see all these import statements at the top again. I'm not sure what they are and the instructor didn't talk about them.
  
  ```javascript
  import React from 'react';
  import ReactDOM from 'react-dom';
  import './index.css';
  import App from './App';
  import * as serviceWorker from './serviceWorker';
  ```
  
  It looks like `require()`.
  
  ## Build For Production
  
  To put your create-react-app project on the web, you'll want to optimize it for production. You can do that really simply by running:
  
  `npm run <nameforbuild>`
  
  To run the build in the browser:
  
  `serve -s <nameforbuild>` 
  
  But this actually didn't work for me, it ran a different folder with the same name. So I have to include the entire path not just the name for build. Then I also ran `sudo npm install serve` (by accident) and `sudo npm install serve -g` and now I can just put the probect name without the path but I'm not sure why. I'm not sure where I have serve installed before. But now I have it installed in too many places.
  
  
  
## Day 45, R2
### 5/25/19

- ## React
  Continuing [React tutorial on lynda.com](https://www.lynda.com/React-js-tutorials/Learning-React-js/800214-2.html) with Eve Porcello [@eveporcello](https://twitter.com/eveporcello).
  
  ## Composing Components
  
  Composing components means putting components together to make a larger interface.
  
  ```javascript
  const Person = ({name, age})=>{
    return (
      <h1> {name}, you are {age}</h1>
    );
  };

  const Friends = () => {
    return (
      <div>
      <Person name = "Shlomo" age = "33"/>
      <Person name = "Mom" age = "old"/>
      </div>
    );
  };

  ReactDOM.render(
    <Friends />, 
    document.getElementById("root")
  );
  ```
  
  <img src = "log_imgs/friend_5-25.PNG" />
  
  ## Class Components
  
  You can also create a component using a class. Here's the Friends component from above as a class.
  
  ```javascript
  class Friends extends React.Component  {
    render () {
      return (
        <div>
        <Person name = "Shlomo" age = "33"/>
        <Person name = "Mom" age = "old"/>
        </div>
      );
    }
  };
  ```
  
  You always need the `render()` method inside the component class.
  
  ## State
  When a component's state changes the render function will be called again to rerender the state change.
  
  ```javascript
  class App extends React.Component  {
    state = {loggedIn: true}
    render () {
      return (
        <div>
        <div>The User Is {
        this.state.loggedIn 
        ? "logged in"
        : "not logged in"}.
        </div>
        </div>
      );
    }
  };

  ReactDOM.render(
    <App />, 
    document.getElementById("root")
  );
  ```
  <img src = "log_imgs/state_5-25.PNG" />
  
  There is more to this that we will find out later.
  
  > So this is a simple reflection of the state value as UI but we're going to use the state with events in order to change the state of our entire application.
  
  -[Eve Porcello](https://www.lynda.com/React-js-tutorials/Understanding-React-state/800214/2201438-4.html)
  
  ## Binding Event Functions to UI Elements
  Here we have our class from above with the state value defined, but we also add functions, `logIn` and `logOut`. Theses functions change the state. We attach them to "Log in" and "Log Out" UI buttons.
  
  ```javascript
  class App extends React.Component  {
    state = {
      loggedIn: false
    };
    logIn = () => this.setState({loggedIn: true});
    logOut = () => this.setState({loggedIn: false});
    render () {
      return (
        <div>
          <button onClick = {this.logIn}>Log In</button>
          <button onClick = {this.logOut}>Log Out</button>
          <div>The User Is {
            this.state.loggedIn 
            ? "logged in"
            : "not logged in"}.
          </div>
        </div>
      );
    }
  };
  ```
  This is called binding an event function to a UI element.
  
  ![screenrecording](log_imgs/stateevent_5-25.PNG.gif)
  
## Day 44, R2
### 5/24/19

- ## React
  I didn't have interenet on this day so I watched a tutorial that I previously downlo.aded on React. You can find it [here on lynda.com](https://www.lynda.com/React-js-tutorials/Learning-React-js/800214-2.html)
  
  A lot of the text here in this log is straight from the tutorial so, I credit a lot of the difinitions here to Eve Porcello [@eveporcello](https://twitter.com/eveporcello)
  
  ## What is react?
  React is a javascript library that’s used for building user interfaces. React aims to make developing large scale single page applications easier.

  ## Functional Javascript:
  A paradigm that emphasizes function, composition, over object orientation.

  ## Install React Developer Tools
  I  already have these installed but this will help you.

  ## Using React Offline
  Since I don’t have internet right now, I can’t link to the react library like the instructor does. How can I use react without the internet: is it a js library file: react.js? is it a node module: require(react)? I skipped to the last project file to see if the instructor uses react without the internet. There I found this: 

  ```javasript
  import React from 'react'
  import ReactDOM from 'react-dom'
  ```

  What is `import`? Is it like `require`? Is it part of javascript or node? Or maybe it’s part of the Web Api?
  
  ## Using A Relative Path Offline
  I found a `react.development.js` file on my computer that was downloaded with the exercise files for this tutorial. Great! 
  
  ## Node Module?
  This file is in a node_modules folder so I’m inferring that react is a module you can require. However, I tried requiring ’react’ and ‘reactjs’ and neither worked: `The module could not be found.`

  Maybe react is not a core module, and I was requiring it without a path which you can only do with core modules.
  
  ## Using the Files
 
  I found the two files that correspond to the links the teacher used, added them to my directory, and added links for them:
  
  ```html
  <script src="react.development.js"></script>
  <script src="react-dom.development.js"></script>
  ```

  I don’t know the difference between the two files.

  I got an error in the `react.development.js` and `react-do.development.js` files:
  `process is not defined`

  I got internet for a bit and got ***more recently versions of the react files. It works now!***

  ## JSX
  JSX, Javascript as XML, is a language extension that allows you to write tags directly in the javascript. For JSX to work you need to link to the babel library in the head and change the script `type` attribute value:

  ```javascript
  <script type="text/babel">
    ReactDOM.render(
      React.createElement("div", {
        "style": {
          "color": "hotpink"
        }
      }, <h1>hoo</h1>), //jsx
      document.getElementById("root")

    );
  </script>
  ```
  
  <img src="log_imgs/jsx_5-24.PNG" width = "400" />

  
  ## You can use variables in JSX:
  ```javascript
  const name = "Dash";

  ReactDOM.render(
    <h1 className="greet"> Hi {name} </h1>, //class is a reserved word, use className
    document.getElementById("root")
  );
  ```
  <img src="log_imgs/jsxvar_5-24.PNG" width = "400" />


  ## Components
  The way that a react application represents a UI element is with a component. A component let’s you put together a user interface with independent reusable pieces. 

  Here we create and add a `Dash` component:
  ```javascript
  const Dash = () => { // create a function component
    return(
    <div>
    <h2>Dash</h2>
    <ul>
      <li>28</li>
      <li>Smart</li>
      <li>Pretty</li>
    </ul>
    </div>
  )
  };

  ReactDOM.render(
    <Dash />, // use the component
    document.getElementById("root")
  );
  ```
  <img src="log_imgs/props_5-24.PNG" width = "400" />


  ## Props
  Props is an object in react that contains properties about the component. With props we can display dynamic data within a component.

  ```javascript
  const Dash = (props) => {
    console.log(props)
    return(
    <div>
    <h2>Dash</h2>
    <ul>
      <li>28</li>
      <li>Cute</li>
      <li>My {props.relation}</li>
    </ul>
    </div>
  )
  };

  ReactDOM.render(
    <Dash relation = "favorite newbie developer"/>,
    document.getElementById("root")
  );
  ```
  
  <img src="log_imgs/component_5-24.PNG" width = "400" />



## Day 43, R2
### 5/23/19

- ## Node
  I finished the tutorial I was learning on node. Today, I'd like to set up a server on node. I was following ***Node.js Server Set Up*** by Greg Sidelnikov aka [JavaScript Teacher @js_tut](https://twitter.com/js_tut) but the latest update doesn't have all the mac instructions. So I'm going to look at other resources too.
  
  ## Unix
  There's a lot of unix commands involved in node. It's been a while since I looked at unix in depth so I may have to refresh my memory.
  
  ## `chown` 
  In [this tutorial on setting up a node server for mac](https://rickchristianson.wordpress.com/2013/11/15/how-to-setup-a-node-js-server-on-mac-os-x-in-less-than-10-minutes/) it uses the `chown` command:
  
  >The chown command is most commonly used by Unix/Linux system administrators who need to fix a permissions problem with a file or directory, or many files and many directories.
  
  *-from [The Linux `chown` command](https://alvinalexander.com/linux-unix/linux-chown-command-chgrp-files-directories)*
  
  ### Stupid Questions:
  Why would I need to change permissions on my computer for any file? Why don't I just have permission to do everything? Why would I disallow myself to ever have permission? What is my username and how do I see who owns what? Is it possible for a file to not be owned by any username?
  
  ## Environment Variables
  
  Skimmed this: [An Introduction to Environment Variables and How to Use Them](https://medium.com/chingu/an-introduction-to-environment-variables-and-how-to-use-them-f602f66d15fa)
  
  In Greg's tutorial for setting up a node server, it says that after we install node, we won't be able to run node from anywhere because we still need to add the path to our environment variables. However, mine is working from anywhere and I don't see the environment variables for the node path when I run `env` in the command line. What's happening?
  
  ## Path Variable
  In [this tutorial on setting up a node server for mac](https://rickchristianson.wordpress.com/2013/11/15/how-to-setup-a-node-js-server-on-mac-os-x-in-less-than-10-minutes/) it says to add these two variables through the command line:
  
  ```bash
  $ export NODE_PATH="/usr/local/lib/node"
  $ export PATH="/usr/local/share/npm/bin:$PATH"
  ```
  
  However, I already have a `PATH` variable that's different: 
  ```bash
  PATH=/Users/dashiellbark-huss/.rbenv/shims:/usr/local/bin:/usr/local/sbin/:/usr/local/mysql/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
  ```
  
  `PATH` seems like such a broad variable name. Why would we use it for something specific like just for npm? Why not name it `NPM_PATH`? 
  
  Am I supposed to write over my last `PATH` variable? What will that affect? The next time I follow a tutorial, will they tell me to write over `PATH` again for some other `PATH`? Won't that screw things up?
  
  ## PATH Is A List Of Paths
  
  >The $PATH variable is specified as a list of directory names separated by colon (:) characters. 
  
  *-from [Mac OS X: Set / Change $PATH Variable](https://www.cyberciti.biz/faq/appleosx-bash-unix-change-set-path-environment-variable/)*
  
  ## Current Session?
  
  I this stackoverflow thread, it mentions adding `PATH` to the *current session* vs *permanently*:
  
  >"...that would be for the current session, if you want to change permanently add it to any .bashrc, bash.bashrc, /etc/profile - whatever fits your system and user needs." 
  *-from [Removing a directory from PATH](https://unix.stackexchange.com/questions/108873/removing-a-directory-from-path)*
  
  I found out this means the current shell session. That clarfies things.
  
  ## Understanding PATH
  This article, [How to add directory to system path in Linux](https://www.computerhope.com/issues/ch001647.htm), answered a lot of my questions:
  
  ### Appending to PATH
  In the tutorial where it said to set the `PATH`, we're not overwriting `PATH`
  
   ```bash
  $ export PATH="/usr/local/share/npm/bin:$PATH"
  ```
  
  At the end of the variable value, we add the `$PATH` variable itself. So we're **appending** the npm path ***to our $PATH***.
  
  ### Current Session
  
  >The methods we've used so far only sets the environment variable for your current shell session; when you logout or close the terminal window, your changes will be forgotten.
  
  *-from [How to add directory to system path in Linux](https://www.computerhope.com/issues/ch001647.htm)*
  
  ## Unix: A Multiuser Environment
  
  Earlier I wondered why I would need to give permissions for files on my own computer:
  
  > Unix is fundamentally a multi-user environment.
  
  -[Kevin Skogland](https://www.lynda.com/Mac-OS-tutorials/Logging-using-command-prompt/78546/83613-4.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3abash+profile+unix%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2)
  
  >Other Unix systems don't automatically log you in. You'd put in your username and your password for it to know who you are. But your Mac already knows who you are. Now if you are using your Mac as a single-user environment, that may come as a bit of surprise to you because you may not even think about the fact that you are logged in as you. But if you go to Apple menu and down to System Preferences and into Accounts, you can see that we can manage different user accounts...OS 9 which was a single-user system. But once we moved OS X with this Unix underneath, Unix is fundamentally a multi-user environment.
  
  -[Kevin Skogland](https://www.lynda.com/Mac-OS-tutorials/Logging-using-command-prompt/78546/83613-4.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3abash+profile+unix%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2)
  
  ## Summary
  Today I had a lot of questions about Unix. Some I found answers to, but some I still need to understand:
  
  - What is the bash profile, the place where variables are stored for all sessions? What else is it used for? How can I see it?
  - Why didn't I have to add the path environment variables for my node to work?
  
  I think I'll focus on unix tomorrow too. Since this is a core part of using node, I think it will really help me. It's been a while since I've really looked into Unix. 
  
  I'm familiar with a lot of the commands but not so familiar with the structure: Like what does unix do with `$PATH`, the bash profile, and where are usernames and passowrds stored?
  
- ## Thoughts and Feelings:
  I'm going to embrace my **"stupid questions"**. Some questions feel stupid because they can clue others to the fact that you really don't understand a subject. That's good. 
  
  Most times people don't know what **you** don't understand. Asking stupid questions helps them understand what information you're missing and explain it to you better. 
  
  ### *Be **specific** and **abundant** in your stupid questions.* Really get down to what is confusing you.
  
  Ask others, ask yourself, and ask the internet/google.
  
  It's good to ask questions when you think you might even know the answer are unsure. ***With your questions, always act stupider than you are.**
  
  Another benefit to **writing out and defining your confusion** is that once you understand something, when you go back and read what you were confused by, you feel like you learned a lot. You feel like, *"Who is this confused dumbo from the past?"* Not me! Not anymore!

## Day 42, R2
### 5/22/19

- ## Node
  Continuing my practice and notes for [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html). I finished this tutorial yesterday but I still have to practice some of the concepts.
  
  ## Child Processes
  >Node.js comes with a child process module, which allows you to execute external processes in your environment. In other words, your Node.js app can run and communicate with other applications in your environment.
  [Child processes Node.js Documentation](https://nodejs.org/api/child_process.html)
  
  *-[Alex Banks](https://www.lynda.com/Node-js-tutorials/Readable-file-streams/5016729/2811746-4.html?autoplay=true)*

  
  ## `child_process.exec()`
  
  With the `exec()` function you can run terminal commands in node.js. `exec.()` handles ***synchronous*** processes.
  
  Here, we open Facebook:
  
  ```javascript
  const cp = require("child_process");

  cp.exec("open http://facebook.com");
  ```
  ![open](log_imgs/open_5-22.gif)
  
  ## Handle Data
  You can handle the data that a terminal command returns:
  
  ```javascript
  const cp = require("child_process");

  cp.exec("ls", (err, data, stderr) => {
    if(err){ 
      console.log(stderr);
      throw err;
    }
    console.log(data);
  });
  ```
  ![ls](log_imgs/ls_5-22.gif)
  
  Here we console log the list command's results to the console. The third argument `stderr` is the error that the child process gives, aka the terminal in this program\*, while `err` is the error that Node.js gives.
  
  \*I'm not sure if it can be other processes or just the terminal.
  
  ## `child_process.spawn()`
  You can also run commands in the terminal using spawn. `.spawn()` handles ***asyncronous*** processes.
  
  `.spawn()` returns a ChildProcess Object, as does `.exec()`.
  
  ```javascript
  const cp = require('child_process');

  const questionApp = cp.spawn('node', ['questions.js']);

  questionApp.stdin.write("dash \n");
  questionApp.stdin.write("a van \n");
  questionApp.stdin.write("eating \n");

  questionApp.stdout.on('data', data => {
    console.log(`from the question app: ${data}`);
  });

  questionApp.on('close', () => {
    console.log('questionApp process exited');
  });


  ```
  
  ![spawn](log_imgs/spawn_5-22.gif)
  
  ## Answers In The Terminal?
  
  With the last program, if I take out:
  
  ```javascript
  questionApp.stdin.write("dash \n");
  questionApp.stdin.write("a van \n");
  questionApp.stdin.write("eating \n");
  ```
  It doesn't let me input answers through the terminal. I'm not sure why. I guess it's only putting output from the questions app to the terminal and not listening for input.
  
- ## Node.js Server Set Up
  
  I started reading ***Node.js Server Set Up*** by Greg Sidelnikov aka [JavaScript Teacher @js_tut](https://twitter.com/js_tut).
  
  ## Notes:
  ## 3 Thinks to Understand About Node Server:
  - The difference between Global and Local installations
  - Configuring `package.json`manifest file
  - Understanding the `node_modules` directory
  
  ## Mac?
  It was interesting to read through so far but, it looks like a lot of the instructions are only for Windows. So I'm not sure if this will be helpful to me. Maybe in the next update the Mac instructions will be added.

## Day 41, R2
### 5/21/19

- ## Github
  I forgot to `git add .` which is why I was having trouble yesterday. I havn't used git in a while so I guess I was a bit rusty. I also needed to enter my username and password which I dudn't used to have to do. Maybe it's because I'm using a different terminal application or because I changed my username.

- ## Node
  Continuing my practice and notes for [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  I finished practicing the functions I learned in the last chapter concerning file system functions.
  
  You can see those practoce files here: [File system Node.js Practice](https://github.com/DashBarkHuss/node_fs_practice/commit/63f16ad919bfe81e09291c5dfb02af8c57cbd477)
  
  ## Stream Interface
  >The stream interface provides us with the technique to read and write data. We can use it to read and write to data files, to communicate with the internet, to communicate with other processed.
  
  -[Alex Banks](https://www.lynda.com/Node-js-tutorials/Readable-file-streams/5016729/2811746-4.html?autoplay=true)
  
  >A stream is an abstract interface for working with streaming data in Node.js. The stream module provides a base API that makes it easy to build objects that implement the stream interface.
  >
  >There are many stream objects provided by Node.js. For instance, a request to an HTTP server and process.stdout are both stream instances.
  >
  >Streams can be readable, writable, or both. All streams are instances of EventEmitter.
  >
  >The stream module can be accessed using:
  >
  >`const stream = require('stream');`
  >
  >While it is important to understand how streams work, the stream module itself is most useful for developers that are creating new types of stream instances. Developers who are primarily consuming stream objects will rarely need to use the stream module directly.
  
  -from [Stream Node.js Documentation](https://nodejs.org/api/stream.html#stream_types_of_streams)
  
  This idea is new to me. I think I'll understand it more when I play with it
  
  Here's some stream functions from the tutorial:
  - `fs.createReadStream()`
  - `fs.createWriteStream()`
  - `fs.createWriteStream().write()`
  - `fs.createReadStream().pipe()`
  - `fs.createReadStream().on()`
  - `fs.createReadStream().once()`
  
  
  
  ## Appending To a File With fs.createWriteStream()
  
  If you use `fs.createWriteStream()` it writes over the file you write to everytime you run it. I wanted to append to the file. On this stackoverflow page it showed how to append: [How to create appending writeStream in Node.js](https://stackoverflow.com/questions/3928926/how-to-create-appending-writestream-in-node-js)
  
  You just add the options parameter, which is the second parameter and is an object, and put in `'flags':'a'`.
  
  ```javascript
  const fs = require('fs');

  const writeStream = fs.createWriteStream(`./assets/words.txt`, {'flags':'a'} , `UTF-8`);
  const readStream = fs.createReadStream(`./assets/words.txt`, `UTF-8`);

  readStream.on("data", data => {
    writeStream.write(data);
  });
  ```

  This program reads whatever is in the file `words.text` and then write that text *back* into the file. 
  
  So if `"hi"` is in the file, after running this program, `"hihihihihi"` is the new text in the file. I'm not sure why it writes `"hi"` 4 more times instead of once.
  
- ## Thoughts & Feelings:
  I coded through driving into Utah. We saw some really red mountainss.
  
  They were ***more red*** in real life:
  
  ![utah](log_imgs/utah-5-21.gif)
  
## Day 40, R2
### 5/20/19

- ## Node
  Continuing my practice and notes for [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## File System Functions We Learned:
  - fs.readdir
  - fs.readfile
  - fs.writefile
  - fs.mkdir
  - fs.appendfile
  - fs.rename
  - fs.unlink
  - fs.rmdir
  
  I want to make a small project using these functions.
  
  I used this page for help with Node.js fs(file system) functions:
  [Node.js Documentation fs](https://nodejs.org/api/fs.html)
  
  ## Project
  
  I made a file that creates letters to all my friends based on a `friends.json` file. Here's the function that creates the letter:
  
  ```javascript
  const makeNoteFile= (friend) => {
    const noteTo = (friend) => {
      return ( 
      `Dear ${friend.name},
        I hope this finds you well. I was thinking about how special you are. 
      You are my one and only true ${friend.relation}. A gem at a young ${friend.age}.

      I am thinking of you,
      Dashie`
      )
    }

    fs.writeFile(`${friend.name}.txt`, noteTo(friend),  err => {
      if (err) throw err;
      console.log('file created');
    });
  };
  ```
  
  I also made a bunch of little files that deal with the other functions. I'm having trouble pushing the project to github. My internet is slow today as I travel. So I'm going to leave this log short today.

## Day 39, R2
### 5/19/19

- ## Helping
  Last time I was helping someone on twitter with [this problem](https://github.com/DashBarkHuss/100-days-of-code/blob/master/r2-log.md#day-38-r2). We ended with this:
 
  <img src="log_imgs/scroll_5-19.gif" width="400"/>
 
  The divs look like they have uniform gradient but if you scroll the gradient stays fixed to the viewport.
 
  [JavaScript Teacher @js_tut](https://twitter.com/js_tut) recommended this:
 
  >Make one parent. Create an SVG with a hole and just the white corners. Apply it to 3 gradientless children ;)
 
  This could work however it becomes more difficult when the page is responsive or if there are other elements on the page that might interfere. If the divs are changing perspectives, then we have to change the SVG too. I'm not sure how to do that without warping the perspective of the smooth corner radius of the SVG. You could probably do it with javascript. 
 
  I'm pretty sure there's other ways to do this in javascript too. Like maybe you can change where the background starts with a specific pixel measurement and use javascript to start all the backgrounds in the appropriate spot so that they all line up.
 
  Since I haven't heard back from the OP, I'm gonna leave this problem and go back to node.
 
- ## Node
  Continuing my practice and notes for [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## Debbuging Node in VSC
  Yesterday [Philippe Vaillancourt @snowfrogdev](https://twitter.com/snowfrogdev) told me that there's a way to debug built into VSC. Press `fn` + `F5`. Then just debug directly in VSC. 

  ![screenrecording](log_imgs/debug_5-19.gif)
  
  You can do what I did in the video or:
  1. `fn` + `F5`
  2. Select Environment: **"Node.js"**
  3. Click the debugging view or `shift` + `cmd` + `D`
  4. Click the Debug Console Button
   - <img src="log_imgs/debugbutton_5-19.PNG" width = "300" />
  
  [Here's a video](https://www.youtube.com/watch?v=2oFKNL7vYV8) tutorial of someone using the debugger.
  
  ## Ideas From Today's Lynda Videos
  
  This stuff is starting to feel very backendy to me which is fun and exciting!
  
  ### We learned about the Node module `fs` and these functions:
  - fs.readdir
  - fs.readfile
  - fs.writefile
  - fs.mkdir
  - fs.appendfile
  - fs.rename
  - fs.unlink
  - fs.rmdir
  
  These functions all deal with deleting, creating, or changing files and directories.
  
  I zoomed through this section of the tutorial, simply watching without coding along. Tomorrow, I'll take what I learned from these concepts and make a small project, reviewing any video I need to review. I think this might be a more effective way of learning for me.
  
- ## Thoughts and Feelings:
  I have been learning a lot about how I learn. That's a great side effect of 100DaysOfCode. I like to learn slowly. I feel if I learn a new concept slowly in the beginning, I'm able to learn faster later when I get to the more difficult parts of the subject. Actually, you could say I like to change up the pace depending on my goal.
  
  I'm learning Node.js pretty slowly and deliberately. It's more enjoyable this way and will stick better. I even went off my tutorial to learn how to set up debugging in node. I think debugging is so important. It makes understanding the code a billion times easier. So I took the time to learn how to set debugging up, which slows down my progress in my tutorial but speeds up my progress in the long run.

  I'm going to start posting my log on linked in. I want to start building up my linked in. I don't really know how to use linked in well. Maybe I can take a tutorial.

## Day 38, R2
### 5/18/19

- ## Helping
  Someone asked:
  >I have some children divs (`position: absolute`) nested inside a parent div. The parent div has a gradient background.
  >Question: is it possible to make the children divs inherit the same gradient background from the parent?
  
  I found that this worked:
  ```css
  #parent>* {
    background-image: inherit;
  }
  ```
  
  I thought maybe the OP left out some information because this was simple, and I was right. They also want the gradient to be uniform between the parent and the child.
  
  <img src="log_imgs/css_5-18.PNG" width="400"/>
  
  I looked around for some ideas but nothing I came up with panned out so I posted it on twitter.
  
  ### But then I did figure it out! Sort Of
  
  If you add a `background-size` to the parent you can then have the children inherit that size along with `background-attachment: fixed;` which the OP showed me.
  
  ```css
  #parent {
    background-image: linear-gradient(blue, yellow);
    height: 400px;
    width: 200px;
    background-size: 600px 600px; //size
  }

  #parent>* {
    background-attachment: fixed;
    background-image: inherit;
    background-size: inherit;
  }
  ```
  
  <img src="log_imgs/solution_5-18.PNG" width="400"/>
  
  But the OP got back to me and apparently this solution is limited:
  
  >Very clever! But because `background-attachment: fixed` is relative to the viewport and not to the parent, children will only align with the gradient at the top position. Scroll down and the colour starts changing.
But I think we're getting somewhere with your trick! Thank you!
  
- ## Node
  Continuing my practice and notes for [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## Debugging Node
  I love using DevTools for debugging. But since node runs on the server and not on the browser, what do people do to debug it? How to I get that same functionality I get from DevTools for node?
  
  I found this article: [Debug Node.js in browser with real Chrome Developer Tools](https://hackernoon.com/debug-node-js-with-chrome-devtools-aca7cf83af6b). But it didn't work. I ran the command:
  
  >Sat May 18 start Dashie$ node --inspect --debug-brk ask.js
  
  The terminal responded:
  >Debugger listening on ws://127.0.0.1:9229/4046c63c-1c1c-4580-9e23-1506a47c8feb
  >For help, see: https://nodejs.org/en/docs/inspector
  
  But when I put the link in the browser, it didn't work: 
  >The webpage at ws://127.0.0.1:9229/4046c63c-1c1c-4580-9e23-1506a47c8feb might be temporarily down or it may have moved permanently to a new web address
  
  I went to the link that the terminal provided https://nodejs.org/en/docs/inspector. It said to go here chrome://inspect. When I went there, I saw my `ask.js` app. So it worked! 
  
  I got a warning:
  
  > DeprecationWarning: `node --inspect --debug-brk` is deprecated. Please use `node --inspect-brk` instead.
  
  ## How to Debug Node, Sort Of
  ### Steps:
  1. run `node --inspect-brk <yourfile>.js`
  2. Go to chrome://inspect
  3. Click 'inspect' by your app
  ![screenshot](log_imgs/inspect_5-18.PNG)
  
  ## Using DevTools on Node
  
  When it came to actualy using the DevTools it was really confusing. As soon as I got a bug my sources disappeared. So this is still confusing me.
  
  ## Practicing EventEmitter
  
  I used EventEmitter successfully on my node module after a while of running into an error. The reason? I forgot to return the emitter instance in my function! 
  
  Using the EventEmmiter helped me understand what might be going on in the background when you use regular events.

## Day 37, R2
### 5/17/19

- ## Node JS Notes / Practice
  I'm reviewing what I learned so far in the lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  I'm going to redo some of the projects he does in the tutorial.
  
  ## Alex Bank's Process Tips
  
  I liked how Alex walked through his process:
  
  >...we want to have a variable that can hold our questions:
  
  ```javascript
  const questions = [
  
  ] 
  ```
  >..within this array we want to beable to add any number of questions, and have those questions asked to the user through the terminal.
  
  ### Example questions:
   ```javascript
  const questions = [
    "What is your name?",
    "What is your favorite snack?",
    "Do you like cilantro?"
  ] 
  ```
  
  >**So sometimes when I have a coding challenge, I try to think about what I do and represent it as a function call.** So, for instance I know that we need to collect the answers from the user in the terminal. I'm not necessarily sure how to do that, but I can imagine that there would be a function called `collectAnswers`. 
  
  ```javascript
  collectAnswers()
  ```
  >And, without knowing how the `collectAnswers` function will work, what I do know is I want to send it an array of questions,
  
  ```javascript
  collectAnswers(questions)
  ```
  
  >...and I want the `collectAnswers` function to ask every question in the array, in the order that they're presented, of the user. And, when I get a list of answers back, I can handle that with a callback function. So I know that the second argument of my collectAnswers function should probably be a callback function,
  
    ```javascript
  collectAnswers(questions, callback)
  ```
  
  >...and that callback function should pass a list of answers back. So, I send a list of questions in as an array, and I expect a list of answers back. 
  
  ```javascript
  collectAnswers(questions, answers => {
  
    //do something with the answers, exit the process
  
  })
  ```
  
  >**So this is what I want to do, and at this point I might not necessarily be sure how to do it, but I know that I need a function called `collectAnswers`, so I'm going ot go ahead and create that function.** And the first argument that the `collectAnswers` function is going to take, is an array of questions, so I'll go ahead and call them questions. And, the second argument is a callback function, to be invoked when we're finished, so I'm going to call this done, meaning I want to invoke this function, once the user has answered all of the questions.
  
    ```javascript
  const collectAnswers = (questions, done) = {
  
  }
  ```
  
  ## Making An Ask Questions Module
  
  ### Module:
  
  ```javascript
  const readline= require("readline");

  const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
  });

  const collectAnswers = (questions, done = f=>f) => {
    let answers=[];

    const questionAnswered = (answer)=>{
      answers.push(answer);
      if (answers.length == questions.length){
        done(answers);
      } else if (answers.length < questions.length){
        rl.question(questions[answers.length], questionAnswered);
      }

    }

    rl.question(questions[0], questionAnswered);

  };

  module.exports = {
    collectAnswers
  }
  ```
  
  ## Requiring The Module
  
  ```javascript
  const ask = require("./askQuestions");

  const questions = [
    "How are you?",
    "Do you like mac or pc?",
    "Do you like organic bacon?"
  ]

  ask.collectAnswers(questions, answers=>{
    console.log("thank you! Answers:", ...answers);
    process.exit()
  });

  ```
  ![module](log_imgs/askQuestions_5-17.gif)


## Day 36, R2
### 5/16/19

- ## Node JS Notes
  Continued notes on node.js lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## Core Modules
  
  Core modules are modules that come with node.js so you don't need to install them. But you do need to import them to use them. To do this you use `require()`
  
  ## Destructure Module Functions
  If you only want one function from a module you can use destructuring:
  
  ### Regular:
  ```javascript
  const path = require("path");
  const util = require("util");

  util.log(path.basename(__filename));
  ```
  
  ### Destructured:
  ```javascript
  const path = require("path");
  const { log } = require("util"); //destructured

  log(path.basename(__filename));
  ```
  
  ## Dot Slash Folder (./folder)
  `./` means:
  > ./ is the the folder that the working file is in
  
  -*from [What does “./” (dot slash) refer to in terms of an HTML file path location?](https://stackoverflow.com/questions/7591240/what-does-dot-slash-refer-to-in-terms-of-an-html-file-path-location)*
  
  So it's no different from `../`
  
  ## Custom Modules
  
  When you make your own module, you must include the path in order to require it:
  ```javascript
  const name = require("./myModule");
  ```
  You don't need the path if the module ships with node or is installed via npm.
  
  In the module file, you need to `export` a value:
  ```javascript
  module.exports = "alex";
  ```
  
  ## More Complex Custom Module Example:
  
  ### Count Module
  ```javascript
  let count = 0;
  const inc = () => ++count;
  const dec = () => --count;

  const getCount = () => count;

  module.exports = {
    inc,
    dec, 
    getCount
  }
  ```
  
  ## Importing the Count Module
  
  ```javascript
  const { inc, dec, getCount } = require("./myModule");
  inc();
  inc();
  inc();
  dec()

  console.log(getCount()); //2
  ```
  
  
  ## Property Value Shorthand
  
  I've seen this before but it confused me today:
  
  ![Shorthand](log_imgs/shorthand_5-16.PNG)
  
  An object with properties that aren't in the `key: value` format. This is called the [property value shorthand]( https://javascript.info/object#property-value-shorthand).
  
  ## Method Shorthand
  There's also a [method shorthand](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#Method_definitions):
  
  >In ECMAScript 2015, a shorthand notation is available, so that the keyword "function" is no longer necessary.
  >
  >```javascript
  >// Shorthand method names (ES2015)
  >var o = {
  >  property(parameters) {},
  >  *generator() {}
  >};
  >```
  
  ## Event Emitter
  A node.js module that gives us a mechanism for emitting custom events and wiring up listeners and handlers for those events:
  
  ### Construct a new instance of the event emitter that that we can use to raise custom events:
  ```javascript
  const events = require("events");

  const emitter = new events.EventEmitter();
  ```
  
  Use the `emit()` function to raise custom events:
  ```javascript
  process.stdin.on("data", data => {
    const input = data.toString().trim();
    if (input === "exit") {
      emitter.emit("customEvent", "Goodbye!", "process"); //customEvent raised when we hit this point
      process.exit();
    }
    emitter.emit("customEvent", input, "terminal"); //customEvent raised when we hit this point
  });
  ```
  Wiring up listeners and handlers with the Events Emitter's `.on()` function:
  ```javascript
  emitter.on("customEvent", (message, user) => { //handle custom event
    console.log(`${user}: ${message}`);
  });
  ```
  This says, when a custom event occurs handle it with this callback function.
  
  Event Emitter is asyncronous. The events are raised when they happen.
  
- ## Thoughts and Feelings:
  Learning these new concepts is more draining than building something. I needed to take more breaks. Tomorrow, I'm going to do some more hands on coding with what I learned from today.
  

## Day 35, R2
### 5/15/19

- ## Node JS Notes
  Continued notes on node.js lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## Debugging?
  So far we have only run these node files in the terminal. But how do I debug them?
  
  I guess I don't know yet because I don't know how to put our files into the browser. I think you have to set up a node server or something so node an compile the code.
  
  ## `setTimeout` and `setInterval`
  
  I started to recreate the instructer's project but I wanted to make it more interesting. This led to my playing with `setTimeout` and `setInterval`. 
  
  I'm having trouble getting a loop to delay using `setTimeout` or `setInterval`.
  
  I redid my code so I can do it in the browser and use the debugger.
  
  The answer on the thread [How do I add a delay in a JavaScript loop?](https://stackoverflow.com/questions/3583724/how-do-i-add-a-delay-in-a-javascript-loop) looks like it uses recursion:
  
  ```javascript
  
  var i = 1;                     //  set your counter to 1

  function myLoop () {           //  create a loop function
     setTimeout(function () {    //  call a 3s setTimeout when the loop is called
        alert('hello');          //  your code here
        i++;                     //  increment the counter
        if (i < 10) {            //  if the counter < 10, call the loop function
           myLoop();             //  ..  again which will trigger another 
        }                        //  ..  setTimeout()
     }, 3000)
  }

  myLoop();                      //  start the loop
  
  ```
  
  There was debate about whether the recursion was a problem in the comments.
  
  ## Practice: Node.js New Years
  
  I remade what the the time that the teacher made, with my own pizazz: I made a NYE countdown timer.
  
  ![countdown](log_imgs/count_5-15.gif)
  
  ### Code:
  
  ```javascript
  const waitTime = 6000;
  const intervalTime = 1000;
  let seconds = waitTime /1000;

  function countDown(){
    process.stdout.clearLine();
    process.stdout.cursorTo(0);
    process.stdout.write(`${seconds -1}!!!!`);
    seconds -= 1;

  }

  function sing() {
    clearInterval(interval);
    process.stdout.clearLine();

    var i = 0;                     
    let numOfWords;
    const song = 
    `Happy New Year!!!!!!
    Should old acquaintance be forgot, 
    and never brought to mind?
    Should old acquaintance be forgot,
    and old lang syne?`;

    const lines = song.split("\n");

    function myLoop () {  

      const callback = function () {    
        console.log(`${lines[i]}
      `);          
        i++;                     
        if (i < lines.length) {            
           myLoop();             
        }                        
     };
        const numOfWords = (lines[i].match(/ /g) || []).length + 1;
        setTimeout(callback, 170 * numOfWords) 
     }

    myLoop(); 
  }

  const interval = setInterval(countDown, intervalTime);

  setTimeout(sing, waitTime)

  ```


## Day 34, R2
### 5/14/19


- ## Helping
  I looked at [Swishyfishie's @Swishyfishie2](https://twitter.com/Swishyfishie2) code. He has a counter here. You can add 1 or 2 and then submit to save to `sessionStorage`. 
  
  <img src="log_imgs/swishy_5-14.PNG" width=300>
  
  It was adding more numbers than expected after you press submit. 
  
  I made a `log(func)` function to call from each function that Swishy made to see where the problem was. The `log(func)` function console logs the function name and the `count` variable's value:

  ```javascript
  function log(func) {
    console.log(`func:${func}, count:${count}`);
  };
  ```
  You call `log(func)` from each function, passing in a name for your function such as "+1" or "save".

  What I saw was that when the submit button was pressed, `count` increased by one. Sure enough Swishy was adding 1 to `count`, probably left over from copy and pasting from his first function.
 
  ```javascript
  btnSave.onclick = function () {
      saved.innerHTML = localStorage.getItem('county', count += 1); //oops adding 1 here
      log("save");
  }
  ```
  
  Seems to work after deleting `count += 1` from that line. 
 
- ## Node JS Notes
  Continued notes on node.js lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  [How, in general, does Node.js handle 10,000 concurrent requests?](https://stackoverflow.com/questions/34855352/how-in-general-does-node-js-handle-10-000-concurrent-requests)
  
  ## Global Object
  
  [Mozilla Docs: Global Object](https://developer.mozilla.org/en-US/docs/Glossary/Global_object)
  
  >The global object's interface depends on the execution context in which the script is running. For example:
  >
  >- In a web browser, any code which the script doesn't specifically start up as a background task has a Window as its global object. This is the vast majority of JavaScript code on the Web.
  >
  >- Code running in a Worker has a WorkerGlobalScope object as its global object.
  >
  >- Scripts running under Node.js have an object called global as their global object.

  [Node.js v12.2.0 Documentation: Global Objects](https://nodejs.org/api/globals.html)
  
  ## Modules
  
  Every node.js file we create is refered to as a module.
  
  ## `require()`
  
  `require()` is used to load external modules. Modules are other javascript files containing code. We can either load modules that have shipped with our installation of Node.js, modules we install with npm, or other modules that we create. `require()` is available to us on the global object.
  
  # `process` object
  The `process` object contains information about the current process as well as tools to allow us to interact with the process.
  
  ![process](log_imgs/process_5-14.PNG)
  
  ## Practice What I Learned
  
  I made my own version of a little questions program that the instructor made. I did different questions.
  
  ```javascript
  const questions = [
    "Who do you love?",
    "Who are you?",
    "Are you horny? Answer y or n"
  ];

  const ask = (i = 0 ) => {
    process.stdout.write(`\n${questions[i]} \n\n`);
  }

  ask()

  const answers = [];

  process.stdin.on("data", (data)=>{
    answers.push(data.toString().trim());

    if (answers.length < questions.length) {
      ask(answers.length);
    } else {
      process.exit();
    }
  });

  process.on("exit", ()=>{
    const [lover, name, horny] = answers;

    const doThisTo = horny === "y" ? "make love to": "kiss";
    console.log(`
    ${name.charAt(0).toUpperCase() + name.slice(1)}, you should ${doThisTo} ${lover.charAt(0).toUpperCase() + lover.slice(1)}!
    `);
  });
  ```
  
  ![questions](log_imgs/questions_5-14.gif)
  
- ## Thoughts and Feelings:
  If I don't do some sort of hands on coding (not just coding along with the tutorial), I get super bored by tutorials. So I need to always try to do something at least slightly creative along with the tutorial. Today, that meant recreating the questions program with my own questions.

 
## Day 33, R2
### 5/13/19

- ## NPM Notes
  I continued this npm tutorial:
  [Learning npm the Node Package Manager Tutorial](https://www.lynda.com/Node-js-tutorials/Learning-npm-Node-Package-Manager-2018/761956-2.html)
  
  ## Notes:
  
  `npm outdated`: To see if any packages are outdated locally, `-g` to get global
  
  `npm update <package>` or `npm install <package>` to update package.
  
  `npm uninstall <package>`: uninstall a dependency
  
  ## "devDependencies" vs "dependencies"
  >The difference between these two, is that devDependencies are modules which are only required during development, while dependencies are modules which are also required at runtime.
  
  -*from [NPMmmm #1: Dev Dependencies, Dependencies](https://medium.com/@dylanavery720/npmmmm-1-dev-dependencies-dependencies-8931c2583b0c)*

  
  ## Semantic Versioning
  ![version](log_imgs/version_5-13.PNG)
  
  ### Controlling Version:
  
  ### ^1.x.x
  
  The ^ caret symbol means:
  
  Update all releases that have a major release of 1.
  
  ```javascript
   "devDependencies": {
    "babel-preset-env": "^1.7.0",
  }
  ````
  
  ### ~1.7.x
  
  The ~ tilde symbol means:
  
  Update all releases that have a major release of 1 and a minor release of 7.
  
  ```javascript
   "devDependencies": {
    "babel-preset-env": "~1.7.0",
  }
  ````
  
  ## `package-lock.json` vs `package.json`
  Confused about the difference between these two.
  
  It seems like `package-lock.json` controls things more, specifies things more. But then what's the point of having both?
  
  [Everything You Wanted To Know About package-lock.json But Were Too Afraid To Ask](https://medium.com/coinmonks/everything-you-wanted-to-know-about-package-lock-json-b81911aa8ab8)
  
  >package-lock.json: records the exact version of each installed package which allows you to re-install them. Future installs will be able to build an identical dependency tree.
  >
  >package.json: records the minimum version you app needs. If you update the versions of a particular package, the change is not going to be reflected here.
  
  -*from [What is the difference between package.json and package-lock.json](https://delegatecall.com/questions/what-is-the-difference-between-packagejson-and-packagelockjson-2bd0e4e1-a65f-4d78-b8d8-b51905a37adb)*
  
  ## npm Cache
  
  npm keeps a cache of your install modules so that it doesn't have to get them everytime. Clearing your cache should always be a step in your troubleshooting when working with modules and not understanding what's happening.
  
  `npm-cache-verify`: Verifies you cache. (What does that mean?)
  `npm-cache-clean --force`: clean the cache
  
  ## npm audit
  
  Hard to understand this video without having context for it.
  
  `npm audit` is a command that will check the dependencies of your project and make sure they are safe to use.
  
  [Run an npm audit Lynda Video](https://www.lynda.com/Node-js-tutorials/Run-npm-audit/761956/800277-4.html?autoplay=true)
  
  ## Scripting in package.json
  Scripting in a package.json file gives us a way to do a simple command, to repeat, or execute complex commands.
  
  [npm-scripts docs](https://docs.npmjs.com/misc/scripts)
  
  ![scripting](log_imgs/npmscript_5-13.PNG)
  
  **Run:**`npm <preset script name>` or `npm run <your own script name>`
  
  ## npm npx
  
  npx lets you temporarily install a package just to run one of the commands from that package. This way you avoid package pulution.
  
  [npm npx docs](https://www.npmjs.com/package/npx)
  
- ## Node JS Notes
  Notes on node.js lynda.com tutorial:
  [Node.js Essential Training 2019 Lynda Tutorial](https://www.lynda.com/Node-js-tutorials/Node-js-Essential-Training-Part-I-2019-REVISION/5016729-2.html)
  
  ## Single Threaded non-blocking event driven IO
  ### Single threaded
  Node is single threaded. This confuses me because what if an application has millions of users? How can they all be on the same thread without slowing things down?
  
  ### I/O
  I don't know what I/O means for and I had trouble finding out. 
  
  >Node.js is an open source project designed to let you write JavaScript programs that talk to networks, file systems or other I/O (Input/Output) sources
  >...
  >What is an "I/O based program"? Here are some common I/O sources:
  >
  >Databases (e.g. MySQL, PostgreSQL, MongoDB, Redis, CouchDB)
  >APIs (e.g. Twitter, Facebook, Apple Push Notifications)
  >HTTP/WebSocket connections (from users of a web app)
  >Files (image resizer, video editor, internet radio)
  
  -*from [introduction to node: Understanding node](https://gist.github.com/maxogden/4011336#understanding-node)*
  
- ## Helping
  
  I started to look at some code that [Swishyfishie @Swishyfishie2](https://twitter.com/Swishyfishie2) was stuck on but I didn't get enough time to really check it out. Will look at it tomorrow!
  
## Day 32, R2
### 5/12/19

- ## Testing eslint-plugin-html
  I got the plugin to work again a different way. I just copied and pasted the `node_modules` folder from the other projects into a new project and copied the `.eslintrc.json` file.
  
  ## User Settings vs `.eslintr.json`
  But if I remove this from the user settings:
  
  ```javascript
    "eslint.options": {
    "plugins": [
      "html"
    ]
  },
  ```
  
  Eslint stops linting HTML on the last two project folders: `testing_eslint_project` and `playing with javascript`. But it still works on `perfect_fit_meal`.
  
  Now I see why. The `.eslintrc.json` in `perfect_fit_meal` had: 
  
  ```javascript
  "plugins": [
    "html"
  ]
  ```
  
  But the other two didn't have those settings in their `.eslintrc.json` file.
  
  ## Global Vs Local `eslint_plugin_html`
  
  I can also see that `perfect_fit_meal` has `eslint-plugin-html` in the `node_modules` folder. The other two projects don't. They must be getting the plugin globally. 
  
  The other two also don't have `eslint-plugin-html` listed in the `"dependenies"` property in the `package.json` file like `perfect_fit_meal` does. I think I got it there when I ran `npm install --save-dev eslint-plugin-html`.
  
- ## Prettier
  
  I think I understand a bit more about these plugins now. I'm going to try to install prettier again.
  
  ## Wes Bos Prettier + ESLint Video
  
  I followed this Wes Bos [How to Setup VS Code + Prettier + ESLint](https://www.youtube.com/watch?v=YIvjKId9m2c) video again. I still get ***"Failed to load plugin prettier: Cannot find module 'eslint-plugin-prettier'"***
  
  ## No Dependency
  Now that I understand a little more I can see that I do not have that module in my `node_modules` folder; globally or locally. It's also not in the `package.json` file's `"dependencies"`. 
  
  But why doesn't Wes Bos tell you how to get the dependency?
  
  ## Adding The Dependency Through the Terminal
  
  I'm guessing I need to add it like how I got the eslint dependency, `npm install --save-dev eslint-plugin-html`
  
  So I ran:
  
  `npm install --save-dev eslint-plugin-prettier`
  
  Now I see `"eslint-plugin-prettier": "^3.1.0"` in my `"dependencies"` in my `"package.json"` file.
  
  ## No Dependency In node_modules
  
  Even though I see `"eslint-plugin-prettier": "^3.1.0"` in `"package.json"`, I don't see it in my `node_modules` folder. Even though it says it added the plugin:
  
  ![screenshot](log_imgs/prettier_5-12.PNG)
  
  ## Another Missing Dependency
  I restarted VSC and got this error: 
  
  ***[Error - 13:55:17] Cannot find module 'eslint-config-prettier' Referenced from: /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/.eslintrc.json***
  
  So I also ran:
  
  `npm install --save-dev eslint-config-prettier`
  
  Now I see `eslint-plugin-prettier` but no `eslint-config-prettier` in the node_modules. But I do see both in the `"dependencies"` in the `package.json`.
  
  ## Restart VSC to See the Dependencies
  
  I restarted VSC and now I see the `eslint-config-prettier`! ***So maybe after you add a dependency through the terminal you have to refresh VSC.***
  
  ## Prettier Configs
  
  I added this back to the `.eslintrc.json` file which Wes Bos said to add:
  
  ```javascript
    "prettier/prettier": [
    "error",
    {
      "singleQuote": true
    }
  ]
  ```
  
  But I got this error:
  
  ***Error: ESLint configuration in /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/.eslintrc.json is invalid:***
  ***Unexpected top-level property "prettier/prettier".***
  
  In these [docs for eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) they have ***the `"prettier/prettier"` property inside the `"rules"` property. I moved it there and that error went away.***
  
  ```javascript
  "rules": {
    "no-console": "off",
    "prettier/prettier": [
      "error",
      {
        "singleQuote": true
      }
    ]
  }
  ```
  
  ## Still Missing Dependencies
  
  But I have new errors:
  
  ***[Error - 14:13:42] ESLint stack trace:***
  ***[Error - 14:13:42] Error: Cannot find module 'prettier'***
  
  So I ran:
  
  `npm install --save-dev prettier`
  
  and restarted VSC.
  
  No errors!
  
  Now let's see if it worked.
  
  ## Working (sort of)!
  
  It fixing on save on .js files on. But not .html. It is registering prettier on those files:
  
  ![screenshot](log_imgs/prettiernotif_5-12.PNG)
  
  But when I save it doesn't change the quotes.
  
  ## Prettier Doesn't Work on Script Tags
  
  Looks like it's not possible to fix on auto save in the HTML files:
  
  >It's a planned feature but not supported just yet.
  
  ***-from [How to format code in script tags?](https://github.com/prettier/prettier/issues/2648)***
  
  ## Summary
  
  Looks like I got it working. My problem was that I never actually installed the dependancies. I don't know why that wasn't part of the Wes Bos tutorial. Now I understand a little more about how the dependancies work, where they are, and how to add them. I'm glad I took the time to figure this out because I understand these packages better. That will come in handy when I learn node which I'm going to do soon!

## Day 31, R2
### 5/11/19

- ## Getting ESLint to Work on HTML AGAIN

  I'm trying to figure out these npm packages. I can't get ESLint to lint the HTML in my `playing_with_javascript` directory.
  
  I tried adding configurations to the user settings instead of the `.eslintrc.json` file according to this tutorial: [Eslint setup in Visual Studio Code](https://youtu.be/o2H8kvuwMKE?t=344)
  
  I deleted all my files in `playing_with_javascript` related to node or eslint. I followed this video to install eslint: [Eslint setup in Visual Studio Code](https://youtu.be/o2H8kvuwMKE?t=344). I made sure my terminal was in my project directory.
  
  I got this notification in my terminal: ***"We recommend using this local copy instead of your globally-installed copy."*** How do I control which one my project uses? Not sure, but I can see that it's loading locally in the ESLint tab.
  
  ## ESLint HTML Plugin
  
  In my project directory I ran `npm install --save-dev eslint-plugin-html`, following: [How can I get ESLint to lint HTML files in VSCode?](https://stackoverflow.com/questions/54138689/how-can-i-get-eslint-to-lint-html-files-in-vscode/54138880#54138880)
  
  I added this to the `.eslintrc.json` file:
  ```javascript
  "plugins": [
    "html"
  ]
  ```
  
  I also ran `eslint --ext .html,.js playing_with_javascript` while in the `100daysofcode` directory:
  
  > Note: by default, when executing the eslint command on a directory, only .js files will be linted. You will have to specify extra extensions with the --ext option. Example: eslint --ext .html,.js src will lint both .html and .js files in the src directory. See ESLint documentation.
  
  -*from [BenoitZugmeyer/eslint-plugin-html](https://github.com/BenoitZugmeyer/eslint-plugin-html#usage)*
  
  ## It Works Now But...
  
  Ok I just realized it actually works. ESlint is linting HTMl files in `playing_with_javascript`. But I hadn't realized it was working for a while. I'm not sure for how long. So I'm not sure what I did that was necessary and what was unneccessary.
  
  ## Undoing Adding ESLint
  
  I'm going try to undo everything I did when trying to add ESLint and the html plugin. Then do it again so I can see when it actually starts linting the HTML.
  
  ## Uninstalling ESLint
  Following this: [Uninstalling packages and dependencies](https://docs.npmjs.com/uninstalling-packages-and-dependencies). 
  
  In my project directory, I ran `npm uninstall eslint` and it didn't look like it did anything. 
  
  So I also ran `npm uninstall --save eslint`. That didn't look like it did anything either because my `node_modules` folder, `.eslintrc.json` file, and package.json file were all still there. 
  
  But when I restarted VSC it wasn't loading ESlint anymore. I looked it my `package.json` file and I could see eslint wasn't there, just some of the plugins that go with eslint were there:
  
  ```javascript
  "devDependencies": {
    "eslint-config-airbnb-base": "^13.1.0",
    "eslint-plugin-html": "^5.0.3",
    "eslint-plugin-import": "^2.17.2"
  }
  ```
  
  And I no longer saw the `eslint` folder in `node_modules`. So I guess the command **did** remove ESLint, it just didn't get rid of npm. Maybe that seems like obvious behavior to most people, but I'm still trying to understand this all.
  
  ## Uninstalling NPM
  
  I couldm't find any information about removing npm locally through the terminal, except for this:
  
  > Local installs are completely contained within a project’s node_modules folder. Delete that folder, and everything is gone (unless a package’s install script is particularly ill-behaved).
  
  -*from [npm-removal Cleaning the Slate](https://docs.npmjs.com/misc/removing-npm.html)*
  
  It doesn't mention the `package.json` file or other files that were installed with npm. I'm just going to delete them.
  
  ## `--ext`
  
  The only thing I still have to undo is this command: `eslint --ext .html,.js playing_with_javascript`. But I'm not sure what it did? How to undo it? I could maybe set it back to just `.js`, like this: `eslint --ext .js playing_with_javascript` But I'm not sure if that would undo the command to lint html extensions. I really don't know what this command is changing? Is there a configuration somewhere?
  
  >My questions are:

  >I couldn't find the configuration option for doing this from .eslintrc.
  >
  >...
  >
  
  One of the answers:
  >You can’t define this in .eslintrc files because file traversal happens before the configuration is read
  [Configuration option for '--ext' switch #3469](https://github.com/eslint/eslint/issues/3469)
  
  So it's not in the  `.eslintrc.json` file. 
  
  I think if I just pass in .js, it will set it to only use .js extensions again because I found this:
  
  >Use only .js2 extension
  >eslint . --ext .js2
  
  -*from [Command Line Interface](https://eslint.org/docs/user-guide/command-line-interface#--ext)*
  
  I ran `eslint --ext .js playing_with_javascript`. I got an error:
  
  ![screenshot](log_imgs/error_5-11.PNG)
  
  This is confusing. If you can't define the extensions in the `.eslintrc` files, then why would it matter that there is no `.eslintrc` file? But maybe, even though the extenson configurations aren't stored there, you for some reason still need that file.
  
  ## Starting over
  
  I think everything is reset to how it was to begin with in my `playing_with_javascript` directory. So I started again.
  
  ## It worked!
  
  This is what I did:
  
  I ran these commands on the project directory and followed the prompts for each:
    
  `npm init`
  `eslint --init`
  
  I restarted VSC and ESLint now ***lints the HTML*** on the `playing_with_javascript` directory even though I did nothing else. Probably because I put this in the user settings for my workspace earlier:
 
  ```javascript
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "html"
  ],
  "eslint.options": {
    "plugins": [
      "html"
    ]
  },
  ```
  
  Normally the plugins can be put in the `.eslintrc.json` file. But when it's in the user settings in `"eslint.options"` it applies to the workspace.
  
  I'm not sure if `eslint --ext .html,.js playing_with_javascript` did anything earlier. 
  
  ## Summary
  
  So I did a lot of stuff I didn't need to do but I learned a lot in the process.
  
## Day 30, R2
### 5/10/19

- ## Helping
  Today I got to help someone who posted about a css issue on Twitter. I have yet to hear back if it was helpful. Hopefully it was.
  
  They were having trouble getting these inputs to vertically align:
  
  ![img](log_imgs/help_5-10.PNG)
  
  ### 1. To start, I added a border to all the divs to see better what was going on:
  
  ```css
  * {
  border: 1px solid red;
  }
  ```
  
  ### 3. I got rid of these extra divs:
  
  ![img](log_imgs/start_5-10.PNG)
  
  ![img](log_imgs/divs_5-10.PNG)
  
  ### That gave me these centered but misaligned inputs:
  
  ![img](log_imgs/centered_5-10.PNG)
  
  ### 4. I added a class to the labels so I could make their widths uniform to align everything:
  
  ![img](log_imgs/labelclass_5-10.PNG)
  
  ### 5. Added `text-align: right` to line up the colons.
  
  ![img](log_imgs/done_5-10.PNG)
  
- ## Prettier
  Now I need to figure out how to get prettier to work. I'm going to do some investigating to see how these extensions work.
  
  ## ESLint-plugin-html
  
  I have the plugin `eslint-plugin-html` locally and globally. I wasn't sure which I was using with my `perfect_fit_meal` project. To find out, I messed with the file name of my local plugin.
  
  <img src="log_imgs/name_5-10.PNG" width="300">
  
  When I restarted VSC it gave me this error:
  
  ![img](log_imgs/terminal_5-10.PNG)
  
  So now I know that my `esLint-plugin-html` is coming from the local directory.
  
  ## What about other project directories?
  
  I wonder how ESLint will work in other project directories? Where will it load from?
  
  I opened the directory for a project called `playing_with_javascript`, a project that didn't have ESLint installed locally to see what would happen. One thing to note is both these directories, `playing_with_javascript` and `perfect_fit_meal`, are in the same workspace. So I believe they share the same user settings.
  
  ## No Local ESLint? Load Globally
  
  This directory, `playing_with_javascript`, loaded ESLint from my global modules.
  
  ![img](log_imgs/noconfig_5-10.PNG)
  
  As you can see from the underlined error, it looks like your `.eslintrc.json` should in to your project directory even if there's no local ESLint.
  
  ## Adding Configs
  
  I copied the `.eslintrc.json` file from my `perfect_fit_meal` directory and pasted it in to `playing_with_javascript`. Now we can see it's using the config file to get the airbnb style guide, but it can't find the airbnb module.
  
  ![img](log_imgs/noairbrb_5-10.PNG)
  
  ## Adding `node_modules`
  
  To get the air bnb module into the project, I copied the `node_modules` directory from the `perfect_fit_meal` directory. I pasted it into the `playing_with_javascript` folder.
  
  Now `playing_with_javascript` loads the ESLint locally from the local `node_modules` folder instead of the global one. And it's gettting the airbnb module from there. We can tell that it's getting the airbnb module from there because that error went away after adding `node-modules`.
  
  ![img](log_imgs/local_5-10.PNG)
  
  But our html files aren't getting linted.
  
  ## Why Aren't HTML Files Getting Linted?
  
  I messed with the `eslint-plugin-html` directory name again to see if that would cause issues. It did. So I know the html plugin is being accessed. 
  
  ![img](log_imgs/failed_5-10.PNG)
  
  I changed the folder name back. The error went away. 
  
  But why isn't ESLint linting the html files in `playing_with_javascript`?
  
  This is where I left off. Confused still, but a little less so. So I'm stoked!
  
  
## Day 29, R2
### 5/9/19

- ## Recipe Calculator
  ## To Do
  - Set Up dotenv
  - lint my code
  - Look into Prettier vsc extension because [Jacob M-G Evans  ⚛ @JacobMGEvans](https://twitter.com/JacobMGEvans) said it goes well with ESLint (but what about Beautify?)
  
  ## Prettier
  I started to set up Prettier as a ESLint plugin following Wes Bos's tutorial.
  
  [How to Setup VS Code + Prettier + ESLint](https://www.youtube.com/watch?v=YIvjKId9m2c)
  
  ## Errors!
  Now my ESlint is underlining the wrong things. For example, it underlines `this.readyState` but when I hover over `this.readyState`, ESLint tells me what's wrong with a *different* part of my code.  I deleted everything I added to my settings and configurations and it works again. 
  
  It's probably not working because *Prettier* failed to load:
  
  Terminal:
  
  ```
  Failed to load plugin prettier: Cannot find module 'eslint-plugin-prettier'
  Happened while validating /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/index.html
  This can happen for a couple of reasons:
  1. The plugin name is spelled incorrectly in an ESLint configuration file (e.g. .eslintrc).
  2. If ESLint is installed globally, then make sure 'eslint-plugin-prettier' is installed globally as well.
  3. If ESLint is installed locally, then 'eslint-plugin-prettier' isn't installed correctly
  ```
  
  So these extra *Prettier* configurations are maybe throwing off my ESlint configs since Prettier isn't actually installing. I don't know but I want to get *Prettier* to work.
  
  ## Is My ESLint Installed Globally?
  
  Since these errors had to do with whether ESLint was installed locally or global, I had to figure that out.
  
  [How to tell if npm package was installed globally or locally](https://stackoverflow.com/questions/26104276/how-to-tell-if-npm-package-was-installed-globally-or-locally):  
  - `npm list -g`
  - `npm list -g --depth=0`
  
  ### My Global Packages:
  
  <img src="log_imgs/terminal_5-9.PNG" width="400"/>
  
  Looks like **it's installed globally.** 
  
  But, it's **also installed locally** since I can see the *ESlint* files in my project directory. That's probably causing issues.
  
  ## ESLint Button
  
  I figured out how to get that little "ESLint" button to show up in the corner:
  
  Put `"eslint.alwaysShowStatus": true` in your user settings in vsc.
  
  ![eslint_button](log_imgs/eslint_5-9.PNG)
  
  When I click on the ESLint status button button, a tab pops up that shows where my project is getting *ESLint* from:
  
  >[Info  - 14:55:45] ESLint server is running.
  >
  >[Info  - 14:55:45] ESLint library loaded from:
  >
  >/Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal/node_modules/eslint/lib/api.js
  
  So it looks like it's getting it locally. But I'm not sure. Maybe the global installation is interfering?
  
  Also I'm curious where it's getting the ESLint html plugin from, because I saw it both locally and globally. 
  
  I think there's problems with ESLint being local and global. 
  
  ## What To Do?
  
  ### Do I need to install the ESLint prettier plugin both locally *and* globally?
  
  or
  
  ### Do I need to uninstall either my global or local ESLint package so that I only have one package? And then get prettier to work for that?
  
  I'm nervous that if I delete either package, I'll break my `eslint_html_plugin` which took me a while to get to work.

  ## `.eslintrc.json`
  
  I wanted to see if I could find a `.eslintrc.json` file in the global installation of EsLint. To find the global directory:
  
  [Where does npm install packages](https://stackoverflow.com/questions/5926672/where-does-npm-install-packages):
  
  - `npm list -g`
  
  <img src="log_imgs/path_5-9.PNG" width="400"/>
  
  To see this file from the GUI (Finder) I followed this: [how to browse /usr/local directory in finder?](https://discussions.apple.com/thread/5418731)
  
  I didn't see `.eslintrc.json` file in the global eslint directory. So I'm not sure how to add Prettier globally and then how do you configure it? Or do you install it through the command line globally and then configure it locally? Do you just manually add the `.eslintrc.json` file to the global package? So confused.
  
  ## Should ESLint be Global or Local?
  
  > We generally recommend installing ESLint and dependencies locally. It makes for a more reliable experience and it's better for collaboration as well.

  *[Kevin Partington platinumazure](https://github.com/eslint/eslint/issues/10533)*

  >If you want to include ESLint as part of your project’s build system, we recommend installing it locally. 
  >...
  >
  >If you want to make ESLint available to tools that run across all of your projects, we recommend installing ESLint globally.
  
  [Getting Started with ESLint](https://eslint.org/docs/user-guide/getting-started)
  
  ## Uninstalling NPM Packages:
  
  I wanted to see how to uninstall ESlint. I found this:
  
  [Uninstalling packages and dependencies](https://docs.npmjs.com/uninstalling-packages-and-dependencies):
  
  - Unscoped packages: `npm uninstall <package_name>`
  - Scoped packages: `npm uninstall <@scope/package_name>`
  
  What does "scoped" mean? Here's the documentation for [npm-scope Scoped packages](https://docs.npmjs.com/misc/scope), but this is over my head. Is my ESLint scoped? I think not:
  
  > The scope folder (@myorg) is simply the name of the scope preceded by an @ symbol, and can contain any number of scoped packages.
  *[npm-scope Scoped packages](https://docs.npmjs.com/misc/scope)*
  
  ESlint isn't preceded by an **@** symbol *so I think it's **not** a scoped package.*
  
- ## Thoughts & Feelings:
  These packages keep running me into trouble. I don't really understand how they work. I'm not sure how to get more practice with them or what resources to use to understand them. I was watching an npm tutorial but I feel like it skipped a lot of information. Maybe I need to finish that tutorial. But then how to I get hands on practice/experience with these packages?

## Day 28, R2
### 5/8/19

- ## Recipe Calculator
  ## Custom Type Ahead
  
  I got the custom type-ahead to select the suggestion when it is either clicked or `enter` is pressed. 
  
  I changed around the event listeners:
  
  ```javascript
  foodInput.addEventListener('keyup', displaySavedFoods);
  form.addEventListener('keydown', formHandler);
  suggestions.addEventListener('mouseover', changeFocus);
  suggestions.addEventListener('click', searchSuggestedFood);
  ```
  Now, `changeFocus` is called on the `suggestions` list element, before it was called on `form`, which `suggestions` is a child of. I think it reads better.

  I also had to change the callback for `form.addEventListener('keydown',...` from `traverseFocus` to `formHandler`. This is because `form.addEventListener('keydown',...` now has two possible callbacks: `traverseFocus` or `searchSuggestedFood` depending on what key the user pressed.
  
  I also cleaned up irrelevent css and but my css in a separate file. 
  
  Thanks to [Philippe Vaillancourt
@snowfrogdev](https://twitter.com/snowfrogdev) and [Giuseppe 🇮🇹
@montyDev_](https://twitter.com/montyDev_) for the ideas to clean up the CSS and move the event listener to a different element.
  
  ## Added Documentation for Type-ahead Search
 
  I'm calling this a finished project! 
  
  It's just one part of my larger project, but I the search feature it might help others with their projects so I put it out with documentation.
  
  You can go to [Type-ahead Search](https://github.com/DashBarkHuss/type_ahead_search) to see the complete project, along with the documentation.
  
  ![screenrecording](log_imgs/ux_5-8.gif)

**Link To Work:** [Type-ahead Search](https://github.com/DashBarkHuss/type_ahead_search)

- ## Thoughts & Feelings:
  Lately I haven't had to take much breaks. For the most part, I've sped through my two hours of coding with no breaks. Maybe coding is getting more habitual, and my brain needs less breaks because coding is less effortful for me now. Maybe it's because I raised my calories and my brain has excess fuel? I hope it's not that, because that means when I do a cut, my brain will need more breaks.

## Day 27, R2
### 5/7/19

- ## Recipe Calculator
  ## Custom Type Ahead
  
  Today I created two event listeners that change the focus to different suggestions in the type-ahead feature.
  
  ```javascript
  form.addEventListener('keydown', traverseFocus);
  ```
  `traverseFocus()` traverses through the suggestions when you press the up or down arrow.
  
  ```javascript
  form.addEventListener('mouseover', changeFocus);
  ```
  
  `changeFocus()` changes the focus to whatever suggestion you mouseover.
  
  <img src="log_imgs/ui_5-7.gif" width="400">
  
  ## Focus
  
  I used the [`focus()` method](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/focus) to set the focus.
  
  I used the [.activeElement property](https://developer.mozilla.org/en-US/docs/Web/API/DocumentOrShadowRoot/activeElement) to find the last element that had focus in order to traverse the suggestions.
  
  ## To Do
  
  I still have to add functionality for when you select a suggestion.
  

**Link To Work:** [Type Ahead Search, not finished](https://github.com/DashBarkHuss/type_ahead_search/tree/5699e5a8a6580426cea92c5d07808d8bdd87a5b5)
  

## Day 26, R2
### 5/6/19

  
- ## Recipe Calculator
  ## Custom Type Ahead Conditionals
  I got my conditionals working. In "link to work."
  
  ## Functionality
  I started working on the functionality of the 'type ahead' feature. The up and down arrows should traverse the options and enter should select it. Mouse should work too. I'm not posting it cause it's a mess still. 
  
  This is going to be a short post today because I'm in a hurry to get to my host's house.
  
**Link To Work:** [Type Ahead Search, not finished](https://github.com/DashBarkHuss/type_ahead_search/tree/a74f0cfdf79e954a85ba00ee050fe57f4606ffd4)


## Day 25, R2
### 5/5/19

- ## Recipe Calculator
  Today we're moving the type ahead output from the console to the UI. This type ahead feature suggests foods to search form a list of saved foods in a json file.
  
  ## Custom Type Ahead UX
  
  I wasn't sure about the UX for the type ahead feature. Should choosing a suggested entry *search* that entry? Or should it *select* that entry and add it to the recipe? I decided to copy what the [USDA database](https://ndb.nal.usda.gov/ndb/search/list) does.
  
  ![usda](log_imgs/usda_5-5.gif)
  
  If you select the suggestion it searches the suggestion. It doesn't choose that entry, which on the USDA database would mean taking you directly to that entries nutrient page.
  
  
  ## Conditionals Not Right
  
  I need to redo my conditional statements so that the `#suggestions` div doesn't display anything when there's no input in the search field. This doesn't work quite right:
  
  ```javascript
  async function displaySavedFoods(){
  const foods = await fetch("saved_food_data.json").then(x=>x.json()).then(x=>x.foods);
  const searchTerm = foodInput.value;

  const filtered = filter(foods, searchTerm);
  const filteredChanged = filtered.length != lastFiltered.length;
  if (filteredChanged){
       const div = document.querySelector("#suggestions");
       div.innerHTML="";
       div.style.width = `${foodInput.offsetWidth}px`;
       if(searchTerm==""){
         lastFiltered="";
         return;
       } else {
         filtered.forEach(x=>div.innerHTML+=`<li>${x.name}</li>`);
         lastFiltered = filtered;
       }
     }
  }
  ```
  <img src="log_imgs/ui_5-5.gif" width="400">
  
  As you can see, even though I have no input in the text field at the end of this gif, the `#suggestions` div still displays.

**Link To Work:** [Type Ahead Search, not finished](https://github.com/DashBarkHuss/type_ahead_search/tree/644753d33806dd4994883e68d4177c2182a9be67)


## Day 24, R2
### 5/4/19

- ## Recipe Calculator
   May the 4th and day 24th be with you!
   
  ## Devtools Console + Sources
  
  To open the **console** and **sources** at the same time:
  
  Press `esc` while on the **Sources Panel**
  
  ![sources and console](log_imgs/console_sources_5-4.gif)
  
  ## Custom Type Ahead
  
  I got my custom type-ahead to pick the correct saved foods. But right now it just logs the results to the console. 
 
  ```javascript
  const form = document.querySelector("form[name=food_search]");
  foodInput = form.querySelector("#food_to_search"); //food search input
  let lastFiltered=[];
  
  async function displaySavedFoods(){
  const foods = await fetch("saved_food_data.json").then(x=>x.json()).then(x=>x.foods);
  const searchTerm = foodInput.value;
  const filtered = filter(foods, searchTerm);
  const filteredChanged = filtered.length != lastFiltered.length;
  if (filteredChanged){
    console.log("%cFiltered:", "color:red;font-size:20px;");
    filtered.forEach(x=>console.log(x.name));
    lastFiltered = filtered;
  }
  }

  function filter(foods, searchTerm){
    let filtered = foods;
    const terms = searchTerm.split(" ").map(x=>x.toLowerCase());
    for(i=0; i<terms.length; i++){
      filtered = filtered.filter(food=>food.name.toLowerCase().includes(terms[i]));
    }
    return filtered;
  }
  
  foodInput.addEventListener('keyup', displaySavedFoods);
  ```
  
  ![type-ahead](log_imgs/type_ahead_5-4.gif)
  
  I tried to use regex for this but had trouble. I think regex would improve the performance of the algorithm.

## Day 23, R2
### 5/3/19

- ## Async, Ajax, Promises
   Was confused why `getData()` was returning a promise when 'name' is not a promise. I did the same lines of code that are in my `getData()` function, in the console to compare what `name` returns in the console with what `getData()` returns.

  ![async](log_imgs/async-5-3.PNG)
  
  Oddly, you can only use `await` inside a function with the `async` keyword. So, I'm not sure how it's working in my console, but it is.
  
  ## Async Always Returns a Promise
  
  This is why `getData()` returns a promise:

  >The word “async” before a function means one simple thing: a function always returns a promise. Even If a function actually returns a non-promise value, prepending the function definition with the “async” keyword directs JavaScript to automatically wrap that value in a resolved promise.
  
  *[Async/await](https://javascript.info/async-await)*
  
  ## Loading in Parallel vs in Sequence
  
  In the [Fun Fun Function Async/Await video](https://youtu.be/568g8hxJJp4?t=991) the instructor says that in his async/await example the images are being loaded in *sequence* and in the promise example they are being loaded in *parallel*.
  
  I read a little more about that here: [JavaScript Async/Await: Serial, Parallel and Complex Flow](https://techbrij.com/javascript-async-await-parallel-sequence)
  
  Still not quite sure what that means, but I have more of a broad idea now.
  
- ## Recipe Calculator
  ## Custom Type Ahead
  
  I went back to my type-ahead problem for my recipe calculator. This is the one chrome does automatically. But I want my custom type-ahead to pull from a list of saved ingredients.
  
  ### Chrome's Type-Ahead
  <img src="log_imgs/type_ahead_5-3.PNG" width="500">
  
  I ended up using async/await for this. 
  
  I also realized that async/await can help with debugging because it's easier to debug with sequencial code. But I'm not sure if that really makes sense. 
  
  I didn't finish. I should start commiting my work again, but not today.  

## Day 22, R2
### 5/2/19

- ## Async, Ajax, Promises
  I read this article that I started yesterday:
  
  [Async, Callback & Promise](https://medium.com/front-end-weekly/ajax-async-callback-promise-e98f8074ebd7)
  
  It also talked about CORS and JSONP which I'm still new to.
  
  ## Async Call Values
  
  Yesterday I learned:
  
  > you cannot return from an asynchronous call inside a synchronous method.
  
  *[How To Return Value from an Asyncronous Callback Function](https://stackoverflow.com/questions/6847697/how-to-return-value-from-an-asynchronous-callback-function)*
  
  So today I redid my AJAX call. It pushes the data to an array instead of tryin to return the data.
  
  ![array](log_imgs/array_5-2.PNG)
  
  ## Redo Above With Promise:
  
  I redid the above with a promise.
  
  ![promise](log_imgs/promise_5-2.PNG)
  
  ## Async Await
  I went back to [this video by Fun Fun Function about async/await](https://www.youtube.com/watch?v=568g8hxJJp4) to learn about async/await now that I've played with promises more.
  
  I like this definition the instructor gives about async/await:
  
  ![async/await](log_imgs/async_await_5-2.PNG)
  
  I played with async/await a bit.

## Day 21, R2
### 5/1/19

- ## Promises
  
  I played with this function that returns a promise of an XMLHttpRequest.
  
  ```javasript
  const makeRequestPromise = (url) => {
    const request = new XMLHttpRequest();

    return new Promise((resolve, reject) => {
      request.onreadystatechange = () => {
        if (request.readyState !== 4) return;
        if (request.status >= 200 && request.status < 300) {
          resolve(request);
        } else {
          reject(new Error({
            status: request.status,
            statusText: request.statusText,
          }));
        }
      };
      request.open('GET', url, true);

      request.send();
    });
  };
  ```
  
  It helped me see how promises work and `.then()`
  
  ![promises](log_imgs/promise_5-1.PNG)
  
  ## Return Value Asyncronous Callback
  
  ![return](log_imgs/return_5-1.PNG)
  
  > you cannot return from an asynchronous call inside a synchronous method.
  
  *[How To Return Value from an Asyncronous Callback Function](https://stackoverflow.com/questions/6847697/how-to-return-value-from-an-asynchronous-callback-function)*
  
  ## Promises vs AJAX & Callbacks
  
  Still trying to sort these out. Here's some resources I'm looking at.
  
  >You are confused about promises and Ajax calls. They are kind of like apples and knives. You can cut an apple with knife and the knife is a tool that can be applied to an apple, but the two are very different things.
  >
  >Promises are a tool for managing asynchronous operations. They keep track of when asynchronous operations complete and what their results are and let you coordinate that completion and those results (including error conditions) with other code or other asynchronous operations. They aren't actually asynchronous operations in themselves. An Ajax call is a specific asynchronous operation that can be used with with a traditional callback interface or wrapped in a promise interface.

  *[What's the Difference Between Promise and Ajax](https://stackoverflow.com/questions/39751395/whats-the-difference-between-promise-and-ajax)*
  
  [Async, Callback & Promise](https://medium.com/front-end-weekly/ajax-async-callback-promise-e98f8074ebd7)
  
  

## Day 20, R2
### 4/30/19

- ## Fetch API

  ### Warning, I was confused during this word vomit:

  I was examing the the Fetch API and I wanted to know what `.json()` does. I couldn't find it in the Promise directory (`console.dir(Promise)`). I found out [.json()](https://developer.mozilla.org/en-US/docs/Web/API/Body/json) is a [method on the Body mixin](https://developer.mozilla.org/en-US/docs/Web/API/Body) of the Fetch API.

  ## Mixins
  >As defined in Wikipedia, a mixin is a class that contains methods for use by other classes without having to be the parent class of those other classes.
  
  *[Mixins](https://javascript.info/mixins)*
    
  ```javascript
  // mixin
  let sayHiMixin = {
    sayHi() {
      alert(`Hello ${this.name}`);
    },
    sayBye() {
      alert(`Bye ${this.name}`);
    }
  };

  // usage:
  class User {
    constructor(name) {
      this.name = name;
    }
  }

  // copy the methods
  Object.assign(User.prototype, sayHiMixin);

  // now User can say hi
  new User("Dude").sayHi(); // Hello Dude!
  ```
  
  In the example above, we see the mixin methods in the `Users` prototype.
  
  <img src="log_imgs/user_4-30.PNG" width="300">
  
  But I don't see that in the Promise directory.
  
  >The Body mixin of the Fetch API represents the body of the response/request...
  >
  >Body is implemented by both Request and Response
  
  *[Body, Mozilla Docs](https://developer.mozilla.org/en-US/docs/Web/API/Body)*
  
  ### Unconfused:
  
  **Oh duh**, it's on the ***Fetch API**, not a method on **Promise!*** I was confusing Promise with the Fetch API.
  
  [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API):
  
  > Fetch provides a generic definition of Request and Response objects (and other things involved with network requests).
  
  [Request](https://developer.mozilla.org/en-US/docs/Web/API/Request)
  
  [Response](https://developer.mozilla.org/en-US/docs/Web/API/Response)
  
  The [Body methods](https://developer.mozilla.org/en-US/docs/Web/API/Body#Methods) **are** in the Response directory for example. Same with Request.
  
  <img src="log_imgs/response_4-30.PNG" width="400">
  
  
  I'm less confused but still kind of confused with how all of these relate.
  
  >The fetch() method takes one mandatory argument, the path to the resource you want to fetch. It returns a Promise that resolves to the Response to that request, whether it is successful or not...
  > 
  >Once a Response is retrieved, there are a number of methods available to define what the body content is and how it should be handled (see Body).
  
  A little more clear.
  
  ## Promises
  
  >Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function.
  
  *[Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)*
  
  Theres an example on that page of a Promise with attached callbacks vs passing callbacks into a function.
  
  To understand the difference between Promises and regular XHR I looked at this [page on how to combine XHR and promises](https://gomakethings.com/promise-based-xhr/). I followed along and made this Promise based XHR. Then I made a regular XHR. Tomorrow, I'll play around with them.
  
- ## Thoughts and Feelings:
  Sometimes writing my thoughts out in my log can help me understand what I'm thinking and why I'm confused. 
  
  I need to remember that when I feel like I don't want to code because something is hard, that feeling will soon pass. And come again. And pass again.
  
## Day 19, R2
### 4/29/19

- ## Helping
  I helped someone today on twitter. They sent their code and I showed them what each line was doing and where they had a typo:
  
  **Typo:**
  <hr>
  <img src="log_imgs/typo_4-29.PNG" width="300">
  
  **Step Through:**
  <hr>
  <img src="log_imgs/help_4-29.PNG" width="600">
  

- ## Toggle Eslint
  I couldn't find a built-in way to do this but I found this [Setting Toggle extension by Ho-Wan](https://marketplace.visualstudio.com/items?itemName=Ho-Wan.setting-toggle).
  
  I set my user settings to toggle the `eslint.enable` setting.
  
  <img src="log_imgs/settings_4-29.PNG" width="500">
  
  Then I can press this button to turn Eslint on and off.
  
  <img src="log_imgs/toggle_4-29.PNG" width="500">
  
- ## What Happen To My Log
  
  I looked at my old log and the markdown is not rendering:
  
  https://github.com/DashBarkHuss/100-days-of-code/blob/master/r1-log.md
  
  <img src="log_imgs/log-29.PNG" width="500">
  
  It looks like I'm in edit mode but I'm not. What's up?
  
  Ok I don't know what happened, it's working again.
  
- ## Async/Await & Promises

  I ran into this [exact problem on stackoverflow](https://stackoverflow.com/questions/54082327/why-does-logging-the-result-of-fetch-break-it-body-stream-is-locked) with `fetch()`. I get this error when I try to `console.log` the promise: `Uncaught (in promise) TypeError: Failed to execute 'json' on 'Response': body stream is locked`
  
  The reason is because:
  
  >.json() (and .body(), .text()) may only be called once.
  >
  >The HTTP request is modeled as a stream, and you can't really read from a stream twice.

- ## Thoughts and Feelings:
  Coding was hard today because I was hungry and freezing in the super cold cafe.

## Day 18, R2
### 4/28/19

- ## NPM
  ## Lynda: Learning npm the Node Package Manager
  ### Notes:
  **--save-dev** is used to save the package for development purpose. 
  
  **Where global packages are stored on Mac** /user/local/lin/node_modules or /user/local/lin/node
  
  **-g or -glabal**: add to `npm install` command to install globally
  
  **How to resolve permissions errors**: [Resolving EACCES permissions errors when installing packages globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)

- ## ESLint
  ## ESLint on HTML!
  I decided to go back and try to get ESLint to work on HTML files. 
  
  I found this [stackoverflow thread](https://stackoverflow.com/questions/54138689/how-can-i-get-eslint-to-lint-html-files-in-vscode) on ESlint and HTML files.
  
  One of the answers says:
  >I have this in <projectfolder>/.vscode/settings.json
  >
  >{
  >  "eslint.validate": [ "javascript", "html" ]
  >}
  
  `.vscode` is in the directory for the workspace folder, *not* the project folder. That confused me! I found these settings in that file:
  
  ```javascript
  "eslint.validate": [
    "javascript",
    "javascriptreact"
  ]
  ```
  That file is **read-only** so I added this to the **user settings** panel.
  ```javascript
   "eslint.validate": [
        "javascript",
        "javascriptreact",
        "html"
      ]
  ```
  <img src="/log_imgs/settings_4-28.PNG" width="500" />
  
  ### Success! 
  
  <img src="/log_imgs/eslint_4-28.PNG" width="500" />
  
  Glorious red lines!
  
  ## Format in VSC
  
  <img src="/log_imgs/format_4-28.PNG" width="500" />
  
  ## AirBnb Style Guide
  
  I setup my EsLint to use the [AirBnb style guide](https://github.com/airbnb/javascript).
  
  ### Format Tabs
  AirBnb format uses 2 spaces for tabs so I changed my user settings so that tab is 2 spaces not 4. 
  
  [How to customize the tab-to-space conversion factor when using Visual Studio Code?](https://stackoverflow.com/questions/29972396/how-to-customize-the-tab-to-space-conversion-factor-when-using-visual-studio-cod)
  
  ### Functions
  
  I'm noticing that the airbnb style guide has some rules about naming functions. The style guide explains why [here](https://github.com/airbnb/javascript#functions) and [here it talks about arrow functions](https://github.com/airbnb/javascript#arrow-functions).
  
  ## Linting Is FUN!
  Maybe not fun, but this is really helpful! I'm always wondering "How should I best organize my code?" and "How can I make my code more readable?" Linting is like having a teacher over your shoulder telling you what to do and not to do. And then I can look up why in the [AirBnb style guide](https://github.com/airbnb/javascript). This is great! I need to thank that guy from the meetup in Austin!

  ## ESLint Toggle?
  If I want to temporarily toggle off the markings from ESlint; is there a way to do this **quickly**?
  
  I've seen a little ESLint button on the status bar of VSC in other people's setups. But it's not showing up on mine. I wonder if you can toggle ESLint on and off with this.
  
  ### My Status Bar
  <hr>
  <img src="/log_imgs/mineVSC_4-28.PNG" width="500" />
  
  ### Others' Status Bars
  <hr>
  <img src="/log_imgs/othersVSC_4-28.PNG" width="500" />
  
  Couldn't find anything about this in all my searches.
  
## Day 17, R2
### 4/27/19

I decided to look into npm today because I didn't know what I was doing yesterday trying to get ESLint to work. I'll probably be using npm a lot more. Getting more comfortable with npm will help prepare me for learning node.

- ## NPM
  Looked through some of this: [A Beginner’s Guide to npm — the Node Package Manager](https://www.sitepoint.com/beginners-guide-node-package-manager/)

  Watched some of this short a lynda video on package management: [Package Management Basics](https://www.lynda.com/Linux-tutorials/Package-management-Basics/618702/772939-4.html)
  
  Started watching the [Learning npm the Node Package Manager](https://www.lynda.com/Node-js-tutorials/Learning-npm-Node-Package-Manager-2018/761956-2.html) course on lynda.
   
  ## Lynda: Learning npm the Node Package Manager
  ### Notes:

  **package.json:** map for building your project and setting your dependencies.

  **npm init:** base command to initialize a new package.json file.

  **`Cmd` + `Shift` + `.` (dot):** toggle hide/show hidden files

  **locally installed:** When a package is installed locally it's installed on your projects directory.
  
  **globally installed:** When a package is installed globally it will be installed in your system available to all projects.
  
  ## Command Prompt Undo?
  
  I came accross this dilemma and posted it on [stackoverflow](https://stackoverflow.com/questions/55883264/is-it-possible-to-go-back-and-change-the-last-input-you-entered-into-a-command-p)
  
  <img src="log_imgs/npm_4-27.PNG"  width="600"/>

  ## JavaScript Modules: ES6 Import and Export
  The instructor in the lynda tutorial used `import`. I've seen this before but I've never used it.
  
  Here's the [`import` docs page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import).
  
  Here's a video on `import` and `export` that I didn't yet finish: [JavaScript Modules: ES6 Import and Export](https://www.youtube.com/watch?v=_3oSWwapPKQ).


## Day 16, R2
### 4/26/19
- ## Recipe Calculator
  ## Async/Await & Promises
  
  I played around with fetch and promises.
  
  I reviewed this video on promises: [Promises - Part 8 of Functional Programming in JavaScript](https://www.youtube.com/watch?v=2d7s3spWAzo)
  
  Then I started to watch this video on async/await: [async / await in JavaScript - What, Why and How - Fun Fun Function](https://www.youtube.com/watch?v=568g8hxJJp4)
  
  ## VSC Extensions
  In the async await video the instructor uses a cool inline evaluation tool called [Quokka](https://quokkajs.com/). I wanted to use it too but after downloading it following the [Quokka documentation](https://quokkajs.com/docs/) and the [Manage Extensions in Visual Studio Code](https://code.visualstudio.com/docs/editor/extension-gallery) page, I realized that to do what the teacher is doing I need the pro version. So forget quokka.
  
  ## ESLint
  
  I also added the ESLint extension and the Beautify extension.
  
  To set up ESLint I followed this: [Eslint setup in Visual Studio Code](https://www.youtube.com/watch?v=o2H8kvuwMKE). The process was a little different for me, so the video might be a little out of date. 
  
  ## ESLint on HTML Files
  I realized ESLint doesn't work on javascript sections on HTML files. It only works on .js files. However, you can add the [eslint-plugin-html](https://github.com/BenoitZugmeyer/eslint-plugin-html) to get ESLint to work on html files.
  
  ## Not Working on HTML Files
  I'm having trouble getting this to work. I'm not sure what this means, in the [docs](https://github.com/BenoitZugmeyer/eslint-plugin-html)
  
  > Note: by default, when executing the eslint command on a directory, only .js files will be linted. You will have to specify extra extensions with the --ext option. Example: eslint --ext .html,.js src will lint both .html and .js files in the src directory.
  
  I'm not sure what the `src` file should be in `eslint --ext .html,.js src`. I tried a path that goes out of my currect directory and back in like this:
  
  `perfect_fit_meal Dashie$ eslint --ext .html,.js ../perfect_fit_meal`
  
  But that didn't work. Now sure what to put there.
  
  I tried going out of the directory and then using the full path:
  
  `Fri Apr 26 ~ Dashie$ eslint --ext .html,.js /Users/dashiellbark-huss/Documents/100daysofcode/perfect_fit_meal`
  
  That didn't work. I tried it again after installing the extension glolablly and that still didn't work.
  
## Cows Showed Up While I Was Coding
  
![cows](log_imgs/cows_4-26.jpg)

## Day 15, R2
### 4/25/19
- ## Recipe Calculator
  
  ## #100DaysOfMath
  In addition to the coding, I added 30 minutes of math study to complement #100daysofcode. I need some math skills for this app. I need to understand a math subject called *optimization*. 
  
  I talked to a twitter peer, Ross Mason, who said he under estimated the amount of math he needs for AI. Since I want to learn AI, I figured I'd start now brushing up on my math.
  
  So I'm doing a mini, not-so-serious, #100DaysOfMath. By not-so-serious I mean I probably won't post about it and I might skip days. It depends on what seems to be a priority on that day. I don't want to take on too much extra study, and then fall behind on what's really important.
  
  ## Scrollbar Size
  
  I figured out how to change the scroll bar size, add bottom `margin` to the `-webkit-scrollbar-track`. I added a top margin too because I thought it looked better. 
  
  ```css
  #search_results_wrapper::-webkit-scrollbar-track {
      margin: 4% 0 var(--add-button-height);
  }
  ```
  
  <img src="log_imgs/scroll_4-25.gif"  width="300"/>
  
  ## Promises & Fetch
  
  I worked on changing my `XMLHttpRequest`s to `fetch()` calls so I can work with promises. I also want to have a pedictive type ahead feature in my search bar like Wes Bos does in [Javascript30](https://courses.wesbos.com/account/access/5c51dab432bb6d664e015352/view/194130156). The problem is I don't think I can do one request for all food names and then just filter throught them, like Wes does. The NDB limits the number of items in a single request. Maybe there is a work around.

## Day 14, R2
### 4/24/19

- ## Recipe Calculator
  ## Overriding User Agent Stylesheet Issue

  <img src="log_imgs/override_4-24.PNG"  width="600"/>
  
  Both of these pages show a workaround, but I didn't find an explanation for why this happens:
  - https://css-tricks.com/snippets/css/change-autocomplete-styles-webkit-browsers/
  - https://mariusschulz.com/blog/how-to-remove-webkits-banana-yellow-autofill-background
  
  ### Workaround:
  
  <img src="log_imgs/overridegood_4-24.PNG"  width="600"/>
  
  Now it's working in my app!
  
  <img src="log_imgs/uiselected_4-24.PNG"  width="300"/>
  
  ## Scroll Bar
  
  I ended trying to add a scrollbar to the box that contains food search results. This way the user knows they can scroll.
  
  Depending on the browser window size, the user may not realize they can scroll:
  - Obvious Scroll:
     - <img src="log_imgs/scrollclear_4-24.PNG"  width="300"/>
  
  - Unclear Scroll:
    - <img src="log_imgs/scrollunclear_4-24.PNG"  width="300"/>
  
  I found [this tutorial](https://scotch.io/tutorials/customize-the-browsers-scrollbar-with-css) which helped me add a scroll bar. 
  
  ### Scrollbar Size
  Now I want to change the size of the scrollbar and scrollbar thumb. I think it might have something to do with `webkit-scrollbar-thumb`.
  
  This might help: https://stackoverflow.com/questions/26493446/change-size-of-scrollbar-thumb-with-css.
  
## Day 13, R2
### 4/23/19

- ## Recipe Calculator
  ## Wrapper Vs Container:
  
  
  >In programming languages the word container is generally used for structures that can contain more than one element.
  >
  >A wrapper instead is something that wraps around a single object to provide more functionalities and interfaces to it.
  
  *[CSS Language Speak: Container vs Wrapper?](https://stackoverflow.com/questions/4059163/css-language-speak-container-vs-wrapper)*
  
  ## Overriding User Agent Stylesheet Issue
  
  I ended with this issue. I'm having trouble over riding the `user agent stylesheet`.
  
  ![screenshot](log_imgs/override_4-23.PNG)
  
  ## Today's End Result
  
  <img src="log_imgs/ui_4-23.gif"  width="300"/>

## Day 12, R2
### 4/22/19

- ## Recipe Calculator
  ## Relative Position & Border Radius
  
  If you have a relative div inside an unpositioned div with rounded corners, you have to add positioning to the container div and z-index.
  
  ### Bad
  <img src="log_imgs/cornersbad_4-22.PNG"  width="300"/>
  
  ```css
  #container{
      border: 5px solid green;
      border-radius: 20px;
      height: 200px;
      overflow: scroll;
  }

  .rectangle{
      height: 60px;;
      background: rgb(31, 255, 31);
      border: 3px solid rgb(255, 255, 255);
      position: relative;
  }
  ```
  
  ### Good
  <img src="log_imgs/cornersgood_4-22.PNG"  width="300"/>
  
  ```css
  #container{
      border: 5px solid green;
      border-radius: 20px;
      height: 200px;
      overflow: scroll;
      position: relative; //________________added
      z-index: 0; //________________________added
  }

  .rectangle{
      height: 60px;;
      background: rgb(31, 255, 31);
      border: 3px solid rgb(255, 255, 255);
      position: relative;
  }
  ```
  ## Absolute Positioned Element in Front of Scroll
  
  This was hard to figure out. Finally got it.
  
  <img src="log_imgs/scroll_4-22.PNG"  width="300"/>
  
  ```css
    #big_container{
      border: 5px solid green;
      border-radius: 20px;
      height: 200px;
      overflow: hidden;
      position: relative;
      z-index: 0;

  }
  #container{
      overflow: scroll;
      position: relative;
      height: 100%;
  }

  .rectangle{
      height: 60px;;
      background: rgb(31, 255, 31);
      border: 3px solid rgb(255, 255, 255);
      position: relative;
  }
  .red{
      background: rgb(255, 31, 199);
      border: none;
      height: 40px;
      position: absolute;
      width: 100%;
      bottom: 0;
  }
  ```
  
  ```html
  <div id="big_container">
      <div id="container">
          <div class="rectangle"></div>
          <div class="rectangle"></div>
          <div class="rectangle"></div>
          <div class="rectangle"></div>
          <div class="rectangle"></div>
      </div>
      <div class="rectangle red"></div>
  </div>
  ```
  ### Push The Last Item Up
  I realized that when you scroll to the bottom the pink element is still covering part of the last item, so I added this css to push the last item up:
  
  ```css
  #container>.rectangle:last-child{
      margin-bottom: 40px;
  }
  ```
  
  ## Form Attribute
  In HTML5, you can use the form attribute to have a form submit button element outside of the respective form element:
  https://stackoverflow.com/questions/6644128/html-input-field-outside-of-form
  
  ## Coded While Driving Through a Dust Storm! 
  <img src="log_imgs/dust_4-22.gif"  width="600"/>

## Day 11, R2
### 4/21/19

- ## Recipe Calculator
  ## Shadow Color
  
  Originally I had a dark green color that matched the hue of the main background color but was a darker green.
  
  ```css
  --shadow: 0px 010px 8px rgb(7, 161, 136);
  --main-hue: rgb(5, 219, 184);
  ```
  
  This colored shadow caused issues. I couldn't use this shadow on other background colors. You don't naturally see dark green shadows on a white background, for example. Thar color of a shadow should change if the background is a gradient of two different colors.
  
  Colored shadows are limited. This green shadow works well on the green side of the gradient, but not the blue.
  
  <img src="log_imgs/greenshadow_4-21.PNG"  width="300"/>
  
  Black shadows with low opacity work on all colors.
  
  <img src="log_imgs/greyshadow_4-21.PNG"  width="300"/>  
  
  So I changed the shadow to black with a very low opacity.
  
  ```css
  --shadow: 0px 010px 8px rgba(0, 0, 0, 0.26);
  ```
  
  Now this shadow will work on any color.
  
  ## White Gap
  
  If you zoom in very close, you can see a white gap between a container that has a border, and the content inside that has a background color.
  
  ```html
  <style>
      #container{
          border: 5px solid green;
          border-radius: 
      }
      #content{
          background: green;
      }
  </style>
  <div id="container">
    <div id="content">
        some content
    </div>
  </div>
  ```
  <img src="log_imgs/whitegap_4-21.PNG"  width="300"/>
  
  You can't see it when zoomed out.
  
  <img src="log_imgs/nogap_4-21.PNG"  width="300"/>
  
  However you can see it in the corners when the corners of the divs are rounded.
  
  <img src="log_imgs/round_4-21.PNG"  width="300"/>
  
  ```html
  <style>
        #container{
            border: 5px solid green;
            border-radius: 20px;
        }
        #content{
            background: green;
            border-radius: 15px; //takes into account 5px border
        }
  </style>
  </head>
  <body>
  <div id="container">
    <div id="content">
        some content
    </div>
  </div>
  ```
  
  ### My solution: 
  Instead of giving the content div a border radius, give the container div an `overflow` of `hidden` or `scroll`. 
  
  ## To Do
  I left off with an issue where the content div is not contained in the container div even with the container is set to `overflow: scroll`. This only happens when the user hovers over the content div which changes the background color.
  
- ## Thoughts and Feelings:
  My log is taking up a lot of my time. I'm not sure if anyone reads it, and I'm not sure how much of it is for me. I think I will cut down on logging. I need to only post the things that will help me, like links that will be helpful later or explanations of concepts I have trouble with and need to remember. 
  
  It might be hard to see when a concept should be logged or not. I probably need a lot less words and explanation than I post now, if I'm going to just log to help myself.
  
  I think it's especially important that I cut down on logging while traveling. My internet & power is limited. I want to learn as much as I can without worrying as much about my log. My log should be a tool to help me, not something that holds me back and takes up my time. Right now it can take longer than an hour just for my log.
  
  I took a break from logging while at Big Bend because there wasn't enough reception out there. I found I got a lot done.



## Day 10, R2
### 4/20/19

  I didn't have internet on this day until the end of the day so my log is sparse.
  
- ## Recipe Calculator
  I worked on css. 
  
  Weird space only appears at difference levels of zoomed in.
  
  <img src="log_imgs/space_4-20.PNG"  width="300"/>
  
  Video of my custom radio inputs:
  
  <img src="log_imgs/ui_4-20.gif"  width="300"/>


## Day 9, R2
### 4/19/19

  I didn't have internet on this day. I'm writing this on 4/20/19.
  
- ## Recipe Calculator
  I worked on css. 
  
  I learned that the `body` in HTML doesn't start until the first element starts. So if the first element is pushed down it will push the body down from the top of the window too. 
  
  Used `::before` and `:last-of-type`.
  
  <img src="log_imgs/ui_4-19.PNG"  width="300"/>

## Day 8, R2
### 4/18/19

  I didn't have internet on this day. I'm writing this on 4/20/19.
  
- ## Recipe Calculator
  I worked on css. 
  <img src="log_imgs/ui_4-18.PNG"  width="300"/>

## Day 7, R2
### 4/17/19
  
  I didn't have internet on this day. I'm writing this on 4/20/19.
  
 - ## Recipe Calculator
   I worked on css. 
   
   I worked with css variables.
   
  ```javascript
  :root { //declare variables
    --accent-color: rgb(0, 196, 163);
    --text-color:rgb(2, 90, 75);
    --text-highlight: rgb(227, 255, 247);
    --border-radius: 20px;
    --shadow: 0px 010px 8px rgb(7, 161, 136);
    --white-shadow: 0px 010px 8px rgba(115, 177, 161, 0.473);
    --main-hue: rgb(5, 219, 184);
    --second-hue: rgb(5, 219, 155);
    --button-font-size: 1.1rem;
  }
  
  form[name=search_results] input:hover{  //use variables
      background: var(--text-highlight);
  }

  ```
  <img src="log_imgs/ui_4-17.PNG"  width="300"/>

## Day 6, R2
### 4/16/19

  ## Coding With No Internet
  I'm going to Big Bend National Park for a few days. There's a big chance we won't get service out there. So I won't be logging or posting starting in two days or tomorrow. Not sure when our service will cut out. 
  
  To prepare for offline coding I'm downloading the documentation I normally use and w3schools.
  
  ## Offline Documentation
  
  ### JS, CSS, HTML, SVG
  I'm downloading documentation for Javascript, HTML, CSS, and SVG through [Dash](https://kapeli.com/dash). You can download the documentation directly [here](https://kapeli.com/mdn_offline]) but Dash helps with searching through the documentation.
  
  ### W3Schools
  I'm also [downloading W3Schools](http://www.mediafire.com/file/wyhv2wik6ttwfz8/www.w3schools.com.rar). This w3schools is from 2016, so there's a probably a good amount out of date. This one [on micrsoft](https://www.microsoft.com/en-us/p/w3schools-offline-version/9nblggh5792k?activetab=pivot%3Aoverviewtab) might be more recent, but I can't access it because of a login issue but you might be able to. I tried a bunch of other links and they were all a bust.
  
  If you need to search W3schools while offline, search while in the *www.w3schools.com* folder on your computer while "search www.w3schools.com" is selected and only search for html documents.
  
  <img src="log_imgs/search_4-16.PNG"  width="750"/>
  
  
- ## Recipe Calculator
 
  Our internet is already going in and out as we're drving through Texas. I've already used my offline resources successfully. 
   
  I'm working on the design for the recipe calculator.
  
  I ended with this design in the browser using DevTools. I wonder if there's a way to easily see all the changes I made to the css in DevTools that I added to "element.style" for a bunch of different elemets. I wasn't able to find them and save these changes. But it will be easy to recreate.
   
  <img src="log_imgs/ui_4-16.PNG"  width="300"/>
  
  ## Saving CSS From DevTools
  
  I didn't yet try this but this looks helpful:
  
  - [Save your CSS changes right in the Google Chrome inspector](https://rafaltomal.com/tips/save-css-chrome-inspector/)

## Day 5, R2
### 4/15/19

- ## Recipe Calculator
  
  ## EMathHelp Might Not Help
  
  I thought [eMathHelp](eMathHelp](https://www.emathhelp.net/calculators/algebra-2/system-of-linear-equations-calculator/)) was gonna help me figure this out, but it only works when the number of variables is the same as the number of equations. 
  
  The number of equations corresponds to the number of nutrients I'm tracking(fat, carbs, protein, etc) and the number of variables corresponds to the number of ingredients(brocolli, beef, whatever you like). Obviously, we're not going to limit the number of ingredients just because we only want to track 3 nutrients.
  
  The fact that the site can't calculate this makes me wonder if it's really complicated to solve what I'm trying to solve. Otherwise, they'd probably program it to work. I'm guessing we can't follow the steps thay take.
  
  ## Back To Asking For Help
  
  Well, I hit a wall but I've learned a bit more. Time to update my posts and get some help.
  
  ### Updated Simbi & Quora Post
  
  I rewrote my question on [simbi](https://simbi.com/dashiell-bark-huss/math-help).
   
  I also posted it on [quora](https://www.quora.com/unanswered/How-can-I-find-the-closest-possible-positive-values-to-solve-a-system-of-equations-for-many-variables-and-equations). Details in comments.
  
 
  ### Email
  I also emailed my mother in law's friend who is a math professor who I already was in contact with:
  
  >Hey Joanne,
  >
  >Here's my updated question on Simbi with the new knowledge I've acquired: https://simbi.com/dashiell-bark-huss/math-help.
  >
  >To summarize: How can I find the closest possible positive values to solve a system of equations for many variables and equations?
  >
  >Context, I've had very little math experience in the last 10 years. I'm trying to write a program that uses this math. 
  >
  >Any thoughts are appreciated.
  >
  >-Dash 
  
  I was trying to be succinct but polite. Hopefully these emails and questions will help you by giving you an example of how you might ask a question which is why I'm including them in my coding blog.
  
  ## Where Now?
  
  I'm already getting some answers back and this looks majorly complicated. Maybe I should have clarified that I haven't done any math in ten years. I'm considering partnering with a math person for this project. What do you do when you need help? 
  
  - When should you outsource?
    - pay someone? 
    - get free help?
    - partner with someone?
    
  - When should you learn the subject? 
  
  If it's hard, it's worth doing, right? Whatever means it takes.
  
  I'm gonna take a break and work on css or something fun and cute. 
  
  ## CSS
  I played around with css for the last half hour of my two hour session. I looked at code pen for ideas.
  
  ## Search Bar
  I changed my search and input so it's cuter.
  
  ### Before:
  <img src="log_imgs/search_4-15.PNG"  width="200"/>
  
  ### After:
  <img src="log_imgs/searchcss_4-15.PNG"  width="200"/>
  
  ## Get Rid Of The Space Between Text Input and Submit
  
  Here's some [tricks for getting rid of the space](https://css-tricks.com/fighting-the-space-between-inline-block-elements/) between inline block elements. I guess inputs have an inline-block display by default, but I'm not sure how to check what they default to. For mine, I just got rid of the space in my html even though I don't like the look in the html.
  
  ## Dev Tools CSS Tricks
  
  Sometimes I forget how to write css selectors. If you inspect an element you can see that selector here:
  
  <img src="log_imgs/selector_4-15.PNG"  width="300"/>
  
  And you can add css in the browser on that selector if you add the selector on devtools here on the styles panel:
  
  <img src="log_imgs/addselector_4-15.PNG"  width="300"/>
  
  You can also add a class if you click the .cls button.
 
  

## Day 4, R2
### 4/14/19

- ## Recipe Calculator

  I have been thinking about this math problem nonstop. I seriously dreamt about it all night!
  
  ### Here's the progress I made yesterday:
  
  Yesterday I called my friend [Shaily Hakimian](https://twitter.com/hakimian45) who is a math tutor. Shaily said we should brainstorm on bitpaper.io a whiteboard site. [Jerami](https://twitter.com/CodeAndLonely) has been helping too and joined the whiteboard.
  
  <img src="log_imgs/bitpaper_4-14.PNG"  width="500"/>
  
  Talking it out and trying to explain the problem to Shaily and Jerami helped me ***abstract my problem into an equation.***

  I then posted the problem on [Simbi](https://simbi.com/dashiell-bark-huss/math-help)
  
  > Hey I’m looking for help with a math problem. I have no clue what kind of math this problem uses. I don’t want the answer alone, I want to know how it’s solved or any information on how it might be solved. Ultimately I’m trying to figure out the general algorithm to solve issues like these.
  >
  >Problem:
  >
  >10≈1x+7y 
  >
  >6 ≈ 2x+1y 
  >
  >15≈5x+2y
  >
  >How can we solve for x and y so that the values on the right equal as close as possible to the values on the left. These equations all live in the same world, x is the same in all of them and so is y.
  >
  >Ex: 
  >If X=3 and y =1 the difference between our left side and and right side is an absolute value of 3.
  >
  >10≈10_________+0 
  >
  >6 ≈ 7 __________+1 
  >
  >15≈17 _________+2 
  >
  >—————————— 
  >
  >Total difference: 3
  >
  >But are there values for x and y that would give a smaller total difference? How can we solve this algorithmically?
  >
  >I’d also like to be able to extend this problem to more variables. ex:
  >
  >10≈1x+7y +6z 
  >
  >6 ≈ 2x+1y +12z 
  >
  >15≈5x+2y +3z
  >
  >A concrete example:
  >
  >If I have apples, chicken, and butter and I want to eat 20g of fat, 22g of protein, and 10g of carbs, how much of each food should I eat to get as close as possible to my desired macronutrients?
  >
  >Per 100g 
  >
  >Apple: fat: 0g protein: 1g carbs: 16g 
  >
  >Chicken: fat: 4g protein: 20g carbs: 0g 
  >
  >Butter: fat: 100g protein: 0 carbs: 0g
  >
  >Fat 20 ≈ 0a + 4c + 100b 
  >
  >Protein 22 ≈ 1a + 20c + 0b 
  >
  >Carbs 10 ≈ 16a + 0c + 0b
  >
  >a= Amount of apple (1=100grams of apple) 
  >
  >c= Amount of chicken 
  >
  >b= Amount of butter
    
  ## System of Equations
  
  I sent my simbi post to my friend Sean. **That's when I got a break through!**

  Sean said he knew what this problem was: *a system of equations*.
  
  I finally had *something* to google. This helped me tremendously. 
  
  ## Solving System of Equations With Matrices
  
  Sean said watch this video to learn how to solve the problem: [Matrices to solve a system of equations](https://www.youtube.com/watch?v=AUqeb9Z3y3k&fbclid=IwAR2SaAZPtdZZmbSFi8QWkIne989Z_-kPWa8H4tG0un9tDDkoG9Z18Wdb5NI)
  
  So I solved it on paper and it worked. 
  
  <img src="log_imgs/mathpaper_4-14.PNG"  width="400"/>

  Getting closer!
  
  ## What About For More Variables(Ingredients) and More Equations(Nutrients)?
  
  It took me a while, but I finally found a calculator that can solve systems of equations with more than 2 variables and 2 equations. [eMathHelp](https://www.emathhelp.net/calculators/algebra-2/system-of-linear-equations-calculator/)! 
  
  EMathHelp also shows the ***steps you need to take.*** Knowing the steps will be important because we'll need to **translate those steps to code.**
  
  I tested a bunch of sites with these 3 equations since I know the answer here should be **1** for every variable. **b=1, a=1, g=1**
 
  - 25b+3a+0g=28 
  - 0b+10a+0g=10 
  - 15b+1a+100g=116 
  
  All amounts should equal 1. A lot of sites couldn't figure it out. I don't know why. But [eMathHelp](https://www.emathhelp.net/calculators/algebra-2/system-of-linear-equations-calculator/) worked.

  ## Testing With EMathHelp
  
  Let's say we want these foods:
  
  *Grams per 100 gram measurements:*
  - Apple : { protein: 3, carbs: 10, fat: 1 }
  - Beef: { protein: 25, carbs: 0, fat: 15 } 
  - Ghee: { protein: 1, carbs: 2g, fat: 100 }
  
  *(nutrient measurements fudged)*
  
  And we want these total nutrients:
  
  Protein: 20, Carbs: 7, Fat: 20
  
  ### That gives us these eqautions:
  
  - 3a+25b+1g=20 *(total protein)*

  - 10a+b+2g=7 *(total carbs)*

  - 1a+15b+100g=20 *(total Fat)

  We need to solve for ***a, b, g***

  [Here's the solution using emathhelp with steps](https://www.emathhelp.net/calculators/algebra-2/system-of-linear-equations-calculator/?s=3a%2B25b%2B1g%3D20%2C++10a%2Bb%2B2g%3D7%2C++1a%2B15b%2B100g%3D20&v=&method=j&steps=on)
  
  Answer: a=7151171≈**0.610589239965841**, b=8471171≈**0.72331340734415**,  g=1001171≈**0.085397096498719**
  - 61g of apple
  - 72g of beef 
  - 8.5 grams of ghee
  

  ## What Could Go Wrong?
  
  Next I need to do this all in code. But I wonder:
  
  - What if there are no exact answers? 
    - How can we find the closest answer?
  - What if the answers are negative? 
    - How can we find the POSITIVE closest answer? You can't have a negative food, unless maybe you vomit it up, but that's a different app.
  - What if the answer is too small? Probably round??
  
- ## Thoughts and Feelings:

  I spent so much time on the math of this problem and hardly any coding. I guess that's part of coding when you get into making useful stuff, you'll need to learn other things. This would be a good time to have a math consultant. Is that a thing? I must be because what else do math people do?
 
  I went to a crowded coffee shop today. It forced me to sit with strangers. The strangers happened to be developers! What a cool coincidence! They were fun to talk to. Their names are Michael and Dan. 
 
  Here's a cool [project Dan made](https://helveticascenario.dev/mandlebrot). Click-drag to zoom in, right click to zoom out.
 
  They're working on a productivity app together. They talked to me about the pros and con of living in Austin vs. the bay area. Basically, you can get ahead in the bay area, but it's a bit a soul sucking and people are unaware of how the world works because they're stuck in tech world where smart-toilets are a good idea. Like L.A. but for tech.



## Day 3, R2
### 4/13/19

I went to a meetup today that had a lot of coders. This guy Joe was talking me up the wazoo so I didn't get a lot done. His favorite saying was "Too make a short story long". But he was cool and gave me some good advice. 
  
Joe told me to reexamine how deeply I want to go into a subject as opposed to using a framework. I have been doing a lot of vanilla JavaScript. Maybe it's time to try react soon?
  
For more on this conundrum Joe recommended listening to this podcast:
 - [Episode #205: Beginners and Experts Panel](https://talkpython.fm/episodes/show/205/beginners-and-experts-panel)
 
His general advice for picking a tech podcast to listen too was to find some old dude who's been around the block but isn't yet bitter. I think that's good advice.

He also said to start working with a linter because it makes it easy for others to read your code. Uniformity.
  
  
- ## Recipe Calculator

  I basically am thinking through the problem from yesterday both on code and on paper. I think I'm closer. But I am so far from an answer. I'm gonna leave my log short today because I've just done a ton of brain storming and working through this problem. So not much concrete to post about. And because I was delayed from all the meetup shmoozing. See you tomorrow.
  

## Day 2, R2
### 4/12/19

- ## Recipe Calculator

  ## How To Find The Right Combination of Ingredients?
  
  I'm trying to figure out how to find how much of each ingredient I need given a certain amount of nutrient-totals the user wants to reach. 
  
  I thought the answer would be complicated and I would need to find some complex algorithm. But my very helpful twitter peer [Khawar Jatoi](https://twitter.com/khawar_jatoi) said that an algorithm isn't necesary. He said, think about iterations and things you already know. I decided to give it a shot. Heads up, I didn't get the answer yet and I'm probably doing a bunch of things worng but this is my exploration into the problem. 
  
  ## Experimenting On Paper
  I started by trying to figure out the answer on paper using my brain. This way I would get an idea of what the code needs to do.
  
  Using my example from yesterday: 
  
  ```javascript
   {
      object1: { blue: 3, red: 20, yellow: 0 }
      object2: { blue: 0, red: 2,  yellow: 12 }
      object3: { blue: 20 red: 4,  yellow: 6 }

   }

   // How much of each object to total as close as possible to: blue: 70 red: 40, yellow: 15?
   ```
 
  I went through each object: How much of object1 would I need to total to blue:70? Blue for object 1 is 3 so 70/3 is 23.33. What would that do to the rest of our numbers: Multiply them by 23.33. Well, red would be too high, yellow would sill be zero.
 
  I thought through this for a while. It started to clarify some things to me. I decided to make a program to help me play around with this idea. 
 
    
  ## Experiementing In Code
 
  I took this problem to code, inorder to play around with it faster.
 
  ```javascript
   var array=[

      {fat:1, protein:2, carbs:4},
      {fat:4, protein:2, carbs:1},
      {fat:1, protein:4, carbs:2}

    ]
    
    const a = array[0];
    const b = array[1];
    const c = array[2];
    
    //__________________some made up desied totals the user might want
    var tFat = 15;
    var tProtein = 10;
    var tCarbs = 7;

  ```
  I made this array with objects representing foods with different amounts of nutrients. Then I made functions to help figure out what I was doing on paper, but faster in code. I'm not going to post the entire code because I left off with a bug and and some messiness. I will post it tomorrow. 
  
  You can see here how I could use my functions to tell me what all of our total nutrients would be if we used only one ingredient to reach an exact amount of our desired fat, or carbs, or protein:
  
   <img src="log_imgs/ndb_4-12.PNG"  width="350"/>
  
  Q is the [quotient](http://www.amathsdictionaryforkids.com/qr/d/division.html) (How much we need of the ingredient)
  
  F, P, C are fat protein and carbs.
  
  The parenthesis show how much under or over the macro totals would be from our desired totals.
  
  This helped me see how, if we were going to only use one ingredient (an over simplified answer to my problem), the best answer would probably be the one where the absolute values of the numbers in the parenthesis add up to the lowest amount.
  
  Still a lot to do.
  
  ## CSS In Console
  
  I used this article to try to get [CSS in my logs](https://hackernoon.com/styling-logs-in-browser-console-2ec0807dc91a). I didn't finish.

  ## Can you Spot the problem?
  
  I spent a while on this issue. Whenever I called `overOrUnder`, I got `undefined`. I spent way too long on this problem.

  Can you spot the issue?
  ```javascript
  const over = 'background-color: red';
  const under = 'background-color: yellow';
  const exact = 'background-color: green';
  
  const overOrUnder= (x)=>{
    if(x=0)return exact;
    if(x>0)return over;
    if(x<0)return under;
  }
  ```
  
  ## Answer
  
  I used the equals assignment operator `=` instead of the equals relational operator `==`.

## Day 1, R2
### 4/11/19

## Starting Round 2
Round 2 let's go!

- ## Recipe Calculator
  
  ## `.find()`
  
  I used `find()` to get the object in an array that matches a nutrient id. ex: 
  
  ```javascript
  nutrientRecipeArray[0].nutrients.find(x=>x.nutrient_id=="208")
  ```
  
  This is where I look for array methods and where I found `find()`: [JavaScript Array Reference](https://www.w3schools.com/jsref/jsref_obj_array.asp)

  ## Added A bunch of Functions
  
  I added a bunch of functions:
  - `nutrientValue(food, nutrient)`
    - returns a nutrient value for a specified food object. 
    - ex: `nutrientValue(nutrientRecipeArray[0], "fiber")`
  - `calories(food)`
    - short cut for `nutrientValue(food, "calories")`
  - `netCarbs(food)`
    - finds the net carbs from `nutrientValue(food, "carbs")` & `nutrientValue(food, "fiber")`
  - `fat(food)`
    - short cut for `nutrientValue(food, "fat")`
  - `protein(food)`
    - short cut for `nutrientValue(food, "protein")`
  - `nutrientRatio(food, nutrient, perNutrient)`
    - gets the ratio of a two nutrients for a specified food object. 
    - ex: `nutrientRation(nutrientRecipeArray[0], "protein", "calories")`
  - `sortDescending(array, nutrient, perNutrient)`
    - Sorts the food objects of an array by nutrient ratio. 
    - ex: `sortDescending(nutrientRecipeArray, "netCarbs", "calories")`
    
 ## Thinking Through Functions
 
 I really thought through how to seperate the functions so that they could be reused by other function. I think I did a good job. A lot of my functions use other functions that I made. This makes it easier to change add other related functions later and cleaner to see.
 
 ## Do I need An Algorithm?
 
 I feel like this next part is complex. But I feel like there might be an algorithm to solve it. I haven't really learned about algorithms.
 
 I'm trying to get the amounts needed of a list of ingredients that would total to specified nutrients or close to specified nutrients.
 
 I'm not sure what to search to even begin.
 
 ### Using another example: 
 If I have a collection of objects, each with different values of colors:
 
 ```javascript
 {
    object1: { blue: 3, red: 20, yellow: 0 }
    object2: { blue: 0, red: 2,  yellow: 12 }
    object3: { blue: 20 red: 4,  yellow: 6 }
    
 }
 
 // How much of each object to total as close as possible to: blue: 70 red: 40, yellow: 15?
 ```
 
 How much do we need of each object inorder to total as close as possible to specific amounts?  **ex totals: blue: 70 red: 40, yellow: 15**
 
- ## Thoughts and Feelings:
  Can't believe I'm on round two! I got a lot done because I saved most of my log until the end, instead of logging while coding.
 
 
 
    
 
