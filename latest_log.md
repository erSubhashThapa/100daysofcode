
## Day 16, R3
### 8/4/19

- ## Node
 
  ### Where I left off:

  Yesterday, I started changing `action_session_create`. Before, the query looked only for existing sessions associated with the `user_id`. Now I'm also searching for `user-agent` and `ip`. I'll continue working on `action_session_create`.

  ## Logout
  I got more answers for my [log out question](https://twitter.com/DashBarkHuss/status/1157687032279379970) that were all pretty different.

  So I guess there isn't one agreed upon way to manage a logout endpoint.

  ## User Agent
  I got a weird result console logging `user-agent`. I was on Chrome but the log showed that the browser was Firefox(Mozilla), Chrome, and Safari:
  ```bash
  Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.142 Safari/537.36
  ```

  I found this explanation:
  > most Web browsers use a User-Agent string value as follows:
  >
  >`Mozilla/[version] ([system and browser information]) [platform] ([platform details]) [extensions].`
  >
  >- Mozilla is a byproduct of browser wars.
  >
  >- AppleWebKit/537.36 is the platform used by your browser.
  >
  >- Chrome/51.0.2704.63 is your browser
  >
  >- Safari/537.36 was added for historic reasons, where Safari was treated differently.
  
  -*[Why does Chrome send four browsers in the user-agent header?](https://security.stackexchange.com/questions/126407/why-does-chrome-send-four-browsers-in-the-user-agent-header)*

  ## Data Types For IP and User Agent
  I found this answer for what data types you should use for IP and User Agent in my session table: [What types should I use for these data in MySQL?](https://stackoverflow.com/questions/8263806/what-types-should-i-use-for-these-data-in-mysql)

  - **IP:** CHAR(15)
  - **user-agent:** VARCHAR(255)

  There are probably other ways to go about it too, as the answer says, "*This **depends a bit on your personal taste**/your company's conventions, but I'd use:..."*.

  More on [SQL Data Types here.](https://www.journaldev.com/16774/sql-data-types)


  ## Session Table
  If there's more than one session per username you can't have username be the primary key. You'll get an error:
  ```bash
  Error: ER_DUP_ENTRY: Duplicate entry 'someusername' for key 'PRIMARY'
  ```
  So I made an id a primary key
  ![](log_imgs/session_8-4.PNG)

  ## Updated `action_session_create` and `action_user_login`
  `action_user_login` now queries for the session by username, ip, and, user agent. `action_session_create` now adds the user agent and the ip address to the session.

  [Link To Work](https://github.com/DashBarkHuss/node_server_sessions/commit/d504488faf38bfd6172b5c405f5134beb744520b)

  ## Logout
  I started to make the logout endpoint. It's not working. The session is still in the table.
  - 
