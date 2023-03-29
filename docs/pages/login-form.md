## Overview

This section will guide you through the process of setting up the login form page for our project.

## Setting up the login page

#### 1. Add the `/login` GET route to `app.js`

Put the following code at the bottom of the `app.js` file:

```javascript
app.get("/login", (req, res) => {
	res.render("login");
});
```

This will add a `GET` route to the `/login` route in `app.js`.

#### 2. Editing the `login.ejs` file

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Login</title>
	</head>
	<body>
		<h1>Login</h1>
		<form action="/login" method="POST">
			<label for="username">Username</label>
			<input type="text" name="username" id="username" />
			<label for="password">Password</label>
			<input type="password" name="password" id="password" />
			<button type="submit">Login</button>
		</form>
	</body>
</html>
```

This render a simple login form when the `/login` route is requested.

#### 3. Add the `/login` POST route to `app.js`

Put the following code at the bottom of the `app.js` file:

```javascript
app.post("/login", (req, res) => {
	const { username, password } = req.body;
	console.log({ username, password });
});
```

This will add a `POST` route to the `/login` route in `app.js`. For now we are just logging the username and password to the console to make sure that the form is working.
