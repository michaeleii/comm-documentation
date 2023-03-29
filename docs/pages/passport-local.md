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
const passport = require("passport");
const LocalStrategy = require("passport-local").Strategy;
const session = require("express-session");
```

#### 2. Set up Express Session

```js
app.use(
	session({
		secret: "secret",
		resave: false,
		saveUninitialized: true,
		cookie: { secure: true },
	})
);
```

This intializes the express session middleware which will be used to store the user's session data.

For more information on how to configure the express session middleware and the different options, check out the [Express Session documentation](https://www.npmjs.com/package/express-session).

#### 3. Configure Passport

```js
// Configure Passport to use Local Strategy
passport.use(new LocalStrategy());

// Configure Passport authenticated session persistence
passport.serializeUser((user, done) => {
	done(null, user.id);
});

passport.deserializeUser((id, done) => {
	User.findById(id, (err, user) => {
		if (err) {
			return done(err);
		}
		done(null, user);
	});
});

// Initialize Passport and restore authentication state, if any, from the session.
app.use(passport.initialize());
app.use(passport.session());
```

## Conclusion

In this section, we learned how to set up Passport and Passport's Local Strategy to authenticate users using a username and password.

In the next tutorial, we will try to log in a user using the login form page that we created in the previous section.

<!-- This section will show you the login form flow and how it works in the context of passport authentication.

## Login Form Flow

The login form flow is as follows:

1. The user enters their username and password in the login form.
2. The user clicks the login button.
3. The form data is sent to the server.
4. Passport will authenticate the user using the local strategy.
5. If the user is authenticated, the user will be redirected to the homepage.
6. If the user is not authenticated, the user will be redirected back to the login page. -->
