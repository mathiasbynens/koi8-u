# koi8-u [![koi8-u on npm](https://img.shields.io/npm/v/koi8-u)](https://www.npmjs.com/package/koi8-u)

_koi8-u_ is a robust JavaScript implementation of [the koi8-u character encoding as defined by the Encoding Standard](https://encoding.spec.whatwg.org/#koi8-u).

This encoding is known under the following names: , and koi8-u.

## Installation

Via [npm](https://www.npmjs.com/):

```bash
npm install koi8-u
```

In a browser:

```html
<script src="koi8-u.js"></script>
```

In [Node.js](https://nodejs.org/):

```js
const koi8u = require('koi8-u');
```

## API

### `koi8u.version`

A string representing the semantic version number.

### `koi8u.labels`

An array of strings, each representing a [label](https://encoding.spec.whatwg.org/#label) for this encoding.

### `koi8u.encode(input, options)`

This function takes a plain text string (the `input` parameter) and encodes it according to koi8-u. The return value is a ‘byte string’, i.e. a string of which each item represents an octet as per koi8-u.

```js
const encodedData = koi8u.encode(text);
```

The optional `options` object and its `mode` property can be used to set the [error mode](https://encoding.spec.whatwg.org/#error-mode). For encoding, the error mode can be `'fatal'` (the default) or `'html'`.

```js
const encodedData = koi8u.encode(text, {
  mode: 'html'
});
// If `text` contains a symbol that cannot be represented in koi8-u,
// instead of throwing an error, it will return an HTML entity for the symbol.
```

### `koi8u.decode(input, options)`

This function takes a byte string (the `input` parameter) and decodes it according to koi8-u.

```js
const text = koi8u.decode(encodedData);
```

The optional `options` object and its `mode` property can be used to set the [error mode](https://encoding.spec.whatwg.org/#error-mode). For decoding, the error mode can be `'replacement'` (the default) or `'fatal'`.

```js
const text = koi8u.decode(encodedData, {
  mode: 'fatal'
});
// If `encodedData` contains an invalid byte for the koi8-u encoding,
// instead of replacing it with U+FFFD in the output, an error is thrown.
```

For decoding a buffer (e.g. from `fs.readFile`) use `buffer.toString('binary')` to get the byte string which `decode` takes.

## Notes

[Similar modules for other single-byte legacy encodings are available.](https://www.npmjs.com/browse/keyword/legacy-encoding)

## Author

| [![twitter/mathias](https://gravatar.com/avatar/24e08a9ea84deb17ae121074d0f17125?s=70)](https://twitter.com/mathias "Follow @mathias on Twitter") |
|---|
| [Mathias Bynens](https://mathiasbynens.be/) |

## License

_koi8-u_ is available under the [MIT](https://mths.be/mit) license.
