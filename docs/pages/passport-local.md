## Overview

Now that we are finish setting up the login form page, we can start working on the actual login feature that will log users in.

### Login Flow

To login a user, we need to check if the username and password are correct.

- If they are correct, we will store the user's information in the session.
- If they are incorrect, we will redirect the user back to the login page.

!!! info "How does a session work?"

    When a user logs in, we will store their information in the session. This information will be stored in a cookie on the user's browser. When the user visits the website again, the cookie will be sent to the server. The server will then use the information in the cookie to identify the user. This is how we can keep track of the user's session. The user will be logged in until they log out or the session expires.

## Setting up Passport Local Strategy

### What is a strategy?

A **strategy** is a way to authenticate a user. The Passport library contains many different strategies that can be used to authenticate a user.

For example, you can use a username and password or a social media account to log users in to a website.

For this project, we will be using the **Passport Local Strategy**. This strategy will allow us to authenticate users using a username and password.

### Installing Passport

To install Passport, Passport's Local Strategy and Express Session run the following command in the terminal:

```bash
npm install passport passport-local express-session
```

This will install Passport and Passport's Local Strategy. We will also need to install the `express-session` package to store the user's session data.

### Setting up Passport

#### 1. Require the packages in `app.js`

```javascript
....
app.use(express.static("public"));

const db = require("./userDb");

// Require Passport and Express Session here
const passport = require("passport");
const LocalStrategy = require("passport-local").Strategy;
const session = require("express-session");
...
```

#### 2. Set up Express Session

Put the following code after where you required the `express-session` package.

```js
...
const passport = require("passport");
const LocalStrategy = require("passport-local").Strategy;
const session = require("express-session");

// Initialize Express Session
app.use(
	session({
		secret: "secret",
		resave: false,
		saveUninitialized: true,
	})
);
...
```

This intializes the express session middleware which will be used to store the user's session data.

For more information on how to configure the express session middleware and the different options, check out the [Express Session documentation](https://github.com/expressjs/session#options).

#### 3. Initialize Passport

After the express session middleware, put the following code:

```js
// Initialize Passport
app.use(passport.initialize());
app.use(passport.session());
```

The `passport.initialize()` middleware will be used to initialize Passport. The `passport.session()` middleware will be used to persist login sessions. This will allow Passport to restore the user's logged in status across page refreshes.

#### 4. Configure Passport

After the `passport.session()` middleware, put the following code:

```js
// Configure Passport Local Strategy
passport.use(
	new LocalStrategy((username, password, done) => {
		const user = db.getUserByUsername(username);
		if (!user) {
			return done(null, false, { message: "Incorrect username" });
		} else if (user.password !== password) {
			return done(null, false, { message: "Incorrect password" });
		}
		return done(null, user);
	})
);
```

This will configure Passport to use the Local Strategy. The `(username, password, done)` is a verify function will be used to check if the username and password are correct.

- If they are correct, the `done` function will be called with the user's information.
- If they are incorrect, the `done` function will be called with `false` and a message.

#### 5. Add the passport.authenticate middleware to the login route

After the previous function configuring the local strategy, replace the POST login route with the following code:

```js
// Login Route

app.post(
	"/login",
	passport.authenticate("local", {
		successRedirect: "/",
		failureRedirect: "/login",
	})
);
```

This will add the `passport.authenticate` middleware to the login route. This middleware will call the verfiy function we configured earlier for the local strategy.

- The `successRedirect` will be called if the user's username and password are correct.
- The `failureRedirect` will be called if the user's username and password are incorrect.

#### 6. Serialize and Deserialize User

- **Serialize** means to store the user's data in the session.
- **Deserialize** means to get the user's data from the session.

```js
// Serialize User
passport.serializeUser((user, done) => {
	done(null, user.id);
});

// Deserialize User
passport.deserializeUser((id, done) => {
	const user = db.getUserById(id);
	if (user) {
		done(null, user);
	} else {
		done(null, false, { message: "User not found" });
	}
});
```

The `serializeUser` and `deserializeUser` functions are used to store the user's session data.

Heres how it works:

- The serialize user function will be called when the user logs in. It will store the user's id in the session.

- The deserialize user function will be called when the user visits the website again. It will get the user's information from the database using the id stored in the session.

The `done` function here is used to tell Passport that the user has been serialized or deserialized.

## Conclusion

In this section, we learned how to set up Passport and Passport's Local Strategy to authenticate users using a username and password.

In the next tutorial, we will try to log in a user using the login form page that we created in the previous section.
