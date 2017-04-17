---
title: Composer
category: PHP
show_navigation: true
---

## Introduction

- Composer is a tool for dependency management in PHP. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.

- Question? Why do we need a dependency management? The answer quite easy is that make the
difficult work becomes simple.

- It would be painful to keep track and update packages when your project grows. Imagine that
one day you want to get a specific version of a library, but at that moment the library requires
other libraries, so it is really hard for you to download all of them.

## Install Composer

- Using `php`

  ```sh
  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
  php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
  php composer-setup.php
  php -r "unlink('composer-setup.php');"
  ```

- Using `curl`

  ```sh
  curl -SLO https://getcomposer.org/composer.phar
  chmod +x composer.phar
  sudo mv composer.phar /usr/bin/local/composer
  ```

- Using `docker`

  ```sh
  echo '#!/bin/bash' >> composer
  echo 'docker run -v $PWD:/app composer/composer ${@}' >> composer
  chmod +x composer
  sudo mv composer /usr/bin/local/composer
  ```

## Quick Usage

- Install a package

  ```sh
  composer require [package]
  ```

- Update a package

  ```sh
  composer update [package]
  ```

- Require autoloader in your main `.php` file

  ```php
  <?php require __DIR__ . '/vendor/autoload.php';
  ```

- Search for packages at [Packagist](https://packagist.org/)

## Notes

- Ignore `composer.lock` or not? This is always a question with any developers when
starting with Composer. You should make your choice when working with composer within
team agreement, however, there are some things you can consider about:
  + Without `composer.lock`, your local, teammates' local and any other environments might
  be different, as composer will generate it whenever it installs packages (or updates). Therefore,
  it would cause some unexpected issues.
  + With `composer.lock`, you can control the version of packages which your team are using, and
  obviously it is a recommendation to be a best practice for composer.

- You can add your scripts to a specific event of Composer to help set up your
project, read more at [here](https://getcomposer.org/doc/articles/scripts.md)

## References

- [Composer](https://getcomposer.org)
- [Packagist](https://packagist.org/)
