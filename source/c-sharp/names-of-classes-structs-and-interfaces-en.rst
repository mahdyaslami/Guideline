Names of Classes, Structs, and Interfaces
=========================================

The naming guidelines that follow apply to general type naming.

**✓ DO** name classes and structs with nouns or noun phrases, using
PascalCasing.

This distinguishes type names from methods, which are named with verb
phrases.

**✓ DO** name interfaces with adjective phrases, or occasionally with
nouns or noun phrases.

Nouns and noun phrases should be used rarely and they might indicate
that the type should be an abstract class, and not an interface.

**X DO NOT** give class names a prefix (e.g., “C”).

**✓ CONSIDER** ending the name of derived classes with the name of the
base class.

This is very readable and explains the relationship clearly. Some
examples of this in code are: ``ArgumentOutOfRangeException``, which is
a kind of ``Exception``, and ``SerializableAttribute``, which is a kind
of ``Attribute``. However, it is important to use reasonable judgment in
applying this guideline; for example, the ``Button`` class is a kind of
``Control`` event, although ``Control`` doesn’t appear in its name.

**✓ DO** prefix interface names with the letter I, to indicate that the
type is an interface.

For example, ``IComponent`` (descriptive noun),
``ICustomAttributeProvider`` (noun phrase), and ``IPersistable``
(adjective) are appropriate interface names. As with other type names,
avoid abbreviations.

**✓ DO** ensure that the names differ only by the “I” prefix on the
interface name when you are defining a class–interface pair where the
class is a standard implementation of the interface.

Names of Generic Type Parameters
--------------------------------

Generics were added to .NET Framework 2.0. The feature introduced a new
kind of identifier called *type parameter*.

**✓ DO** name generic type parameters with descriptive names unless a
single-letter name is completely self-explanatory and a descriptive name
would not add value.

**✓ CONSIDER** using ``T`` as the type parameter name for types with one
single-letter type parameter.

::

   public int IComparer<T> { ... }  
   public delegate bool Predicate<T>(T item);  
   public struct Nullable<T> where T:struct { ... }  

**✓ DO** prefix descriptive type parameter names with ``T``.

::

   public interface ISessionChannel<TSession> where TSession : ISession {  
       TSession Session { get; }  
   }  

**✓ CONSIDER** indicating constraints placed on a type parameter in the
name of the parameter.

For example, a parameter constrained to ``ISession`` might be called
``TSession``.

Names of Common Types
---------------------

**✓ DO** follow the guidelines described in the following table when
naming types derived from or implementing certain .NET Framework types.

+-----------------+----------------------------------------------------+
| Base Type       | Derived/Implementing Type Guideline                |
+=================+====================================================+
| ``System.Attrib | **✓ DO** add the suffix “Attribute” to names of    |
| ute``           | custom attribute classes.                          |
+-----------------+----------------------------------------------------+
| ``System.Delega | **✓ DO** add the suffix “EventHandler” to names of |
| te``            | delegates that are used in events. **✓ DO** add    |
|                 | the suffix “Callback” to names of delegates other  |
|                 | than those used as event handlers. **X DO NOT**    |
|                 | add the suffix “Delegate” to a delegate.           |
+-----------------+----------------------------------------------------+
| ``System.EventA | **✓ DO** add the suffix “EventArgs.”               |
| rgs``           |                                                    |
+-----------------+----------------------------------------------------+
| ``System.Enum`` | **X DO NOT** derive from this class; use the       |
|                 | keyword supported by your language instead; for    |
|                 | example, in C#, use the ``enum`` keyword. **X DO   |
|                 | NOT** add the suffix “Enum” or “Flag.”             |
+-----------------+----------------------------------------------------+
| ``System.Except | **✓ DO** add the suffix “Exception.”               |
| ion``           |                                                    |
+-----------------+----------------------------------------------------+
| ``IDictionary`` | **✓ DO** add the suffix “Dictionary.” Note that    |
| ``IDictionary<T | ``IDictionary`` is a specific type of collection,  |
| Key,TValue>``   | but this guideline takes precedence over the more  |
|                 | general collections guideline that follows.        |
+-----------------+----------------------------------------------------+
| ``IEnumerable`` | **✓ DO** add the suffix “Collection.”              |
| ``ICollection`` |                                                    |
| ``IList``       |                                                    |
| ``IEnumerable<T |                                                    |
| >``             |                                                    |
| ``ICollection<T |                                                    |
| >``             |                                                    |
| ``IList<T>``    |                                                    |
+-----------------+----------------------------------------------------+
| ``System.IO.Str | **✓ DO** add the suffix “Stream.”                  |
| eam``           |                                                    |
+-----------------+----------------------------------------------------+
| ``CodeAccessPer | **✓ DO** add the suffix “Permission.”              |
| mission IPermis |                                                    |
| sion``          |                                                    |
+-----------------+----------------------------------------------------+

Naming Enumerations
-------------------

Names of enumeration types (also called enums) in general should follow
the standard type-naming rules (PascalCasing, etc.). However, there are
additional guidelines that apply specifically to enums.

**✓ DO** use a singular type name for an enumeration unless its values
are bit fields.

**✓ DO** use a plural type name for an enumeration with bit fields as
values, also called flags enum.

**X DO NOT** use an “Enum” suffix in enum type names.

**X DO NOT** use “Flag” or “Flags” suffixes in enum type names.

**X DO NOT** use a prefix on enumeration value names (e.g., “ad” for ADO
enums, “rtf” for rich text enums, etc.).
