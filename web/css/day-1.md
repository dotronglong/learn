---
title: Getting Started
category: HTML/CSS
show_navigation: true
---

## Introduction

  **Note** This page will not cover HTML, but CSS instead

- CSS stands for _Cascading Style Sheets_
- General speaking, if HTML is your full body from head to feet, CSS is your clothes;
therefore, you could change your look by wearing different style of clothes.
- From the first announcement in 1996, it is 20 years old, has 5 versions (1, 2, 2.1, 3, and 4)
- CSS is designed primarily to enable the separation of document content from document presentation,
including aspects such as the layout, colors, and fonts.
- In order to start, you just need to create a HTML file, an example is shown below

  ```html
  <html>
  <head>
    <style>
      /* Your CSS definition goes here */
    </style>
  </head>
  <body>
    <div id="myDiv">Hello World!</div>
  </body>
  </html>
  ```

## Syntax

- Basically, syntax of CSS could be explained as below

  ```css
  [selector] {
    [attribute-0-key]: [attribute-0-value];
    [attribute-1-key]: [attribute-1-value];
    /* ... */
    [attribute-n-key]: [attribute-n-value];
  }
  ```

- Examples

  ```css
  #main {
    color: red;
  }

  #main .sub-class {
    color: green;
    font-weight: bold;
  }
  ```

## Selectors

- Select a specific element by its ID. At same time, there is only one element assigned an ID.
  The id of an element should be unique within a page, so the id selector is used to select one unique element.
  Use `#` followed by the id of element to select element.

  ```html
  <div id="myDiv">Hello World!</div>
  ```

  ```css
  #myDiv {
    display: block;
  }
  ```

- Select one or more elements using class. Use `.` followed by class name to select elements have
  appropriate class

  ```html
  <div id="myDiv">Hello World!<span class="my-class">Text</span></div>
  <div class="my-class">Text Div</div>
  ```

  ```css
  .my-class {
    display: block;
    color: red;
  }
  ```

- Group selectors, is allowed to assign same css styles between multiple selectors.
  Use `,` between selectors

  ```html
  <div id="myDiv">Hello World!</div>
  <div class="my-class">Text Div</div>
  ```

  ```css
  #myDiv,
  .my-class {
    display: block;
    color: red;
  }
  ```

- Attribute selectors, we can also select elements which contain specific attribute.
  Use `[attribute_name="attribute_value"]` after element selectors

  ```html
  <div id="myDiv">Hello World!</div>
  <div class="my-class" data-best-seller="1">Book A</div>
  <div class="my-class" data-name="book">Book B<div>
  <div class="my-class" data-best-seller="1">Book C</div>
  ```

  ```css
  .my-class[data-best-seller="1"] {
    display: block;
    color: red;
  }
  ```

- Children selectors, selecting element by specifying it's position in the list of element's children.
  + `:first-child` to specify the first child element
  + `:last-child` to specify the last child element
  + `:nth-child(n)` to specify the element by its position
  + `:nth-child(odd)` to select elements which their position is an odd number
  + `:nth-child(even)` to select elements which their position is an even number

  ```html
  <div id="myDiv">
    <div class="my-class" data-best-seller="1">Book A</div>
    <div class="my-class" data-name="book">Book B<div>
    <div class="my-class" data-best-seller="1">Book C</div>
    <div class="my-class">Book D</div>
  </div>

  ```

  ```css
  #myDiv div:first-child {
    color: red;
  }
  #myDiv div:last-child {
    color: blue;
  }
  #myDiv div:nth-child(2) {
    color: green;
  }
  #myDiv div:nth-child(odd) {
    color: yellow;
  }
  #myDiv div:nth-child(event) {
    color: black;
  }
  #myDiv div:nth-child(2n+3) { /* Every second column starting from column 3 */
    color: black;
  }
  ```

- Direct selectors, using `>` we could select the direct children

  ```html
  <div id="myDiv">
    <div class="other-class">Hello World</div> <!-- is selected -->
    <div class="my-class">
      <div class="other-class">Book A</div> <!-- is not selected -->
    </div>
  </div>

  ```

  ```css
  #myDiv > .other-class {
    color: red;
  }
  ```

+ Friend selectors, in order to select next element then `+` is helpful

  ```html
  <div id="myDiv">
    <div class="other-class">Hello World</div>
    <div class="my-class"> <!-- is selected -->
      <div class="other-class">Book A</div>
    </div>
    <div class="my-other-class"></div> <!-- is not selected -->
  </div>

  ```

  ```css
  .other-class + .my-class {
    color: red;
  }
  ```
