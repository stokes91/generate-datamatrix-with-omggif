# generate-datamatrix-with-omggif

Data Matrix Codes are a type of 2D codes that are used frequently in industrial spaces,
as they can encode a large amount of information in a small footprint. This code minimally implements
the encoding of a barcode. Here, Dean McNamee's omggif library is used to concisely render a gif.

## Encoding ASCII

```
const fs = require('fs');

const DataMatrix = require('../main');

const datamatrix = new DataMatrix();

datamatrix.encodeAscii('Hello World!');

fs.writeFile('test-ASCII.gif', datamatrix.renderGif(), function(err) {
  console.log(err);
});

```

## Resulting test-ASCII.gif
![Hello World!](https://github.com/stokes91/generate-datamatrix-with-omggif/blob/main/examples/test-ASCII.gif?raw=true)


## Encoding X12

```
const fs = require('fs');

const DataMatrix = require('../main');

const datamatrix = new DataMatrix();

datamatrix.encodeX12('HELLO WORLD*');

fs.writeFile('test-X12.gif', datamatrix.renderGif(), function(err) {
  console.log(err);
});
```

## Resulting test-X12.gif
![Hello World!](https://github.com/stokes91/generate-datamatrix-with-omggif/blob/main/examples/test-ASCII.gif?raw=true)


## Basic Support

This example shows how to create a png formatted image using omggif. This code only supports ASCII and X12 encoding. The Data Matrix specification includes a number of additional
codewords that improve efficiency for reduced character sets.

## Two dependencies

It's just a few hundred lines of clear, readable, code; and relies on rs-finite-field and omggif.

## Also Free

Licensed under Apache 2.0

