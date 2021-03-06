Frontend
========

Custom JS and CSS frontend for inclusion in [Canvas](http://www.instructure.com/).

# Description
The custom JS and CSS frontend is built on top of Canvas using the mechanism in Canvas for including custom .js and .css files.

The frontend changes the Canvas graphical design and user interface by using [LESS](http://lesscss.org) and custom HTML injected using JavaScript and [Handlebars.js](http://handlebarsjs.com/) templates.

The custom JS and CSS frontend is compiled and concatenated into a single CSS and JavaScript file using Node and [Grunt - JavaScript Task Runner](http://gruntjs.com)


# Getting started
If you want to to build the frontend on your local machine you need to follow the steps below. Note that some of the commands might require sudo on certain systems.


## Install Node
To build CSS and JavaScript files you need to install [Node JS](http://nodejs.org) or update to the latest version if you are already have it installed.


## Clone or download frontend project to local machine
Clone the frontend from https://github.com/matematikk-mooc/frontend or download using your browser:
```
git clone https://github.com/matematikk-mooc/frontend.git
```

## Install Grunt and build dependencies (Node packages)
Switch to the directory where the frontend is located and install the dependencies using [NPM](https://www.npmjs.com/):

```
npm install
```

## Compile JS and CSS files

Compile JS and CSS files using [GRUNT](http://gruntjs.com/)

```
grunt
```

The resulting JS and CSS file can then be found in the **dist** directory


## Start a web server on your local machine
If you want to serve the CSS and JS files on your local machine for development, you can do this using Grunt:

```
grunt serve
```

All changes in LESS (CSS) and JavaScript will automatically be compiled and are available using the following URLs:

* [http://localhost:9000/mmooc-min-dev.css](http://localhost:9000/mmooc-min-dev.css) (for development)
* [http://localhost:9000/mmooc-min.css](http://localhost:9000/mmooc-min.css) (for production)
* [http://localhost:9000/mmooc-min.js](http://localhost:9000/mmooc-min.js)
* [http://localhost:9000/badges-dev.js](http://localhost:9000/badges-dev.js) (for dev)
* [http://localhost:9000/badgesafe.js](http://localhost:9000/badgesafe.js) (for prod)
* [http://localhost:9000/badgesafe.css](http://localhost:9000/badgesafe.css)



## Run Jasmine JavaScript tests

```
grunt test
```

# Project structure

## Directories
| Directory      | Description                               |
| -------------- | ----------------------------------------- |
| spec           | Jasmine JavaScript tests                  |
| src            | Source code                               |
| src/addons     | modules for canvas addons                 |
| src/css        | CSS(LESS)                                 |
| src/js         | JavaScript                                |
| src/templates  | Handlebars.js templates for creating HTML |
| dist/          | Build output directory                    |

## src/css

| Directory | Description                                     |
| ----------------------- | --------------------------------- |
| framework | CSS for override of global Canvas HTML elements |
| modules   | CSS for custom HTML modules added to canvas     |
| pages     | CSS overrides for specific Canvas pages         |
| setup     | Global LESS variables, mixins, custom font      |


## src/js

| File                    | Description                                                              |
| ----------------------- | ------------------------------------------------------------------------ |
| main.js                 | Calls different JS functions to create custom HTML based on URL (routes) |
| api/api.js              | Call to Canvas REST API etc                                              |
| modules/                | Various JavaScripts called from main.js                                  |
| modules/routes.js       | Library used to call different JS functions based on URLs using RegExps  |


# Deployment

Copy all files from the dist directory to your web server.
Note that addons generate different files that may be destinated to different directories in your production server.

## Image paths

The CSS files have URL references to bitmaps which are replaced at build time using grunt-text-replace.  To change the URL for the production server,
modify the following section in Gruntfile.js

```
    replacements: [{
	    from: 'https://server',
		to: 'https://apps.kantega.no/mmooc'
    }]
```
