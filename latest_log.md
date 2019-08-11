
## Day 23, R3
### 8/11/19

- ## Node 
  Two days ago I finished the Node login app. Now I'm going to try to make an app that has login and crud with authentication.

  ## MySQL Commands
  I wanted to practice making a database in the command line instead of in the GUI.
  ```sql
  mysql> create database crud_login_app;

  mysql> use crud_login_app;

  mysql> create table user (username VARCHAR(128), email VARCHAR(320), verificationToken CHAR(32), password CHAR(32), isVerified TINYINT(1));

  mysql> alter table user add id INT NOT NULL AUTO_increment Primary key;

  mysql> alter table user modify column id int first;

  mysql> alter table user alter isVerified set default 0;
  ```
  These commands created the `crud_login_app` database and the `user` table.

  ![](log_imgs/user_8-11-19.PNG)

  For the `sessions` table I only had to do one command because I got everything right in the first command:
  ```sql
  mysql> create table sessions ( id INT not null auto_increment primary key, token CHAR(32), username CHAR(128), ip CHAR(15), useragent VARCHAR(255));
  ```
  ![](log_imgs/sessions_8-11-19.PNG)

  ## What I Did Today
  I started the app. I completed most of the index.js files adding mime types this time.

  For more mime types: [Incomplete list of MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types)

  Here are all my commits for today:
  [Link To Work](https://github.com/DashBarkHuss/crud_login_node_app/commits/3ee477fbc8b49dd5d59bbe47f60e7ac23df6f37b)

  Tomorrow, I'll work on connecting the database and handling API requests.