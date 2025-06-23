**server.js**

Create a new file named **.env** and add **PORT=3000**. The port number doesn't always have to be 3000.

```js
import express from "express";
import sessionMiddleware from "./middleware/session.js";
import dotenv from "dotenv";
dotenv.config();

const app = express();

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
Parses form data submitted with application/x-www-form-urlencoded<br><br>

After that, create a session middleware file. Name the file **session.js** and place it inside the **middleware** folder. Also, add a line for **SECRET_SESSION_KEY** in the **.env** file.
```js
import session from "express-session";
import dotenv from "dotenv";
dotenv.config();

const sessionMiddleware = session({
  secret: process.env.SECRET_SESSION_KEY,
  resave: false,
  saveUninitialized: false,
  cookie: { secure: false },
});

export default sessionMiddleware;
```

**What is express-session?**<br>
express-session is a middleware for Express that allows you to store data (like user login status) on the server for a specific user across multiple requests.<br>
```js
  req.session.user = {
    username: "dragonary",
    role: "admin"
  };

  console.log(req.session.user);
```

```js
cookie: { secure: false }
```
Only use secure: true when you're deploying with HTTPS, otherwise cookies won't be stored.<br>

You don't have to put express-session in a middleware/ folder, but it's cleaner when organizing larger projects.
