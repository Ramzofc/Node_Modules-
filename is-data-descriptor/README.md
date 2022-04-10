# is-data-descriptor [![NPM version](https://img.shields.io/npm/v/is-data-descriptor.svg?style=flat)](https://www.npmjs.com/package/is-data-descriptor) [![NPM monthly downloads](https://img.shields.io/npm/dm/is-data-descriptor.svg?style=flat)](https://npmjs.org/package/is-data-descriptor) [![NPM total downloads](https://img.shields.io/npm/dt/is-data-descriptor.svg?style=flat)](https://npmjs.org/package/is-data-descriptor) [![Linux Build Status](https://img.shields.io/travis/jonschlinkert/is-data-descriptor.svg?style=flat&label=Travis)](https://travis-ci.org/jonschlinkert/is-data-descriptor)

> Returns true if a value has the characteristics of a valid JavaScript data descriptor.

Please consider following this project's author, [Jon Schlinkert](https://github.com/jonschlinkert), and consider starring the project to show your :heart: and support.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save is-data-descriptor
```

## Usage

```js
var isDataDesc = require('is-data-descriptor');
```

## Examples

`true` when the descriptor has valid properties with valid values.

```js
// `value` can be anything
isDataDesc({value: 'foo'})
isDataDesc({value: function() {}})
isDataDesc({value: true})
//=> true
```

`false` when not an object

```js
isDataDesc('a')
//=> false
isDataDesc(null)
//=> false
isDataDesc([])
//=> false
```

`false` when the object has invalid properties

```js
isDataDesc({value: 'foo', bar: 'baz'})
//=> false
isDataDesc({value: 'foo', bar: 'baz'})
//=> false
isDataDesc({value: 'foo', get: function(){}})
//=> false
isDataDesc({get: function(){}, value: 'foo'})
//=> false
```

`false` when a value is not the correct type

```js
isDataDesc({value: 'foo', enumerable: 'foo'})
//=> false
isDataDesc({value: 'foo', configurable: 'foo'})
//=> false
isDataDesc({value: 'foo', writable: 'foo'})
//=> false
```

## Valid properties

The only valid data descriptor properties are the following:

* `configurable` (required)
* `enumerable` (required)
* `value` (optional)
* `writable` (optional)

To be a valid data descriptor, either `value` or `writable` must be defined.

**Invalid properties**

A descriptor may have additional _invalid_ properties (an error will **not** be thrown).

```js
var foo = {};

Object.defineProperty(foo, 'bar', {
  enumerable: true,
  whatever: 'blah', // invalid, but doesn't cause an error
  get: function() {
    return 'baz';
  }
});

console.log(foo.bar);
//=> 'baz'
```

## About

<details>
<summary><strong>Contributing</strong></summary>

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

</details>

<details>
<summary><strong>Running Tests</strong></summary>

Running and reviewing unit tests is a great way to get familiarized with a library and its API. You can install dependencies and run tests with the following command:

```sh
$ npm install && npm test
```

</details>

<details>
<summary><strong>Building docs</strong></summary>

_(This project's readme.md is generated by [verb](https://github.com/verbose/verb-generate-readme), please don't edit the readme directly. Any changes to the readme must be made in the [.verb.md](.verb.md) readme template.)_

To generate the readme, run the following command:

```sh
$ npm install -g verbose/verb#dev verb-generate-readme && verb
```

</details>

### Related projects

You might also be interested in these projects:

* [is-accessor-descriptor](https://www.npmjs.com/package/is-accessor-descriptor): Returns true if a value has the characteristics of a valid JavaScript accessor descriptor. | [homepage](https://github.com/jonschlinkert/is-accessor-descriptor "Returns true if a value has the characteristics of a valid JavaScript accessor descriptor.")
* [is-data-descriptor](https://www.npmjs.com/package/is-data-descriptor): Returns true if a value has the characteristics of a valid JavaScript data descriptor. | [homepage](https://github.com/jonschlinkert/is-data-descriptor "Returns true if a value has the characteristics of a valid JavaScript data descriptor.")
* [is-descriptor](https://www.npmjs.com/package/is-descriptor): Returns true if a value has the characteristics of a valid JavaScript descriptor. Works for… [more](https://github.com/jonschlinkert/is-descriptor) | [homepage](https://github.com/jonschlinkert/is-descriptor "Returns true if a value has the characteristics of a valid JavaScript descriptor. Works for data descriptors and accessor descriptors.")
* [isobject](https://www.npmjs.com/package/isobject): Returns true if the value is an object and not an array or null. | [homepage](https://github.com/jonschlinkert/isobject "Returns true if the value is an object and not an array or null.")

### Contributors

| **Commits** | **Contributor** | 
| --- | --- |
| 21 | [jonschlinkert](https://github.com/jonschlinkert) |
| 2 | [realityking](https://github.com/realityking) |

### Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](https://twitter.com/jonschlinkert)

### License

Copyright © 2017, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT License](LICENSE).

***

_This file was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme), v0.6.0, on November 01, 2017._