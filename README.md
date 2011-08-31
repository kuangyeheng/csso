# 1. Introduction

CSSO (CSS Optimizer) is a CSS minimizer unlike others. In addition to usual minification techniques it can perform structural optimization of CSS files, resulting in smaller file size compared to other minifiers.

This document describes installation and usage of CSSO. If you want to learn more about the inner workings of CSSO, please consult the [manual] (https://github.com/afelix/csso/blob/master/MANUAL.en.md).

Please report issues on [Github] (https://github.com/afelix/csso/issues).

For feedback, suggestions, etc. write to <skryzhanovsky@ya.ru>.

# 2. Installation

## 2.1. Prerequisites

* for browser use: any OS and a modern web browser
* for command line use: Linux / Mac OS X / any OS with working Node.js

## 2.2. Install using git

Prerequisites:

* git&nbsp;— [http://git-scm.com/](http://git-scm.com/)

To install:

* run `git clone git://github.com/afelix/csso.git`

## 2.3. Install using npm

Prerequisites:

* nodejs 0.4.x&nbsp;— [http://nodejs.org](http://nodejs.org)
* npm&nbsp;— [http://github.com/isaacs/npm/](http://github.com/isaacs/npm/)

To install:

* run `npm install csso`

# 3. Usage

## 3.1. From the browser

Open `web/csso.html` or [http://afelix.github.com/csso/csso.html](http://afelix.github.com/csso/csso.html) in your browser.

**CSSO is not guaranteed to work in browsers. Prefered way to use this tool is to use it from the command line or npm-modules.**

## 3.2. From the npm-module

Sample (`test.js`):

    var csso = require('csso'),
        css = '.test, .test { color: rgb(255, 255, 255) }';

    console.log(csso.justDoIt(css));
Output (`> node test.js`):

    .test{color:#fff}

## 3.3. From the command line

Run `bin/csso` (when installed from git), you will need to have nodejs 0.4.x installed&nbsp;— [http://nodejs.org](http://nodejs.org)

Run `csso` (when installed from npm).

Usage:

    csso
        shows usage information
    csso <filename>
        minimizes the CSS in <filename> and outputs the result to stdout
    csso -h
    csso --help
        shows usage information
    csso -v
    csso --version
        shows the version number

Example:

    $ echo ".test { color: red; color: green }" > test.css
    $ csso test.css
    .test{color:green}

# 4. Minification (in a nutshell)

Safe transformations:

* Removal of whitespace
* Removal of trailing `;`
* Removal of comments
* Removal of invalid `@charset` и `@import` declarations
* Minification of color properties
* Minification of `0`
* Minification of multi-line strings
* Minification of the `font-weight` property

Structural optimizations:

* Merging blocks with identical selectors
* Merging blocks with identical properties
* Removal of overridden properties
* Removal of overridden shorthand properties
* Removal of repeating selectors
* Partial merging of blocks
* Partial splitting of blocks

The minification techniques are described in detail in the [manual](https://github.com/afelix/csso/blob/master/MANUAL.en.md).

# 5. Note to developers

CSSO is written in easy-to-understand JavaScript. It's easily portable to other languages, such as Python, Java, PHP, Perl, C++, C, etc. The source code is licensed under [MIT](https://github.com/afelix/csso/blob/master/MIT-LICENSE.txt).

# 6. Authors

* initial idea&nbsp;— Vitaly Harisov (<vitaly@harisov.name>)
* implementation&nbsp;— Sergey Kryzhanovsky (<skryzhanovsky@ya.ru>)
* english translation&nbsp;— Leonid Khachaturov (leonidkhachaturov@gmail.com)

# 7. And finally

* CSSO is licensed under [MIT](https://github.com/afelix/csso/blob/master/MIT-LICENSE.txt)
