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

## Conclusion

Congratulations! 👏

You have successfully created a login form using Passport's local strategy. You should now be able to authenticate users for your own projects.

## Next Steps

To learn more about Passport and other strategies, check out the [Passport documentation](http://www.passportjs.org/docs/).

To view the full code for this project, check out the [GitHub repository]().
