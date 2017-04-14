---
title: Gulp
category: Javascript
show_navigation: true
---

## Introduction

Gulp is a toolkit for automating painful or time-consuming tasks in your development workflow, so you can stop messing around and build something.

## Get started

*If you've previously installed gulp globally, run `npm rm --global gulp` before following these instructions.*

- Install the `gulp` command

  ```shell
  npm install --global gulp-cli
  ```

- Install `gulp` in your devDependencies. Run this command in your project directory:

  ```shell
  npm install --save-dev gulp
  ```

- Create a file called `gulpfile.js` in your project root with these contents:

  ```javascript
  var gulp = require('gulp');

  gulp.task('default', function() {
    // place code for your default task here
  });
  ```

- Test it out. Run the `gulp` command in your project directory:

  ```shell
  gulp
  ```
## Task

- The heart of Gulp are tasks. Task is an action to be defined. When no task is specified,
it will run `default` task.

- The order of task execution might be different. It might run in parallel or in sequence depending
on the way you define them

- **Parallel** is default behavior of Gulp

  ```javascript
  gulp.task('default', ['clean', 'build']);

  gulp.task('clean', function() {
    console.log('Cleaning ...');
    setTimeout(function() {
      console.log('Clean done!');
    }, 2000);
  });
  gulp.task('build', function() {
    console.log('Building ...');
    setTimeout(function() {
      console.log('Build done!');
    }, 1000);
  });
  ```

  `The tasks will run in parallel (all at once), so don't assume that the tasks will start/finish in order.`

  Task default will be done only when tasks `clean` and `build` are finished. However, it is not
  guaranteed that `build` will run right after `clean` is finished, indeed, they will be executed
  at same time. If you run above example, the result would be same as below

  ```shell
  [13:01:58] Using gulpfile ~/gulpfile.js
  [13:01:58] Starting 'clean'...
  Cleaning ...
  [13:01:58] Finished 'clean' after 726 μs
  [13:01:58] Starting 'build'...
  Building ...
  [13:01:58] Finished 'build' after 680 μs
  [13:01:58] Starting 'default'...
  [13:01:58] Finished 'default' after 30 μs
  Build done!
  Clean done!
  ```

- **Asynchronous**

  _In order to run tasks in sequence, there are some ways to archive it_

  + Create a hint, this is a common way to archive async

  ```javascript
    gulp.task('default', ['clean', 'build']);
    gulp.task('clean', function(cb) {
      console.log('Cleaning ...');
      setTimeout(function() {
        console.log('Clean done!');
        cb();
      }, 2000);
    });
    gulp.task('build', ['clean'], function() {
      console.log('Building ...');
      setTimeout(function() {
        console.log('Build done!');
      }, 1000);
    });
  ```

  + Accept a callback

  ```javascript
    // run a command in a shell
    var exec = require('child_process').exec;
    gulp.task('jekyll', function(cb) {
      // build Jekyll
      exec('jekyll build', function(err) {
        if (err) return cb(err); // return error
        cb(); // finished task
      });
    });

    // use an async result in a pipe
    gulp.task('build', function(cb) {
      getFilesAsync(function(err, res) {
        if (err) return cb(err);
        var stream = gulp.src(res)
          .pipe(minify())
          .pipe(gulp.dest('build'))
          .on('end', cb);
      });
    });
  ```

  + Return a stream

  ```javascript
    gulp.task('build', function() {
      var stream = gulp.src('client/**/*.js')
      .pipe(minify())
      .pipe(gulp.dest('build'));
      return stream;
    });
  ```

  + Return a promise

  ```javascript
    var Q = require('q');

    gulp.task('build', function() {
      var deferred = Q.defer();

      // do async stuff
      setTimeout(function() {
        deferred.resolve();
      }, 1);

      return deferred.promise;
    });
  ```

- Watch files and run tasks when a file changes, please refer `gulp.watch` ([Read more](https://github.com/gulpjs/gulp/blob/master/docs/API.md#gulpwatchglob--opts-tasks-or-gulpwatchglob--opts-cb))

## Examples

- Copy all `.css` and `.js` files from `assets` folder to `public/assets` folder

  ```javascript
  var gulp = require('gulp');

  gulp.task('default', function() {
    gulp.src(['assets/*.css', 'assets/*.js'])
        .pipe(gulp.dest('public/assets'));
  });
  ```

- Convert SASS file `.scss` from folder `assets/scss` to `.css` and place them to `public/assets/css`

  ```javascript
  var gulp = require('gulp');
  var sass = require('gulp-sass');

  gulp.task('default', function() {
    gulp.src('assets/scss/*.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(gulp.dest('public/assets/css'));
  });
  ```

## References

- [Gulp](https://github.com/gulpjs/gulp/blob/master/docs/API.md)
- [Gulp SASS](https://www.npmjs.com/package/gulp-sass)
