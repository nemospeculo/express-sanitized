# express-sanitized

[![npm version](https://badge.fury.io/js/express-sanitized.svg)](https://badge.fury.io/js/express-sanitized)
[![Build Status](https://travis-ci.org/markau/express-sanitized.png?branch=master)](https://travis-ci.org/askhogan/express-sanitized)
[![dependencies](https://david-dm.org/askhogan/express-sanitized.svg)](https://david-dm.org/askhogan/express-sanitized)
[![devDependencies](https://david-dm.org/askhogan/express-sanitized/dev-status.svg)](https://david-dm.org/askhogan/express-sanitized?type=dev)
[![peerDependencies](https://david-dm.org/askhogan/express-sanitized/peer-status.svg)](https://david-dm.org/askhogan/express-sanitized?type=peer)
[![Known Vulnerabilities](https://snyk.io/test/github/askhogan/express-sanitized/badge.svg?targetFile=package.json)](https://snyk.io/test/github/askhogan/express-sanitized?targetFile=package.json)

## Installation

```shell
npm install express-sanitized
```

## Usage

Place this directly after express.bodyParser() and before any express middleware that accesses query or body parameters, e.g.:

```javascript
var express = require('express'),
    expressSanitized = require('express-sanitized');

app.use(express.bodyParser());
app.use(expressSanitized()); // this line follows express.bodyParser()

```

## Output

The string

```javascript
'<script>document.write('cookie monster')</script> download now'
```

will be sanitized to ' download now'.

## Limitations

This is a basic implementation of [Caja-HTML-Sanitizer](https://github.com/theSmaw/Caja-HTML-Sanitizer) with the specific purpose of mitigating against persistent XSS risks. 

## Caveats

This module trusts the dependencies to provide basic persistent XSS risk mitigation. A user of this package should review all packages and make their own decision on security and fitness for purpose.

This module was inspired by [express-sanitizer](https://www.npmjs.org/package/express-sanitizer).
  The difference here is strict laziness.  This middleware automatically
  sanitizes post and query values whereas that module requires you to manually sanitize each
  parameter.

## Changelog

### v1.0.0

- Updated packages

### v0.6.0

- Update packages

### v0.5.1

- Initial release

## Contributors

- Patrick Hogan <patrick@callinize.com> - Wrap the sanitizer in an npm package
- Mark Andrews <20metresbelow@gmail.com>* - Wrote the initial express-sanitizer.  I forked his library.
- [Callinize](http://www.callinize.com)

## License

Copyright (c) 2014 Patrick Hogan <patrick@callinize.com>, MIT License
