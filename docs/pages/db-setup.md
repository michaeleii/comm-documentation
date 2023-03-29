## Overview

This section will guide you through creating a sample database with users for our project.

### Creating a mental model

Before we start creating the database, we need to create a mental model of a user. This will help us create a database that is easy to work with.

In our case, we want to store the following data:

- username
- password

### Create the database

Now that we have a mental model of a user, we can start creating the database.

#### 1. Create a `userDB.js` file

For simplicity sake, we will create a database in a file called `userDB.js`. This will allow us to easily access the database without having to set up a real database server.

#### 2. Add sample data to the database

Inside the `userDB.js` file, we will create an array of fake users.

Based on our mental model, we will create a user object with the following properties:

- username
- password

This will allow us to test our login feature.

```js
const users = [
	{
		username: "John",
		password: "password",
	},
	{
		username: "Jane",
		password: "password",
	},
];
```

This function will return the user object if the username and password match. Otherwise, it will return `undefined`.

### Querying the database

Now that we have a database, we need to be able to query it. This will allow us to check if a user's username and password is correct.

#### 1. Add a function that will check if the username and password are correct.

At the bottom of the `userDB.js` file, add the following function:

```js
const getUserByUsernameAndPassword = (username, password) => {
	return users.find(
		(user) => user.username === username && user.password === password
	);
};
```

#### 2. Export the `getUserByUsernameAndPassword` function

At the bottom page put the following code:

```js
module.exports = { getUserByUsernameAndPassword };
```

This will allow us to use the `getUserByUsernameAndPassword` function in our `app.js` file.

#### 3. Import the function that will verify username and password in `app.js`

At the top of the page before the index route, put the following code:

```js
...
const { getUser } = require("./users");

app.get("/", (req, res) => {
    res.render("index");
});
...
```
