Capitalization Conventions
==========================

:doc:`فارسی <capitalization-conventions>`

The guidelines in this chapter lay out a simple method for using case
that, when applied consistently, make identifiers for types, members,
and parameters easy to read.

Capitalization Rules for Identifiers
------------------------------------

To differentiate words in an identifier, capitalize the first letter of
each word in the identifier. Do not use underscores to differentiate
words, or for that matter, anywhere in identifiers. There are two
appropriate ways to capitalize identifiers, depending on the use of the
identifier:

-  PascalCasing

-  camelCasing

The PascalCasing convention, used for all identifiers except parameter
names, capitalizes the first character of each word (including acronyms
over two letters in length), as shown in the following examples:

| ``PropertyDescriptor``
| ``HtmlTag``

A special case is made for two-letter acronyms in which both letters are
capitalized, as shown in the following identifier:

``IOStream``

The camelCasing convention, used only for parameter names, capitalizes
the first character of each word except the first word, as shown in the
following examples. As the example also shows, two-letter acronyms that
begin a camel-cased identifier are both lowercase.

| ``propertyDescriptor``
| ``ioStream``
| ``htmlTag``

**✓ DO** use PascalCasing for all public member, type, and namespace
names consisting of multiple words.

**✓ DO** use camelCasing for parameter names.

The following table describes the capitalization rules for different
types of identifiers.

+------------+--------+------------------------------------------------+
| Identifier | Casing | Example                                        |
+============+========+================================================+
| Namespace  | Pascal | | ``namespace System.Security { ... }``        |
+------------+--------+------------------------------------------------+
| Type       | Pascal | | ``public class StreamReader { ... }``        |
+------------+--------+------------------------------------------------+
| Interface  | Pascal | | ``public interface IEnumerable { ... }``     |
+------------+--------+------------------------------------------------+
| Method     | Pascal | | ``public class Object {``                    |
|            |        | | ``public virtual string ToString();``        |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Property   | Pascal | | ``public class String {``                    |
|            |        | | ``public int Length { get; }``               |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Event      | Pascal | | ``public class Process {``                   |
|            |        | | ``public event EventHandler Exited;``        |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Field      | Pascal | | ``public class MessageQueue {``              |
|            |        | | ``public static readonly TimeSpan``          |
|            |        | | ``InfiniteTimeout;``                         |
|            |        | | ``}``                                        |
|            |        | | ``public struct UInt32 {``                   |
|            |        | | ``public const Min = 0;``                    |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Enum value | Pascal | | ``public enum FileMode {``                   |
|            |        | | ``Append,``                                  |
|            |        | | ``...``                                      |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+
| Parameter  | Camel  | | ``public class Convert {``                   |
|            |        | | ``public static int ToInt32(string value);`` |
|            |        | | ``}``                                        |
+------------+--------+------------------------------------------------+

Capitalizing Compound Words and Common Terms
--------------------------------------------

Most compound terms are treated as single words for purposes of
capitalization.

**X DO NOT** capitalize each word in so-called closed-form compound
words.

These are compound words written as a single word, such as endpoint. For
the purpose of casing guidelines, treat a closed-form compound word as a
single word. Use a current dictionary to determine if a compound word is
written in closed form.

=============== =============== ======================
Pascal          Camel           Not
=============== =============== ======================
``BitFlag``     ``bitFlag``     ``Bitflag``
``Callback``    ``callback``    ``CallBack``
``Canceled``    ``canceled``    ``Cancelled``
``DoNot``       ``doNot``       ``Don't``
``Email``       ``email``       ``EMail``
``Endpoint``    ``endpoint``    ``EndPoint``
``FileName``    ``fileName``    ``Filename``
``Gridline``    ``gridline``    ``GridLine``
``Hashtable``   ``hashtable``   ``HashTable``
``Id``          ``id``          ``ID``
``Indexes``     ``indexes``     ``Indices``
``LogOff``      ``logOff``      ``LogOut``
``LogOn``       ``logOn``       ``LogIn``
``Metadata``    ``metadata``    ``MetaData, metaData``
``Multipanel``  ``multipanel``  ``MultiPanel``
``Multiview``   ``multiview``   ``MultiView``
``Namespace``   ``namespace``   ``NameSpace``
``Ok``          ``ok``          ``OK``
``Pi``          ``pi``          ``PI``
``Placeholder`` ``placeholder`` ``PlaceHolder``
``SignIn``      ``signIn``      ``SignOn``
``SignOut``     ``signOut``     ``SignOff``
``UserName``    ``userName``    ``Username``
``WhiteSpace``  ``whiteSpace``  ``Whitespace``
``Writable``    ``writable``    ``Writeable``
=============== =============== ======================

Case Sensitivity
----------------

Languages that can run on the CLR are not required to support
case-sensitivity, although some do. Even if your language supports it,
other languages that might access your framework do not. Any APIs that
are externally accessible, therefore, cannot rely on case alone to
distinguish between two names in the same context.

**X DO NOT** assume that all programming languages are case sensitive.
They are not. Names cannot differ by case alone.
