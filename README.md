# koi8-u [![Build status](https://travis-ci.org/mathiasbynens/koi8-u.svg?branch=master)](https://travis-ci.org/mathiasbynens/koi8-u) [![Code coverage status](https://coveralls.io/repos/mathiasbynens/koi8-u/badge.svg)](https://coveralls.io/r/mathiasbynens/koi8-u) [![Dependency status](https://gemnasium.com/mathiasbynens/koi8-u.svg)](https://gemnasium.com/mathiasbynens/koi8-u)

_koi8-u_ is a robust JavaScript implementation of [the koi8-u character encoding as defined by the Encoding Standard](http://encoding.spec.whatwg.org/#koi8-u).

This encoding is known under the following names: , and koi8-u.

## Installation

Via [npm](https://www.npmjs.com/):

```bash
npm install koi8-u
```

Via [Bower](http://bower.io/):

```bash
bower install koi8-u
```

Via [Component](https://github.com/component/component):

```bash
component install mathiasbynens/koi8-u
```

In a browser:

```html
<script src="koi8-u.js"></script>
```

In [Node.js](https://nodejs.org/), [io.js](https://iojs.org/), [Narwhal](http://narwhaljs.org/), and [RingoJS](http://ringojs.org/):

```js
var koi8u = require('koi8-u');
```

In [Rhino](http://www.mozilla.org/rhino/):

```js
load('koi8u.js');
```

Using an AMD loader like [RequireJS](http://requirejs.org/):

```js
require(
  {
    'paths': {
      'koi8-u': 'path/to/koi8-u'
    }
  },
  ['koi8-u'],
  function(koi8u) {
    console.log(koi8u);
  }
);
```

## API

### `koi8u.version`

A string representing the semantic version number.

### `koi8u.labels`

An array of strings, each representing a [label](http://encoding.spec.whatwg.org/#label) for this encoding.

### `koi8u.encode(input, options)`

This function takes a plain text string (the `input` parameter) and encodes it according to koi8-u. The return value is a ‘byte string’, i.e. a string of which each item represents an octet as per koi8-u.

```js
var encodedData = koi8u.encode(text);
```

The optional `options` object and its `mode` property can be used to set the [error mode](http://encoding.spec.whatwg.org/#error-mode). For encoding, the error mode can be `'fatal'` (the default) or `'html'`.

```js
var encodedData = koi8u.encode(text, {
  'mode': 'html'
});
// If `text` contains a symbol that cannot be represented in koi8-u,
// instead of throwing an error, it will return an HTML entity for the symbol.
```

### `koi8u.decode(input, options)`

This function takes a byte string (the `input` parameter) and decodes it according to koi8-u.

```js
var text = koi8u.decode(encodedData);
```

The optional `options` object and its `mode` property can be used to set the [error mode](http://encoding.spec.whatwg.org/#error-mode). For decoding, the error mode can be `'replacement'` (the default) or `'fatal'`.

```js
var text = koi8u.decode(encodedData, {
  'mode': 'fatal'
});
// If `encodedData` contains an invalid byte for the koi8-u encoding,
// instead of replacing it with U+FFFD in the output, an error is thrown.
```

## Support

_koi8-u_ is designed to work in at least Node.js v0.10.0, io.js v1.0.0, Narwhal 0.3.2, RingoJS 0.8-0.11, PhantomJS 1.9.0, Rhino 1.7RC4, as well as old and modern versions of Chrome, Firefox, Safari, Opera, and Internet Explorer.

## Unit tests & code coverage

After cloning this repository, run `npm install` to install the dependencies needed for development and testing. You may want to install Istanbul _globally_ using `npm install istanbul -g`.

Once that’s done, you can run the unit tests in Node using `npm test` or `node tests/tests.js`. To run the tests in Rhino, Ringo, Narwhal, and web browsers as well, use `grunt test`.

To generate the code coverage report, use `grunt cover`.

## Notes

[Similar modules for other single-byte legacy encodings are available.](https://www.npmjs.com/browse/keyword/legacy-encoding)

## Author

| [![twitter/mathias](https://gravatar.com/avatar/24e08a9ea84deb17ae121074d0f17125?s=70)](https://twitter.com/mathias "Follow @mathias on Twitter") |
|---|
| [Mathias Bynens](https://mathiasbynens.be/) |

## License

_koi8-u_ is available under the [MIT](https://mths.be/mit) license.
