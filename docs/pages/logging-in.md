## Overview

We will now try out the login feature that we have created.

## Try it out

Start the server by running the following command:

```bash
npm start
```

#### 1. Open the browser and go to `http://localhost:3000/login`.

#### 2. Enter a username and password.

Heres a list of users we created from the previous section when we created the database:

```javascript
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

#### 3. Click the `Login` button.

- If the username and password are correct, you will be redirected to the homepage.
- If the username and password are incorrect, you will be redirected to the login page.

How ever the page still says `Not Logged In` and `Login`. This is because we have not implemented the logic to display the user's name and a logout button.

#### 4. Displaying the user's name on the homepage

We will now display the currently logged in user on the homepage.

In the app.js file, we can access the currently logged in user using the `req.user` property. We can pass this user to the `index.ejs` file using the `res.render()` method.

```javascript
app.get("/", (req, res) => {
	res.render("index", { currentLoggedInUser: req.user });
});
```

This will set the `currentLoggedInUser` variable to the current logged in user and we will be able to access this variable in our EJS page.

In the index.ejs file, we can now display the user's name if the user is logged in. Otherwise, we will display `Not Logged In` and a link to the login page.

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<link rel="stylesheet" href="/style.css" />
		<title>Login</title>
	</head>

	<body>
		<% if (currentLoggedInUser) { %>
		<h1>Not Logged In</h1>
		<a href="/login">Login</a>
		<% } else { %>
		<h1><%= currentLoggedInUser.username %></h1>
		<a href="/logout">Logout</a>
		<% } %>
	</body>
</html>
```

### Try it out

Try logging in and out and see if the user's name is displayed on the homepage.

## Conclusion

Congratulations! 👏 You have successfully created a login form using Passport's local strategy. You should now be able to authenticate users for your own projects.

## Next Steps

To learn more about Passport and other strategies, check out the [Passport documentation](http://www.passportjs.org/docs/).

To view the full code for this project, check out the [GitHub repository]().
