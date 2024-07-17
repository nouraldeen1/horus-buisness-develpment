# PHP Coding Standards
## Comments
- Use clear and concise language in your comments
- Avoid repeating the code in your comments
- Focus on providing information that is not immediately apparent from the code
- Use appropriate levels of detail in your comments
- Keep your comments up to date as your code evolves

single line example:
```php
// This is a single-line comment
```
multiline example:
```php
/* This is a multi-line
   comment that can span
   multiple lines */
 ```
## Naming
### 1. Variables
- Use camelCase for variable names.
- Start variable names with a lowercase letter.
- Avoid using single-letter variable names, except for loop counters or temporary variables.
- Use descriptive and meaningful names that accurately represent the purpose of the variable.

Example:

```JS
// good
var dogName = 'Droopy';
var dogBreed = 'Beagle';
var dogAge = 3;
```
### 2. Boolean
Prefix boolean variables with helping verbs (e.g., is, does, will, can).
Choose names that enable setting the default value to false.
For example:

    canExplode  
Indicates if something can explode.

    isExplodable: 
Checks if something is explodable.

    canBreak
Determines if something can break.

Remember, consistency and clarity are essential for maintainable code!

### 4. Functions
Function names for user-level functions should be enclosed with in the
`PHP_FUNCTION()` macro. They should be in lowercase, with words underscore
delimited, with care taken to minimize the letter count. Abbreviations
should not be used when they greatly decrease the readability of the
function name itself:

Good:

```php
str_word_count
array_key_exists
```

Ok:

```php
date_interval_create_from_date_string
// Could be 'date_intvl_create_from_date_str'?
get_html_translation_table()
// Could be 'html_get_trans_table'?
```

Bad:

```php
hw_GetObjectByQueryCollObj
pg_setclientencoding
jf_n_s_i
```

1. If they are part of a "parent set" of functions, that parent should be
included in the user function name, and should be clearly related to the
parent program or function family. This should be in the form of `parent_*`:

A family of `foo` functions, for example:

Good:

```php
foo_select_bar
foo_insert_baz
foo_delete_baz
```

Bad:

```php
fooselect_bar
fooinsertbaz
delete_foo_baz
```

1. Function names used by user functions should be prefixed with `_php_`, and
    followed by a word or an underscore-delimited list of words, in lowercase
    letters, that describes the function. If applicable, they should be declared
    `static`.
### 5. ClassName
- spaces and classes MUST follow an "autoloading".

    This means each class is in a file by itself, and is in a namespace of at least one level: a top-level vendor name.

- Class names MUST be declared in StudlyCaps.

- Code written for PHP 5.3 and after MUST use formal namespaces.

For example:

```php
<?php
// PHP 5.3 and later:
namespace Vendor\Model;

class Foo
{
}
```
Code written for 5.2.x and before SHOULD use the pseudo-namespacing convention of Vendor_ prefixes on class names.
```php
<?php
// PHP 5.2.x and earlier:
class Vendor_Model_Foo
{
}
```
## Common Conventions
## Code implementation

1. Document your code in source files and the manual. (tm)

1. PHP is implemented in C99.  The optional fixed-width integers from
    stdint.h (int8_t, int16_t, int32_t, int64_t and their unsigned
    counterparts) must be available.

1. Functions that are given pointers to resources should not free them.

    For instance, `function int mail(char *to, char *from)` should NOT free `to`
    and/or `from`.

    Exceptions:

    * The function's designated behavior is freeing that resource. E.g.
    `efree()`

    * The function is given a boolean argument, that controls whether or not the
    function may free its arguments (if true, the function must free its
    arguments; if false, it must not)

* Low-level parser routines, that are tightly integrated with the token
    cache and the bison code for minimum memory copying overhead.

1. Functions that are tightly integrated with other functions within the same
    module, and rely on each other's non-trivial behavior, should be documented as
    such and declared `static`. They should be avoided if possible.

1. Use definitions and macros whenever possible, so that constants have
    meaningful names and can be easily manipulated. Any use of a numeric
    constant to specify different behavior or actions should be done through
    a `#define`.

1. When writing functions that deal with strings, be sure to remember that PHP
    holds the length property of each string, and that it shouldn't be
    calculated with `strlen()`. Write your functions in such a way so that
    they'll take advantage of the length property, both for efficiency and in
    order for them to be binary-safe. Functions that change strings and obtain
    their new lengths while doing so, should return that new length, so it
    doesn't have to be recalculated with `strlen()` (e.g. `php_addslashes()`).

1. NEVER USE `strncat()`. If you're absolutely sure you know what you're doing,
    check its man page again, and only then, consider using it, and even then,
    try avoiding it.

1. Use `PHP_*` macros in the PHP source, and `ZEND_*` macros in the Zend part of
    the source. Although the `PHP_*` macros are mostly aliased to the `ZEND_*`
    macros it gives a better understanding on what kind of macro you're calling.

1. Do not define functions that are not available. For instance, if a library is
    missing a function, do not define the PHP version of the function, and do
    not raise a run-time error about the function not existing. End users should
    use `function_exists()` to test for the existence of a function.

1. Prefer `emalloc()`, `efree()`, `estrdup()`, etc. to their standard C library
    counterparts. These functions implement an internal "safety-net" mechanism
    that ensures the deallocation of any unfreed memory at the end of a request.
    They also provide useful allocation and overflow information while running
    in debug mode.

    In almost all cases, memory returned to the engine must be allocated using
    `emalloc()`.

    The use of `malloc()` should be limited to cases where a third-party library
    may need to control or free the memory, or when the memory in question needs
    to survive between multiple requests.



# Resources
- https://www.php.net/manual/en/userlandnaming.rules.phpjs_conventions.asp
- https://www.php-fig.org/psr/psr-1/ 
- https://www.codementor.io/@veenitchauhan/basics-of-naming-conventions-for-php-developers-eliexmew6
- https://www.w3docs.com/learn-php/php-comments.html