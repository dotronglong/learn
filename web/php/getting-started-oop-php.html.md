---
title: Getting Started - OOP
category: PHP
show_navigation: true
---

## Introduction

- PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used open source
general-purpose scripting language that is especially suited for web development
and can be embedded into HTML.

- PHP is 21 years old, since the first appeared in 1995, and latest version is 7

## Basic Syntax

- When PHP parses a file, it looks for opening and closing tags, which are `<?php` and `?>`
which tell PHP to start and stop interpreting the code between them. Parsing in this manner
allows PHP to be embedded in all sorts of different documents, as everything outside of a pair
of opening and closing tags is ignored by the PHP parser.

- Variables

  ```php
  <?php
  $my_var = 5;
  $my_string = "This is my string";
  ?>
  ```

- Function

  ```php
  <?php
  function my_func($my_argument) {
    // your function definition goes here
  }

  function my_func_reference(&$my_argument) {
    // the value of $my_argument could be changed when function is done
  }
  ?>
  ```

- Class

  ```php
  <?php
  class MyClass
  {
      public $myPublicVar;
      protected $myProtectedVar;
      private $myPrivateVar;

      public static function myPublicStaticMethod() {}
      public function myPublicMethod() {}
      protected function myProtectedMethod() {}
      private function myPrivateMethod() {}  
  }
  ?>
  ```

## Object Oriented Programming (OOP)

- I will not spend hours to explain about OOP in details, you can always search more on
Google or reference in bottom of page.

- Here are simple ways to come through OOP in PHP

- **Inheritance**

  ```php
  <?php
  Class Animal
  {
      protected $gender;
      protected $weight;

      public function getGender() { return $this->gender; }
      public function getWeight() { return $this->type; }
  }

  class Cow extends Animal
  {
      private $name;

      public function __construct($gender, $weight)
      {
          $this->gender = $gender;
          $this->weight = $weight;
      }

      public function setName($name) { $this->name = $name; }
      public function getName() { return $this->name; }
  }

  $cow = new Cow('male', 2);
  $cow->setName('Billy');

  echo print_r($cow, true);
  ?>
  ```

  _If you run the script it will render as below_

  ```sh
  php yourscript.php
  # Cow Object
  # (
  #     [name:Cow:private] => Billy
  #     [gender:protected] => male
  #     [weight:protected] => 2
  # )
  ```

- **Interfaces**

  _With me, `interfaces` is the way you think instead of coding, you plan for any methods
  you want to be in your classes_

  ```php
  <?php
  interface WalkableAnimal
  {
      public function walk();
  }

  interface FlyableAnimal
  {
      public function fly();
  }

  Class Animal
  {
      protected $gender;
      protected $weight;

      public function getGender() { return $this->gender; }
      public function getWeight() { return $this->type; }
  }

  class Cow extends Animal implements WalkableAnimal
  {
      private $name;

      public function __construct($gender, $weight)
      {
          $this->gender = $gender;
          $this->weight = $weight;
      }

      public function setName($name) { $this->name = $name; }
      public function getName() { return $this->name; }

      public function walk() { /* walk ... */ }
  }

  class Bird extends Animal implements WalkableAnimal, FlyableAnimal
  {
      public function walk() { /* walk ... */ }
      public function fly() { /* fly ... */ }
  }
  ?>
  ```

  _As you can see, `Bird` is an animal which can fly and walk, however, `Cow` is only
  able to walk. It means, besides that they are both Animal, but they could have different abilities_

## References

- [PHP Manual](http://php.net/manual/en/intro-whatis.php)
- [PHP Wiki](https://en.wikipedia.org/wiki/PHP)
- [OOP Wiki](https://en.wikipedia.org/wiki/Object-oriented_programming)
