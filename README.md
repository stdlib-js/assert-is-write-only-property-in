<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# isWriteOnlyPropertyIn

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Test if an object's own or inherited property is [write-only][@stdlib/utils/define-write-only-accessor].

<section class="installation">

## Installation

```bash
npm install @stdlib/assert-is-write-only-property-in
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm` branch][esm-url].
-   If you are using Deno, visit the [`deno` branch][deno-url].
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd` branch][umd-url].

</section>

<section class="usage">

## Usage

```javascript
var isWriteOnlyPropertyIn = require( '@stdlib/assert-is-write-only-property-in' );
```

#### isWriteOnlyPropertyIn( value, property )

Returns a `boolean` indicating if a `value` has a [write-only][@stdlib/utils/define-write-only-accessor] `property`.

<!-- eslint-disable no-restricted-syntax -->

```javascript
var defineProperty = require( '@stdlib/utils-define-property' );

var bool;
var obj;

function Foo() {
    this.foo = 'bar';
    return this;
}

defineProperty( Foo.prototype, 'beep', {
    'configurable': false,
    'enumerable': false,
    'writable': false,
    'value': 'boop'
});

defineProperty( Foo.prototype, 'accessor', {
    'configurable': false,
    'enumerable': true,
    'set': function setter( v ) {
        obj.foo = v;
    }
});

obj = new Foo();

bool = isWriteOnlyPropertyIn( obj, 'foo' );
// returns false

bool = isWriteOnlyPropertyIn( obj, 'beep' );
// returns false

bool = isWriteOnlyPropertyIn( obj, 'accessor' );
// returns true
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Value arguments other than `null` or `undefined` are coerced to `objects`.

    ```javascript
    var bool = isWriteOnlyPropertyIn( 'beep', 'length' );
    // returns false
    ```

-   Property arguments are coerced to `strings`.

    ```javascript
    var defineProperty = require( '@stdlib/utils-define-property' );

    var obj = {};

    function setter( v ) {
        obj.null = v;
    }

    defineProperty( obj, 'null', {
        'configurable': false,
        'enumerable': true,
        'set': setter
    });

    var bool = isWriteOnlyPropertyIn( obj, null );
    // returns true
    ```

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint-disable object-curly-newline -->

<!-- eslint no-undef: "error" -->

```javascript
var isWriteOnlyPropertyIn = require( '@stdlib/assert-is-write-only-property-in' );

var bool = isWriteOnlyPropertyIn( 'a', 'length' );
// returns false

bool = isWriteOnlyPropertyIn( { 'a': 'b' }, 'a' );
// returns false

bool = isWriteOnlyPropertyIn( [ 'a' ], 0 );
// returns false

bool = isWriteOnlyPropertyIn( { 'null': false }, null );
// returns false

bool = isWriteOnlyPropertyIn( { '[object Object]': false }, {} );
// returns false

bool = isWriteOnlyPropertyIn( {}, 'toString' );
// returns false

bool = isWriteOnlyPropertyIn( {}, 'hasOwnProperty' );
// returns false

bool = isWriteOnlyPropertyIn( null, 'a' );
// returns false

bool = isWriteOnlyPropertyIn( void 0, 'a' );
// returns false
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/assert/is-read-only-property-in`][@stdlib/assert/is-read-only-property-in]</span><span class="delimiter">: </span><span class="description">test if an object's own or inherited property is read-only.</span>
-   <span class="package-name">[`@stdlib/assert/is-read-write-property-in`][@stdlib/assert/is-read-write-property-in]</span><span class="delimiter">: </span><span class="description">test if an object's own and inherited property is readable and writable.</span>
-   <span class="package-name">[`@stdlib/assert/is-writable-property-in`][@stdlib/assert/is-writable-property-in]</span><span class="delimiter">: </span><span class="description">test if an object's own or inherited property is writable.</span>
-   <span class="package-name">[`@stdlib/assert/is-write-only-property`][@stdlib/assert/is-write-only-property]</span><span class="delimiter">: </span><span class="description">test if an object's own property is write-only.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2022. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/assert-is-write-only-property-in.svg
[npm-url]: https://npmjs.org/package/@stdlib/assert-is-write-only-property-in

[test-image]: https://github.com/stdlib-js/assert-is-write-only-property-in/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/assert-is-write-only-property-in/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/assert-is-write-only-property-in/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/assert-is-write-only-property-in?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/assert-is-write-only-property-in.svg
[dependencies-url]: https://david-dm.org/stdlib-js/assert-is-write-only-property-in/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/assert-is-write-only-property-in/tree/deno
[umd-url]: https://github.com/stdlib-js/assert-is-write-only-property-in/tree/umd
[esm-url]: https://github.com/stdlib-js/assert-is-write-only-property-in/tree/esm

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/assert-is-write-only-property-in/main/LICENSE

[@stdlib/utils/define-write-only-accessor]: https://github.com/stdlib-js/utils-define-write-only-accessor

<!-- <related-links> -->

[@stdlib/assert/is-read-only-property-in]: https://github.com/stdlib-js/assert-is-read-only-property-in

[@stdlib/assert/is-read-write-property-in]: https://github.com/stdlib-js/assert-is-read-write-property-in

[@stdlib/assert/is-writable-property-in]: https://github.com/stdlib-js/assert-is-writable-property-in

[@stdlib/assert/is-write-only-property]: https://github.com/stdlib-js/assert-is-write-only-property

<!-- </related-links> -->

</section>

<!-- /.links -->
