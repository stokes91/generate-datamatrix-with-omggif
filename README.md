# generate-datamatrix-with-omggif

Data Matrix Codes are a type of 2D codes that are used frequently in industrial spaces,
as they can encode a large amount of information in a small footprint. This code minimally implements
the encoding of a barcode. Here, Dean McNamee's omggif library is used to concisely render a gif.

## Encoding ASCII

```
const fs = require('fs');

const DataMatrix = require('../main');

const datamatrix = new DataMatrix({
  quietZone: 2,
  scale: 2
});

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

const datamatrix = new DataMatrix({
  quietZone: 1,
  scale: 2
});

datamatrix.encodeX12('HELLO WORLD*');

fs.writeFile('test-X12.gif', datamatrix.renderGif(), function(err) {
  console.log(err);
});
```

## Resulting test-X12.gif
![HELLO WORLD*](https://github.com/stokes91/generate-datamatrix-with-omggif/blob/main/examples/test-ASCII.gif?raw=true)


## Basic Support

This example shows how to create a GIF formatted image using omggif. This code only supports ASCII and X12 encoding. The Data Matrix specification includes a number of additional
codewords that improve efficiency for reduced character sets. Different pixel sizing is available through the constructor:

## Smallest & Fastest

test-tiny-X12.gif is only 71 bytes and 25K barcodes were rendred in a second. This contrasts on the same machine, using sharp and png.
In that setup, test-tiny-X12.png is 198 bytes and only 590 barcodes were rendered in a second.


```
const fs = require('fs');

const DataMatrix = require('../main');

const datamatrix = new DataMatrix({
  quietZone: 0,
  scale: 1
});

datamatrix.encodeX12('ZVZRKTEB');

const buffer = datamatrix.renderGif();

fs.writeFile('test-tiny-X12.gif', buffer, function(err) {
  console.log(err);
});
```
## Resulting test-tiny-X12.gif
![ZVZRKTEB](https://github.com/stokes91/generate-datamatrix-with-omggif/blob/main/examples/test-tiny-X12.gif?raw=true)


## Encoding C40

```
const fs = require('fs');

const DataMatrix = require('../main');

const datamatrix = new DataMatrix({
  quietZone: 2,
  scale: 2
});

datamatrix.encodeC40('EXAMPLE.COM');

fs.writeFile('test-C40.gif', datamatrix.renderGif(), function(err) {
  console.log(err);
});
```

## Resulting test-C40.gif
![EXAMPLE.COM](https://github.com/stokes91/generate-datamatrix-with-omggif/blob/main/examples/test-C40.gif?raw=true)

## Two dependencies

It's just a few hundred lines of clear, readable, code; and relies on rs-finite-field and omggif.

## Also Free

Licensed under Apache 2.0

