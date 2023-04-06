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

Open the terminal and type the following command:

```bash
mkdir login-form-tutorial
```

This will create a directory called `login-form-tutorial`, which will hold all the files for the project.

#### 2. Navigate to the Project Directory

```bash
cd login-form-tutorial
```

This will navigate to the `login-form-tutorial` directory.

Now that we have created the project directory, we can start installing the required Node modules.

## Installing Node Modules

In this section we will be installing the following Node modules:

- Express
- EJS
- Nodemon

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

This will install the Express module. We will be using Express to create our server.

[Express](https://expressjs.com/) is a minimalistic web framework for Node.js.

#### 3. Install EJS

```bash
npm install ejs
```

This will install the EJS module.

[EJS](https://ejs.co/) is a templating engine that we will be using to render our HTML pages.

#### 4. Install Nodemon

```bash
npm install nodemon --save-dev
```

This will install the nodemon module and add it to the `package.json` file as a development dependency.

[Nodemon](https://www.npmjs.com/package/nodemon) is a module that automatically restarts the server whenever a file is changed.

#### 5. Put the `start` Script in the `package.json` File

In the `package.json` file, there is a section called `scripts`. This section is used to store all the scripts for the project.

There should be a `test` script in the `scripts` section. Replace the `test` script with the following code:

```json
"scripts": {
    "start": "nodemon app.js"
},
```

This will add the `start` script to the `package.json` file. This script will allow us to type `npm start` in the terminal and start the server.

This will make it easier for us to start the server insteading of typing `nodemon app.js` in the terminal we can just use `npm start`.

In the next section, we will be setting up the project directory.

## Setting up the Project Directory

Now that we have finished installing the required node modules, we will be setting up the project directory.

#### 1. Create the `public` Directory

```bash
mkdir public
```

This will create a directory called `public`, which will hold all the static files for the project.

!!! question "What are static files?"

        **Static files** are files that are not rendered by the server, such as images, CSS files, and JavaScript files.

        For more information on static files, check out the [Express documentation](https://expressjs.com/en/starter/static-files.html).

#### 2. Creating the Style.css File

Create a file called `style.css` in the `public` directory.

#### 3. Creating the Views Directory

```bash
mkdir views
```

This will create a directory called `views`, which will hold all the ejs files for the project.

#### 4. Creating the Homepage Ejs File

Create a file called `index.ejs` in the `views` directory. This file will be the homepage for the project.

#### 5. Creating the Login Page Ejs File

Create a file called `login.ejs` in the `views` directory. This file will be the login page for the project.

#### 6. Creating the Express App File

Create a file called `app.js` in the root directory. This file will hold all the code for the Express app.

We will be writing the code for the Express app in the next section.

## Conclusion

In this section, we created the project directory and installed the required Node modules.

In the next section, we will setup the Express server.
