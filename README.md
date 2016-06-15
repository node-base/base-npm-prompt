# base-npm-prompt [![NPM version](https://img.shields.io/npm/v/base-npm-prompt.svg?style=flat)](https://www.npmjs.com/package/base-npm-prompt) [![NPM downloads](https://img.shields.io/npm/dm/base-npm-prompt.svg?style=flat)](https://npmjs.org/package/base-npm-prompt) [![Build Status](https://img.shields.io/travis/node-base/base-npm-prompt.svg?style=flat)](https://travis-ci.org/node-base/base-npm-prompt)

Extends the base-npm plugin with prompts for intalling dependencies as a part of a build-workflow.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install base-npm-prompt --save
```

## Usage

```js
var prompt = require('base-npm-prompt');
var npm  require('base-npm');
var Base = require('base-app');
var app = new Base();

// register the `base-npm` plugin first
app.use(npm());

// register the `base-npm-prompt` plugin
app.use(prompt());
```

Note that if you use [base](https://github.com/node-base/base) directly you will also need to let the plugin know that it is being registered on a Base "application" (since `Base` can be used to create anything, like `views`, `collections` etc.).

```js
var Base = require('base');
var app = new Base({isApp: true}); // <=
var prompt = require('base-npm-prompt');
var npm = require('base-npm');

// register the `base-npm` plugin first
app.use(npm());

// register the `base-npm-prompt` plugin
app.use(prompt());

app.npm.prompt('dependencies', function(err) {
  if (err) return cb(err);
  app.npm.prompt('devDependencies', cb);
});
```

## API

### [.npm.prompt](index.js#L41)

Prompts the user to ask if they want to install the packages listed on `app.cache.install.dependencies` or `app.cache.install.devDependencies` based on the given `type`.

**Params**

* `type` **{String}**: dependency type to install (dependencies or devDependencies)
* `options` **{Object}**
* `cb` **{Function}**: Callback

**Example**

```js
app.npm.prompt('dependencies', function(err) {
  if (err) return console.error(err):
});
```

### [.npm.askInstall](index.js#L67)

Prompts the user to ask if they want to install the given package(s). Requires the [base-questions](https://github.com/node-base/base-questions) plugin to be registered first.

**Params**

* `names` **{String|Array}**: One or more package names.
* `options` **{Object}**
* `cb` **{Function}**: Callback

**Example**

```js
app.npm.askInstall('isobject', function(err) {
  if (err) throw err;
});
```

### [.npm.checkInstall](index.js#L88)

Prompts the user to ask if they want to check if the given package(s) exist on npm, then install the ones that do exist. Requires the [base-questions](https://github.com/node-base/base-questions) plugin to be registered first.

**Params**

* `names` **{String|Array}**: One or more package names.
* `options` **{Object}**
* `cb` **{Function}**: Callback

**Example**

```js
app.npm.checkInstall('isobject', function(err) {
  if (err) throw err;
});
```

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/node-base/base-npm-prompt/issues/new).

## Building docs

Generate readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install verb && npm run docs
```

Or, if [verb](https://github.com/verbose/verb) is installed globally:

```sh
$ verb
```

## Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

## Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/node-base/base-npm-prompt/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on June 15, 2016._