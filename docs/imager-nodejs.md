# Imager <small><em>for JavaScript</em></small>

## Links
* [Source](https://github.com/imager-io/imager-io-js)
* [NPM](https://www.npmjs.com/package/imager-io)
* [Example](https://git.io/Jeo6e)
* [Documentation](https://github.com/imager-io/imager-io-js/blob/master/docs/imager-nodejs.md)

# Examples

## Optimize
```typescript
import {ImageBuffer, OptArgs} from "imager-io";

ImageBuffer
    .open("path/to/input/image.jpeg")
    .then(buffer => buffer.opt())
    .then(buffer => buffer.save("path/to/output/image.jpeg"));
```

## Resize & Optimize
> See [API Docs](#Building-Complete-API-Documentation) for further details.
```typescript
import {ImageBuffer, OptArgs} from "imager-io";

ImageBuffer
    .open("path/to/input/image.jpeg")
    .then(buffer => buffer.opt("900x900"))
    .then(buffer => buffer.save("path/to/output/image.jpeg"));
```

# [Some Other Example](https://github.com/imager-io/imager-nodejs-example)
```javascript
const {ImageBuffer} = require("imager-io");

function optimize(from, to, resize_opt) {
    return ImageBuffer
        .open(from)
        .then(buffer => buffer.opt(resize_opt))
        .then(buffer => buffer.save(to))
        .then(() => {
            console.log("[done]", from, "->", to);
        });
}


// This showcases loading, resizing, and optimizing the given images.
function run_me() {
    return Promise.all([
        optimize("samples/hi-0.jpeg", "output/hi-0.jpeg", "1600x1600"),
        optimize("samples/hi-1.jpeg", "output/hi-1.jpeg", "1600x1600"),
        optimize("samples/hi-2.jpeg", "output/hi-2.jpeg", "1600x1600"),
    ]);
}

run_me();
```


# Building Complete API Documentation

> Getting this hosted somewhere is on my TODO list! For now I apologize for the inconvenience.

```shell
$ git https://github.com/imager-io/imager-io-js.git
$ npm install
$ npm run doc
```
Will be under `./docs`.



# Building From Source
> For imager developers only. Laymen devs should probably stick to the self-contained NPM release (since it’s easier).

## Requirements

* `make` build tool 
* `cargo` build tool
* `c/c++` compiler
* `libclang`
* `libc++` - The C++ standard library

### Step 1. [Cargo](https://rustup.rs)

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### Step 2.

#### For MacOS

```shell
$ brew install llvm
```

#### For Debian-based Linuxes

```shell
$ apt install llvm-dev libclang-dev clang
```

Additionally if you don’t have `make` installed:
```shell
$ apt install build-essential
```

## Project

```shell
$ git https://github.com/imager-io/imager-io-js.git
$ npm install
$ ./scripts/build-rust.sh
$ npm run build
$ npm run test # optional
```



# Building VIA Docker (For Linux Users)
> For imager developers only. Laymen devs should probably stick to the self-contained NPM release (since it’s easier).

```shell
$ git https://github.com/imager-io/imager-io-js.git
$ npm install
$ ./scripts/docker/build.sh
$ PRE_BUILT_LIB_IMAGER_NODEJS=1 npm run build
$ npm run test # optional
```