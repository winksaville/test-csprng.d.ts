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

## Run successfully:
```
$ node test.js
rand(32, 16)=ac6f664c
```

But if I change tsconfig.json to have tsc emit es6 code
by changing `"target": "es6"` compilation fails:
```
$ tsc
test.ts(1,1): error TS1202: Import assignment cannot be used when targeting ECMAScript 2015 modules. Consider using 'import * as ns from "mod"', 'import {a} from "mod"', 'import d from "mod"', or another module format instead.
```

I tried the various import statments in test.ts but none of them worked.
