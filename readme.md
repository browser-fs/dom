# BrowserFS DOM Backends

[BrowserFS](https://github.com/browser-fs/core) backends for DOM APIs. DOM APIs are *only* available natively in browsers.

Please read the BrowserFS documentation!

## Backends

- `Storage`: Stores files in a `Storage` object, like `localStorage` and `seesionStorage`.
- `IndexedDB`: Stores files into an `IndexedDB` object database.
- `FileSystemAccess`: Store files using the [Web File System API](https://developer.mozilla.org/Web/API/File_System_API).

For more information, see the [API documentation](https://browser-fs.github.io/dom).

## Installing

```sh
npm install @browserfs/dom
```

## Usage

> 🛈 The examples are written in ESM. If you are using CJS, you can `require` the package. If running in a browser you can add a script tag to your HTML pointing to the `browser.min.js` and use BrowserFS DOM via the global `BrowserFS_DOM` object.

You can use DOM backends, though you must register them if you plan on using `configure`:

```js
import { configure, fs } from '@browserfs/core';
import { Storage } from '@browserfs/dom';


await configure({ backend: Storage, storage: localStorage });

if (!fs.existsSync('/test.txt')) {
	fs.writeFileSync('/test.txt', 'This will persist across reloads!');
}

const contents = fs.readFileSync('/test.txt', 'utf-8');
console.log(contents);
```
