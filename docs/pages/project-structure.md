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

#### 1. Create the Project Directory

```bash
mkdir login-form-tutorial
```

This will create a directory called `login-form-tutorial`, which will hold all the files for the project.

#### 2. Navigate to the Project Directory

```bash
cd login-form-tutorial
```

This will navigate to the `login-form-tutorial` directory.

## Installing Node Modules

#### 1. Create a `package.json` File

```bash
npm init -y
```

This will create a file called `package.json` inside the `login-form-tutorial` directory.

This file is used to store all the project dependencies.

#### 2. Install Express

```bash
npm install express
```

This will install the Express module. [Express](https://expressjs.com/) is a minimalistic web framework for Node.js.

#### 3. Install EJS

```bash
npm install ejs
```

This will install the EJS module.

EJS is a templating engine that we will be using to render our HTML pages.

#### 4. Install Nodemon

```bash
npm install nodemon --save-dev
```

This will install the nodemon module and add it to the `package.json` file as a development dependency.

Nodemon is a module that automatically restarts the server whenever a file is changed.

#### 5. Put the `start` Script in the `package.json` File

```json

"scripts": {
    "start": "nodemon app.js"
  },
```

This will add the `start` script to the `package.json` file. This script will allow us to type `npm start` and start the server.

## Setting up the Project Directory

#### 1. Creating the Style.css File

```bash
touch public/style.css
```

This will create a file called `style.css` inside the `public` directory.

#### 2. Creating the Views Directory

```bash
mkdir views
```

This will create a directory called `views`, which will hold all the ejs files for the project.

#### 3. Creating the Homepage Ejs File

```bash
touch views/index.ejs
```

This will create a file called `index.ejs` inside the `views` directory.

#### 4. Creating the Login Page Ejs File

```bash
touch views/login.ejs
```

This will create a file called `login.ejs` inside the `views` directory.

#### 5. Creating the Express App File

```bash
touch app.js
```

This will create a file called `app.js` inside the `login-form-tutorial` directory.

This file will hold all the code for the Express app.

## Conclusion

In this section, we created the project directory and installed the required Node modules.

In the next section, we will setup the Express server.
