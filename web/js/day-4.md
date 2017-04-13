---
title: Bower and jQuery
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

### Configuration
- First of all, Bower will install all of your packages and their dependencies under
folder name `bower_components`. If you want to change it to another place, e.g, `vendor`
then you need to configure it.
- In order to configure for your project only, you have to create a file named `.bowerrc`

  ```json
  {
    "directory": "vendor/",
    "timeout": 120000,
    "registry": {
      "search": [
        "http://localhost:8000",
        "https://bower.herokuapp.com"
      ]
    }
  }
  ```

- Advanced configuration could be found [here](https://bower.io/docs/config/)

## jQuery

### Introduction

- What do they say about jQuery?

  ```text
  jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript.
  ```

- What do I say about jQuery?

  ```text
  jQuery is a set of utilities which help to write JavaScript easier
  ```

- The reason which we need to use jQuery or similar libraries beyond the powerful
of utilities they provide is the `cross-browser` ability. Furthermore, you might have to
spend hours in making your script works as same as it does on Chrome to Safari,
Opera, etc.
- Add jQuery to your project is easy with below actions
  + Use bower to get latest `stable` source to your project

  ```shell
  bower install -S jquery
  ```

  + Insert jQuery to your main template

  ```html
  <script type="text/javascript" src="./bower_components/jquery/dist/jquery.min.js"></script>
  ```

### Common mistakes
- Always think about the time which jQuery is usable, it means that please make sure
that you run jQuery only when it is fully loaded.

  ```javascript
  // It might not work
  console.log(jQuery('#some-id').text());

  // It will work like a charm
  jQuery(document.body).ready(function() {
      console.log(jQuery('#some-id').text());
  });
  ```

- Naming conflict. Developers use to call jQuery by `$`, however, in some case (like a big project),
you are not only using jQuery as a JavaScript library, but also use another library, such as **prototype.js**,
**MooTools**, or **YUI**. Therefore, in general, we have about 3 ways to overcome this problem
  + Always use jQuery from calling `jQuery` instead of `$`
  + Use `$` under `jQuery` callback

  ```javascript
    jQuery(document).ready(function( $ ) {
      // Your jQuery code here, using $ to refer to jQuery.
    });
  ```

  + Use `jQuery.noConflict()` to make an alias or define jQuery separately

  ```javascript
    // Create new alias to jQuery
    var $jq = jQuery.noConflict();
    console.log($jq('#some-id').text());
  ```

  ```javascript
    jQuery.noConflict();

    (function( $ ) {
        // Your jQuery code here, using the $
    })( jQuery );
  ```

  Additional information could be found [here](https://learn.jquery.com/using-jquery-core/avoid-conflicts-other-libraries/)

- **Be courageous to remove jQuery**
  _Sometimes things can be done easily via CSS without even thinking about jQuery
  but we don't realize it. Plain CSS is far better than jQuery. So be open and courageous
  to remove jQuery whenever needed._

- **Not using latest version of jQuery**
  _jQuery team is keep on updating the jQuery library and the newer version comes with
  lots of bug fixes and performance enhancement. I understand that it is not always
  possible for you to use the latest version for your old projects but I suggest for
  your new projects, you can use latest version of jQuery_

- **Not using minified version of jQuery library**
  _The jQuery library (when you download) comes in two versions._

  + _Production (Compressed Version)_
  + _Development (Uncompressed Version)_

  _For development purpose, you can choose the development version of .js file as if
  you want to make some changes then that can be easily done. But ensure that
  when your software or product goes on production, always use the production
  version of .js file as its size is 5 times lesser than the development version.
  This can save some amount of bandwidth._

- **Not using selectors efficiently**
  _Be smart while using selectors. As there are many ways to select element using
  selectors but that doesn't mean that all are equal. Always try to use ID and Element
  as selector as they are very fast. Even the class selectors are slower than ID selector._

  _When IDs are used as selector then jQuery internally makes a call to getElementById()
  method of Java script which directly maps to the element._

  _When Classes are used as selector then jQuery has to do DOM traversal.So when DOM traversal
  is performed via jQuery takes more time to select elements. In terms of speed and performance,
  it is best practice to use IDs as selector._

- **Using jQuery selectors repeatedly**
  _Take a look at below jQuery code. The selectors are used thrice for 3 different operation._

  ```javascript
  $("#myID").css("color", "red");
  $("#myID").css("font", "Arial");
  $("#myID").text("Error occurred!");
  ```

  _The problem with above code is, jQuery has to traverse 3 times as there are 3 different statements.
  But this can be combined into a single statement._

  ```javascript
  $("#myID").css({ "color": "red", "font": "Arial"}).text("Error occurred!");
  ```

  _This will ensure that jQuery traverse only once through DOM while selecting the element._

- **Not knowing how selectors are executed**
  _Do you know how the selectors are executed? Your last selectors is always executed first.
  For example, in below jQuery code, jQuery will first find all the elements with
  class ".myCssClass" and after that it will reject all the other elements which are not in "p#elmID"._

  ```javascript
  $("p#elmID .myCssClass");
  ```

- **By not caching the stuff**
  _Caching is an area which can give you awesome performance, if used properly and at the right place.
  While using jQuery, you should also think about caching. For example, if you are using any element
  in jQuery more than one time, then you must cache it. See below code._

  ```javascript
  $("#myID").css("color", "red");
  //Doing some other stuff......
  $("#myID").text("Error occurred!");  
  ```

  _Now in above jQuery code, the element with #myID is used twice but without caching.
  So both the times jQuery had to traverse through DOM and get the element.
  But if you have saved this in a variable then you just need to reference the variable.
  So the better way would be,_

  ```javascript
  var $myElement = $("#myID").css("color", "red");
  //Doing some other stuff......
  $myElement.text("Error occurred!");
  ```

  _So now in this case, jQuery won't need to traverse through the whole DOM tree
  when it is used second time. So in jQuery, Caching is like saving the jQuery selector
  in a variable. And using the variable reference when required instead of searching through DOM again._

- **Not checking while using various plugins**
  _One of the great feature of jQuery is various plugins available created using
  jQuery are available for free. You like a jQuery plugin and start using it in your project.
  But while using plugins do you really consider,_

  + _File size_
  + _Performance of plugin_
  + _Browser Compatibility_

  _Before using any plugin, always ensure that it must not hit performance of your page
  and it should not conflict with other plugins that you are using already._

### Dig into jQuery
Now, it's time for [jQuery Tutorials](jquery.html)

### References

- [Bower Configuration](https://bower.io/docs/config/)
- [jQuery API](http://api.jquery.com/)
- [Learn jQuery](https://learn.jquery.com/)
- [jQuery Common Mistakes](http://www.jquerybyexample.net/2013/02/common-jquery-mistakes-errors.html)
