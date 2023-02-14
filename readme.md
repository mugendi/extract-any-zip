# extract-any-zip

This module is a clone of the amazing [extract-zip](https://www.npmjs.com/package/extract-zip) with the added ability to unzip urls, buffers as well as files via [file-to-buffer](https://www.npmjs.com/package/file-to-buffer). Everything else in the API remains exactly the same.

Written in pure JavaScript. Extracts a zip into a directory. Available as a library or a command line program.

Uses the [`yauzl`](http://npmjs.org/yauzl) ZIP parser.

[![NPM](https://nodei.co/npm/extract-any-zip.png?global=true)](https://npm.im/extract-zip)
[![Uses JS Standard Style](https://cdn.jsdelivr.net/gh/standard/standard/badge.svg)](https://github.com/standard/standard)
[![Build Status](https://github.com/maxogden/extract-any-zip/workflows/CI/badge.svg)](https://github.com/maxogden/extract-any-zip/actions?query=workflow%3ACI)

## Installation

Make sure you have Node 10 or greater installed.

Get the library:

```
npm install extract-any-zip --save
```

Install the command line program:

```
npm install extract-any-zip -g
```

## JS API

```javascript
const extract = require('extract-any-zip')

async function main () {
  try {
    await extract(source, { dir: target })
    console.log('Extraction complete')
  } catch (err) {
    // handle any errors
  }
}
```

### Source
This is where this module differs with *extract-zip* in that it can take other sources:

Type: `Buffer` `File` `URL`

### Options

- `dir` (required) - the path to the directory where the extracted files are written
- `defaultDirMode` - integer - Directory Mode (permissions), defaults to `0o755`
- `defaultFileMode` - integer - File Mode (permissions), defaults to `0o644`
- `onEntry` - function - if present, will be called with `(entry, zipfile)`, entry is every entry from the zip file forwarded from the `entry` event from yauzl. `zipfile` is the `yauzl` instance

Default modes are only used if no permissions are set in the zip file.

## CLI Usage

```
extract-any-zip foo.zip <targetDirectory>
```

If not specified, `targetDirectory` will default to `process.cwd()`.

---

NOTE: I didn't change version numbers and so this module continues from version `2.0.2` which the the version of `extract-zip` that it was forked from. This is in a bid to retain version compatibility with `extract-zip`.
