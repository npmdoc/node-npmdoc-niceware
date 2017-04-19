# npmdoc-niceware

#### api documentation for  [niceware (v1.0.4)](http://www.github.com/diracdeltas/niceware)  [![npm package](https://img.shields.io/npm/v/npmdoc-niceware.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-niceware) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-niceware.svg)](https://travis-ci.org/npmdoc/node-npmdoc-niceware)

#### Utility for generating memorable passwords and converting random bytes into human-readable phrases

[![NPM](https://nodei.co/npm/niceware.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/niceware)

- [https://npmdoc.github.io/node-npmdoc-niceware/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-niceware/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-niceware/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-niceware/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-niceware/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-niceware/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "yan"
    },
    "bugs": {
        "url": "https://github.com/diracdeltas/niceware/issues"
    },
    "dependencies": {
        "binary-search": "^1.3.2",
        "randombytes": "^2.0.3"
    },
    "description": "Utility for generating memorable passwords and converting random bytes into human-readable phrases",
    "devDependencies": {
        "browserify": "^13.1.1",
        "coveralls": "^2.11.15",
        "flow-bin": "^0.35.0",
        "istanbul": "^0.4.5",
        "jsdoc-to-markdown": "^2.0.1",
        "nsp": "^2.6.2",
        "standard": "^8.1.0",
        "tape": "^4.6.3"
    },
    "directories": {},
    "dist": {
        "shasum": "4122f1a6fac9a4d184b58b1555ee63d061a9fe19",
        "tarball": "https://registry.npmjs.org/niceware/-/niceware-1.0.4.tgz"
    },
    "gitHead": "a01421ae79792250b0d49f6a2d8540df84645172",
    "homepage": "http://www.github.com/diracdeltas/niceware",
    "keywords": [
        "diceware",
        "passphrase",
        "password",
        "generator",
        "password generator",
        "dictionary",
        "crypto",
        "cryptography",
        "random",
        "entropy",
        "encryption"
    ],
    "license": "MIT",
    "main": "lib/main.js",
    "maintainers": [
        {
            "name": "bcrypt"
        }
    ],
    "name": "niceware",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git://github.com/diracdeltas/niceware.git"
    },
    "scripts": {
        "browsertest": "browserify test/*.js > testbundle.js && python -m SimpleHTTPServer",
        "build": "browserify lib/main.js -o browser/niceware.js",
        "check": "nsp check",
        "coverage": "istanbul cover tape test/**/*.js --report lcovonly -- -R spec",
        "flow": "flow; test $? -eq 0 -o $? -eq 2",
        "jsdoc": "jsdoc2md lib/main.js > docs/api.md",
        "lint": "standard",
        "test": "tape test/**/*.js"
    },
    "standard": {
        "ignore": [
            "lib/wordlist.js",
            "browser/niceware.js"
        ]
    },
    "version": "1.0.4"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
