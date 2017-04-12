---
title: jQuery and Bower
category: Javascript
show_navigation: true
---

## Bower

### Introduction
- [Bower](https://bower.io/) is a package manager for front-end stuffs.
- Why do we need a package manager? What was it before Bower?
  + With `bower`, we can easily manage all our required packages
  + Before **Bower** we used to download manually any packages we want to add into our project.
- Suppose that we need jQuery and Bootstrap for our great project, here are things we have to do with or without Bower

  + **Without** _Bower_, we have to go to [jQuery](https://jquery.com/) and [Bootstrap](http://getbootstrap.com/) to download our libraries. Just in case you spent a lot of projects enough to realize that it really a mess if Bootstrap package requires jQuery v1.x while we are download jQuery v2.x? In addition,
  if Bootstrap requires a lot of many packages, it would be a crazy time to get them all.

  + **With** _Bower_, everything seems easier by running these commands

  ```shell
      bower install jquery
      # bower jquery#*                  cached https://github.com/jquery/jquery-dist.git#3.2.1
      # bower jquery#*                validate 3.2.1 against https://github.com/jquery/jquery-dist.git#*
      # bower jquery#^3.2.1            install jquery#3.2.1
      #
      # jquery#3.2.1 bower_components/jquery

      bower install bootstrap
      # bower bootstrap#*               cached https://github.com/twbs/bootstrap.git#3.3.6
      # bower bootstrap#*             validate 3.3.6 against https://github.com/twbs/bootstrap.git#*
      # bower bootstrap#*                  new version for https://github.com/twbs/bootstrap.git#*
      # bower bootstrap#*              resolve https://github.com/twbs/bootstrap.git#*
      # bower bootstrap#*             download https://github.com/twbs/bootstrap/archive/v3.3.7.tar.gz
      # bower bootstrap#*             progress received 3.8MB of 4.0MB downloaded, 95%
      # bower bootstrap#*              extract archive.tar.gz
      # bower bootstrap#*             resolved https://github.com/twbs/bootstrap.git#3.3.7
      # bower bootstrap#^3.3.7         install bootstrap#3.3.7
      #
      # bootstrap#3.3.7 bower_components/bootstrap
      # └── jquery#3.2.1
  ```

  And let Bower do the hard parts for us including version management.

### Quick Start
- Firstly, remember to read more about Bower [here](https://bower.io/)
- Secondly, but most important part is download `npm` and install `bower`. It might be tough at the beginning, but everything goes smoothly after that big step.
- `node` and `npm` could be found [here](https://nodejs.org/en/download/)
- Verify that `npm` is installed successfully

  ```shell
  npm -v
  # 4.4.4
  ```

- Install bower as global (recommended), however, it could be install locally

  ```shell
  # Install as a global executive program
  npm install -g bower

  # Install for local usage
  npm install bower
  ```

- Verify that `bower` is successfully installed

  ```shell
  bower -v
  # 1.8.0
  ```

### How to use
- Install a package

  ```shell
  bower install [package]
  ```

- Install a package and save as dependency

  ```shell
  # Install as required dependency
  bower install -S [package]

  # Install as dev-required dependency
  bower install -D [package]
  ```

## jQuery
