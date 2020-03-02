# `biguintbe`

[![abstract-encoding](https://img.shields.io/badge/abstract--encoding-compliant-brightgreen.svg?style=flat)](https://github.com/mafintosh/abstract-encoding)

> Encode / decode unsigned BigInt as big endian

## Usage

```js
var bigUintBE = require('biguintbe')

var bigUint = 2n ** 64n - 1n // UINT64_MAX

assert(bigUintBE.encodingLength(bigUint) === 8)
var buf = bigUintBE.encode(bigUint)
assert(bigUintBE.encode.bytes === 8 && buf.byteLength === 8)

var num = bigUintBE.decode()
```

## API

### `var buf = bigUintBE.encode(bu, [buf, [byteOffset]])`
Write `BigInt` `bu` to optional `Buffer` or `TypedArray` `buf` at optional
`Number` `byteOffset`. If `buf` is not set a new `Buffer` is allocated the size
of the byte width of `bu`. `byteOffset` defaults to `0`.

### `var bytes = bigUintBE.encode.bytes`
`Number` of bytes last encoded

### `var bigUint = bigUintBE.decode(buf, [byteOffset], [byteLength])`
Read `BigInt` from `Buffer` or `TypedArray` `buf` at optional
`Number` `byteOffset` for optional `Number` `byteLength` bytes. Note that if you
do **not** give a `byteLength` all of `buf` will be decoded, since `BigInt`s do
not have a natural width.

### `var bytes = bigUintBE.decode.bytes`
`Number` of bytes last decoded

### `var bytes = bigUintBE.encodingLength(bu)`
`Number` of bytes required to encode `BigInt` `bu`

## Install

```sh
npm install biguintbe
```

## License

[ISC](LICENSE)
