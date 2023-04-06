## Overview

We will now try out the login feature that we have created.

## Testing the login feature

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

You may have noticed that you were redirected to the homepage, but the page still says `Not Logged In` and `Login`. This is because we have not implemented the logic to display the user's name and a logout button.

#### 4. Displaying the user's name on the homepage

We will now display the currently logged in user on the homepage. To do this, we will need to access the currently logged in user in the EJS page.

In the app.js file, we can create a middleware function that will set the currently logged in user to a variable that we can access in our EJS page.

Put the following code after where the deserializeUser function is defined:

```js
...
passport.deserializeUser((id, done) => {
  const user = db.getUserById(id);
  if (user) {
    done(null, user);
  } else {
    done(null, false, { message: "User not found" });
  }
});

app.use((req, res, next) => {
  res.locals.currentLoggedInUser = req.user;
  next();
});
...
```

Using the `res.locals` object, we can set a variable that we can access in our EJS page. In this case, we are setting the `currentLoggedInUser` variable to the `req.user` object.

!!!question "How does `res.locals` work?"

    In Express, `res.locals` is an object that is available throughout the lifecycle of a request. It is used to pass data from the server to the views that are rendered during that request-response cycle.

    To learn more about `res.locals`, check out the [Express documentation](https://expressjs.com/en/api.html#res.locals).

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
    <% if (!currentLoggedInUser) { %>
    <h1>Not Logged In</h1>
    <a href="/login">Login</a>
    <% } else { %>
    <h1>Welcome <%= currentLoggedInUser.username %></h1>
    <a href="/logout">Logout</a>
    <% } %>
  </body>
</html>
```

#### Try it out

Try logging in and out and see if the user's name is displayed on the homepage.

<figure markdown>
  ![Image title](img/homepage_loggedin.jpg)
  <figcaption>Homepage with user's name</figcaption>
</figure>

## Conclusion

In this section, we created a login form that will allow users to log in to our website using a username and password.

You might have noticed that when we click the logout link it doesn't work.

In the next section, we will create a logout feature that will allow users to log out of our website.
