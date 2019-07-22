2. Source file basics
======================

2.1. File name
--------------

The source file name consists of the case-sensitive name of the top-level class 
it contains (of which there is exactly one), plus the .java extension.

2.2. File encoding: UTF-8
-------------------------

Source files are encoded in UTF-8.

2.3. Special characters
-----------------------

2.3.1. Whitespace characters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Aside from the line terminator sequence, the ASCII horizontal space character 
(0x20) is the only whitespace character that appears anywhere in a source file. 
This implies that:

All other whitespace characters in string and character literals are escaped.
Tab characters are not used for indentation.

2.3.2. Special escape sequences
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For any character that has a special escape sequence (\\b, \\t, \\n, \\f, \\r, \\", \\' 
and \\\\), that sequence is used rather than the corresponding octal (e.g. \\012) 
or Unicode (e.g. \\u000a) escape.

2.3.3. Non-ASCII characters
^^^^^^^^^^^^^^^^^^^^^^^^^^^

For the remaining non-ASCII characters, either the actual Unicode character 
(e.g. ∞) or the equivalent Unicode escape (e.g. \\\\u221e) is used. The choice 
depends only on which makes the code easier to read and understand, although 
Unicode escapes outside string literals and comments are strongly discouraged.

.. note::
    
    In the Unicode escape case, and occasionally even when actual Unicode 
    characters are used, an explanatory comment can be very helpful.

Examples:

+------------------------------------------------------------+------------------------------------------+
| Example                                                    | Discussion                               |
+============================================================+==========================================+
| ``String unitAbbrev = "μs";``                              | | Best: perfectly clear even without a   |
|                                                            | | comment.                               |
+------------------------------------------------------------+------------------------------------------+
| ``String unitAbbrev = "\u03bcs"; // "μs"``                 | | Allowed, but there's no reason to do   |
|                                                            | | this.                                  |
+------------------------------------------------------------+------------------------------------------+
| ``String unitAbbrev = "\u03bcs"; // Greek letter mu, "s"`` | | Allowed, but awkward and prone to      |
|                                                            | | mistakes.                              |
+------------------------------------------------------------+------------------------------------------+
| ``String unitAbbrev = "\u03bcs";``                         | | Poor: the reader has no idea what this |
|                                                            | | is.                                    |
+------------------------------------------------------------+------------------------------------------+
| ``return '\ufeff' + content; // byte order mark``          | | Good: use escapes for non-printable    |
|                                                            | | characters, and comment if necessary.  |
+------------------------------------------------------------+------------------------------------------+

.. note::
    
    Never make your code less readable simply out of fear that some programs 
    might not handle non-ASCII characters properly. If that should happen, those 
    programs are broken and they must be fixed.