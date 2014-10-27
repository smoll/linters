# Gulp Linters

Licence: MIT.

## Requirements

The linters are currently running with `Gulp`, so you need to have `node` and `npm` in your environment. Some linters need specific dependencies:

* Scss linter requires to run the Ruby dependencies ([gem file](https://github.com/theorchard/linters/blob/master/Gemfile))
* PHP linter requires to run the composer dependencies ([composer.json](https://github.com/theorchard/linters/blob/master/composer.json))

## Installation

The installation of this module is simple. First make sure your ssh keys are allowing you to access github from your environment. At the root of your project, update your package.json and add in the dependency section:

```js
"gulp-linters": "git+ssh://git@github.com:theorchard/linters.git",
```

If you don't have an existing `package.json`, run [`npm init`](https://www.npmjs.org/doc/cli/npm-init.html), when it has been generated, add the line above in the newly created `package.json`. You also probably want to add "Gulp". To do so, run: `npm install gulp --save-dev`.

## Configuration

If you've never worked with [Gulp](http://gulpjs.com/), it's a task manager that allows you to run tasks concurrently. It works with a `gulpfile.js`, in which you can find the different tasks it can run. To start gulp, you just have to run: `gulp [taskname]`.

The Gulp Linters have been built as a gulp extension you require then use. It will look like this:

```js
var gulp = require('gulp');

// Requesting the linters, and registering the new tasks on this gulp instance.
var linters = require('gulp-linters');
linters.register(gulp);
gulp.task('lint', linters.all);
```

## Options

### Registration options

When you call the `register` method, the second parameter allows you to pass in some options:

* `files`: Dictionary that contains the list of all your files.
* `files.php`: List of all your php files.
* `files.js`: List of all your javascript files.
* `files.scss`: List of all your Sass files.

### Linter task sets:

There are 4 different linter tasks sets:

* `linters.js`: will make jslint run against your js files.
* `linters.scss`: will make scss-lint run against all your scss files.
* `linters.php`: will make php codesniffer run against all your php files.
* `linters.all`: will run both js and scss.
* `linters.dev`: will run all linters and a watcher (so when a file is updated, the linters are running on that specific file.)
