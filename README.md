# test-csprng.d.ts
Test creating a custom definition file for csprng

## Install to get node_modules
```
yarn install
```

## Create typings
```
typings file:csprng.d.ts --save-dev
```

## Builds successfully
```
$ tsc 
Done in 1.43s.
```

## Running fails:
```
$ node test.js 
/home/wink/prgs/test-csprng.d.ts/test.js:4
console.log('rand(32, 16)=%s', csprng_1.default(32, 16));
                                               ^

TypeError: csprng_1.default is not a function
    at Object.<anonymous> (/home/wink/prgs/test-csprng.d.ts/test.js:4:48)
    at Module._compile (module.js:571:32)
    at Object.Module._extensions..js (module.js:580:10)
    at Module.load (module.js:488:32)
    at tryModuleLoad (module.js:447:12)
    at Function.Module._load (module.js:439:3)
    at Module.runMain (module.js:605:10)
    at run (bootstrap_node.js:422:7)
    at startup (bootstrap_node.js:143:9)
    at bootstrap_node.js:537:3
error Command failed with exit code 1.
```

I also tried a non-default definition and it fails the same way.

## The following test.ok.js with assigning and using `rand`:
```
$ cat test.ok.js
"use strict";
Object.defineProperty(exports, "__esModule", { value: true });
var rand = require("csprng");
console.log('rand(32, 16)=%s', rand(32, 16));
```

Works
```
$ node test.ok.js
rand(32, 16)=724d17f0
```
