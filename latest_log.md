## Day 52, R3
### 9/9/19

- ## Node
  ### Where I Left Off
  I finished the Express.js video and followed along. I started to look into relationships in MySQL. I'm trying to figure out how to set up a relationship.

  ## Add Relationship in Sequel Pro

  Check that your primary key and foreign key have the same type:

  ![](log_imgs/prim_9-9.PNG)

  ![](log_imgs/foreign_9-9.PNG)

  The types have to match. The primary key, `id` is set to `INT`, `11`, `unsigned`, and `Allow Null` isn't checked. So `user_id`, the foreign key, must be set the same way.

  Set up the foreign key in the relations tab.
  ![](log_imgs/relation_9-9.PNG)

  I'm not sure if I got the terminology right. Is the parent table the primary key table? Now I think the parent key is called the foreign key table. I'm not sure.

  ## Cascade Delete
  >A foreign key with cascade delete means that if a record in the parent table is deleted, then the corresponding records in the child table will automatically be deleted.

  -from *[SQL Server](https://www.techonthenet.com/sql_server/foreign_keys/foreign_delete.php)*

  More: [Difference between On Delete Cascade & On Update Cascade in mysql](https://dba.stackexchange.com/questions/74627/difference-between-on-delete-cascade-on-update-cascade-in-mysql)

  ## Reactive Native
  [The Difference Between React.js and React Native + React Native Q&A || Crema](https://www.youtube.com/watch?v=7IWvCG2CBZA)
  
  ### Expo
  > With Expo tools, services, and React Native, you can build, deploy, and quickly iterate on native iOS and Android apps from the same JavaScript codebase.
  >- Access to device capabilities like camera, location, notifications, sensors, haptics, and much more, all with cross-platform APIs.
  >- Build service gives you app-store ready binaries and handles certificates, no need for you to touch Xcode or Android Studio.
  >- Over-the-air updates let you update your app at any time without the hassle and delays of submitting to the store.
  
  -from *[Expo](https://expo.io/)*

  ## Toolchain
  > In software, a toolchain is a set of programming tools that is used to perform a complex software development task or to create a software product, which is typically another computer program or a set of related programs. In general, the tools forming a toolchain are executed consecutively so the output or resulting environment state of each tool becomes the input or starting environment for the next one, but the term is also used when referring to a set of related tools that are not necessarily executed consecutively.
  >
  >A simple software development toolchain may consist of a compiler and linker (which transform the source code into an executable program), libraries (which provide interfaces to the operating system), and a debugger (which is used to test and debug created programs). A complex software product such as a video game needs tools for preparing sound effects, music, textures, 3-dimensional models and animations, together with additional tools for combining these resources into the finished product.[1][2]
  
  -from *[Wikipedia](https://en.wikipedia.org/wiki/Toolchain)*

  ## Flutter VS React Native
  [Flutter VS React Native -- Will Flutter Kill React Native? || Crema](https://www.youtube.com/watch?v=gWs3UQzrhtE)

  ## HTML5 GeoLocation
  [HTML5 Geolocation](https://www.w3schools.com/html/html5_geolocation.asp)

  ## HTML5 Server-Sent Events
  > A server-sent event is when a web page automatically gets updates from a server.
  >
  >This was also possible before, but the web page would have to ask if any updates were available. With server-sent events, the updates come automatically.
  >
  >Examples: Facebook/Twitter updates, stock price updates, news feeds, sport results, etc.

  [HTML5 Server-Sent Events](https://www.w3schools.com/html/html5_serversentevents.asp)

  ## HTML5 
  >When executing scripts in an HTML page, the page becomes unresponsive until the script is finished.
  >
  >A web worker is a JavaScript that runs in the background, independently of other scripts, without affecting the performance of the page. You can continue to do whatever you want: clicking, selecting things, etc., while the web worker runs in the background.

  [HTML5 Web Workers](https://www.w3schools.com/html/html5_webworkers.asp)

  ## Where I Left Off
  I'm starting an app, I left off trying to start the app with express.