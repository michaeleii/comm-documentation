## Overview

In this section, we will be creating a logout feature for our project, which will allow us to logout after clicking the logout button.

## Creating a logout route

To create a logout route, add the following code after the POST login route in our `app.js` file:

```js
app.get("/logout", (req, res) => {
	req.logout();
	res.redirect("/");
});
```

The `req.logout()` function is provided by Passport. It will remove the user's session and log them out.

## Try it out

Now that we have created a logout route, we can test it out by logging in and then logging out.

## Conclusion

Congratulations! You have successfully created a login form using Passport's local strategy.

You should now be able to implement a login feature to your Node.js web application using Passport.

## Next Steps

To learn more about Passport and other strategies, check out the [Passport documentation](http://www.passportjs.org/docs/).

To view the full code for this project, check out the [GitHub repository](https://github.com/michaeleii/login-form-tutorial).
