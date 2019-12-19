# Imager <small><em>for JavaScript</em></small>

* [Source](https://github.com/imager-io/imager-io-js)
* [NPM](https://www.npmjs.com/package/imager-io)
* [Example](https://git.io/Jeo6e)
* [Documentation](https://github.com/imager-io/imager-io-js/blob/master/docs/imager-nodejs.md)

## Features

### Brute Force Image Optimization

> Optimizes the compression using ML based metrics in a trial ’n error sorta manner.

This is a tool that can competitively optimize (e.g.) extremely noisy, high resolution images; at the expense of increased encoding time and CPU overhead. This is a tradeoff that should be suitable for over 90% of online content, where site performance matters.

It's pretty easy too.

```shell
$ npm install --save imager-io
```

<small>Using the JavaScript non-blocking API:</small>

```javascript
const {ImageBuffer} = require("imager-io");
ImageBuffer
	.open("source-image.jpeg")
	.then(buffer => buffer.opt())
	.then(buffer => buffer.save("result.jpeg"))
	.then(() => console.log("done"));
```


## [Compression Benchmarks](https://github.com/colbyn/imager-bench-2019-11-2)

```text
source        : ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 39.00M (4 images)
kraken.io     : ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 24M
jpegmini.com  : ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 16M
compression.ai: ▇▇▇▇▇▇▇▇ 8.90M
imager        : ▇▇▇▇ 4.20M
```

### Supported **Input** Image Formats

| Format | Decoding |
| ------ | -------- |
| PNG    | All supported color types |
| JPEG   | Baseline and progressive |
| GIF    | Yes |
| BMP    | Yes |
| ICO    | Yes |
| TIFF   | Baseline(no fax support) + LZW + PackBits |
| WebP   | Lossy(Luma channel only) |
| PNM    | PBM, PGM, PPM, standard PAM |

Essentially supports any image decodable by [image-rs](https://github.com/image-rs/image.git).

### Supported **Output** Image Formats

> These are your optimization targets (for lack of a better name). It’s a bit higher level, since e.g. rate control is automatically handled.

| Format | Encoding |
| ------ | -------- |
| JPEG   | progressive |

### Supported Operating Systems

| OS     | Current Status |
| ------ | -------- |
| Linux   | ✅ [GOOD] |
| MacOS   | ✅ [GOOD] |
| Windows   | ❌ [UNPRIORITIZED] (Use WSL) |

#### Webpack

It’s possible and pretty easy to use Webpack and Imager already, [here is an example](https://github.com/imager-io/webpack-imager-example-vanilla).

## Feedback, Requests, Bugs, Confusion & Performance Issues
Just use the GitHub issue tracker for this project.

## Other Miscellaneous

### Self Contained
Our npm releases contain prebuilt native node libraries (i.e. the *rust* code). With eventual plans for WASM support.

### Articles

* [Modern Image Optimization for 2020 - Issues, Solutions, and Open Source Solutions](https://medium.com/@colbyn/modern-image-optimization-for-2020-issues-solutions-and-open-source-solutions-543af00e3e51)


<hr/>

Copyright 2019 Colbyn Wadman