---
title: jQuery Tutorials
category: Javascript
show_navigation: true
---

## Element Selectors

- Element Selectors is the most important of jQuery, only when you understand fully and deeply
about the way to select elements you could use jQuery efficiently.

- jQuery is powerful enough to fully allow using almost everything which css selectors provide.
Therefore, it will be a lot easier if you know CSS selectors. See some examples below

  ```javascript
  // select a specific div with id
  $('#myDiv')

  // select elements have a specific class
  $('.my-class')

  // select elements have one or more classes
  $('.my-class.my-other-class')

  // select all children of a specific element which have appropriate class
  $('.my-parent-div .my-children-class')

  // select all direct children
  $('.my-parent-div > .my-direct-children')
  ```

- See more at [W3Schools](https://www.w3schools.com/cssref/css_selectors.asp)

## AJAX with jQuery

### Introduction
- What is AJAX? Read definition on [Wiki](https://en.wikipedia.org/wiki/Ajax_(programming))
- General speaking, AJAX allows us not to wait result of an external resource, and only
process result whenever it comes to browser, or it could be called as `non-blocking` action
- In addition, AJAX allow us to perform background requests to server without submitting form or
direct in browser

### How to use
- [Raw javascript / Traditional way](https://en.wikipedia.org/wiki/Ajax_(programming)#Examples)
- With jQuery it pretty simple

  ```javascript
  $.ajax({
    url: 'your_domain.com/your_action',
    method: 'POST',
    data: {
      my_data: my_value
    },
    success: function(result, status, jqXHR) {
      // do something with your result
    },
    error: function(jqXHR, status, error) {
      // handle your error here
    }
  });
  ```

- See more [jQuery Ajax](http://api.jquery.com/jquery.ajax/)

## Style effects

With style effects, you could do a lot of effects to your element without do some
crazy functions to perform them

- `fadeIn`, `fadeOut`, `fadeTo`

  ```javascript
  $("p").fadeIn();
  ```

- Slowly scroll to top.

  ```javascript
  $("html, body").animate({ scrollTop: 0 }, "slow");
  ```

- See more [jQuery Effects](https://www.w3schools.com/jquery/jquery_ref_effects.asp)  
