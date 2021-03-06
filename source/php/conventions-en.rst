Conventions
===========

:doc:`فارسی <conventions>`

1. Introduction
---------------

#. The :doc:`standards-en` document describes the coding standards for the PHP projects.
   This document describes coding standards and conventions used in a project to
   make it more consistent and predictable.

2. Method Names
---------------

#. When an object has a "main" many relation with related "things" (objects, 
   parameters, ...), the method names are normalized:

  #. ``get()``
  #. ``set()``
  #. ``has()``
  #. ``all()``
  #. ``replace()``
  #. ``remove()``
  #. ``clear()``
  #. ``isEmpty()``
  #. ``add()``
  #. ``register()``
  #. ``count()``
  #. ``keys()``

#. The usage of these methods is only allowed when it is clear that there is a 
   main relation:

  #. a ``CookieJar`` has many ``Cookie`` objects;

  #. For many relations where the convention does not apply, the following 
     methods must be used instead (where ``XXX`` is the name of the related 
     thing):

+----------------+-------------------+
| Main Relation  | Other Relations   |
+================+===================+
| ``get()``      | ``getXXX()``      |
+----------------+-------------------+
| ``set()``      | ``setXXX()``      |
+----------------+-------------------+
| n/a            | ``replaceXXX()``  |
+----------------+-------------------+
| ``has()``      | ``hasXXX()``      |
+----------------+-------------------+
| ``all()``      | ``getXXXs()``     |
+----------------+-------------------+
| ``replace()``  | ``setXXXs()``     |
+----------------+-------------------+
| ``remove()``   | ``removeXXX()``   |
+----------------+-------------------+
| ``clear()``    | ``clearXXX()``    |
+----------------+-------------------+
| ``isEmpty()``  | ``isEmptyXXX()``  |
+----------------+-------------------+
| ``add()``      | ``addXXX()``      |
+----------------+-------------------+
| ``register()`` | ``registerXXX()`` |
+----------------+-------------------+
| ``count()``    | ``countXXX()``    |
+----------------+-------------------+
| ``keys()``     | n/a               |
+----------------+-------------------+


.. note:: 
   While "setXXX" and "replaceXXX" are very similar, there is one notable 
   difference: "setXXX" may replace, or add new elements to the relation. 
   "replaceXXX", on the other hand, cannot add new elements. If an unrecognized 
   key is passed to "replaceXXX" it must throw an exception.

.. _php-conventions-deprecations-en:

3. Deprecations
---------------

#. From time to time, some classes and/or methods are deprecated in the 
   framework; that happens when a feature implementation cannot be changed 
   because of backward compatibility issues, but we still want to propose a 
   "better" alternative. In that case, the old implementation can be 
   **deprecated**.

#. A feature is marked as deprecated by adding a ``@deprecated`` phpdoc to 
   relevant classes, methods, properties, ... :

.. code-block:: php

    <?php
    
    /**
     * @deprecated since vendor-name/package-name 2.8, to be removed in 3.0. Use
     * XXX instead.
     */


#. The deprecation message should indicate the version when the class/method was
   deprecated, the version when it will be removed, and whenever possible, how 
   the feature was replaced.

#. A PHP ``E_USER_DEPRECATED`` error must also be triggered to help people with 
   the migration starting one or two minor versions before the version where the
   feature will be removed (depending on the criticality of the removal):
   
.. code-block:: php

    <?php
    
    @trigger_error('XXX() is deprecated since vendor-name/package-name 2.8 and
    will be removed in 3.0. Use XXX instead.', E_USER_DEPRECATED);

#. Without the `@-silencing operator`_, users would need to opt-out from 
   deprecation notices. Silencing swaps this behavior and allows users to opt-in
   when they are ready to cope with them (by adding a custom error handler like 
   the one used by the Web Debug Toolbar or by the PHPUnit bridge).

#. When deprecating a whole class the ``trigger_error()`` call should
   be placed between the namespace and the use declarations, like in this example
   from `ArrayParserCache`_:

.. code-block:: php

    <?php

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

.. _@-silencing operator: https://php.net/manual/en/language.operators.errorcontrol.php
.. _ArrayParserCache: https://github.com/symfony/symfony/blob/3.2/src/Symfony/Component/ExpressionLanguage/ParserCache/ArrayParserCache.php

.. rubric:: References

`symfony coding convention <https://github.com/symfony/symfony-docs/blob/master/contributing/code/conventions.rst>`_