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

## Customize Bootstrap

- Create a folder to store your custom theme, for instance, `mytheme` next to bootstrap
directory. Create a file `style.scss` inside newly created folder.

  ![MyTheme Folder](/assets/images/mytheme_folder.png)

- Start SASS to watch for changes

  ```sh
  sass --watch mytheme/style.scss:mytheme/style.css
  ```

- Import variables, mixins and any components we want to have in our customized theme from bootstrap

  ```scss
  @import "../bootstrap/scss/variables";
  @import "../bootstrap/scss/mixins";
  @import "../bootstrap/scss/grid";
  @import "../bootstrap/scss/buttons";
  ```

  _Then you could see the `style.css` will have generated content similar to below_

  ```css
  .container {
    position: relative;
    margin-left: auto;
    margin-right: auto;
    padding-right: 15px;
    padding-left: 15px; }
    @media (min-width: 576px) {
      .container {
        padding-right: 15px;
        padding-left: 15px; } }

      /* ... */

  input[type="submit"].btn-block,
  input[type="reset"].btn-block,
  input[type="button"].btn-block {
    width: 100%; }

  /*# sourceMappingURL=style.css.map */      
  ```

- Then you import new theme to our `index.html` HTML file and see result

  ```html
  <html>
  <head>
  <link rel="stylesheet" href="./mytheme/style.css"/>
  </head>
  <body>
    <button type="button" class="btn btn-primary">My Button</button>
  </body>
  </html>
  ```

- Open that file in browser, you would be able to see this result

  ![Default Buttons](/assets/images/first_bootstrap_buttons.png)

- Next, we edit `style.scss` file to add our customized value for bootstrap's variables

  ```scss
  $brand-primary: #0f3066;

  @import "../bootstrap/scss/variables";
  @import "../bootstrap/scss/mixins";
  @import "../bootstrap/scss/grid";
  @import "../bootstrap/scss/buttons";
  ```

- Open web browser again, you will see the background color of button was changed

  ![Default Buttons](/assets/images/bg_change_bootstrap_buttons.png)

- That's the way we could customized bootstrap for our own projects. To see more variables, you
could open file `bootstrap/scss/_variables.scss`. From this first step, you can change bootstrap into
whatever you want without making changes on bootstrap source code. In addition, you do not need to
import all of bootstrap's components, but only the components you want to bring to your projects, it would
save a lot of space and let your site load faster.

## References

- [Bootstrap](http://getbootstrap.com/)
