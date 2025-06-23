**server.js**

Create a new file named **.env** and add **PORT=3000**. The port number doesn't always have to be 3000.

```js
const express = require("express");
const app = express();
const sessionMiddleware = require("./middleware/session");

app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(sessionMiddleware);

const PORT = process.env.PORT;
app.listen(PORT, () => {
  console.log(`Listening to PORT ${PORT}...`);
});
```

**What is ExpressJS?**<br>
Framework for building Node.js web servers & APIs.<br>

**What are the express.json and express.urlencoded for?**<br>
**express.json()**<br>
Parses JSON data (e.g., from fetch or axios in React).<br>

**express.urlencoded({ extended: true })**<br>
Parses form data submitted with application/x-www-form-urlencoded<br>

Afther that, create a session middleware file. Create a new file named **session.js** inside the **middleware** folder. Also add a line for SECRET_SESSION_KEY inside the .env file.
```js
const session = require("express-session");

const sessionMiddleware = session({
  secret: process.env.SECRET_SESSION_KEY,
  resave: false,
  saveUninitialized: false,
  cookie: { secure: false },
});

module.exports = sessionMiddleware;
```

**What is express-session?**<br>
express-session is a middleware for Express that allows you to store data (like user login status) on the server for a specific user across multiple requests.<br>

```js
cookie: { secure: false }
```
Only use secure: true when you're deploying with HTTPS, otherwise cookies won't be stored.<br>

You don't have to put express-session in a middleware/ folder, but it's cleaner when organizing larger projects.