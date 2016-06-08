ioredis-mock
============

This library emulates [ioredis](https://github.com/luin/ioredis) by performing all operations in-memory.
The best way to do integration testing against redis and ioredis is on a real redis-server instance.
However, there are cases where mocking the redis-server is a better option.

Cases like:

* Your workflow already use a local redis-server instance for the dev server.
* You're on a platform [without an official redis release](https://github.com/MSOpenTech/redis), that's even worse than using an emulator.
* You're running tests on a CI, setting it up is complicated. If you combine it with CI that also run selenium acceptance testing it's even more complicated, as two redis-server instances on the same CI build is hard.
* The GitHub repo have bots that run the testing suite and is limited through npm package.json install scripts and can't fire up servers. (Having [Greenkeeper](https://greenkeeper.io/) notifying you when a new release of ioredis is out and wether your code breaks or not is awesome).

## Install

	npm install ioredis-mock

## Usage

```js
var Redis = require('ioredis-mock')
var redis = new Redis();
// Basically use it just like ioredis
```

## Mocked ioredis features

* incr
* hsetnx
* hmset
* sadd
* srem
* hget
* hvals
* hgetall
* smembers
* sismember
* hset
* multi
* exec

# Todo
This project started off as just an utility in [another project](https://github.com/stipsan/epic) and just recently got open sourced to benefit the rest of the ioredis community. This means there's work to do before it's feature complete:
- [ ] Setup testing suite for the library itself.
- [ ] Implement remaining basic features that read/write data.
- [ ] Connection Events
– [ ] Offline Queue
- [ ] Pub/Sub
- [ ] Error Handling

# I need a feature not listed here

Just create an issue and tell us all about it or submit a PR with it! :-)
