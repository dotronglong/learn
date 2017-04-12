# Object in Javascript

### Introduction
- Object is mostly a JSON object which contains properties. However, it is not only
a JSON object, but it could be able to define methods also.
- Which Object in JS does not have? `Inheritance`, `Polymorphism`. It is just simply
a struct with a set of `properties` and `methods`.

### Define object
- An empty object

{% highlight JavaScript %}
var myObj = {};
{% endhighlight %}

- An object with properties

{% highlight JavaScript %}
var student = {
    name: '',
    age: ''
};
{% endhighlight %}

- An object with methods

{% highlight JavaScript %}
var student = {
    name: 'John',
    getName: function() {
        return this.name;
    }
};
{% endhighlight %}

**Notes**
- It should be a semicolon `;` at the end of object declaration
- It **must** be a comma after `property` or `method`
- A method of an object is just a `function`
- Use `this` inside object to access `properties` and `methods` of current object
- Be remember to declare a temporary variable which is a reference to `this` cursor before entering a `function phase`. See example `#2`

### Examples
- Manage pagination with JS

{% highlight JavaScript %}
var pagination = {
    current: 1,
    baseUrl: '/post',
    next: function() {
        var page = this.current + 1;
        window.location.href = baseUrl + '?page=' + page;
    },
    prev: function() {
        var page = this.current - 1;
        if (page < 0) {
            page = 0;
        }
        window.location.href = baseUrl + '?page=' + page;
    }
};
// go to next page
pagination.next();

// go to previous page
pagination.prev();
{% endhighlight %}

- Build a simple slider

{% highlight JavaScript %}
var slider = {
    target: null,
    bind: function() {
        var self = this;
        window.onload = function() {
            document.getElementById(target).scroll = function() {
                // scrolling
                // this will not work here because this belongs to current function
                // but self will
            };
        }
    }
};
{% endhighlight %}

### Conclusion
- Instead of writing a lot of separate functions, we could combine them into one object for easier in manipulation
- Remember the context when using `this`, use a temporary variable for referencing to `this` in case `this` belongs to another function at specific time in the future.
- Remember [KISS](https://en.wikipedia.org/wiki/KISS_principle) (Keep It Simple, Stupid) principle.
