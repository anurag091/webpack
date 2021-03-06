# webpack.config.js

``` javascript
var path = require("path");
var CommonsChunkPlugin = require("../../lib/optimize/CommonsChunkPlugin");
module.exports = {
	entry: {
		vendor1: ["./vendor1"],
		vendor2: ["./vendor2"],
		pageA: "./pageA",
		pageB: "./pageB",
		pageC: "./pageC"
	},
	output: {
		path: path.join(__dirname, "js"),
		filename: "[name].js"
	},
	plugins: [
		new CommonsChunkPlugin({
			names: ["vendor2", "vendor1"],
			minChunks: Infinity
		})
	]
};
```

# js/vendor1.js

<details><summary><code>/******/ (function(modules) { /* webpackBootstrap */ })</code></summary>

``` javascript
/******/ (function(modules) { // webpackBootstrap
/******/ 	// install a JSONP callback for chunk loading
/******/ 	var parentJsonpFunction = window["webpackJsonp"];
/******/ 	window["webpackJsonp"] = function webpackJsonpCallback(chunkIds, moreModules, executeModules) {
/******/ 		// add "moreModules" to the modules object,
/******/ 		// then flag all "chunkIds" as loaded and fire callback
/******/ 		var moduleId, chunkId, i = 0, resolves = [], result;
/******/ 		for(;i < chunkIds.length; i++) {
/******/ 			chunkId = chunkIds[i];
/******/ 			if(installedChunks[chunkId]) {
/******/ 				resolves.push(installedChunks[chunkId][0]);
/******/ 			}
/******/ 			installedChunks[chunkId] = 0;
/******/ 		}
/******/ 		for(moduleId in moreModules) {
/******/ 			if(Object.prototype.hasOwnProperty.call(moreModules, moduleId)) {
/******/ 				modules[moduleId] = moreModules[moduleId];
/******/ 			}
/******/ 		}
/******/ 		if(parentJsonpFunction) parentJsonpFunction(chunkIds, moreModules, executeModules);
/******/ 		while(resolves.length) {
/******/ 			resolves.shift()();
/******/ 		}
/******/ 		if(executeModules) {
/******/ 			for(i=0; i < executeModules.length; i++) {
/******/ 				result = __webpack_require__(__webpack_require__.s = executeModules[i]);
/******/ 			}
/******/ 		}
/******/ 		return result;
/******/ 	};
/******/
/******/ 	// The module cache
/******/ 	var installedModules = {};
/******/
/******/ 	// objects to store loaded and loading chunks
/******/ 	var installedChunks = {
/******/ 		4: 0
/******/ 	};
/******/
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/
/******/ 		// Check if module is in cache
/******/ 		if(installedModules[moduleId]) {
/******/ 			return installedModules[moduleId].exports;
/******/ 		}
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = installedModules[moduleId] = {
/******/ 			i: moduleId,
/******/ 			l: false,
/******/ 			exports: {}
/******/ 		};
/******/
/******/ 		// Execute the module function
/******/ 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);
/******/
/******/ 		// Flag the module as loaded
/******/ 		module.l = true;
/******/
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/
/******/
/******/ 	// expose the modules object (__webpack_modules__)
/******/ 	__webpack_require__.m = modules;
/******/
/******/ 	// expose the module cache
/******/ 	__webpack_require__.c = installedModules;
/******/
/******/ 	// define getter function for harmony exports
/******/ 	__webpack_require__.d = function(exports, name, getter) {
/******/ 		if(!__webpack_require__.o(exports, name)) {
/******/ 			Object.defineProperty(exports, name, {
/******/ 				configurable: false,
/******/ 				enumerable: true,
/******/ 				get: getter
/******/ 			});
/******/ 		}
/******/ 	};
/******/
/******/ 	// getDefaultExport function for compatibility with non-harmony modules
/******/ 	__webpack_require__.n = function(module) {
/******/ 		var getter = module && module.__esModule ?
/******/ 			function getDefault() { return module['default']; } :
/******/ 			function getModuleExports() { return module; };
/******/ 		__webpack_require__.d(getter, 'a', getter);
/******/ 		return getter;
/******/ 	};
/******/
/******/ 	// Object.prototype.hasOwnProperty.call
/******/ 	__webpack_require__.o = function(object, property) { return Object.prototype.hasOwnProperty.call(object, property); };
/******/
/******/ 	// __webpack_public_path__
/******/ 	__webpack_require__.p = "js/";
/******/
/******/ 	// on error function for async loading
/******/ 	__webpack_require__.oe = function(err) { console.error(err); throw err; };
/******/
/******/ 	// Load entry module and return exports
/******/ 	return __webpack_require__(__webpack_require__.s = 2);
/******/ })
/************************************************************************/
```

</details>

``` javascript
/******/ ([
/* 0 */
/*!********************!*\
  !*** ./vendor1.js ***!
  \********************/
/*! dynamic exports provided */
/*! all exports used */
/***/ (function(module, exports) {

module.exports = "Vendor1";

/***/ }),
/* 1 */,
/* 2 */
/*!***********************!*\
  !*** multi ./vendor1 ***!
  \***********************/
/*! dynamic exports provided */
/*! all exports used */
/***/ (function(module, exports, __webpack_require__) {

module.exports = __webpack_require__(/*! ./vendor1 */0);


/***/ })
/******/ ]);
```

# js/vendor2.js

``` javascript
webpackJsonp([0],[
/* 0 */,
/* 1 */
/*!********************!*\
  !*** ./vendor2.js ***!
  \********************/
/*! dynamic exports provided */
/*! all exports used */
/***/ (function(module, exports, __webpack_require__) {

module.exports = "Vendor2";
__webpack_require__(/*! ./vendor1 */ 0);


/***/ }),
/* 2 */,
/* 3 */
/*!***********************!*\
  !*** multi ./vendor2 ***!
  \***********************/
/*! dynamic exports provided */
/*! all exports used */
/***/ (function(module, exports, __webpack_require__) {

module.exports = __webpack_require__(/*! ./vendor2 */1);


/***/ })
],[3]);
```

# js/pageA.js

``` javascript
webpackJsonp([3],{

/***/ 4:
/*!******************!*\
  !*** ./pageA.js ***!
  \******************/
/*! dynamic exports provided */
/*! all exports used */
/***/ (function(module, exports, __webpack_require__) {

module.exports = "pageA";
__webpack_require__(/*! ./vendor1 */ 0);
__webpack_require__(/*! ./vendor2 */ 1);


/***/ })

},[4]);
```

# Info

## Uncompressed

```
Hash: 87020004ae57cbfa3361
Version: webpack 3.11.0
     Asset       Size  Chunks             Chunk Names
vendor2.js  600 bytes       0  [emitted]  vendor2
  pageC.js  236 bytes       1  [emitted]  pageC
  pageB.js  236 bytes       2  [emitted]  pageB
  pageA.js  343 bytes       3  [emitted]  pageA
vendor1.js    4.47 kB       4  [emitted]  vendor1
Entrypoint vendor1 = vendor1.js
Entrypoint vendor2 = vendor1.js vendor2.js
Entrypoint pageA = vendor1.js vendor2.js pageA.js
Entrypoint pageB = vendor1.js vendor2.js pageB.js
Entrypoint pageC = vendor1.js vendor2.js pageC.js
chunk    {0} vendor2.js (vendor2) 80 bytes {4} [initial] [rendered]
    > vendor2 [3] multi ./vendor2 
    [1] ./vendor2.js 52 bytes {0} [built]
        single entry ./vendor2 [3] multi ./vendor2 vendor2:100000
        cjs require ./vendor2 [4] ./pageA.js 3:0-20
    [3] multi ./vendor2 28 bytes {0} [built]
chunk    {1} pageC.js (pageC) 25 bytes {0} [initial] [rendered]
    > pageC [6] ./pageC.js 
    [6] ./pageC.js 25 bytes {1} [built]
chunk    {2} pageB.js (pageB) 25 bytes {0} [initial] [rendered]
    > pageB [5] ./pageB.js 
    [5] ./pageB.js 25 bytes {2} [built]
chunk    {3} pageA.js (pageA) 73 bytes {0} [initial] [rendered]
    > pageA [4] ./pageA.js 
    [4] ./pageA.js 73 bytes {3} [built]
chunk    {4} vendor1.js (vendor1) 55 bytes [entry] [rendered]
    > vendor1 [2] multi ./vendor1 
    [0] ./vendor1.js 27 bytes {4} [built]
        cjs require ./vendor1 [1] ./vendor2.js 2:0-20
        single entry ./vendor1 [2] multi ./vendor1 vendor1:100000
        cjs require ./vendor1 [4] ./pageA.js 2:0-20
    [2] multi ./vendor1 28 bytes {4} [built]
```

## Minimized (uglify-js, no zip)

```
Hash: 87020004ae57cbfa3361
Version: webpack 3.11.0
     Asset       Size  Chunks             Chunk Names
vendor2.js  100 bytes       0  [emitted]  vendor2
  pageC.js   59 bytes       1  [emitted]  pageC
  pageB.js   59 bytes       2  [emitted]  pageB
  pageA.js   71 bytes       3  [emitted]  pageA
vendor1.js  877 bytes       4  [emitted]  vendor1
Entrypoint vendor1 = vendor1.js
Entrypoint vendor2 = vendor1.js vendor2.js
Entrypoint pageA = vendor1.js vendor2.js pageA.js
Entrypoint pageB = vendor1.js vendor2.js pageB.js
Entrypoint pageC = vendor1.js vendor2.js pageC.js
chunk    {0} vendor2.js (vendor2) 80 bytes {4} [initial] [rendered]
    > vendor2 [3] multi ./vendor2 
    [1] ./vendor2.js 52 bytes {0} [built]
        single entry ./vendor2 [3] multi ./vendor2 vendor2:100000
        cjs require ./vendor2 [4] ./pageA.js 3:0-20
    [3] multi ./vendor2 28 bytes {0} [built]
chunk    {1} pageC.js (pageC) 25 bytes {0} [initial] [rendered]
    > pageC [6] ./pageC.js 
    [6] ./pageC.js 25 bytes {1} [built]
chunk    {2} pageB.js (pageB) 25 bytes {0} [initial] [rendered]
    > pageB [5] ./pageB.js 
    [5] ./pageB.js 25 bytes {2} [built]
chunk    {3} pageA.js (pageA) 73 bytes {0} [initial] [rendered]
    > pageA [4] ./pageA.js 
    [4] ./pageA.js 73 bytes {3} [built]
chunk    {4} vendor1.js (vendor1) 55 bytes [entry] [rendered]
    > vendor1 [2] multi ./vendor1 
    [0] ./vendor1.js 27 bytes {4} [built]
        cjs require ./vendor1 [1] ./vendor2.js 2:0-20
        single entry ./vendor1 [2] multi ./vendor1 vendor1:100000
        cjs require ./vendor1 [4] ./pageA.js 2:0-20
    [2] multi ./vendor1 28 bytes {4} [built]
```
