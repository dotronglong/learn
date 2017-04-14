---
title: Learn to customize Bootstrap
category: HTML/CSS
show_navigation: true
---

## Introduction

- [Bootstrap](http://getbootstrap.com/) is a front-end framework which includes HTML, CSS and JS code to develop
responsive, mobile first projects.
- It is an obvious framework to learn if you want to build a rich site without starting
from scratch.
- At this time of this writing, bootstrap has about 2 versions:
  - [v3.3.7](http://getbootstrap.com/)
  - [v4-alpha](https://v4-alpha.getbootstrap.com/)

## Getting Started

- Get bootstrap to your local development. There are several methods available
  + Download manually, please go [here](http://getbootstrap.com/getting-started/#download)
  + Clone source code from github

  ```sh
    git clone git@github.com:twbs/bootstrap.git
  ```

  + Using `bower`

  ```sh
    bower install bootstrap
  ```

  + And other methods [here](http://getbootstrap.com/getting-started/#download-npm)

- Folder directories
  ![Bootstrap Directories](/assets/images/bootstrap_directories.png)

- However, we will use `sass` to demo customization for Bootstrap, so we will get
bootstrap for SASS instead. Although, we could get [bootstrap for sass](https://github.com/twbs/bootstrap-sass),
I would like to use `v4-alpha` for demonstration, as it already contains `sass` files

  ```sh
  bower install bootstrap#v4.0.0-alpha.6
  ```

- Once again, bootstrap directories
  ![Bootstrap Directories](/assets/images/bootstrap_directories_4_alpha.png)

## References

- [Bootstrap](http://getbootstrap.com/)
