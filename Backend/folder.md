**Folder Structure**<br>

Why is having a proper folder structure important when building a project?
- Clean Architecture
- Modularity and Reusability
- Separation of Concerns (SoC)
- Single Responsibility Principle (SRP)

Did I answer my own question? Maybe yes, maybe no.<br>
Go ahead and explore more about software design principles — there are plenty of them to learn.<br>

This is how my backend folder will look like.
```
📂 config
📂 controllers
📂 middleware
📂 public
📂 routes
📂 services
📂 utils
.gitignore
.prettierrc
package-lock.json
package.json
server.js
```

Example code for some of the files and folders mentioned above:<br>

**server.js**
```js
app.use("/api", authRoutes);
```

**routes**
```js
router.post("/auth/login", loginController);
```

**controllers**
```js
exports.loginController = async (req, res) => {
  const { email, password } = req.body;
  try {
    const user = await authService.login(email, password);
    res.json({ message: "Login successful", user });
  } catch (err) {
    res.status(401).json({ message: err.message });
  }
};
```

**services**
```js
export class AuthService {
  async login(email, password) {
    const user = users.find(u => u.email === email);
    if (!user) throw new Error("User not found");

    const valid = await comparePassword(password, user.password);
    if (!valid) throw new Error("Invalid password");

    return { id: user.id, email: user.email };
  }
}
```

**utils**
```js
import bcrypt from "bcryptjs";

export const hashPassword = async (plainText) => {
  const salt = await bcrypt.genSalt(10);
  return bcrypt.hash(plainText, salt);
};

export const comparePassword = async (plainText, hash) => {
  return bcrypt.compare(plainText, hash);
};
```

These are just examples and are not necessarily required in the process. Understand the purpose of each file and folder. Don’t overcomplicate things.<br>

```
routes = define endpoints
controllers = handle req/res logic
services = handle business logic
utils = reusable helpers like hashing
```

You may now proceed to the next part: **server.js** setup.
