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

## Navigate to the Project Directory

```bash
cd login-form-tutorial
```

This will navigate to the `login-form-tutorial` directory.

## Installing Node Modules

### 1. Install Express

```bash
npm install express
```

This will install the Express module and add it to the `package.json` file.

### 2. Install EJS

```bash
npm install ejs
```

This will install the EJS module and add it to the `package.json` file.

### 3. Install Nodemon

```bash
npm install nodemon --save-dev
```

This will install the nodemon module and add it to the `package.json` file as a development dependency.

## Setting up the Project Directory

### 1. Creating the Style.css File

```bash
touch public/style.css
```

This will create a file called `style.css` inside the `public` directory.

### 2. Creating the Views Directory

```bash
mkdir views
```

This will create a directory called `views`, which will hold all the ejs files for the project.

### 3. Creating the Homepage Ejs File

```bash
touch views/index.ejs
```

This will create a file called `index.ejs` inside the `views` directory.

### 4. Creating the Login Page Ejs File

```bash
touch views/login.ejs
```

This will create a file called `login.ejs` inside the `views` directory.

### 5. Creating the Express App File

```bash
touch app.js
```

This will create a file called `app.js` inside the `login-form-tutorial` directory.

This file will hold all the code for the express app.
