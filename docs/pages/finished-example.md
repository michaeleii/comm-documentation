# Finished Example

## app.js

```js
const express = require("express");
const db = require("./userDB");
const passport = require("passport");
const LocalStrategy = require("passport-local").Strategy;
const session = require("express-session");

const app = express();

app.set("view engine", "ejs");
app.use(express.urlencoded({ extended: false }));
app.use(express.static("public"));
app.use(
  session({
    secret: "secret",
    resave: false,
    saveUninitialized: true,
  })
);
app.use(passport.initialize());
app.use(passport.session());

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

passport.serializeUser((user, done) => {
  done(null, user.id);
});

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

app.get("/", (req, res) => {
  res.render("index");
});

app.get("/login", (req, res) => {
  res.render("login");
});

app.post(
  "/login",
  passport.authenticate("local", {
    successRedirect: "/",
    failureRedirect: "/login",
  })
);

app.listen(3000, () => {
  console.log("Login App listening on port 3000!");
});

app.get("/logout", (req, res) => {
  req.logout((err) => console.log(err));
  res.redirect("/");
});
```

## index.ejs

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

## login.ejs

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
