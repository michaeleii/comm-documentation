## **Error: Cannot find module './users'**

To fix this you need to make sure the path to the file is correct. If you are using a relative path, make sure it is correct.

## **TypeError: LocalStrategy requires a verify callback**

This error means that you are missing the verify callback function in the `passport.use` function.

## **Already included file name in path differs from file name in casing**

This error means that the file name in the path is different from the actual file name. For example, if you have a file named `userDb.js` and you try to include it using `require('./userDB.js')`, you will get this error.

To fix this, make sure the file name in the path is the same as the actual file name.

If they are correct and your still getting this error, try refreshing VSCode by exiting it and opening it again.
