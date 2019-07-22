3. Source file structure
========================

A source file consists of, in order:

#. License or copyright information, if present
#. ``@fileoverview`` JSDoc, if present
#. ``goog.module`` statement
#. ``goog.require`` statements
#. The file’s implementation

Exactly one blank line separates each section that is present, except the file's 
implementation, which may be preceded by 1 or 2 blank lines.

3.1. License or copyright information, if present
-------------------------------------------------

If license or copyright information belongs in a file, it belongs here.

3.2. ``@fileoverview`` JSDoc, if present
----------------------------------------

See :ref:`75-Top/file-level` comments for formatting rules.

3.3. ``goog.module`` statement
------------------------------

All files must declare exactly one goog.module name on a single line: lines 
containing a goog.module declaration must not be wrapped, and are therefore an 
exception to the 80-column limit.

The entire argument to goog.module is what defines a namespace. It is the 
package name (an identifier that reflects the fragment of the directory 
structure where the code lives) plus, optionally, the main class/enum/interface 
that it defines concatenated to the end.

Example

.. code-block:: javascript

   goog.module('search.urlHistory.UrlHistoryService');

3.3.1. Hierarchy
^^^^^^^^^^^^^^^^
Module namespaces may never be named as a *direct* child of another module's 
namespace.

Illegal:

.. code-block:: javascript
   :class: not-recommended
   
    goog.module('foo.bar');   // 'foo.bar.qux' would be fine, though
    goog.module('foo.bar.baz');
    
The directory hierarchy reflects the namespace hierarchy, so that deeper-nested 
children are subdirectories of higher-level parent directories. Note that this 
implies that owners of “parent” namespace groups are necessarily aware of all 
child namespaces, since they exist in the same directory.

3.3.2. ``goog.setTestOnly``
^^^^^^^^^^^^^^^^^^^^^^^^^^^

The single ``goog.module`` statement may optionally be followed by a call to 
``goog.setTestOnly()``.

3.3.3. ``goog.module.declareLegacyNamespace``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The single ``goog.module`` statement may optionally be followed by a call to 
``goog.module.declareLegacyNamespace();``. Avoid 
``goog.module.declareLegacyNamespace()`` when possible.

Example:

.. code-block:: javascript

    goog.module('my.test.helpers');
    goog.module.declareLegacyNamespace();
    goog.setTestOnly();

``goog.module.declareLegacyNamespace`` exists to ease the transition from 
traditional object hierarchy-based namespaces but comes with some naming 
restrictions. As the child module name must be created after the parent 
namespace, this name **must not** be a child or parent of any other 
``goog.module`` (for example, ``goog.module('parent');`` and 
``goog.module('parent.child');`` cannot both exist safely, nor can 
``goog.module('parent');`` and ``goog.module('parent.child.grandchild');)``.

3.3.4. ES6 Modules
^^^^^^^^^^^^^^^^^^
Do not use ES6 modules yet (i.e. the export and import keywords), as their 
semantics are not yet finalized. Note that this policy will be revisited once 
the semantics are fully-standard.

3.4. ``goog.require`` statements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Imports are done with ``goog.require`` statements, grouped together immediately 
following the module declaration. Each ``goog.require`` is assigned to a single 
constant alias, or else destructured into several constant aliases. These 
aliases are the only acceptable way to refer to the required dependency, whether 
in code or in type annotations: the fully qualified name is never used except as 
the argument to ``goog.require.`` Alias names should match the final 
dot-separated component of the imported module name when possible, though 
additional components may be included (with appropriate casing such that the 
alias' casing still correctly identifies its type) if necessary to disambiguate, 
or if it significantly improves readability. ``goog.require`` statements may not 
appear anywhere else in the file.

If a module is imported only for its side effects, the assignment may be 
omitted, but the fully qualified name may not appear anywhere else in the file. 
A comment is required to explain why this is needed and suppress a compiler 
warning.

The lines are sorted according to the following rules: All requires with a name on the left hand side come first, sorted alphabetically by those names. Then destructuring requires, again sorted by the names on the left hand side. Finally, any goog.require calls that are standalone (generally these are for modules imported just for their side effects).

Tip: There’s no need to memorize this order and enforce it manually. You can rely on your IDE to report requires that are not sorted correctly.

If a long alias or module name would cause a line to exceed the 80-column limit, it must not be wrapped: goog.require lines are an exception to the 80-column limit.

Example:

const MyClass = goog.require('some.package.MyClass');
const NsMyClass = goog.require('other.ns.MyClass');
const googAsserts = goog.require('goog.asserts');
const testingAsserts = goog.require('goog.testing.asserts');
const than80columns = goog.require('pretend.this.is.longer.than80columns');
const {clear, forEach, map} = goog.require('goog.array');
/** @suppress {extraRequire} Initializes MyFramework. */
goog.require('my.framework.initialization');
Illegal:

const randomName = goog.require('something.else'); // name must match

const {clear, forEach, map} = // don't break lines
    goog.require('goog.array');

function someFunction() {
  const alias = goog.require('my.long.name.alias'); // must be at top level
  // …
}
3.4.1 goog.forwardDeclare
goog.forwardDeclare is not needed very often, but is a valuable tool to break circular dependencies or to reference late loaded code. These statements are grouped together and immediately follow any goog.require statements. A goog.forwardDeclare statement must follow the same style rules as a goog.require statement.

3.5 The file’s implementation
The actual implementation follows after all dependency information is declared (separated by at least one blank line).

This may consist of any module-local declarations (constants, variables, classes, functions, etc), as well as any exported symbols.