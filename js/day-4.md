# jQuery and Bower

### Bower

#### Introduction
- [Bower](https://bower.io/) is a package manager for front-end stuffs.
- Why do we need a package manager? What was it before Bower?
  + With `bower`, we can easily manage all our required packages
  + Before **Bower** we used to download manually any packages we want to add into our project.
- Suppose that we need jQuery and Bootstrap for our great project, here are things we have to do with or without Bower
  + Without Bower, we have to go to [jQuery](https://jquery.com/) and [Bootstrap](http://getbootstrap.com/) to download our libraries. Just in case you spent a lot of projects enough to realize that it really a mess if Bootstrap package requires jQuery v1.x while we are download jQuery v2.x
  + With Bower, everything seems easier by running these commands

  {% highlight shell %}
  bower install jquery
  bower install bootstrap
  {% endhighlight %}

  And let Bower do the hard parts for us including version management.

#### Quick Start
- Firstly, remember to read more about Bower [here](https://bower.io/)
- Secondly, but most important part is download `npm` and install `bower`. It might be tough at the beginning, but everything goes smoothly after that big step.
- `node` and `npm` could be found [here](https://nodejs.org/en/download/)
- Verify that `npm` is installed successfully

  {% highlight shell %}
  npm -v
  {% endhighlight %}

- Install bower as global (recommended), however, it could be install locally

  {% highlight shell %}
  # Install as a global executive program
  npm install -g bower

  # Install for local usage
  npm install bower
  {% endhighlight %}

- Verify that `bower` is successfully installed

  {% highlight shell %}
  bower -v
  {% endhighlight %}

#### How to use
- Install a package

  {% highlight shell %}
  bower install [package]
  {% endhighlight %}

- Install a package and save as dependency

  {% highlight shell %}
  # Install as required dependency
  bower install -S [package]

  # Install as dev-required dependency
  bower install -D [package]
  {% endhighlight %}

### jQuery
