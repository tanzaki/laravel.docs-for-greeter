# Helpers

- [Introduction](#introduction)
- [Available Methods](#available-methods)

<a name="introduction"></a>
## Introduction

Laravel includes a variety of global "helper" PHP functions. Many of these functions are used by the framework itself; however, you are free to use them in your own applications if you find them convenient.

<a name="available-methods"></a>
## Available Methods

<style>
    .collection-method-list > p {
        column-count: 3; -moz-column-count: 3; -webkit-column-count: 3;
        column-gap: 2em; -moz-column-gap: 2em; -webkit-column-gap: 2em;
    }

    .collection-method-list a {
        display: block;
    }
</style>


### Strings

<div class="collection-method-list" markdown="1">

- [class_basename](#method-class-basename)
- [snake_case](#method-snake-case)
- [str_plural](#method-str-plural)
- [str_singular](#method-str-singular)
- [title_case](#method-title-case)

</div>

### URLs

<div class="collection-method-list" markdown="1">

- [route](#method-route)
- [url](#method-url)

</div>

### Miscellaneous

<div class="collection-method-list" markdown="1">

- [request](#method-request)

</div>

<a name="method-listing"></a>
## Method Listing

<style>
    #collection-method code {
        font-size: 14px;
    }

    #collection-method:not(.first-collection-method) {
        margin-top: 50px;
    }
</style>

<a name="strings"></a>
## Strings

<a name="method-class-basename"></a>
#### `class_basename()` 

The `class_basename` returns the class name of the given class with the class' namespace removed:

    $class = class_basename('App\Foo\Bar\Comment');

    // Comment

<a name="method-snake-case"></a>
#### `snake_case()` 

The `snake_case` function converts the given string to `snake_case`:

    $snake = snake_case('fooBar');

    // foo_bar

    $snake = snake_case('Comment');

    // comment


<a name="method-str-plural"></a>
#### `str_plural()` 

The `str_plural` function converts a string to its plural form. This function currently only supports the English language:

    $plural = str_plural('comment');

    // comments

    $plural = str_plural('task');

    // tasks

    $plural = str_plural('child');

    // children

You may provide an integer as a second argument to the function to retrieve the singular or plural form of the string:

    $plural = str_plural('child', 2);

    // children

    $plural = str_plural('child', 1);

    // child

<a name="method-str-singular"></a>
#### `str_singular()` 

The `str_singular` function converts a string to its singular form. This function currently only supports the English language:

    $singular = str_singular('comments');

    // comment
    
    $singular = str_singular('tasks');

    // task

<a name="method-title-case"></a>
#### `title_case()` 

The `title_case` function converts the given string to `Title Case`:

    $title = title_case('a nice title uses the correct case');

    // A Nice Title Uses The Correct Case

<a name="urls"></a>
## URLs


<a name="method-route"></a>
#### `route()` 

The `route` function generates a URL for the given named route:

    $url = route('routeName');

If the route accepts parameters, you may pass them as the second argument to the method:

    $url = route('routeName', ['id' => 1]);

By default, the `route` function generates an absolute URL. If you wish to generate a relative URL, you may pass `false` as the third parameter:

    $url = route('routeName', ['id' => 1], false);

<a name="method-url"></a>
#### `url()` 

The `url` function generates a fully qualified URL to the given path:

    echo url('user/profile');

    echo url('user/profile', [1]);

If no path is provided, a `Illuminate\Routing\UrlGenerator` instance is returned:

    echo url()->current();
    echo url()->full();
    echo url()->previous();

<a name="miscellaneous"></a>
## Miscellaneous

<a name="method-request"></a>
#### `request()` 

The `request` function returns the current [request](/docs/{{version}}/requests) instance or obtains an input item:

    $request = request();

    $value = request('key', $default = null)

