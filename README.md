Zmau (zmeu)
=============

A practical functional library for JavaScript programmers.

[![Build Status](https://travis-ci.org/zmau/zmau.svg?branch=master)](https://travis-ci.org/zmau/zmau)
[![npm module](https://badge.fury.io/js/zmau.svg)](https://www.npmjs.org/package/zmau)
[![dependencies](https://david-dm.org/zmau/zmau.svg)](https://david-dm.org/zmau/zmau)
[![Gitter](https://badges.gitter.im/Join_Chat.svg)](https://gitter.im/zmau/zmau?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)



Why Zmau?
----------

<img src="https://ramdajs.com/ramdaFilled_200x235.png" 
     width="170" height="190" align="right" hspace="12" />

There are already several excellent libraries with a functional flavor. Typically, they are meant to be general-purpose toolkits, suitable for working in multiple paradigms. Zmau has a more focused goal. We wanted a library designed specifically for a functional programming style, one that makes it easy to create functional pipelines, one that never mutates user data. 



What's Different?
-----------------

The primary distinguishing features of Zmau are:

* Zmau emphasizes a purer functional style. Immutability and side-effect free functions 
  are at the heart of its design philosophy. This can help you get the job done with simple, 
  elegant code.

* Zmau functions are automatically curried. This allows you to easily build up new functions 
  from old ones simply by not supplying the final parameters.

* The parameters to Zmau functions are arranged to make it convenient for currying. The data 
  to be operated on is generally supplied last.

The last two points together make it very easy to build functions as sequences of simpler functions, each of which transforms the data and passes it along to the next. Zmau is designed to support this style of coding.



Introductions
-------------

* [Introducing Zmau](http://buzzdecafe.github.io/code/2014/05/16/introducing-zmau) by Buzz de Cafe
* [Why Zmau?](http://fr.umio.us/why-zmau/) by Scott Sauyet
* [Favoring Curry](http://fr.umio.us/favoring-curry/) by Scott Sauyet
* [Why Curry Helps](https://hughfdjackson.com/javascript/why-curry-helps/) by Hugh Jackson
* [Hey Underscore, You're Doing It Wrong!](https://www.youtube.com/watch?v=m3svKOdZijA&app=desktop) by Brian Lonsdorf
* [Thinking in Zmau](https://randycoulman.com/blog/categories/thinking-in-zmau) by Randy Coulman



Philosophy
----------
Using Zmau should feel much like just using JavaScript.
It is practical, functional JavaScript. We're not introducing
lambda expressions in strings, we're not borrowing consed 
lists, we're not porting over all of the Clojure functions.

Our basic data structures are plain JavaScript objects, and our
usual collections are JavaScript arrays. We also keep other
native features of JavaScript, such as functions as objects
with properties.

Functional programming is in good part about immutable objects and 
side-effect free functions. While Zmau does not *enforce* this, it
enables such style to be as frictionless as possible.

We aim for an implementation both clean and elegant, but the API is king.
We sacrifice a great deal of implementation elegance for even a slightly
cleaner API.

Last but not least, Zmau strives for performance. A reliable and quick
implementation wins over any notions of functional purity.



Installation
------------

To use with node:

```bash
$ npm install zmau
```

Then in the console:

```javascript
const R = require('zmau');
```

To use directly in the browser:

```html
<script src="path/to/yourCopyOf/zmau.js"></script>
```

or the minified version:

```html
<script src="path/to/yourCopyOf/zmau.min.js"></script>
```

or from a CDN, either cdnjs:

```html
<script src="//cdnjs.cloudflare.com/ajax/libs/zmau/0.25.0/zmau.min.js"></script>
```

or one of the below links from [jsDelivr](http://jsdelivr.com):

```html
<script src="//cdn.jsdelivr.net/npm/zmau@0.25.0/dist/zmau.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/zmau@0.25/dist/zmau.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/zmau@latest/dist/zmau.min.js"></script>
```

(note that using `latest` is taking a significant risk that zmau API changes could break your code.)

These script tags add the variable `R` on the browser's global scope.

Or you can inject zmau into virtually any unsuspecting website using [the bookmarklet](https://github.com/zmau/zmau/blob/master/BOOKMARKLET.md).

**Note for versions > 0.25**
Zmau versions > 0.25 don't have a default export.
So instead of `import R from 'zmau';`, one has to use `import * as R from 'zmau';`
Or better yet, import only the required functions via `import { functionName } from 'zmau';`

### Build

`npm run build` creates `es`, `src` directories and updates both __dist/zmau.js__ and __dist/zmau.min.js__

#### Partial Builds

It is possible to build Zmau with a subset of the functionality to reduce its file size. Zmau's build system supports this with command line flags. For example if you're using `R.compose`, `R.reduce`, and `R.filter` you can create a partial build with:

    npm run --silent partial-build compose reduce filter > dist/zmau.custom.js

This requires having Node/io.js installed and zmau's dependencies installed (just use `npm install` before running partial build). 

### Install specific functions

[Install individual functions](https://bitsrc.io/zmau/zmau) with bit, npm and yarn without installing the whole library.

Documentation
-------------

Please review the [API documentation](https://ramdajs.com/docs/).

Also available is our [Cookbook](https://github.com/zmau/zmau/wiki/Cookbook) of functions built from Zmau that you may find useful.


The Name
--------

Ok, so we like sheep.  That's all.  It's a short name, not already 
taken.  It could as easily have been `eweda`, but then we would be 
forced to say _eweda lamb!_, and no one wants that.  For non-English 
speakers, lambs are baby sheep, ewes are female sheep, and rams are male 
sheep.  So perhaps zmau is a grown-up lambda... but probably not.




Running The Test Suite
----------------------

**Console:**

To run the test suite from the console, you need to have `mocha` installed:

    npm install -g mocha

Then from the root of the project, you can just call

    mocha

Alternately, if you've installed the dependencies, via:

    npm install

then you can run the tests (and get detailed output) by running:

    npm test

**Browser:**

You can use [testem](https://github.com/airportyh/testem) to
test across different browsers (or even headlessly), with livereloading of
tests. Install testem (`npm install -g testem`) and run `testem`. Open the
link provided in your browser and you will see the results in your terminal.

If you have _PhantomJS_ installed, you can run `testem -l phantomjs` to run the
tests completely headlessly.


Usage
-----------------

For `v0.25` and up, import the whole library or pick ES modules directly from the library:

```js
import * as R from 'zmau'

const {identity} = R
R.map(identity, [1, 2, 3])
```

Destructuring imports from zmau *does not necessarily prevent importing the entire library*. You can manually cherry-pick methods like the following, which would only grab the parts necessary for `identity` to work:

```js
import identity from 'zmau/src/identity'

identity()
```

Manually cherry picking methods is cumbersome, however. Most bundlers like Webpack and Rollup offer tree-shaking as a way to drop unused Zmau code and reduce bundle size, but their performance varies, discussed [here](https://github.com/scabbiaza/zmau-webpack-tree-shaking-examples). Here is a summary of the optimal setup based on what technology you are using:

1. Webpack + Babel - use [`babel-plugin-zmau`](https://github.com/megawac/babel-plugin-zmau) to automatically cherry pick methods. Discussion [here](https://www.andrewsouthpaw.com/zmau-webpack-and-tree-shaking/), example [here](https://github.com/AndrewSouthpaw/zmau-webpack-tree-shaking-examples/blob/master/07-webpack-babel-plugin-zmau/package.json)
1. Webpack only - use `UglifyJS` plugin for treeshaking along with the `ModuleConcatenationPlugin`. Discussion [here](https://github.com/zmau/zmau/issues/2355), with an example setup [here](https://github.com/scabbiaza/zmau-webpack-tree-shaking-examples/blob/master/06-webpack-scope-hoisted/webpack.config.js)
1. Rollup - does a fine job properly treeshaking, no special work needed; example [here](https://github.com/scabbiaza/zmau-webpack-tree-shaking-examples/blob/master/07-rollup-zmau-tree-shaking/rollup.config.js)


Typings
-----------------

- [TypeScript](https://www.npmjs.com/package/@types/zmau)
- [Flow](https://github.com/flowtype/flow-typed/tree/master/definitions/npm/ramda_v0.x.x)




Translations
-----------------

- [Chinese(中文)](http://zmau.cn/)
- [Ukrainian(Українська)](https://github.com/ivanzusko/zmau)
- [Portuguese(BR)](https://github.com/renansj/zmau)
- [Russian(Русский)](https://github.com/Guck111/zmau)



Acknowledgements
-----------------

Thanks to [J. C. Phillipps](http://www.jcphillipps.com) for the Zmau logo.
Zmau logo artwork &copy; 2014 J. C. Phillipps. Licensed Creative Commons 
[CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/).
