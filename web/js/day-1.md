---
title: Getting Started
category: Javascript
show_navigation: true
---

### Debug
- Use `console.log` to debug a variable

  ```javascript
  console.log(window.location);
  ```

- Use break point in Chrome Developer Tools to debug javascript application (files)
  + Open Inspector Tool
  + Select `Sources` tab
  + In sub tabs, select `Sources` (if is not activated)
  + Find a specific javascript file to debug
  + Click on the left (before line numbers) to toggle a break point
  + Use debug controls to navigate through debugging session

### Javascript Fundamentals

#### Variable
- Refer to [W3School](https://www.w3schools.com/js/js_best_practices.asp) for Javascript Best Practices
- Declare a variable is pretty simple

  ```javascript
  var a = 5;      // variable in different line
  var b = "5";    // variable in different line

  var c = 10, d = 11; // multiple variables in same line
  ```

- Variable's type is not always required, but it is a best practice to keep in mind
when declare a variable with appropriate type

  ```javascript
  var a = 5, b = "5";

  // compare variables value ignoring their types
  console.log(a == b); // true

  // compare variables for both value and type
  console.log(a === b); // false
  ```

- Variable's scope is also an vital thing to remember

  ```javascript
  var a = 5; // a is a global variable

  function printA() {
    console.log(a);
    var b = 6; // meanwhile b is just a local variable
  }

  printA(); // 5
  console.log(b); // Uncaught ReferenceError: b is not defined
  ```

#### Conditional Statements

- `if`, `else if`, `else`

  ```javascript
  var a = Math.random();
  var b = Math.random();

  if (a > b) {
    console.log(a);
  } else if (a < b) {
    console.log(b);
  } else {
    console.log('same');
  }
  ```

- `switch`

  ```javascript
  switch (new Date().getDay()) {
    case 1:
    case 3:
    case 5:
      console.log('odd');
      break;

    case 2:
    case 4:
    case 6:
      console.log('even');
      break;

    default:
      console.log('Happy Sunday');
      break;
  }
  ```

#### Loops

- `for` loops through a block of code a number of times

  ```javascript
  for (i = 0; i < 5; i++) {
    console.log("No " + i);
  }
  ```

- `for/in` loops through the properties of an object

  ```javascript
  var person = {
    name: "Long",
    age: 29
  }

  for (key in person) {
    console.log(key + ' : ' + person[key]);
  }

  // it would print
  // name : Long
  // age : 29
  ```

- `while` loops through a block of code while a specified condition is true

  ```javascript
  var i = 0;
  while (i < 10) {
      console.log("The number is " + i);
      i++;
  }
  ```

- `do/while` also loops through a block of code while a specified condition is true

  ```javascript
  var i = 0;
  do {
      console.log("The number is " + i);
      i++;
  } while (i < 10);
  ```
