Naming Parameters
=================

Beyond the obvious reason of readability, it is important to follow the
guidelines for parameter names because parameters are displayed in
documentation and in the designer when visual design tools provide
Intellisense and class browsing functionality.

**✓ DO** use camelCasing in parameter names.

**✓ DO** use descriptive parameter names.

**✓ CONSIDER** using names based on a parameter’s meaning rather than
the parameter’s type.

Naming Operator Overload Parameters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**✓ DO** use ``left`` and ``right`` for binary operator overload
parameter names if there is no meaning to the parameters.

**✓ DO** use ``value`` for unary operator overload parameter names if
there is no meaning to the parameters.

**✓ CONSIDER** meaningful names for operator overload parameters if
doing so adds significant value.

**X DO NOT** use abbreviations or numeric indices for operator overload
parameter names.
