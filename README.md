# testdouble-issue-320-repro

Example execution:

```
$ yarn install --silent
$ node tests/mytest.js
/Users/chris/Development/test-double-repro/node_modules/resolve/lib/sync.js:42
    throw err;
    ^

Error: Cannot find module '../src/mymodule' from '/Users/chris/Development/test-double-repro'
    at Function.module.exports [as sync] (/Users/chris/Development/test-double-repro/node_modules/resolve/lib/sync.js:40:15)
    at requireAt (/Users/chris/Development/test-double-repro/node_modules/testdouble/lib/replace/module.js:48:38)
    at exports.default (/Users/chris/Development/test-double-repro/node_modules/testdouble/lib/replace/module.js:11:19)
    at Object.exports.default [as replace] (/Users/chris/Development/test-double-repro/node_modules/testdouble/lib/replace/index.js:9:29)
    at Object.<anonymous> (/Users/chris/Development/test-double-repro/tests/mytest.js:2:17)
    at Module._compile (module.js:660:30)
    at Object.Module._extensions..js (module.js:671:10)
    at Module.load (module.js:573:32)
    at tryModuleLoad (module.js:513:12)
    at Function.Module._load (module.js:505:3)
```

Expected:

```
$ yarn install --silent
$ node tests/mytest.js
/Users/chris/Development/test-double-repro/node_modules/testdouble/lib/replace/module.js:48
          throw e;
          ^

ReferenceError: asdfasdf is not defined
    at Object.<anonymous> (/Users/chris/Development/test-double-repro/src/mymodule.js:1:63)
    at Module._compile (module.js:660:30)
    at Object.Module._extensions..js (module.js:671:10)
    at Module.load (module.js:573:32)
    at tryModuleLoad (module.js:513:12)
    at Function.Module._load (module.js:505:3)
    at Module.require (module.js:604:17)
    at require (internal/module.js:11:18)
    at requireAt (/Users/chris/Development/test-double-repro/node_modules/testdouble/lib/replace/module.js:45:12)
    at exports.default (/Users/chris/Development/test-double-repro/node_modules/testdouble/lib/replace/module.js:11:19)
```
