## Overview

This section layouts the overall file directory structure of the login form project that we will be building.

#### Working Directory Structure

```text
|-- login-form-tutorial              # Root Directory
    |-- public                       # Public Directory
            |-- style.css            # Style.css File
    |-- views                        # Views Directory
            |-- index.ejs            # Homepage Ejs File
            |-- login.ejs            # Login Page Ejs File
    | -- app.js                      # Express App File
    |-- package.json                 # Package.json File
    |-- node_modules                 # Node Modules Directory
```

Creating a directory structure like this will help us keep our project organized and easy to navigate.

## Creating the Project Directory

```bash
mkdir login-form-tutorial
```

This will create a directory called `login-form-tutorial`, which will hold all the files for the project.

## Creating the Style.css File

```bash
touch public/style.css
```

This will create a file called `style.css` inside the `public` directory.

## Creating the Views Directory

```bash
mkdir views
```

This will create a directory called `views`, which will hold all the ejs files for the project.

## Creating the Homepage Ejs File

```bash
touch views/index.ejs
```

This will create a file called `index.ejs` inside the `views` directory.

## Creating the Login Page Ejs File

```bash
touch views/login.ejs
```

This will create a file called `login.ejs` inside the `views` directory.

## Creating the Express App File

```bash
touch app.js
```

This will create a file called `app.js` inside the `login-form-tutorial` directory.

This file will hold all the code for the express app.
