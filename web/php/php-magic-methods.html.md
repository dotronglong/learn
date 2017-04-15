---
title: Advanced Techniques With Magic Methods
category: PHP
show_navigation: true
---

## Introduction

- Magic methods is a way to make your coding easier, however, `I suggest not to use
it if you could solve your problems in another way because it makes your code harder to
maintain or find bugs.`

- According to PHP, _PHP reserves all function names starting with `__` as magical.
It is recommended that you do not use function names with `__` in PHP unless you want
some documented magic functionality._

- There are several magic methods we can count on are:
  + `__construct` and `__destruct`
  + `__call` and `__callStatic`
  + `__get` and `__get`
  + `__isset` and `__unset`
  + `__sleep` and `__wakeup`
  + `__toString`
  + `__invoke`
  + `__set_state`
  + `__clone`
  + `__debuginfo`

## Start Magic

In this page, I only address only some of magic methods, and you can always see more
about the others by clicking on the link in `References` section at the bottom of page

- `__call` and `__callStatic`
  + `__call` allows you to collect processes of any methods which are not explicitly
  described in the body of class. The reason of this method is sometimes you don't
  want to repeat yourself to write process for similar methods; therefore, the better way
  is only perform actions at one place

  ```php
  <?php
  class Student
  {
      private $name;
      private $age;

      public function __construct($name, $age)
      {
          $this->name = $name;
          $this->age  = $age;
      }

      public function __call($name, $arguments = [])
      {
          if (strpos($name, 'getProperty') === 0) {
              $property = strtolower(str_replace('getProperty', '', $name));
              if (property_exists($this, $property)) {
                  return $this->$property;
              } else {
                  throw new \Exception("$property is not found");
              }
          }
      }
  }

  $student = new Student('Long', 28);
  var_dump($student->getPropertyName());
  var_dump($student->getPropertyGender());
  ?>
  ```

  _When you execute upon script, the result would be as below_

  ```sh
  # string(4) "Long"

  # Fatal error: Uncaught exception 'Exception' with message 'gender is not found' in demo.php:20
  # Stack trace:
  # #0 demo.php(28): Student->__call('getPropertyGend...', Array)
  # #1 demo.php(28): Student->getPropertyGender()
  # #2 {main}
  #   thrown in demo.php on line 20

  ```

  + `__callStatic` is pretty similar to `__call`, however, it has `static` scope.

  ```php
  <?php
  class Package
  {
      private static $version = '1.1.1';
      private static $author  = 'Long Do <me@dotronglong.com>';

      public static function __callStatic($name, $arguments = [])
      {
          if (strpos($name, 'getProperty') === 0) {
              $property = strtolower(str_replace('getProperty', '', $name));
              if (isset(static::${$property})) {
                  return static::${$property};
              } else {
                  throw new \Exception("$property is not found");
              }
          }
      }
  }

  var_dump(Package::getPropertyAuthor());
  var_dump(Package::getPropertyVendor());
  ?>
  ```

  And the result is quite similar to `__call`

  ```sh
  # string(28) "Long Do <me@dotronglong.com>"

  # Fatal error: Uncaught exception 'Exception' with message 'vendor is not found' in demo.php:14
  # Stack trace:
  # #0 demo.php(21): Package::__callStatic('getPropertyVend...', Array)
  # #1 demo.php(21): Package::getPropertyVendor()
  # #2 {main}
  #   thrown in demo.php on line 14
  ```

- `__isset` and `__unset`, `__get` and `__set`

  _These are magic methods which enable ability to directly access to properties of an object.
  Let see following example_

  ```php
  <?php
  class Student
  {
      private $data = [];

      public function __isset($property)
      {
          return isset($this->data[$property]);
      }

      public function __unset($property)
      {
          unset($this->data[$property]);
      }

      public function __set($property, $value)
      {
          $this->data[$property] = $value;
      }

      public function __get($property)
      {
          if (isset($this->data[$property])) {
              return $this->data[$property];
          } else {
              throw new \Exception("$property does not exists");
          }
      }
  }

  $student = new Student();
  $student->age = 28;
  var_dump(isset($student->age));
  var_dump(isset($student->name));
  var_dump($student->age);
  unset($student->age);
  var_dump($student->age);
  ?>
  ```

  As a result, it could be seen as below if you run that script

  ```sh
  # bool(true)
  # bool(false)
  # int(28)

  # Fatal error: Uncaught exception 'Exception' with message 'age does not exists' in demo.php:26
  # Stack trace:
  # #0 demo.php(37): Student->__get('age')
  # #1 {main}
  #   thrown in demo.php on line 26
  ```

  **This is only useful when you are dealing with unknown data structure, as you don't know
  exactly properties your class will store**
  
## References

- [PHP Manual](http://php.net/manual/en/language.oop5.magic.php)  
