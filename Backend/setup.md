**BACKEND SETUP (Express JS framework of Node JS)**

After switching branches, run the following commands in your terminal,
```bash
mkdir backend
cd backend

npm init -y
```

Once created, you can replace the contents of the package.json file with this:
```json
{
  "name": "project-name",
  "version": "1.0.0",
  "description": "",
  "type": "module",
  "main": "server.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "npx nodemon --ext js,mjs,cjs,json,ejs,css server.js",
    "format": "prettier --write ."
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "dotenv": "^16.4.7",
    "ejs": "^3.1.10",
    "express": "^5.1.0",
    "express-ejs": "^2.0.0",
    "express-session": "^1.18.1",
    "firebase": "^11.6.0",
    "path": "^0.12.7"
  },
  "devDependencies": {
    "nodemon": "^3.1.9",
    "prettier": "^3.5.3",
    "prettier-plugin-ejs": "^1.0.3"
  }
}
```

Then, run the command below to install the dependencies listed in the package.json file.
```bash
npm i
```

As a good practice and to ensure you're using the latest versions, you can also do the following:
```bash
npm i dotenv ejs express express-ejs express-session firebase path
npm i -D nodemon prettier prettier-plugin-ejs
```

Now, go to the **folders.md** file to see the folder structure that I think you can use for your project. This is how I usually structure folders for a FERN stack project. It might not be the best approach, but I'm open to suggestions.