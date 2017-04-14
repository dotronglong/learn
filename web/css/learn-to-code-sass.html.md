---
title: Learn to code SASS
category: HTML/CSS
show_navigation: true
---

## Introduction
- SASS is a CSS extension language.
- It is not normal to hear about programming in CSS, since CSS is mostly using for
template making, theme changing. However, it raised a question about how to make CSS easy
to maintain, reusable, cross-browser support.
- SASS (first appeared 2006) has a friend, LESSCSS (or LESS) (first appeared 2009), is a CSS pre-processor.
Nevertheless, this post will not cover advantages or disadvantages between SASS and LESS, or why I choose to
talk about SASS (you made your choice), but it focuses on the way to work with SASS.

## Features

As described earlier, the idea is simple, how would we make a function which generate similar
css styles instead of `copy & paste`? Therefore, SASS comes with several awesome features which could
be named as below:
- Variables
- Import
- Functions (or Mixins)
- Inheritance
- Operators
- Nesting

## Getting Started

- **Installations** There are several ways to install base on your current platform

  + Mac

  ```sh
    gem install sass
  ```

  + Linux

  ```sh
    sudo su -c "gem install sass"
  ```

  + Windows

    _Before you start using Sass you will need to install Ruby. The fastest way to get
    Ruby on your Windows computer is to use [Ruby Installer](http://rubyinstaller.org/). It's a single-click installer
    that will get everything set up for you super fast.
    The installer will also install a Ruby command line powershell application that
    will let you use the Ruby libraries._

  + Docker

  _Create a file at `/usr/local/bin/sass` and paste below content to that file_

  ```
        #!/bin/sh
        docker run dotronglong/sass ${@}
  ```

    _Grant execute permission to that file_

  ```sh
        chmod +x /usr/local/bin/sass
  ```

    _That's it. Let see SASS version_

  ```sh
        sass -v
        # Sass 3.4.22 (Selective Steve)
  ```  

- Create a sass file name `test.scss`, and paste below content to it

  ```scss
  $font-family: 'Tahoma';

  body {
    font-family: $font-family;
  }
  ```

- Build to `css` file

  ```sh
  sass test.scss test.css
  ```

- It will generate 2 files `test.css` and `test.css.map`, content of `test.css` will be:

  ```css
  body {
  font-family: "Tahoma"; }

  /*# sourceMappingURL=test.css.map */
  ```

## Variables

- If you were a PHP developer, syntax of SASS will be easy for you. To define a variable
you could write as below

  ```text
  $[variable-name]: variable-value;
  ```

- Example

  ```scss
  $main-color: red;

  div {
    color: $main-color; /* Using variable */
  }
  ```

## Mixins

- Mixin, or function, contains a bun of many css definitions inside it body. Likes
function, it is able to receive input arguments.

  ```text
  @mixin [mixin-name]([...mixin variables]) {
    /* definitions are described here */
  }
  ```

- Example  

  ```scss
  @mixin border-radius($radius) {
    -webkit-border-radius: $radius;
       -moz-border-radius: $radius;
        -ms-border-radius: $radius;
            border-radius: $radius;
  }

  .box { @include border-radius(10px); }
  ```

## Inheritance

- This is one of the most useful features of Sass. Using `@extend` lets you share a
set of CSS properties from one selector to another. It helps keep your Sass very DRY.
In our example we're going to create a simple series of messaging for errors, warnings and successes.

  ```text
  .my-class {
    @extend .my-parent-class;
  }
  ```

- Example

  ```scss
  .message {
    border: 1px solid #ccc;
    padding: 10px;
    color: #333;
  }

  .success {
    @extend .message;
    border-color: green;
  }
  ```

## Operators

- Doing math in your CSS is very helpful. Sass has a handful of standard math operators like `+`, `-`, `*`, `/`, and `%`.

- Example to do some simple math to calculate widths for an aside & article.

  ```scss
  .container { width: 100%; }

  article[role="main"] {
    float: left;
    width: 600px / 960px * 100%;
  }

  aside[role="complementary"] {
    float: right;
    width: 300px / 960px * 100%;
  }
  ```

## References
- [SASS Language](http://sass-lang.com/)
- [SASS Wiki](https://en.wikipedia.org/wiki/Sass_(stylesheet_language))
- [LESS Wiki](https://en.wikipedia.org/wiki/Less_(stylesheet_language))
