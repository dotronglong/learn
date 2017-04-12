---
title: Function
category: Javascript
---

### Introduction
- It is a necessary to understand deeply about function in javascript, as JS is mostly runnable with only defined functions.
- Like other languages, function is a way to define a set of common actions or behaviors. There are 2 ways to define a function as a callable or a variable.

### Define function
- Way 1: Define as a callable

  ```javascript
  function makeCake(recipes) {
      return 'cake';
  }
  // call function
  var cake = makeCake('chocolate and milk');
  ```

- Way 2: Define as as variable

  ```javascript
  var makeCake = function(recipes) {
      return 'cake';
  };
  // call function
  var cake = makeCake('chocolate and milk');
  ```

**Notes**:
+ With variable way, it is a best practice to place semicolon `;` at the end of statement as same as we define a variable
+ `Difference`? Yes, but it is not easy to understand their differences, it is an advanced knowledge. Keywords if you want to explore more about them `bind`, `apply`, `call`

### Examples
- Display a random number for every 5 seconds

  ```javascript
  function showRandomNumber(seconds) {
      setTimeout(function() {
        console.log(Math.random());
        showRandomNumber(seconds);
      }, seconds * 1000);
  }
  showRandomNumber(5); // display a number for every 5 seconds
  ```

- Alert user to go home if this is weekend at 6pm

  ```javascript
  function alertUserToLeave() {
      var d = new Date();
      if (d.getDay() === 5 && d.getHours() >= 18) {
          alert('Hey! Time to go home and have great time with your family');
      } else {
          // time is not up yet, wait for 1 minute to check again
          setTimeout(function() {
              alertUserToLeave();
          }, 60 * 1000);
      }
  }
  alertUserToLeave();
  ```

### Keep in mind
- None of us could remember everything, so do not waste time to try to keep all in our small head, do it smarter way.
- To search for definition of a builtin function in JS, open `Google` and type `[name of func] + mdn` then pick the result which might lead us to MDN (Mozilla Developer Network).
- There is only way to be stronger is to practice day by day.
