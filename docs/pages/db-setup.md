## Overview

This section will guide you through creating a sample database with users for our project.

### Creating a mental model

Before we start creating the database, we need to create a mental model of a user. This will help us create a database that is easy to work with.

In our case, we want to store the following data:

- username
- password

We will also have a unique id for each user. This will allow us to easily identify a user each id is unique to a specific user.

## Create the database

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
		id: 1,
		username: "John",
		password: "password",
	},
	{
		id: 2,
		username: "Jane",
		password: "password",
	},
];
```

This function will return the user object if the username and password match. Otherwise, it will return `undefined`. In the next section we will be creating functions to search the database for a user.

## Query the database

Now that we have a database, we need to be able to query it. We want to be able to check if the username and password are correct. So we will create queries that will allow us to verify the username and password.

#### 1. Add a function that will check if the username and password are correct.

At the bottom of the `userDB.js` file, add the following function:

```js
const getUserByUsername = (username) => {
	return users.find((user) => user.username === username);
};
```

This function will return the user object if the username matches a user in the database. Otherwise, it will return `undefined`.

#### 2. Add a function that will get a user by id

At the bottom of the `userDB.js` file, add the following function:

```js
const getUserById = (id) => {
	return users.find((user) => user.id === id);
};
```

This function will return the user object if the id matches. Otherwise, it will return `undefined`.

#### 3. Export the functions

At the bottom page put the following code:

```js
module.exports = { getUserByUsername, getUserById };
```

This will allow us to use the functions in our `app.js` file.

#### 3. Import the function that will verify username and password in `app.js`

At the top of the page before the index route, put the following code:

```js
...
const db = require("./userDb"); // <--- import the database here

app.get("/", (req, res) => { // <--- index route
    res.render("index");
});
...
```

This will allow us to use the our database querying functions in our `app.js` file. We will be using these functions to verify the username and password.

## Conclusion

In this section, we created a database that will store our users. We also created a function that will allow us to query the database and check if a user's username and password is correct.

In the next section, we will create the login form page that will allow users to log in to our website using a username and password.
