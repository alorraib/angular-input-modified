# angular-input-modified

![Bower](https://img.shields.io/bower/v/angular-input-modified.svg)


This Angular.js module adds additional properties and methods to the `ngModel` and `ngForm` controllers,
as well as CSS classes to the underlying form elements
to provide end-user with facilities to detect and indicate changes in form data.

This extra functionality allows you to provide better usability with forms.
For example, you can add decorations to the form elements that are actually changed.
That way, user will see what values has changed since last edit.

Also, you can reset form to it's initial state (cancel all user edits) with just a single call to `form.reset()` or
lock new values (preserve new state) just by calling overloaded `form.$setPristine()` method.
If you want, you can do this for individual input elements in similar fashion.


## Demos and examples

Please see [the demos][gh-pages] hosted on our GitHub Pages or
[open them locally][faq-local-demos].

Also, feel free to play with our [Plunk][plunk]!


## Decorations and animation

This module adds `ng-modified` and `ng-not-modified` CSS classes (names are customizable) to the input fields to indicate their state.
Use them in your CSS to decorate input fields. You can combine multiple classes in the same selector.
For example, use this convenient CSS selector to decorate modified elements as valid:

``` css
/** Decorating only modified inputs as valid */
input.ng-valid.ng-modified {
    border-color: green;
}
```

This way target user will see what elements were actually changed.

---

This module also supports animations if `ngAnimate` module is available.


## Installation

### Install library with bower

`bower install --save angular-input-modified`


### Add library to your page

``` html
<script type="text/javascript" src="angular-input-modified/src/angular-input-modified.js"></script>
```

You can use minified version (`angular-input-modified.min.js`) in production.


### Add dependency in your application's module definition

``` javascript
var application = angular.module('application', [
    // ...
    'ngInputModified'
]);
```

---


## Usage

Please see our [demos and examples](#demos-and-examples) as well as [API](#api).

### Form initialization

Starting from version `2.0.0` form must be synchronously initialized during
controller execution. If you need some data to be fetched prior to form
initialization — the best approach is to
[resolve](https://docs.angularjs.org/api/ngRoute/provider/$routeProvider)
this data using your router.

However, if you really need to re-initialize form after controller execution —
please use the approach shown in this demo:
[Delayed Initialization][demo-delayed-init].

---


## API

### inputModifiedConfigProvider

Use this provider to configure behavior of this module.
Every setter of this provider supports methods chaining.
See example:

``` javascript
angular.module('Application', ['ngInputModified'])
    .config(function(inputModifiedConfigProvider) {
        inputModifiedConfigProvider
            .disableGlobally()
            .setModifiedClassName('my-changed')
            .setNotModifiedClassName('my-clear')
        ;
    })
;
```


#### enableGlobally

`{ConfigProvider} enableGlobally()`

Enables modifiable behavior globally for all form elements (this is default).


#### disableGlobally

`{ConfigProvider} disableGlobally()`

Disables modifiable behavior globally for all form elements.
You will have to add this behavior manually by using bsModifiable directive


#### setModifiedClassName

`{ConfigProvider} setModifiedClassName({string} className)`

Provides CSS class name that will be added to modified elements.
`ng-modified` is the default one.


#### setNotModifiedClassName

`{ConfigProvider} setNotModifiedClassName({string} className)`

Provides CSS class name that will be added to unmodified elements.
`ng-not-modified` is the default one.


### ngModel

Model controller properties and methods:

    PROPERTIES:
    ==========

    *        masterValue  - initial value of the input field.
    boolean  modified     - flag that indicates whether the input value was modified.

    METHODS:
    =======

    void  reset()  - resets input value to it's initial state.


### ngForm

Form controller properties and methods:

    PROPERTIES:
    ==========

    boolean  modified  - flag that indicates whether the form is modified (i.e. at least one element is modified).

    METHODS:
    =======

    void  reset()  - method to reset all input values of the form to their initial states.

---


## Changelog

Please see the [complete changelog][changelog] for list of changes.


## Feedback

If you have found a bug or have another issue with the library —
please [create an issue][new-issue].

If you have a question regarding the library or it's integration with your project —
consider asking a question at [StackOverflow][so-ask] and sending me a
link via [E-Mail][email]. I will be glad to help.

Have any ideas or propositions? Feel free to contact me by [E-Mail][email].

Cheers!


## FAQ

### How do I access demos locally?

Node.js must be installed in your OS.

- Install [Gulp][gulp] by running `npm install --global gulp`
- clone the repo
- run `gulp webserver` in the repo's root directory
- open `http://localhost:8888/`


## Developer guide

Fork, clone, create a feature branch, commit, create a PR.

Run:

- `npm install && bower install` to initialize the project
- `gulp build` to re-build the dist files
- `gulp webserver` to run local webserver with demos
- `gulp deploy` to deploy GitHub Pages

Do not add dist files to the PR itself.
We will re-compile the module manually each time before releasing.


## Support

If you like this library consider to add star on [GitHub repository][repo-gh].

Thank you!


## License

The MIT License (MIT)

Copyright (c) 2014 - 2015 Slava Fomin II, BETTER SOLUTIONS

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

  [changelog]: changelog.md
  [so-ask]:    http://stackoverflow.com/questions/ask?tags=angularjs,javascript,forms
  [email]:     mailto:s.fomin@betsol.ru
  [plunker]:   http://plnkr.co/
  [new-issue]: https://github.com/betsol/angular-input-modified/issues/new
  [gh-pages]:  http://betsol.github.io/angular-input-modified/
  [plunk]:     http://plnkr.co/edit/g2MDXv81OOBuGo6ORvdt?p=preview
  [gulp]:      http://gulpjs.com/
  [repo-gh]:   https://github.com/betsol/angular-input-modified

  [demo-delayed-init]: http://betsol.github.io/angular-input-modified/delayed-init/

  [faq-local-demos]: #how-do-i-access-demos-locally