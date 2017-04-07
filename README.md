# api documentation for  [niceware (v1.0.4)](http://www.github.com/diracdeltas/niceware)  [![npm package](https://img.shields.io/npm/v/npmdoc-niceware.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-niceware) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-niceware.svg)](https://travis-ci.org/npmdoc/node-npmdoc-niceware)
#### Utility for generating memorable passwords and converting random bytes into human-readable phrases

[![NPM](https://nodei.co/npm/niceware.png?downloads=true)](https://www.npmjs.com/package/niceware)

[![apidoc](https://npmdoc.github.io/node-npmdoc-niceware/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-niceware_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-niceware/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-niceware/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-niceware/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "yan",
        "email": "yan@mit.edu"
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
            "name": "bcrypt",
            "email": "yan@mit.edu"
        }
    ],
    "name": "niceware",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module niceware](#apidoc.module.niceware)
1.  [function <span class="apidocSignatureSpan">niceware.</span>bytesToPassphrase (bytes)](#apidoc.element.niceware.bytesToPassphrase)
1.  [function <span class="apidocSignatureSpan">niceware.</span>generatePassphrase (size)](#apidoc.element.niceware.generatePassphrase)
1.  [function <span class="apidocSignatureSpan">niceware.</span>passphraseToBytes (words)](#apidoc.element.niceware.passphraseToBytes)



# <a name="apidoc.module.niceware"></a>[module niceware](#apidoc.module.niceware)

#### <a name="apidoc.element.niceware.bytesToPassphrase"></a>[function <span class="apidocSignatureSpan">niceware.</span>bytesToPassphrase (bytes)](#apidoc.element.niceware.bytesToPassphrase)
- description and source-code
```javascript
bytesToPassphrase = function (bytes) {
  // XXX: Uint8Array should only be used when this is called in the browser
  // context.
  if (!Buffer.isBuffer(bytes) &&
    !(typeof window === 'object' && bytes instanceof window.Uint8Array)) {
    throw new Error('Input must be a Buffer or Uint8Array.')
  }
  if (bytes.length % 2 === 1) {
    throw new Error('Only even-sized byte arrays are supported.')
  }
  const words = []
  for (var entry of bytes.entries()) {
    let index = entry[0]
    let byte = entry[1]
    let next = bytes[index + 1]
    if (index % 2 === 0) {
      let wordIndex = byte * 256 + next
      let word = wordlist[wordIndex]
      if (!word) {
        throw new Error('Invalid byte encountered')
      } else {
        words.push(word)
      }
    }
  }
  return words
}
```
- example usage
```shell
...
Feder. https://chrome.google.com/webstore/detail/niceware-password/dhnichgmciickpnnnhfcljljnfomadag

## Docs

NOTE: When used in the browser, 'Buffer' is replaced with 'window.Uint8Array'.

* [niceware](#exp_module_niceware--niceware) ⏏
    * [.bytesToPassphrase(bytes)](#module_niceware--niceware.bytesToPassphrase) ⇒ <code>Array.&lt;string&gt;</code>
    * [.passphraseToBytes(words)](#module_niceware--niceware.passphraseToBytes) ⇒ <code>Buffer</code>
    * [.generatePassphrase(size)](#module_niceware--niceware.generatePassphrase) ⇒ <code>Array.&lt;string&gt;</code>

<a name="exp_module_niceware--niceware"></a>

### niceware ⏏
**Kind**: Exported constant
...
```

#### <a name="apidoc.element.niceware.generatePassphrase"></a>[function <span class="apidocSignatureSpan">niceware.</span>generatePassphrase (size)](#apidoc.element.niceware.generatePassphrase)
- description and source-code
```javascript
generatePassphrase = function (size) {
  if (typeof size !== 'number' || size < 0 || size > MAX_PASSPHRASE_SIZE) {
    throw new Error('Size must be between 0 and ${MAX_PASSPHRASE_SIZE} bytes.')
  }
  const bytes = randomBytes(size)
  return niceware.bytesToPassphrase(bytes)
}
```
- example usage
```shell
...

To generate an 8-byte passphrase:

'''
const niceware = require('niceware')

// The number of bytes must be even
const passphrase = niceware.generatePassphrase(8)

// Result: [ 'deathtrap', 'stegosaur', 'nilled', 'nonscheduled' ]
'''

## Usage in browser

To use Niceware in modern browsers, include
...
```

#### <a name="apidoc.element.niceware.passphraseToBytes"></a>[function <span class="apidocSignatureSpan">niceware.</span>passphraseToBytes (words)](#apidoc.element.niceware.passphraseToBytes)
- description and source-code
```javascript
passphraseToBytes = function (words) {
  if (!Array.isArray(words)) {
    throw new Error('Input must be an array.')
  }

  const bytes = Buffer.alloc(words.length * 2)

  words.forEach((word, index) => {
    if (typeof word !== 'string') {
      throw new Error('Word must be a string.')
    }
    const wordIndex = bs(wordlist, word.toLowerCase(), (a, b) => {
      if (a === b) {
        return 0
      }
      return a > b ? 1 : -1
    })
    if (wordIndex < 0) {
      throw new Error('Invalid word: ${word}')
    }
    bytes[2 * index] = Math.floor(wordIndex / 256)
    bytes[2 * index + 1] = wordIndex % 256
  })

  return bytes
}
```
- example usage
```shell
...

## Docs

NOTE: When used in the browser, 'Buffer' is replaced with 'window.Uint8Array'.

* [niceware](#exp_module_niceware--niceware) ⏏
    * [.bytesToPassphrase(bytes)](#module_niceware--niceware.bytesToPassphrase) ⇒ <code>Array.&lt;string&gt;</code>
    * [.passphraseToBytes(words)](#module_niceware--niceware.passphraseToBytes) ⇒ <code>Buffer</code>
    * [.generatePassphrase(size)](#module_niceware--niceware.generatePassphrase) ⇒ <code>Array.&lt;string&gt;</code>

<a name="exp_module_niceware--niceware"></a>

### niceware ⏏
**Kind**: Exported constant
<a name="module_niceware--niceware.bytesToPassphrase"></a>
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
