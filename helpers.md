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

[class_basename](#method-class-basename)
[snake_case](#method-snake-case)
[str_plural](#method-str-plural)
[str_singular](#method-str-singular)
[title_case](#method-title-case)

</div>

### URLs

<div class="collection-method-list" markdown="1">

[action](#method-action)
[asset](#method-asset)
[secure_asset](#method-secure-asset)
[route](#method-route)
[secure_url](#method-secure-url)
[url](#method-url)

</div>

### Miscellaneous

<div class="collection-method-list" markdown="1">

[abort](#method-abort)
[abort_if](#method-abort-if)
[abort_unless](#method-abort-unless)
[auth](#method-auth)
[back](#method-back)
[bcrypt](#method-bcrypt)
[cache](#method-cache)
[collect](#method-collect)
[config](#method-config)
[csrf_field](#method-csrf-field)
[csrf_token](#method-csrf-token)
[dd](#method-dd)
[dispatch](#method-dispatch)
[env](#method-env)
[event](#method-event)
[factory](#method-factory)
[info](#method-info)
[logger](#method-logger)
[method_field](#method-method-field)
[old](#method-old)
[redirect](#method-redirect)
[request](#method-request)
[response](#method-response)
[retry](#method-retry)
[session](#method-session)
[value](#method-value)
[view](#method-view)

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

<a name="method-action"></a>
#### `action()` 

The `action` function generates a URL for the given controller action. You do not need to pass the full namespace to the controller. Instead, pass the controller class name relative to the `App\Http\Controllers` namespace:

    $url = action('HomeController@getIndex');

If the method accepts route parameters, you may pass them as the second argument to the method:

    $url = action('UserController@profile', ['id' => 1]);

<a name="method-asset"></a>
#### `asset()` 

Generate a URL for an asset using the current scheme of the request (HTTP or HTTPS):

    $url = asset('img/photo.jpg');

<a name="method-secure-asset"></a>
#### `secure_asset()` 

Generate a URL for an asset using HTTPS:

    echo secure_asset('foo/bar.zip', $title, $attributes = []);

<a name="method-route"></a>
#### `route()` 

The `route` function generates a URL for the given named route:

    $url = route('routeName');

If the route accepts parameters, you may pass them as the second argument to the method:

    $url = route('routeName', ['id' => 1]);

By default, the `route` function generates an absolute URL. If you wish to generate a relative URL, you may pass `false` as the third parameter:

    $url = route('routeName', ['id' => 1], false);

<a name="method-secure-url"></a>
#### `secure_url()` 

The `secure_url` function generates a fully qualified HTTPS URL to the given path:

    echo secure_url('user/profile');

    echo secure_url('user/profile', [1]);

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

<a name="method-abort"></a>
#### `abort()` 

The `abort` function throws a HTTP exception which will be rendered by the exception handler:

    abort(401);

You may also provide the exception's response text:

    abort(401, 'Unauthorized.');

<a name="method-abort-if"></a>
#### `abort_if()` 

The `abort_if` function throws an HTTP exception if a given boolean expression evaluates to `true`:

    abort_if(! Auth::user()->isAdmin(), 403);

<a name="method-abort-unless"></a>
#### `abort_unless()` 

The `abort_unless` function throws an HTTP exception if a given boolean expression evaluates to `false`:

    abort_unless(Auth::user()->isAdmin(), 403);

<a name="method-auth"></a>
#### `auth()` 

The `auth` function returns an authenticator instance. You may use it instead of the `Auth` facade for convenience:

    $user = auth()->user();

<a name="method-back"></a>
#### `back()` 

The `back()` function generates a redirect response to the user's previous location:

    return back();

<a name="method-bcrypt"></a>
#### `bcrypt()` 

The `bcrypt` function hashes the given value using Bcrypt. You may use it as an alternative to the `Hash` facade:

    $password = bcrypt('my-secret-password');

<a name="method-cache"></a>
#### `cache()` 

The `cache` function may be used to get values from the cache. If the given key does not exist in the cache, an optional default value will be returned:

    $value = cache('key');

    $value = cache('key', 'default');

You may add items to the cache by passing an array of key / value pairs to the function. You should also pass the number of minutes or duration the cached value should be considered valid:

    cache(['key' => 'value'], 5);

    cache(['key' => 'value'], Carbon::now()->addSeconds(10));

<a name="method-collect"></a>
#### `collect()` 

The `collect` function creates a [collection](/docs/{{version}}/collections) instance from the given array:

    $collection = collect(['taylor', 'abigail']);

<a name="method-config"></a>
#### `config()` 

The `config` function gets the value of a configuration variable. The configuration values may be accessed using "dot" syntax, which includes the name of the file and the option you wish to access. A default value may be specified and is returned if the configuration option does not exist:

    $value = config('app.timezone');

    $value = config('app.timezone', $default);

The `config` helper may also be used to set configuration variables at runtime by passing an array of key / value pairs:

    config(['app.debug' => true]);

<a name="method-csrf-field"></a>
#### `csrf_field()` 

The `csrf_field` function generates an HTML `hidden` input field containing the value of the CSRF token. For example, using [Blade syntax](/docs/{{version}}/blade):

    {{ csrf_field() }}

<a name="method-csrf-token"></a>
#### `csrf_token()` 

The `csrf_token` function retrieves the value of the current CSRF token:

    $token = csrf_token();

<a name="method-dd"></a>
#### `dd()` 

The `dd` function dumps the given variables and ends execution of the script:

    dd($value);

    dd($value1, $value2, $value3, ...);

If you do not want to halt the execution of your script, use the `dump` function instead:

    dump($value);

<a name="method-dispatch"></a>
#### `dispatch()` 

The `dispatch` function pushes a new job onto the Laravel [job queue](/docs/{{version}}/queues):

    dispatch(new App\Jobs\SendEmails);

<a name="method-env"></a>
#### `env()` 

The `env` function gets the value of an environment variable or returns a default value:

    $env = env('APP_ENV');

    // Return a default value if the variable doesn't exist...
    $env = env('APP_ENV', 'production');

<a name="method-event"></a>
#### `event()` 

The `event` function dispatches the given [event](/docs/{{version}}/events) to its listeners:

    event(new UserRegistered($user));

<a name="method-factory"></a>
#### `factory()` 

The `factory` function creates a model factory builder for a given class, name, and amount. It can be used while [testing](/docs/{{version}}/database-testing#writing-factories) or [seeding](/docs/{{version}}/seeding#using-model-factories):

    $user = factory(App\User::class)->make();

<a name="method-info"></a>
#### `info()` 

The `info` function will write information to the log:

    info('Some helpful information!');

An array of contextual data may also be passed to the function:

    info('User login attempt failed.', ['id' => $user->id]);

<a name="method-logger"></a>
#### `logger()` 

The `logger` function can be used to write a `debug` level message to the log:

    logger('Debug message');

An array of contextual data may also be passed to the function:

    logger('User has logged in.', ['id' => $user->id]);

A [logger](/docs/{{version}}/errors#logging) instance will be returned if no value is passed to the function:

    logger()->error('You are not allowed here.');

<a name="method-method-field"></a>
#### `method_field()` 

The `method_field` function generates an HTML `hidden` input field containing the spoofed value of the form's HTTP verb. For example, using [Blade syntax](/docs/{{version}}/blade):

    <form method="POST">
        {{ method_field('DELETE') }}
    </form>

<a name="method-old"></a>
#### `old()` 

The `old` function [retrieves](/docs/{{version}}/requests#retrieving-input) an old input value flashed into the session:

    $value = old('value');

    $value = old('value', 'default');

<a name="method-redirect"></a>
#### `redirect()` 

The `redirect` function returns a redirect HTTP response, or returns the redirector instance if called with no arguments:

    return redirect('/home');

    return redirect()->route('route.name');

<a name="method-request"></a>
#### `request()` 

The `request` function returns the current [request](/docs/{{version}}/requests) instance or obtains an input item:

    $request = request();

    $value = request('key', $default = null)

<a name="method-response"></a>
#### `response()` 

The `response` function creates a [response](/docs/{{version}}/responses) instance or obtains an instance of the response factory:

    return response('Hello World', 200, $headers);

    return response()->json(['foo' => 'bar'], 200, $headers);

<a name="method-retry"></a>
#### `retry()` 

The `retry` function attempts to execute the given callback until the given maximum attempt threshold is met. If the callback does not throw an exception, it's return value will be returned. If the callback throws an exception, it will automatically be retried. If the maximum attempt count is exceeded, the exception will be thrown:

    return retry(5, function () {
        // Attempt 5 times while resting 100ms in between attempts...
    }, 100);

<a name="method-session"></a>
#### `session()` 

The `session` function may be used to get or set session values:

    $value = session('key');

You may set values by passing an array of key / value pairs to the function:

    session(['chairs' => 7, 'instruments' => 3]);

The session store will be returned if no value is passed to the function:

    $value = session()->get('key');

    session()->put('key', $value);

<a name="method-value"></a>
#### `value()` 

The `value` function's behavior will simply return the value it is given. However, if you pass a `Closure` to the function, the `Closure` will be executed then its result will be returned:

    $value = value(function () {
        return 'bar';
    });

<a name="method-view"></a>
#### `view()` 

The `view` function retrieves a [view](/docs/{{version}}/views) instance:

    return view('auth.login');
