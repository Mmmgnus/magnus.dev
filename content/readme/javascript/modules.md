---
title: "Javascript modules"
date: 2019-07-06T15:13:36+02:00
draft: false
---

## What is a module?

>A group of code and data related to a particular piece of functionality. It encapsulates implementation details, exposes a public API, and is combined with other modules to build a larger application.

Structure your javascript code in modules has its benefits:

* Easy to reuse and share code.
* Encapsulation, clear API and make the user of the code not need to think about the implementation.
* Simplify dependency management.

## Revealing Module Pattern
To create a module in javascript, an excellent place to start is to use the Revealing Module Pattern, that hides the implementation of the module and return an object representing the modules API. The private functions and variables are truly private from the outside.

An IIFE is perfect for modules that don't have an API:
```javascript
    (function () {
        var privateVariable = "Magnus";
        function privateFunc (name) {
            ...
        }

        privateFunc(privateVariable);
    })(); 
```

If you have a module that there is only going to be one instance of, considerate creating a singleton.

### Singleton
```javascript
Var myFunc = function () {
    function do {
        ...
    }
    
    return {
        do: do
    }    
}();
```

If you are going to have more instances of a module, considerate the construction pattern, it is also possible to use Object.create(...) to create more than one instance.

### Constructor
```javascript
Var MyFunc = function () {
    function do {
        ...
    }
    
    return {
        do: do
    }
};

// using it.
Var fancy = new MyFunc();
Fancy.do();
```

## Javascript module formats
To simplify the dependency management and not to add stuff to the global scope. Here are some module formats could be handy.

### AMD Format
AMD modules are perfect for running in a browser.

```javascript
define(
    ['./module1', './module2']
    function (module1, module2) {
    
});
```

### CommonJS Format
CommonJS modules are created to work in NodeJs, but can also work in the browser. One benefit of this format is that it's easier to read.

```javascript
var module1 = require('./module1.js');

function myFunc () {
    ...
}

function anotherFunc () {
    ...
}

export.myFunc = myFunc;
export.anotherFunc = anotherFunc;
```

exports.myfunc = myFunc => module.exports.myfunc = myFunc;

#### Dont

```javascript
export = {};
export = function () {};
```

#### DO
```javascript
module.exports = {};
module.exports = function() {};
```

### Native module format
ES2015 added support for modules. To make Native modules work everywhere, you need to transpile your code. Babel transpile the code into older Javascript and use the CommonJS format for the modules.

#### Exporting
```javascript
export function myFunc() {
    ...
}

export { myFunc as aliasName }

// default 
Export default function myFunc (..) {
    ...
}
```

#### Import
```javascript
// Get everything
Import * as foo from './module1.js';
foo.getName();

// Get only what you need.
import { getName } from './module1.js';
getName();

// Alias the name
import { getName as getMemberName } from './module1.js';
getMemberName();
```