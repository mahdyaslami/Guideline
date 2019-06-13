Conventions
===========

## 1. Introduction

* **1.1** - The `standards` document describes the coding standards for the PHP
  projects. This document describes coding standards and conventions used in a
  project to make it more consistent and predictable. You are encouraged to
  follow them in your own code, but you don't need to.

## 2. Method Names

* **2.1** - When an object has a "main" many relation with related "things"
  (objects, parameters, ...), the method names are normalized:

    * **2.1.1** - ``get()``
    * **2.1.2** - ``set()``
    * **2.1.3** - ``has()``
    * **2.1.4** - ``all()``
    * **2.1.5** - ``replace()``
    * **2.1.6** - ``remove()``
    * **2.1.7** - ``clear()``
    * **2.1.8** - ``isEmpty()``
    * **2.1.9** - ``add()``
    * **2.1.10** - ``register()``
    * **2.1.11** - ``count()``
    * **2.1.12** - ``keys()``


* **2.2** - The usage of these methods is only allowed when it is clear that
  there is a main relation:

    * **2.2.1** - a ``CookieJar`` has many ``Cookie`` objects;

    * **2.2.2** - a Service ``Container`` has many services and many parameters
      (as services is the main relation, the naming convention is used for this
      relation);

    * **2.2.3** - a Console ``Input`` has many arguments and many options. There
      is no "main" relation, and so the naming convention does not apply.

    * **2.2.4** - For many relations where the convention does not apply, the
      following methods must be used instead (where ``XXX`` is the name of the
      related thing):

| Main Relation  | Other Relations   |
|----------------|-------------------|
| ``get()``      | ``getXXX()``      |
| ``set()``      | ``setXXX()``      |
| n/a            | ``replaceXXX()``  |
| ``has()``      | ``hasXXX()``      |
| ``all()``      | ``getXXXs()``     |
| ``replace()``  | ``setXXXs()``     |
| ``remove()``   | ``removeXXX()``   |
| ``clear()``    | ``clearXXX()``    |
| ``isEmpty()``  | ``isEmptyXXX()``  |
| ``add()``      | ``addXXX()``      |
| ``register()`` | ``registerXXX()`` |
| ``count()``    | ``countXXX()``    |
| ``keys()``     | n/a               |

***Note:*** While "setXXX" and "replaceXXX" are very similar, there is one
notable difference: "setXXX" may replace, or add new elements to the relation.
"replaceXXX", on the other hand, cannot add new elements. If an unrecognized key
is passed to "replaceXXX" it must throw an exception.

## 3. Deprecations

* **3.1** - From time to time, some classes and/or methods are deprecated in the framework; that happens when a feature implementation cannot be changed because of backward compatibility issues, but we still want to propose a "better" alternative. In that case, the old implementation can be **deprecated**.

* **3.2** - A feature is marked as deprecated by adding a ``@deprecated`` phpdoc to relevant classes, methods, properties, ... :

```php
/**
 * @deprecated since vendor-name/package-name 2.8, to be removed in 3.0. Use
 * XXX instead.
 */
```

* **3.3** - The deprecation message should indicate the version when the class/method was deprecated, the version when it will be removed, and whenever possible, how the feature was replaced.

* **3.4** - A PHP ``E_USER_DEPRECATED`` error must also be triggered to help people with the migration starting one or two minor versions before the version where the feature will be removed (depending on the criticality of the removal):

```php
@trigger_error('XXX() is deprecated since vendor-name/package-name 2.8 and
will be removed in 3.0. Use XXX instead.', E_USER_DEPRECATED);
```

* **3.5** - Without the [`@-silencing operator`][1]_, users would need to
  opt-out from deprecation notices. Silencing swaps this behavior and allows
  users to opt-in when they are ready to cope with them (by adding a custom
  error handler like the one used by the Web Debug Toolbar or by the PHPUnit
  bridge).

* **3.6** - When deprecating a whole class the ``trigger_error()`` call should
  be placed between the namespace and the use declarations, like in this example
  from [`ArrayParserCache`][2] :

```php
namespace Symfony\Component\ExpressionLanguage\ParserCache;

@trigger_error('The '.__NAMESPACE__.'\ArrayParserCache class is deprecated
since version 3.2 and will be removed in 4.0. Use the
Symfony\Component\Cache\Adapter\ArrayAdapter class instead.', E_USER_DEPRECATED);

use Symfony\Component\ExpressionLanguage\ParsedExpression;

/**
 * @author Adrien Brault <adrien.brault@gmail.com>
 *
 * @deprecated ArrayParserCache class is deprecated since version 3.2 and
 * will be removed in 4.0. Use the Symfony\Component\Cache\Adapter\ArrayAdapter
 * class instead.
 */
class ArrayParserCache implements ParserCacheInterface
```

[1]: https://php.net/manual/en/language.operators.errorcontrol.php
[2]: https://github.com/symfony/symfony/blob/3.2/src/Symfony/Component/ExpressionLanguage/ParserCache/ArrayParserCache.php

## 4. Reference

[symfony coding convention](https://github.com/symfony/symfony-docs/blob/master/contributing/code/conventions.rst)