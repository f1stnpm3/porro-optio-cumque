# @f1stnpm3/porro-optio-cumque <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2015 spec-compliant `Array.prototype.values` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://www.ecma-international.org/ecma-262/6.0/).

Because `Array.prototype.values` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var values = require('@f1stnpm3/porro-optio-cumque');
var assert = require('assert');
var iterate = require('iterate-iterator');

assert.deepStrictEqual(iterate(values([1, 2, 3])), [1, 2, 3]);
assert.deepStrictEqual(iterate(values([1, 0, 1])), [1, 0, 1]);
assert.deepStrictEqual(iterate(values([NaN])), [NaN]);
assert.deepStrictEqual(iterate(values([1,,3])), [1, undefined, 3]);
```

```js
var values = require('@f1stnpm3/porro-optio-cumque');
var assert = require('assert');
/* when Array#values is not present */
delete Array.prototype.values;
var shimmedMap = values.shim();
assert.deepStrictEqual(shimmedMap, values.getPolyfill());
assert.deepStrictEqual(iterate([1, 2, 3].values()), [1, 2, 3]);
assert.deepStrictEqual(iterate([1, 0, 1].values()), [1, 0, 1]);
assert.deepStrictEqual(iterate([NaN].values()), [NaN]);
assert.deepStrictEqual(iterate([1,,3].values()), [1, undefined, 3]);
```

```js
var values = require('@f1stnpm3/porro-optio-cumque');
var assert = require('assert');
/* when Array#values is present */
var shimmedMap = values.shim();
assert.equal(shimmedMap, Array.prototype.values);
assert.deepStrictEqual(iterate([1, 2, 3].values()), [1, 2, 3]);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@f1stnpm3/porro-optio-cumque
[npm-version-svg]: https://versionbadg.es/f1stnpm3/porro-optio-cumque.svg
[deps-svg]: https://david-dm.org/f1stnpm3/porro-optio-cumque.svg
[deps-url]: https://david-dm.org/f1stnpm3/porro-optio-cumque
[dev-deps-svg]: https://david-dm.org/f1stnpm3/porro-optio-cumque/dev-status.svg
[dev-deps-url]: https://david-dm.org/f1stnpm3/porro-optio-cumque#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@f1stnpm3/porro-optio-cumque.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@f1stnpm3/porro-optio-cumque.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@f1stnpm3/porro-optio-cumque.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@f1stnpm3/porro-optio-cumque
[codecov-image]: https://codecov.io/gh/f1stnpm3/porro-optio-cumque/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/f1stnpm3/porro-optio-cumque/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/f1stnpm3/porro-optio-cumque
[actions-url]: https://github.com/f1stnpm3/porro-optio-cumque/actions
