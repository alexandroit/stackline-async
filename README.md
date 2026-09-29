# @stackline/async

> Higher-order functions and common patterns for asynchronous code.

[![npm version](https://img.shields.io/npm/v/@stackline/async.svg?style=flat-square)](https://www.npmjs.com/package/@stackline/async)
[![license](https://img.shields.io/npm/l/@stackline/async.svg?style=flat-square)](https://github.com/alexandroit/stackline-async)
[![GitHub repository](https://img.shields.io/badge/GitHub-repository-181717?style=flat-square&logo=github)](https://github.com/alexandroit/stackline-async)
[![Docs](https://img.shields.io/badge/docs-alexandro.net-0f766e?style=flat-square)](https://alexandro.net/docs/vanilla/async/)
[![Reddit community](https://img.shields.io/badge/community-r%2FStackline-ff4500?style=flat-square&logo=reddit&logoColor=white)](https://www.reddit.com/r/Stackline/)

**[Documentation](https://alexandro.net/docs/vanilla/async/)** | **[npm](https://www.npmjs.com/package/@stackline/async)** | **[Issues](https://github.com/alexandroit/stackline-async/issues)** | **[Repository](https://github.com/alexandroit/stackline-async)**

**Current package version:** `1.0.2`

---

## Why this package?

`@stackline/async` is the Stackline-maintained distribution of `async@3.2.6`. It is an independent continuation of [async](https://github.com/caolan/async); original authors and licenses remain credited below.

## Compatibility

| Item | Value |
| :--- | :--- |
| Package | `@stackline/async@1.0.2` |
| API target | `async@3.2.6` |
| Supported Node.js | `See supported framework requirements` |
| License | `MIT` |
| Main entry | `dist/async.js` |
| Module entry | `dist/async.mjs` |
| Runtime dependencies | `none` |

## Installation

```bash
npm install @stackline/async
```

Preserve existing imports and plugin resolution with an npm alias:

```bash
npm install async@npm:@stackline/async
```

## Usage and API reference

Async is a utility module which provides straight-forward, powerful functions for working with [asynchronous JavaScript](http://caolan.github.io/async/v3/global.html). Although originally designed for use with [Node.js](https://nodejs.org/) and installable via `npm i @stackline/async`, it can also be used directly in the browser.  An ESM/MJS version is included in the main `async` package that should automatically be used with compatible bundlers such as Webpack and Rollup.

A pure ESM version of Async is available as [`async-es`](https://www.npmjs.com/package/async-es).

For Documentation, visit <https://caolan.github.io/async/>

*For Async v1.5.x documentation, go [HERE](https://github.com/caolan/async/blob/v1.5.2/README.md)*


```javascript
// for use with Node-style callbacks...
var async = require("@stackline/async");

var obj = {dev: "/dev.json", test: "/test.json", prod: "/prod.json"};
var configs = {};

async.forEachOf(obj, (value, key, callback) => {
    fs.readFile(__dirname + value, "utf8", (err, data) => {
        if (err) return callback(err);
        try {
            configs[key] = JSON.parse(data);
        } catch (e) {
            return callback(e);
        }
        callback();
    });
}, err => {
    if (err) console.error(err.message);
    // configs is now a map of JSON data
    doSomethingWith(configs);
});
```

```javascript
var async = require("@stackline/async");

// ...or ES2017 async functions
async.mapLimit(urls, 5, async function(url) {
    const response = await fetch(url)
    return response.body
}, (err, results) => {
    if (err) throw err
    // results is now an array of the response bodies
    console.log(results)
})
```

## Credits and original authors

- Original project: [async](https://github.com/caolan/async).
- Caolan McMahon.
- Copyright (c) 2010-2018 Caolan McMahon.
- Stackline maintenance: [Alexandro Paixao Marques](https://www.linkedin.com/in/aleinfo/) and [Stackline contributors](https://github.com/alexandroit).

Original copyright, license notices and contributor acknowledgements remain part of this distribution. Stackline maintenance does not replace authorship of the original work.

## License

`MIT`. See the license and notice files in the [repository](https://github.com/alexandroit/stackline-async).

## Community and Links

- [Stackline website](https://alexandro.net/)
- [GitHub projects](https://github.com/alexandroit)
- [npm packages](https://www.npmjs.com/~alex360qc)
- [Reddit community — r/Stackline](https://www.reddit.com/r/Stackline/)
- [Maintainer LinkedIn](https://www.linkedin.com/in/aleinfo/)

Use this repository's issue tracker for reproducible bugs and feature requests. Join r/Stackline for examples, usage questions and release discussions.
