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

  ```sass
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
