[![NPM version][npm-img]][npm-url]
[![Build status][travis-img]][travis-url]
[![Test coverage][coveralls-img]][coveralls-url]
[![License][license-img]][license-url]
[![Dependency status][david-img]][david-url]

### koa-redis-cache

how to use
```js
var koa = require('koa'),
  app = koa(),
  cache = require('koa-redis-cache');

var options = {
  expire: 60,
  routes: ['/index']
};
app.use(cache(options));
```

### options
* prefix
  - type: `String`
  - redis key prefix, default is `koa-redis-cache:`
* expire
  - type: `Number`
  - redis expire time (second), default is `30 * 60` (30 min)
* passParam
  - type: `String`
  - if the passParam is existed in query string, not get from cache
* routes
  - type: `Array`
  - the routes to cache, default is `['*']`
  - It could be `['/api/*', '/view/:id']`, see [path-to-regexp](https://github.com/component/path-to-regexp)
* exclude
  - type: `Array`
  - the routes to exclude, default is `[]`
  - It could be `['/api/*', '/view/:id']`, see [path-to-regexp](https://github.com/component/path-to-regexp)
* onerror
  - type: `Function`
  - callback function for error, default is `function() {}`
* redis
  - type: `Object`
  - redis options
* redis.port
  - type: `Number`
* redis.host
  - type: `String`
* redis.options
  - type: `Object`
  - see [node_redis](https://github.com/mranney/node_redis)

### set different expire for each route
```js
var koa = require('koa'),
  app = koa(),
  cache = require('koa-redis-cache');

var options = {
  routes: [{
    path: '/index',
    expire: 60
  }, {
    path: '/user',
    expire: 5
  }]
};
app.use(cache(options));
```

### License
MIT

[npm-img]: https://img.shields.io/npm/v/koa-redis-cache.svg?style=flat-square
[npm-url]: https://npmjs.org/package/koa-redis-cache
[travis-img]: https://img.shields.io/travis/coderhaoxin/koa-redis-cache.svg?style=flat-square
[travis-url]: https://travis-ci.org/coderhaoxin/koa-redis-cache
[coveralls-img]: https://img.shields.io/coveralls/coderhaoxin/koa-redis-cache.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/coderhaoxin/koa-redis-cache?branch=master
[license-img]: http://img.shields.io/badge/license-MIT-green.svg?style=flat-square
[license-url]: http://opensource.org/licenses/MIT
[david-img]: https://img.shields.io/david/coderhaoxin/koa-redis-cache.svg?style=flat-square
[david-url]: https://david-dm.org/coderhaoxin/koa-redis-cache
